.. include:: ../../Includes.txt


.. _configuration:

========================
Configuration & Settings
========================

A primary feature of TYPO3 is its configurability. Not only can
it be configured by users with special user privileges in the backend,
most configuration can also be changed by extensions or
configuration files. Additionally, configuration can be extended by
extensions.

This chapter will give you an overview of configuration
in TYPO3. We will not go into detail, but rather show
a comparison of the various methods and resolve some common
sources of confusion.

For a more extensive introduction we will refer you to the
respective chapter or reference.

.. Note for editors: configuration documentation exists in various places
..   This is a first shot to give an overview.
..   Once the (menu) structure is more clear, we may move some of the files to
..   make it more consistent.

.. We currently have documentation in
.. 1) As subchapters in this chapter, they are in the toctree and displayed in menu
.. 2) As links to other places in this manual
.. 3) As links to other manuals, e.g. TCAref


**How configuration documentation is structured:**

Explanations for various files of an extension are handled in the chapter
:ref:`extension-development`. This contains the section
:ref:`extension-files-locations`, which gives an overview of all configuration
files in an extensions:

* :ref:`extension-configuration-files`
* :ref:`extension-configuration`
* :ref:`composerJsonExt`
* ... more, see :ref:`extension-files-locations`

For some configuration, more information exists in additional references:

* :ref:`t3tca:start`
* :ref:`t3tsconfig:start`
* :ref:`t3tsref:start`

Configuration for system extensions can be found in the system extension
documentation of the respective system extension:

* :ref:`Configuration of the Form Framework <form:quickstartIntegrators>`
* :ref:`Configuration of the rich text editor <ckedit:configuration>` for
  editing fields in the backend
* :ref:`Configuration of the search extension indexed-search <indexedSearch:configuration>`
* :ref:`Configuration of the system extension linkvalidator <linkvalidator:configuration>`
  to check for broken links in the site.


More information can be found in these subchapters. The :ref:`configuration-glossary`
explains the terms used to categorize the types of configuration. The :ref:`config-overview`
lists and explains configuration used in TYPO3, such as the :ref:`typoscript-syntax-start`
or :ref:`globals-variables`.

.. toctree::
   :maxdepth: 1

   Glossary
   ConfigurationOverview
   ../FlexForms/Index
   ../GlobalValues/GlobalVariables/Index
   ../GlobalValues/Typo3ConfVars/Index
   ../../DataFormats/T3datastructure/Index
   ../Tsconfig/Index
   ../TypoScriptSyntax/Index
   ../UserSettingsConfiguration/Index
   ../YamlSyntax/Index
   ../Yaml/Index












