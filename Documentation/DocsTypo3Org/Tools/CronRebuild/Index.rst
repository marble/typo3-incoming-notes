
.. include:: ../../../Includes.txt

==================================================
Build a single documentation project
==================================================

Rendered: |today|

**Jump up and down on this page:**

.. contents::
   :local:


Makedir
=======

Starting point of a build process is a ``makedir`` folder with several
files in it that control the build process. More files will be placed
there during the build process and serve as logfiles.

::


   ((WIP))
   cron_rebuild.sh
      Is a symlink to the one and only common build script.

   conf.py

   cron_rebuild.checksum
      A generated checksum of the documentation subtree in the
      project. Used to decide wether a new build is needed.

   warnings.txt
      Very important! Here you find the Sphinx messages.

   request_rebuild.php
      Run this file or request it from the web to create the
      necessary REBUILD_REQUESTED files that are used to
      indicate that a rebuild should be done.

   REBUILD_REQUESTED

   ...

..

cron_rebuild.conf
=================

Example file ``cron_rebuild.conf``
----------------------------------

:file:`cron_rebuild.conf` is a configuration file, format is bash, included (=sourced) by cron_rebuild.sh
to know what to do (name of the project, where it is located, where to publish to, ...).
In case of [git-TERautomation], it is dynamically generated for the currently-processed extension.

::

   PROJECT=sphinx
   VERSION=1.3.1

   # Where to publish documentation
   BUILDDIR=/home/mbless/public_html/typo3cms/extensions/sphinx/$VERSION

   # If GITURL is empty then GITDIR is expected to be "ready" to be processed
   GITURL=git://git.typo3.org/TYPO3CMS/Extensions/sphinx.git
   GITDIR=/home/mbless/HTDOCS/git.typo3.org/TYPO3v4/Extensions/sphinx.git
   GITBRANCH=$VERSION

   ((# Path to the documentation within the Git repository)) should be named:
   # Path to the documentation start folder
   T3DOCDIR=$GITDIR/Documentation

   # Packaging information
   PACKAGE_ZIP=1
   PACKAGE_KEY=typo3cms.extensions.sphinx
   PACKAGE_LANGUAGE=default

..

Definitions in ``cron_rebuild.conf``
------------------------------------

::

   PROJECT
      Example:
         sphinx

   VERSION
      Example:
         1.2.3 | latest | ...
      The final build will end up in a folder with that name.

   BUILDDIR
      Example:
         /home/mbless/public_html/typo3cms/extensions/sphinx/$VERSION
      Where to publish documentation

      Important: Must end with .../$PROJECT/$VERSION

   GITURL
      Example:
         git://git.typo3.org/TYPO3CMS/Extensions/sphinx.git
      Where to clone the data from.
      Note: If GITURL is not set it is assumed that the data in GITDIR
      is ready and no ``git pull`` operation will be done.

   GITDIR
      Example:
         /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/Extensions/sphinx.git
      Absolute path to the clone of the project.

      Note: As a convention the folder names of these local copies
            have '.git' at the end.

   GITBRANCH
      Example:
         master | 6-2 | 0a1b2c3d | ...
      A valid argument for a ``git checkout`` command. So it can be
      a branch name, a tag or a revision number.

   PACKAGE_ZIP
      Example:
         1 | 0 | <missing>
      Whether a package is to be created.

   PACKAGE_KEY
      Example:
         typo3cms.extensions.sphinx
      The PACKAGE_KEY is only used if PACKAGE_ZIP is given and TRUE.
      In this case subroutine ``packagedocumentation`` is called.

   PACKAGE_LANGUAGE
      Example:
         default | fr | fr_CH | anything | ...
      Is always used!
      The language can for example be given as 'de' or 'de_XXX' or 'something'.
      It will then be forced to become one of the Sphinx languages
      or to become 'default':

      SPHINX_LANGUAGES="bn ca cs da de es et eu fa fi fr hr hu it ja ko
         lt lv nb_NO ne nl pl pt_BR ru sk sl sv tr uk_UA zh_CN zh_TW "

   T3DOCDIR
      Example:
         $GITDIR/Documentation
      This is the absolute path to the folder that contains the ``master_doc``.
      If there is no $GITDIR/Documentation/Index.rst but we have a
      $GITDIR/README.rst then T3DOCDIR will be set equal to GITDIR.

..

cron_rebuild.sh
===============

This is the script that actually builds a single documentation project
on the server.

Steps
-----

::

   Check REBUILD_REQUESTED
      Do nothing if the file doesn't exist.

   Call projectinfo2stdout
      Echo some parameters to stdout.

   If we have $GITURL:
      Checkout branch $GITBRANCH
      Pull from repository $GITURL

   Call rebuildneeded
      Create md5 checksum over documentation part of the repository
      Compare with file build.checksum
      if file is older than 12 hours or different:
        continue
      else:
        exit

   Run check_include_files.py as a safety check
      Here we check by reading the ReST sources what ReST files will be
      included. Process information goes to included-file-check.log.txt.
      Stop everything if a file from outside the project is detected.

   Temporarily remove localization directories
      from Sphinx to prevent warnings with unreferenced files and
      duplicate labels

   Render the documentation like
      BACKUP_T3DOCDIR=$T3DOCDIR
      renderdocumentation $T3DOCDIR $T3DOCDIR 0

..

Steps in subroutine ``renderdocumentation``
-------------------------------------------

Steps in subroutine ``renderdocumentation`` in ``cron_rebuild.sh``::

   renderdocumentation  BASE_DIR  T3DOCDIR  IS_TRANSLATION
      find SPHINXCODE from Sphinx languages and $PACKAGE_LANGUAGE
      export SPHINXCODE as LANGUAGE if given and not 'default'
      prepare Settings.yml if IS_TRANSLATION
      make Sphinx HTML in a tempdir /tmp/...
      call compilepdf
      call packagedocumentation if $PACKAGE_ZIP==1
      make Sphinx singlefile HTML
      symlink the $MAKE_DIRECTORY to $BUILD_DIR/_make
      make README.html accessible as Index.html if necessary
      switch the newley rendered documentation with the public one

..

Steps in subroutine ``compilepdf``
----------------------------------

Steps in subroutine ``compilepdf`` in ``renderdocumentation`` in ``cron_rebuild.sh``::

   ...

..

Variables in ``cron_rebuild.sh``
--------------------------------

::

   BIN_DIRECTORY
      Absolute path to the script folder as given by the cron_rebuild.sh script.
      There should be:
         $BIN_DIRECTORY/cron_rebuild.sh
         $BIN_DIRECTORY/check_include_files.py

   ...

..
