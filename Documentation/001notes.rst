.. include:: Includes.txt

==================================================
001notes
==================================================

- http://docs.typo3.org/typo3cms/drafts/github/marble/IncomingNotes/stable/
- http://docs.typo3.org/~mbless/github.com/marble/typo3-incoming-notes.git.make/
- http://docs.typo3.org/typo3cms/drafts/github/marble/IncomingNotes/Index.html

.htaccess files that turn directory listing on:
- /home/mbless/HTDOCS
- /home/mbless/public_html/typo3cms/drafts/.htaccess


ToDo
====
- make adaptive layout default


Problem
=======

In this project it does not work to have a file ``./Documentation/001notes.rst``.
The reason probably is the :file:`.htaccess`::

  Options -Indexes
  RewriteEngine On
  RewriteRule ^(([0-9]+)(\.[0-9])*|latest|packages|stable|manuals.json)(.*)$ -  [L]
  RewriteRule ^(.*)$ stable/$1

This works: http://docs.typo3.org/typo3cms/drafts/github/marble/IncomingNotes/stable/001notes.html

This does not work: http://docs.typo3.org/typo3cms/drafts/github/marble/IncomingNotes/001notes.html



Hi all,

There are some tasks to perform to prepare our code sprint. The good news is that I planned some budget for them.

1) Inventory of docs.typo3.org

a) I would like to have a full inventory of the resources used on docs.typo3.org as a basis for discussion. By resources I mean all tools used (applications, libraries, ...), custom code (PHP, Python, …), databases of any kind (SQL, flat files, …), frontend stuff (HTML templates, CSS, JS, etc., in particular from the glue pages). For everything that is source code, I would like to have an indication whether it is kept in a Git repo or not.

b) Aside from that I would like to have an overview of the features that are already functional in the Flow application.

For the first point I think it is Martin and Xavier who have the knowledge. For the second point, Karsten should be the most up to date, although Fabien may know of some older features which Karsten didn't touch upon during his recent work.

I have budgeted 10 hours for this. I imagine that it should be split 80-20 between a and b (further split among the people who do the work). The work should be done by March 31.

Is that okay with you? Do you feel you can do the work within the allotted budget and time frame?

2) I also plan to work on producing draft wireframes for the Flow application, listing the features we would like to add to it. This would also be used to kickstart discussions during the code sprint. I am in touch with Christian Zenker of the T3O/TER team to understand what needs they would have. I'll also query the Flow team whether they have similar needs. There are another 10 hours for this. I'll try to have this ready before March 31, so that we can feed it for brainstorming to the documentation ML before the sprint.

Any remarks about the above is welcome.

Cheers

Francois Suter


TYPO3 .... inspiring people to share!
Get involved: typo3.org

