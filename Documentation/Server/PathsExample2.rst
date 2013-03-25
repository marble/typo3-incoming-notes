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


Example of Github hook data "payload"
=====================================

::

  {
      "commits": [{
              "timestamp": "2013-03-22T03:55:13-07:00",
              "message": "Working on Github automisation",
              "committer": {
                  "username": "marble",
                  "email": "martin.bless@gmail.com",
                  "name": "Martin Bless"
              },
              "url": "https://github.com/marble/typo3-incoming-notes/commit/4d80782570b50d1ecfebb00d8e126a9e388150d1",
              "distinct": true,
              "removed": ["Documentation/Server/scratch.rst"],
              "modified": [],
              "id": "4d80782570b50d1ecfebb00d8e126a9e388150d1",
              "added": ["Documentation/Server/PathsExample1.rst", "Documentation/Server/PathsExample2.rst"],
              "author": {
                  "username": "marble",
                  "email": "martin.bless@gmail.com",
                  "name": "Martin Bless"
              }
          }
      ],
      "repository": {
          "size": 496,
          "language": "Python",
          "has_downloads": true,
          "watchers": 0,
          "forks": 0,
          "url": "https://github.com/marble/typo3-incoming-notes",
          "stargazers": 0,
          "fork": false,
          "owner": {
              "email": "m.bless@gmx.de",
              "name": "marble"
          },
          "description": "While I'm working on TYPO3 documentation I'm trying to take notes about the what when why how and so on. This is the first place these notes go to.",
          "has_wiki": true,
          "master_branch": "master",
          "created_at": 1363943089,
          "private": false,
          "id": 8948375,
          "name": "typo3-incoming-notes",
          "pushed_at": 1363949726,
          "open_issues": 0,
          "has_issues": true
      },
      "compare": "https://github.com/marble/typo3-incoming-notes/compare/fd337a7ee0c3...4d80782570b5",
      "before": "fd337a7ee0c3b91998024ffe0cd6d82508b6dc43",
      "ref": "refs/heads/master",
      "created": false,
      "head_commit": {
          "timestamp": "2013-03-22T03:55:13-07:00",
          "message": "Working on Github automisation",
          "committer": {
              "username": "marble",
              "email": "martin.bless@gmail.com",
              "name": "Martin Bless"
          },
          "url": "https://github.com/marble/typo3-incoming-notes/commit/4d80782570b50d1ecfebb00d8e126a9e388150d1",
          "distinct": true,
          "removed": ["Documentation/Server/scratch.rst"],
          "modified": [],
          "id": "4d80782570b50d1ecfebb00d8e126a9e388150d1",
          "added": ["Documentation/Server/PathsExample1.rst", "Documentation/Server/PathsExample2.rst"],
          "author": {
              "username": "marble",
              "email": "martin.bless@gmail.com",
              "name": "Martin Bless"
          }
      },
      "after": "4d80782570b50d1ecfebb00d8e126a9e388150d1",
      "pusher": {
          "email": "m.bless@gmx.de",
          "name": "marble"
      },
      "forced": false,
      "deleted": false
  }

