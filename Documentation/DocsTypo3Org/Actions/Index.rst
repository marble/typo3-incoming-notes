
.. include:: ../../Includes.txt

==================================================
Actions
==================================================

Rendered: |today|

**Jump up and down on this page:**

.. contents::
   :local:

.. highlight:: bash


Various scripts
===============

- `/home/mbless/scripts/`__

- `/home/mbless/HTDOCS/github.com/xperseguers/TYPO3.docs.ter-automation/`__ and at Github__.

- [git-TERautomation]::

    /home/mbless/HTDOCS/github.com/xperseguers/
       RENDER-DOC/
          force-render.sh   ::   helper script to manually enqueue a
                                 given extension+version's manual
          bin/
             t3xutils.phar

          queue/   ::  unpacked extensions (full) waiting to be rendered,
                       populated by TerTask.php, emptied by RenderTask.php

          render/  ::  working directory, processed by RenderTask.php,
                       see "directory for build" below

  * `RENDER-DOC/`__
  * `RENDER-DOC/queue/`__
  * `RENDER-DOC/render/`__

__ https://github.com/marble/typo3-docs-typo3-org-resources/tree/master/userroot/scripts
__ http://docs.typo3.org/~mbless/github.com/xperseguers/TYPO3.docs.ter-automation/
__ https://github.com/xperseguers/TYPO3.docs.ter-automation
__ http://docs.typo3.org/~mbless/github.com/xperseguers/RENDER-DOC/
__ http://docs.typo3.org/~mbless/github.com/xperseguers/RENDER-DOC/queue/
__ http://docs.typo3.org/~mbless/github.com/xperseguers/RENDER-DOC/render/



CRON
====

Cronjob Overview
----------------

It's run as user 'mbless'. The console output of each run is send to typo3logs@mbless.de.
Details::

  mbless@srv123:~$ crontab -l

  # 45    */4 * * * /home/mbless/HTDOCS/render-ter-extensions/010_cronjob_get_new_from_ter.py
    10,40 *   * * * /usr/bin/php /home/mbless/HTDOCS/github.com/xperseguers/TYPO3.docs.ter-automation/Classes/Task/TerTask.php    >/dev/null 2>&1
    */30  *   * * * /usr/bin/php /home/mbless/HTDOCS/github.com/xperseguers/TYPO3.docs.ter-automation/Classes/Task/RenderTask.php >/dev/null 2>&1
    */5   *   * * * /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild.sh

Cronjob every five minutes
--------------------------

Runs::

  /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild.sh

This is mainly a dispatcher that makes sure that in the end each individual
:file:`cron_rebuild.sh` file of each documentation project is being called. Only one such process at a time
should be running on the server. To achieve that a lockfile is created at the beginning of the
job. Normally it is removed at the end of the job. In case something goes wrong and the lock file
persists building documentation is being skipped. To provide a "self healing" recovery from that misery
any lockfile that is older than twelve hours will be ignored and removed automatically.

Several build files of individual documentation projectss will be called directly from this starter script.
Additionally some more scripts are called that call other scripts before returning.

For example these "final build scripts" are directly called from here::

  # Guides:
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Extbase.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/FrontendLocalization.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Installation.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Installation.git.make_4.5/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Installation.git.make_4.6/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Installation.git.make_4.7/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Installation.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Installation.git.make_6.1/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Maintenance.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Guide/Security.git.make/cron_rebuild.sh

One of these "final build scripts" is the one that builds the so called "glue pages"::

  # glue pages ...
  /home/mbless/HTDOCS/git.typo3.org/Documentation/DocsTypo3Org.git.make/cron_rebuild.sh

A call is made to the following. It is a script that automates the creation of new
documentation projects that are hosted on Github. See XXX how this works::

  /home/mbless/HTDOCS/github.com/marble/typo3-manage-github-repositories.git/cronjob-process-incoming.sh

A bunch of calls is bundled in :file:`cron_rebuild_included.sh`. New documentation projects like those from Github are currently
added at the end of this file::

  # 2nd file ...
  /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild_included.sh

In the further course of program execution more scripts are processed. They watch
there own semaphore file :file:`REBUILD_REQUESTED' to decide if anything has to be
done at all. And they use ther own lockfile :file:`cron_rebuild.lockfile`::

  # Extensions ...
  # using: /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/REBUILD_REQUESTED
  # using: /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/cron_rebuild.lockfile
  /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/cron_rebuild.sh

  # Forge ...
  # not active any more
  # /home/mbless/HTDOCS/svn.typo3.org/TYPO3v4/cron_rebuild.sh

  # sysext/* extensions
  /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/Extensions/TYPO3.CMS.ALL-SYSEXT.master.make/cron_rebuild.sh

..

