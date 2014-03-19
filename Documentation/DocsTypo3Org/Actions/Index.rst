
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

Another documentation project that is called from here are the so called "glue pages"::

  # glue pages ...
  /home/mbless/HTDOCS/git.typo3.org/Documentation/DocsTypo3Org.git.make/cron_rebuild.sh

A call is made to::

  /home/mbless/HTDOCS/github.com/marble/typo3-manage-github-repositories.git/cronjob-process-incoming.sh

This is a script that automates the creation of new documentation projects that are hosted on Github.
See XXX how this works.






:ref:`Sitemap <sitemap>`





  # 2nd file ...
  /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild_included.sh

  # Extensions ...
  /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/cron_rebuild.sh

  # Forge ...
  /home/mbless/HTDOCS/svn.typo3.org/TYPO3v4/cron_rebuild.sh

  # sysext/* extensions
  /home/mbless/HTDOCS/git.typo3.org/TYPO3v4/Extensions/TYPO3.CMS.ALL-SYSEXT.master.make/cron_rebuild.sh

  # verified: 1 x Example/ working
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Example/ExtensionManual.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Example/OfficialManual.git.make/cron_rebuild.sh

  # book: should work
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Book/ExtbaseFluid.git.make/cron_rebuild.sh

  # verified: 5 x Guide/ working
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

  # verified: 9 x Reference/ working
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CodingGuidelines.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CodingGuidelines.git.make_4.5/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CodingGuidelines.git.make_4.6/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CodingGuidelines.git.make_4.7/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CodingGuidelines.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CodingGuidelines.git.make_6.1/cron_rebuild.sh

  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CoreApi.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CoreApi.git.make_4.5/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CoreApi.git.make_4.6/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CoreApi.git.make_4.7/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CoreApi.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/CoreApi.git.make_6.1/cron_rebuild.sh

  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/FileAbstractionLayer.git.make/cron_rebuild.sh
  #/home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/FileAbstractionLayer.git/cron_rebuild.sh
  #/home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/IndexedSearch.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/InsideTypo3.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Skinning.git.make/cron_rebuild.sh

  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Tca.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Tca.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Tca.git.make_6.1/cron_rebuild.sh

  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Tsconfig.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Tsconfig.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Tsconfig.git.make_6.1/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Typo3Services.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_4.7/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/Typoscript.git.make_6.1/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/TyposcriptSyntax.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/TyposcriptSyntax.git.make_4.7/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/TyposcriptSyntax.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Reference/TyposcriptSyntax.git.make_6.1/cron_rebuild.sh

  # verified: 4 x Tutorial/ working
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Tutorial/Editors.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Tutorial/Editors.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Tutorial/GettingStarted.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Tutorial/Templating.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Tutorial/Typoscript45Minutes.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Tutorial/Typoscript45Minutes.git.make_6.0/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Documentation/TYPO3/Tutorial/Typoscript45Minutes.git.make_6.1/cron_rebuild.sh


  /home/mbless/HTDOCS/git.typo3.org/Packages/TYPO3.Flow.git.make/cron_rebuild.sh
  /home/mbless/HTDOCS/git.typo3.org/Packages/TYPO3.Neos.git.make/cron_rebuild.sh

  # # github.com
  # /home/mbless/HTDOCS/github.com/froemken/typo3-extbase-guide.git.make/cron_rebuild.sh
  # /home/mbless/HTDOCS/github.com/froemken/typo3-fluid-guide.git.make/cron_rebuild.sh
  # #/home/mbless/HTDOCS/github.com/marble/notes-about-TYPO3-ReST-stuff.git.make.DocumentationContributionGuide/cron_rebuild.sh
  # /home/mbless/HTDOCS/github.com/marble/typo3-incoming-notes.git.make/cron_rebuild.sh

  cd /home/mbless/HTDOCS/git.typo3.org/Documentation/
  rm -I REBUILD_REQUESTED
  rm -I "$lockfile"
fi
popd   >/dev/null
