
.. include:: ../../Includes.txt

==================================================
Files and Folders
==================================================

:ref:`Sitemap <sitemap>`

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


/home/mbless/HTDOCS/github.com/
-------------------------------
Data cloned from http://github.com/ resides here. The folder structure of
the source site is replicated. See http://docs.typo3.org/~mbless/github.com/.


/home/mbless/public_html/
-------------------------
This is the webroot folder of http://docs.typo3.org/.


The "Glue Pages
---------------
These are the content pages::

  # glue pages content
  /home/mbless/HTDOCS/git.typo3.org/Documentation/DocsTypo3Org.git

The make script::

  # glue pages make
  /home/mbless/HTDOCS/git.typo3.org/Documentation/DocsTypo3Org.git.make/cron_rebuild.sh

The destination directory::

  /home/mbless/public_html/


The "Make" directory of a documentation project
===============================================

Each documentation project is cloned to its own folder. If the project has different
branches the branch is checked out *in that folder* when needed. Example::

  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git/

See the `folder <http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git/>`__.

Currently each branch has its own "build folder". Examples:
`TypoScript (master)<http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make/>`__,
`TypoScript 6.1<http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make/>`__,
`TypoScript 6.1<http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_6.1/>`__,
`TypoScript 6.0<http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_6.0/>`__,
`TypoScript 4.7<http://docs.typo3.org/~mbless/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_4.7/>`__.

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












:ref:`Sitemap <sitemap>`