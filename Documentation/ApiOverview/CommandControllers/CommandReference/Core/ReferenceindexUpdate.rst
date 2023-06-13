.. include:: /Includes.rst.txt

.. _console-command-reference_referenceindex_update:

=====================
referenceindex:update
=====================

*command (schedulable)*, in EXT:core

Update the reference index of TYPO3

It is recommended to run this regularly, e.g. once a day.

It is also possible to run the reference index check or update in the "DB check"
System module.

It is important for the reference index to be kept up-to-date because
the reference index keeps track of references (connections) between records
(e.g. files, pages). For example if a page links to another page using a page
link a connection is formed from page A via the link to page B. If page B
is deleted, the link will no longer work. The same is true for links to files.
It is possible to see the number of references for a file in the filelist.
This uses the reference index. If no references are displayed, editors might
delete the file, unaware that it is still being used.

In theory, the reference index will be automatically updated when
references change, but for some reason this may not always be the case.

It is the responsibility of DataHandler to update the reference index. Changes
in content which are performed via DataHandler will initiate an update of the
reference index, while changes which are performed via direct database changes
(e.g. via QueryBuilder) will not.
