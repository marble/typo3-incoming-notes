.. ==================================================
.. FOR YOUR INFORMATION 
.. --------------------------------------------------
.. -*- coding: utf-8 -*- with BOM.  ÄÖÜäöüß

.. include:: ../Includes.txt


=================================
Paths example 2
=================================


Clone github repository
=======================

::

    mbless@srv123:~$ cd ~
    $ git clone https://github.com/marble/typo3-incoming-notes    /home/mbless/HTDOCS/github.com/marble/typo3-incoming-notes.git


Create a ".git.make" folder
===========================

::

    $ cp -rp /home/mbless/HTDOCS/github.com/make-folder-template  /home/mbless/HTDOCS/github.com/marble/typo3-incoming-notes.git.make


Edit files in copied ".git.make" folder
=======================================
    
In conf.py::

  # do a global string replace
  # old string: '../REST-SOURCE-FOLDER.git/Documentation'
  # new string: '../typo3-incoming-notes.git/Documentation'

  
In Makefile::

  # do a global string replace
  # old string: '../REST-SOURCE-FOLDER.git/Documentation'
  # new string: '../typo3-incoming-notes.git/Documentation'

  # do a global string replace for /home/mbless/public_html/PRODUCT/drafts/github/GITHUB_USER/MANUAL_NAME
  # old string:  /PRODUCT/drafts/github/GITHUB_USER/MANUAL_NAME
  # new string:  /typo3cms/drafts/github/marble/IncomingNotes
  


In cron_rebuild.sh::

  # do a global string replace
  # old string: '/GITHUB_USER/REPOSITORY_NAME.git'
  # new string: '/marble/typo3-incoming-notes.git'


Make manual known to cron job
=============================

Add this line::

    /home/mbless/HTDOCS/github.com/marble/typo3-incoming-notes.git.make/cron_rebuild.sh

to file :file:`/home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild.sh`


Make manual known to hook processor
===================================

Add this line::

    'https://github.com/marble/typo3-incoming-notes.git' => 'http://docs.typo3.org/~mbless/github.com/marble/typo3-incoming-notes.git.make/request_rebuild.php',

to file :file:`/home/mbless/public_html/services/handle_github_post_receive_hook.php`
