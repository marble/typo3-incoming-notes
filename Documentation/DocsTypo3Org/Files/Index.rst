
.. include:: ../../Includes.txt

==================================================
Files and Folders
==================================================

Rendered: |today|

**Jump up and down on this page:**

.. contents::
   :local:


What is where?
==============


/home/mbless/
-------------

This is where everything starts. Forget about the user name - it should be
thought of as the "docs.typo3.org"-user.


/home/mbless/HTDOCS/
--------------------
Directory listing is turned on. This is the webroot folder of

- http://docs.typo3.org/~mbless/ alias
- http://srv123.typo3.org/~mbless/

It is a big public collection of data and stuff like a repository. It is not
versioned as a whole.


/home/mbless/HTDOCS/git.typo3.org/
----------------------------------
Data cloned from http://git.typo3.org/ resides here. The folder structure of
the source site is replicated. See http://docs.typo3.org/~mbless/git.typo3.org/.


/home/mbless/HTDOCS/svn.typo3.org/
----------------------------------
Data checked out from http://svn.typo3.org/ resides here. The folder structure of
the source site should be replicated. See http://docs.typo3.org/~mbless/svn.typo3.org/.
It looks like we don't use and don't need this tree any more.


/home/mbless/HTDOCS/github.com/
-------------------------------
Data cloned from http://github.com/ resides here. The folder structure of
the source site is replicated. See http://docs.typo3.org/~mbless/github.com/.


/home/mbless/public_html/
-------------------------
This is the webroot folder of http://docs.typo3.org/.


The "Glue Pages"
----------------
The "glue pages" contain the editorial content on docs.typo3.org.
They are made up from just a normal Sphinx documentation project itself
with carefully chosen filenames so that the fit in the "empty spots"
between the normal manuals.

.. attention:: Unfortunately the glue pages are not in a Git repository.
   This should be changed!

This is the `glue pages content <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/DocsTypo3Org.git/Documentation/>`__::

  # glue pages content
  /home/mbless/HTDOCS/git.typo3.org/Documentation/DocsTypo3Org.git

The `make folder <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/DocsTypo3Org.git.make/>`__
with the file :file:`request_rebuild.php` to request a rebuild::

  # glue pages make
  /home/mbless/HTDOCS/git.typo3.org/Documentation/DocsTypo3Org.git.make/cron_rebuild.sh

The destination directory::

  /home/mbless/public_html/


The "Make" directory of a documentation project
===============================================

Each documentation project is cloned to its own folder. If the project has different
branches the branch is checked out *in that folder* when needed.
See the clone of the
`TypoScript reference <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git/>`__
as an example. It's here::

  # startdir              source site     relative path                   project folder
  # /home/mbless/HTDOCS/  git.typo3.org/  Documentation/TYPO3/Reference/  Typoscript.git

  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git/


Additionally there is a "build folder" for each branch. Examples:
`TypoScript (master) <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make/>`__,
`TypoScript 6.1 <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_6.1/>`__,
`TypoScript 6.0 <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_6.0/>`__,
`TypoScript 4.7 <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_4.7/>`__.

The build folder contains a mixture of configuration files and log files.


Configuration files
-------------------

- cron_rebuild.conf
- cron_rebuild.sh
- conf.py
- Makefile
- build.checksum


Trigger file
------------

- request_rebuild.php


Log files
---------

10_conf_py.yml
~~~~~~~~~~~~~~
Represents the initial state of the Sphinx configuration data and contains
built in values plus merged values from 'conf.py'.

20_GlobalSettings.yml
~~~~~~~~~~~~~~~~~~~~~
Represents global settings that have been found during the last build.

30_Settings.yml
~~~~~~~~~~~~~~~
Represents the local settings of this documentation project that have
been found during the last build.

10+20_conf.py.yml
~~~~~~~~~~~~~~~~~
This show an intermediate result after applying th global settings.

10+20+30_conf.py.yml
~~~~~~~~~~~~~~~~~~~~
This represents the final settings that had been used during the last build.

dirs-of-last-build.txt
~~~~~~~~~~~~~~~~~~~~~~
A file that summarizes which directories had bee involved during
the last build.

included-files-check.log.txt
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This is written by XXX ...



Stash file
----------

The current :file:`objects.inv` is copied here before doing a "make clean" XXX ...


((find correct headline))
=========================

manuals.json
------------
http://docs.typo3.org/typo3cms/extensions/manuals.json

extensions.js
-------------
http://docs.typo3.org/typo3cms/extensions/extensions.js

extensions-search.js
--------------------
http://docs.typo3.org/typo3cms/extensions/extensions-search.js


::

   $GLOBALS['config']['DIR']['work']
      '/home/mbless/HTDOCS/github.com/xperseguers/RENDER-DOC/'
         Path to a working directory for this extension. Will hold
	     cache files and queue of conversion jobs

   $GLOBALS['config']['DIR']['publish']
      '/home/mbless/public_html/typo3cms/extensions/'
         Publish to http://docs.typo3.org/typo3cms/extensions/<ext-key>/

   '/home/mbless/public_html/typo3cms/extensions/manuals.json'




   $GLOBALS['config']['DIR']['scripts']
      '/home/mbless/scripts/'
         Path to the local clone of git project
		 https://github.com/marble/typo3-docs-typo3-org-resources
		 actually: userroot/scripts/

   $GLOBALS['config']['BIN']['t3xutils.phar']
      '/home/mbless/HTDOCS/github.com/xperseguers/RENDER-DOC/bin/t3xutils.phar',
         Path to t3xutils.phar, available off
         https://github.com/etobi/Typo3ExtensionUtils

..

documents.txt
-------------
The server team has been pointed to ``documents.txt`` to use it as input
list for the Solr indexer:

- http://docs.typo3.org//typo3cms/documents.txt
- /home/mbless/public_html/typo3cms/documents.txt


documents.json
--------------
What's this?:

- /home/mbless/public_html/typo3cms/documents.json
- http://docs.typo3.org//typo3cms/documents.json
