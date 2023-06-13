.. include:: /Includes.rst.txt

.. _console-command-reference_cache_warmup:

============
cache:warmup
============

*command only*

Cache warmup.

Optionally use the -g option to specify the cache group to warmup. Without
the option, all caches are warmed up.

Cache groups:

*   system
*   pages
*   di (dependency injection cache)
*   all

Examples:

.. code-block:: shell
    :caption: console command

    php vendor/bin/typo3 -g system

.. attention::

    This does not warmup all pages. This is just a basic warming up of caches.
