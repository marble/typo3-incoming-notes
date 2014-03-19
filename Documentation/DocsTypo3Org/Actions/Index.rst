
.. include:: ../../Includes.txt

==================================================
Actions
==================================================

:ref:`Sitemap <sitemap>`


CRON
====

Cronjob Overview
----------------

It's run as user 'mbless'. The console output of each run is send to `typo3logs@mbless.de`_.
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

A lockfile will be created and remove at the end of the job. A lockfile that is older than
twelve hours will always be ignored and removed. In the course of this script several calls will
be made.

Several build files of individual documentation projects will be called directly from here.
For example::

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

The build of the so called "glue pages" is triggered from here::

  # glue pages ...
  /home/mbless/HTDOCS/git.typo3.org/Documentation/DocsTypo3Org.git.make/cron_rebuild.sh

A call is made to the following. It is a script that automates the creation of new
documentation projects that are hosted on Github. See XXX how this works::

  /home/mbless/HTDOCS/github.com/marble/typo3-manage-github-repositories.git/cronjob-process-incoming.sh


Another is made to the following. It is the place where newer documentation project are added::

  # 2nd file ...
  /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild_included.sh

And these scripts are called as well one after the other::

  # Extensions ...
  /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/cron_rebuild.sh

  # Forge ...
  /home/mbless/HTDOCS/svn.typo3.org/TYPO3v4/cron_rebuild.sh

  # sysext/* extensions
  /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/Extensions/TYPO3.CMS.ALL-SYSEXT.master.make/cron_rebuild.sh


:ref:`Sitemap <sitemap>`
