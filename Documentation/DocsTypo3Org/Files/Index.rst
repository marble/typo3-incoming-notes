
.. include:: ../../Includes.txt

==================================================
Files and Folders
==================================================

:ref:`Sitemap <sitemap>`

What is where?
==============


/home/mbless/
-------------

This is where everything starts. Forget about the user name - it should be read as "docstypo3org".


/home/mbless/HTDOCS/
--------------------

Directory listing is turned on. Currently it is just a huge public collection of data and stuff.
It is available as http://docs.typo3.org/~mbless/ or http://srv123.typo3.org/~mbless/.


/home/mbless/HTDOCS/git.typo3.org/
----------------------------------

Data cloned from http://git.typo3.org/ resides here. It should replicate the folder structure of
the source repositories. See http://docs.typo3.org/~mbless/git.typo3.org/.


/home/mbless/HTDOCS/github.com/
-------------------------------

Data cloned from http://github.com/ resides here. It should replicate the folder structure of
the source repositories. See http://docs.typo3.org/~mbless/github.com/.


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

Trigger file















:ref:`Sitemap <sitemap>`