.. include:: /Includes.rst.txt
.. index:: Extension development; Publishing
.. _publish-extension:

========================================================
Publish your extension to the Extension Repository (TER)
========================================================

Prerequisites
=============

*  **requirement** The extension key MUST be unique and MUST comply with
   the :ref:`rules for extension keys <extension-key>`.
*  It is recommended to follow the other recommendations on
   :ref:`publish-extension-prerequisites` as well, especially
   :ref:`semantic versioning <publish-extension-semantic-versioning>` and
   having a public repository on e.g. GitHub, Gitlab or Bitbucket.

How to publish an extension
===========================

Now we come to the process of publishing. You have two possibilites to release an extension:

#. Via the web form on extensions.typo3.org (click on "Publish" next to your extension key in the `extension key management <https://extensions.typo3.org/my-extensions>`__).
#. Via `Tailor <https://github.com/TYPO3/tailor>`__: Tailor is a CLI application to help you maintain your extensions. Tailor talks with the TER REST API and enables you to register new keys, update extension information and publish new versions to the extension repository. (recommended)
#. Via the SOAP interface using a tool like the `TYPO3 Repository Client <https://github.com/NamelessCoder/typo3-repository-client>`__ (`Documentation <https://github.com/NamelessCoder/typo3-repository-client#typo3-repository-client-apicli>`__) or the `TER client <https://github.com/helhum/ter-client>`__ (`Documentation <https://github.com/helhum/ter-client#ter-client>`__) (deprecated)

.. _publish-extension-feedback:

Add metadata
============

It is recommended to add the following information in the
`extension key management <https://extensions.typo3.org/my-extensions>`__
(after login).

"Link to issue tracker":
   A possibility to get in contact with you and open bug reports (link to an
   issue tracker, e.g. on GitHub, etc.).
"Link to repository":
   A possibility to look into the code (link to a public repository).
"External manual":
   Only fill this out, if your documentation is **NOT** rendered on docs.typo3.org.
   If it is rendered on docs.typo3.org, the link to your documentation will be
   added automatically.
"Sponsoring link":
   Add to a page with information on how to donate.
"Tags":
   Add tags for the extension.

