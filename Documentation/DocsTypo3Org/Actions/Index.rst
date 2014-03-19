
.. include:: ../../Includes.txt

==================================================
Actions
==================================================

:ref:`Sitemap <sitemap>`


CRON
====

Cronjob Overview
----------------

It's run as user 'mbless'. The console output of each run is send to :mail:`typo3logs@mbless.de`.
Details::

  mbless@srv123:~$ crontab -l

  # 45    */4 * * * /home/mbless/HTDOCS/render-ter-extensions/010_cronjob_get_new_from_ter.py
    10,40 *   * * * /usr/bin/php /home/mbless/HTDOCS/github.com/xperseguers/TYPO3.docs.ter-automation/Classes/Task/TerTask.php    >/dev/null 2>&1
    */30  *   * * * /usr/bin/php /home/mbless/HTDOCS/github.com/xperseguers/TYPO3.docs.ter-automation/Classes/Task/RenderTask.php >/dev/null 2>&1
    */5   *   * * * /home/mbless/HTDOCS/git.typo3.org/Documentation/cron_rebuild.sh

Cronjob: Build documentation
----------------------------

It is running every five minutes.








:ref:`Sitemap <sitemap>`