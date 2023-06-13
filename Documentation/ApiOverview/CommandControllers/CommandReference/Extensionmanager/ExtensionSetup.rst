.. include:: /Includes.rst.txt

.. _console-command-reference_extension_setup:

===============
extension:setup
===============

*command only*, in EXT:extensionmanager

Set up extensions. This will perform necessary setup after installing or
updating an extension (including system extensions!).

.. attention::

    This is only relevant for non-Composer installations. Extensions are
    automatically setup when installed via the Extension Manager in non-Composer
    mode.

This includes, but is not limited to:

*   Update the database based on the database schema supplied by the extension
    (in :file:`ext_tables.sql`).
*   Import site configuration from the extension.
*   ...

After running this command, it is usually necessary to also flush the cache.
