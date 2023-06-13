.. include:: /Includes.rst.txt

.. _console-command-reference:

=================
Command Reference
=================

This is a list of console commands provided by TYPO3 core extensions.

In the following list, the commands are tagged with one of the following:

command (schedulable):
    is a console command (based on Symfony commands) which can be run from
    the command line, but can also be run via the scheduler (by selecting
    the task "Execute console commands").

command only:
    is a console commands (based on Symfony commands) which is not available
    in the scheduler.

Further information:

*   :ref:`symfony-console-commands`

.. contents::
    :depth: 2
    :local:
    :caption: Table of contents (on this page)

general commands
================

Running the typo3 command without parameters will show a list of all commands.
This is the same as running the command list.

list
----

Show a list of all commands, grouped by (command) namespace. The namespace is
automatically determined by the first part of the command name before the
colon (":"). It has nothing to do with the PHP namespace.

help
----

Displays help for a command.

Example:

.. code-block:: shell
    :caption: console command

    php vendor/bin/typo3 help redirects:checkintegrity


Is the same as running:

.. code-block:: shell
    :caption: console command

    php vendor/bin/typo3 redirects:checkintegrity -h



impexp:import
-------------

*command (schedulable)*

Imports a T3D / XML file with content into a page tree.

More information can be found in the impexp documentation:

*   :ref:`ext_impexp:command_line`

EXT:install
===========

.. _console-command-reference_language_update:

language:update
---------------

*command (schedulable)*

Update the language files of all activated extensions.

The language update can also be run via Admin Tools
:guilabel:`Maintenance > Manage Language Packs`.

.. _console-command-reference_upgrade_run:

upgrade:run
-----------

*command only*

Run upgrade wizard. Without arguments all available wizards will be run.

The upgrade wizards can also be run via Admin Tools
:guilabel:`Upgrade > Upgrade Wizard`.

.. _console-command-reference_upgrade_list:

upgrade:list
------------

*command only*

List available upgrade wizards.

EXT:lowlevel
============

.. _console-command-reference_cleanup_flexform:

cleanup:flexforms
-----------------

*command (schedulable)*

Updates all database records which have a FlexForm field and the XML data does
not match the chosen datastructure.

This command is supplied by the system extension lowlevel. More information
about this extension:

*   :ref:`ext_lowlevel:command-line`

.. _console-command-reference_cleanup_localprocessedfiles:

cleanup:localprocessedfiles
---------------------------

*command (schedulable)*

Delete processed files and their database records.

This command is supplied by the system extension lowlevel. More information
about this extension:

*   :ref:`ext_lowlevel:command-line`


.. _console-command-reference_cleanup_deletedrecords:

cleanup:deletedrecords
----------------------

*command (schedulable)*

Permanently deletes all records marked as "deleted" in the database.

This command is supplied by the system extension lowlevel. More information
about this extension:

*   :ref:`ext_lowlevel:command-line`

.. _console-command-reference_cleanup_missingrelations:

cleanup:missingrelations
------------------------

*command (schedulable)*

Find all record references pointing to a non-existing record.

This command is supplied by the system extension lowlevel. More information
about this extension:

*   :ref:`ext_lowlevel:command-line`

.. _console-command-reference_cleanup_orphanrecords:

cleanup:orphanrecords
---------------------

*command (schedulable)*

Find and delete records that have lost their connection with the page tree.

This command is supplied by the system extension lowlevel. More information
about this extension:

*   :ref:`ext_lowlevel:command-line`

.. _console-command-reference_syslog_list:

syslog:list
-----------

*command (schedulable)*

Show entries from the sys_log database table of the last 24 hours.

.. note::

    This is a schedulable command, but it does not make sense currently to run
    this via the scheduler since this command will output information on the
    console. If you schedule it via the scheduler and then run it via the
    command line with scheduler:run, it will also not output any information.
    Just run the command on the command line directly!

Example output:

.. code-block:: text

    Show entries from the sys_log database table of the last 24 hours.
    ==================================================================

    -------- ---------------- --------- ----------------------------------------------------------------------------------------------------------------------------------
     Log ID   Date & Time      User ID   Message
    -------- ---------------- --------- ----------------------------------------------------------------------------------------------------------------------------------
     87       13-06-23 06:55   1         Scheduler task "Execute console commands" (UID: 11, Class: "TYPO3\CMS\Scheduler\Task\ExecuteSchedulableCommandTask") was updated
     86       13-06-23 06:54   1         Scheduler task "Execute console commands" (UID: 11, Class: "TYPO3\CMS\Scheduler\Task\ExecuteSchedulableCommandTask") was added
     85       13-06-23 06:19   1         User system logged in from ###IP###
     84       12-06-23 19:08   1         User system logged in from ###IP###
    -------- ---------------- --------- ----------------------------------------------------------------------------------------------------------------------------------

This command is supplied by the system extension lowlevel. More information
about this extension:

*   :ref:`ext_lowlevel:command-line`

EXT:redirects
=============

.. _console-command-reference_redirects_checkintegrity:

redirects:checkintegrity
------------------------

*command (schedulable)*

Check integrity of redirects.

The output can also be viewed in the system report.

More information is available in the redirects documentation:

*   :ref:`ext_redirects:redirects-checkintegrity`

.. _console-command-reference_redirects_cleanup:

redirects:cleanup
-----------------

*command (schedulable)*

Cleanup old redirects periodically for given constraints like days, hit count
or domains.

More information is available in the redirects documentation:

*   :ref:`ext_redirects:redirects-cleanup`

EXT:scheduler
=============

.. _console-command-reference_scheduler_run:

scheduler:run
-------------

*command only*

Start the TYPO3 Scheduler from the command line.

.. _console-command-reference_scheduler_execute:

scheduler:execute
-----------------

*command only*

Execute given Scheduler tasks. You must use the id (uid) of an existing
scheduler task.

Example:

.. code-block:: shell
    :caption: command line

    php vendor/bin/typo3 scheduler:execute -i 43 -f


.. _console-command-reference_scheduler_list:

scheduler:list
--------------

*command only*

List all Scheduler tasks.

EXT:styleguide
==============

The styleguide extension is a very helpful tool for developers, used in core
development and for viewing FormEngine / TCA styles in the backend. It is
usually not used in production.

.. _console-command-reference_styleguide_generate:

styleguide:generate
-------------------

*command only*

Generate page tree for Styleguide TCA backend and/or Styleguide frontend.

The commands are not available in the scheduler but generating the page tree
can also be performed in the TYPO3 backend by selecting the helpmenu (in the
topbar, click on "?") and then :guilabel:`Styleguide > Index`.

.. _console-command-reference_styleguide_kauderwelsch:

styleguide:kauderwelsch
-----------------------

*command only*

Generate some bacon text.

EXT:workspaces
==============

.. _console-command-reference_cleanup_previewlinks:

cleanup:previewlinks
--------------------

*command (schedulable)*

Clean up expired preview links from shared workspace previews.

.. note::

    This command is supplied by the workspaces extension, even though it is
    listed in the "cleanup" namespace together with the other cleanup commands
    supplied by EXT:lowlevel.

More information can be found in the workspaces extension manual:

* :ref:`ext_workspaces:scheduler`

.. _console-command-reference_cleanup_versions:

cleanup:versions
----------------

*command (schedulable)*

.. note::

    This command is supplied by the workspaces extension, even though it is
    listed in the "cleanup" namespace together with the other cleanup commands
    supplied by EXT:lowlevel.

Find all versioned records and possibly cleans up invalid records in the database.

.. _console-command-reference_workspace_autopublish:

workspace:autopublish
---------------------

*command (schedulable)*

Publish a workspace with a publication date.

More information can be found in the workspaces extension manual:

* :ref:`ext_workspaces:scheduler`


EXT:core
========

.. toctree::
    :glob:
    :titlesonly:

    Core/*

EXT:extensionmanager
====================

.. toctree::
    :glob:
    :titlesonly:

    Extensionmanager/*

EXT:impexp
==========

.. toctree::
    :glob:
    :titlesonly:

    Impexp/*

