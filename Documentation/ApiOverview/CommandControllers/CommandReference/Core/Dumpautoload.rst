.. include:: /Includes.rst.txt

.. _console-command-reference_dumpautoload:

============
dumpautoload
============

*command only*, in EXT:core

.. attention::

    Only relevant in non-Composer mode! In Composer mode composer dump-autoload
    can be used.

Updates class loading information in non-composer mode.

This command does not have a namespace and is thus shown at the top if listing
all commands.

Autoloading can also be triggered in Admin Tools :guilabel:`Maintenance >
Rebuild PHP Autoload Information`.

It is usually not necessary to run this command. If sextension are installed via
the Extension Manager, autoloading of classes is performed automatically. However,
it may be necessary to install an extension via Git or other means and then
it is necessary to manually flush the cache and rebuild the PHP autoload
information.

