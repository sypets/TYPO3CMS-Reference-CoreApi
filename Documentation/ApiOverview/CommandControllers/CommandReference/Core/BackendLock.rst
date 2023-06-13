.. include:: /Includes.rst.txt

.. _console-command-reference_backend_lock:

============
backend:lock
============

*command (schedulable)*, in EXT:core

Lock the TYPO3 Backend.

It is possible to lock the backend, so that users cannot log in and existing
sessions will be terminated. This can be used for example during administrative
tasks, major updates, during a security breach and in particular during
tasks which make it necessary to restrict editing.

Use :ref:`backend:unlock <console-command-reference_backend_unlock>` to unlock
the backend again.
