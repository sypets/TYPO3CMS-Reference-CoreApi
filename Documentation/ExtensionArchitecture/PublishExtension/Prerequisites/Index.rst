.. include:: /Includes.rst.txt
.. index:: Extension development; Publishing prerequisites
.. _publish-extension-prerequisites:

=========================================
Prerequisites for publishing an extension
=========================================

Before publishing extension
===========================

First of all ask yourself some questions before publishing or even putting some
effort in coding:

*  What additional benefit does your extension have for the TYPO3 community?
*  Does your extension key describe the extension?
*  The extension key must be unique and follow the
   :ref:`extension key requirements <extension-key>`.
*  Are there any extensions in the TER yet which have the same functionalities?
*  If yes, why do we need your extension? Wouldn't it be an option to contribute
   to other extensions?
*  Did you read and understand the
   `TYPO3 Extension Security Policy <https://typo3.org/community/teams/security/extension-security-policy>`__?
*  Does your extension include or need external libraries?
   Watch for the license! Learn more about the
   `right licensing <https://typo3.org/project/licenses/>`__.
*  Do you have a public repository on e.g. GitHub, Gitlab or Bitbucket? This is
   recommended so that the community can give feedback, open issues or pull
   requests.
*  Do you have the resources to maintain this extension?
*  This means that you should

   *  support users and integrators using your extension
   *  review and test contributions
   *  test your extension for new TYPO3 releases
   *  provide and update a documentation for your extension


.. _publish-extension-semantic-versioning:

Use semantic versions
=====================

We would like you to stick to semantic versions.

Given a version number **MAJOR.MINOR.PATCH**, increment the:

*  **MAJOR** version when you make incompatible API changes (known as "**breaking changes**"), 
*  **MINOR** version when you **add functionality in a backwards-compatible manner**, and
*  **PATCH** version when you **make backwards-compatible bug fixes**.

Additional labels for pre-release and build metadata are available as extensions
to the **MAJOR.MINOR.PATCH format**.

See `https://semver.org <https://semver.org>`__

