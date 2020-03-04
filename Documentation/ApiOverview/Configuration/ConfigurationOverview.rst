.. include:: ../../Includes.txt

.. _config-overview:

========================
Configuration overview
========================

A common problem is mixing up TypoScript and TSconfig.
What is most important here, is that TypoScript has its own syntax. And the
TypoScript syntax is used for the configuration methods **TypoScript and TSconfig**.
While TypoScript and TSconfig look very similar because they
share the same syntax, the set of variables and where they are set and applied is
different. TSconfig defines backend functionality, while TypoScript defines mostly
frontend functionality and is used in templating.

.. tip::

   Hence, the term **TypoScript** is used for both the pure syntax TypoScript
   and the configuration method TypoScript. These are different things. To avoid
   confusion, we will use the term "TypoScript syntax" for the syntax and
   "TypoScript Templating" for the method, at least in this chapter.
   For more definitions of terms and clarifications, see :ref:`configuration-glossary`.

.. _configuration-syntax:

Syntax languages
================

These are the main languages TYPO3 uses for configuration:

TypoScript syntax
-----------------

:ref:`TypoScript syntax <typoscript-syntax-start>` is used for TypoScript Templating
and TSconfig.

TypoScript constant declaration syntax
--------------------------------------

The TypoScript constant declaration syntax is used to define settings for

#. Extension Configuration
#. and for defining constants for TypoScript.

The syntax used for both currently not 100% identical but very similar.

Example:

.. code-block:: typoscript
    :linenos:

    # cat=Login; type=string; label=Login logo
    loginLogo = EXT:backend/Resources/Public/Icons/typo3.svg

The first line is a **variable declaration** which defines the category, datatype and a
descriptive title for the configuration option in the second line.

More information:
    * :ref:`TypoScript constant declaration syntax <t3tsref:typoscript-syntax-constant-editor>`
    * :ref:`Extension Configuration <extension-options>`


YAML syntax
-----------

:ref:`Yaml <yaml-syntax>` is the configuration language of choice for
the sites module in the core and newer TYPO3 system extensions
like rte-ckeditor and form.

XML syntax
----------

XML is used in FlexForms.

PHP syntax
----------

PHP is used for the :php:`$GLOBALS` array which includes TCA
(:php:`$GLOBALS['TCA']`), Global Configuration (:php:`GLOBALS['TYPO3_CONF_VARS']`),
User Settings (:php:`$GLOBALS['TYPO3_USER_SETTINGS']`, etc.


.. _configuration-methods:

Configuration methods
=====================

A part of configuration is simply setting variables at
some point using a defined structure. Some of these variables can be changed
in extensions or modified in the backend. The methods described here partly
overlap. For example, "Extension Configuration" is written into
the array :php:`$GLOBALS['TYPO3_CONF_VARS']`, which is also used
for the "Global Configuration", but there is an API for "Extension
Configuration", a dedicated schema file (:file:`ext_conf_template.txt`)
and setting the variables in the backend is separate.

.. important::

   It is bad practices to just change variables in :php:`$GLOBALS` at
   random.
   Use the defined API and the recommended files to change configuration.

These are the main configuration methods used by TYPO3:

Global variables ($GLOBALS)
---------------------------

The global variables (and some other configuration) can be viewed in the
TYPO3 backend :guilabel:`SYSTEM > Configuration` or by viewing the
:php:`$GLOBALS` array in a debugger.

More information:
    :ref:`globals-variables`.

The :php:`$GLOBALS` array consists of:

Global Configuration ($GLOBALS['TYPO3_CONF_VARS'])
--------------------------------------------------

:ref:`Global Configuration <typo3ConfVars>` :php:`$GLOBALS['TYPO3_CONF_VARS']`
is used for system wide configuration.

Changing of variables can be done in the backend in :guilabel:`Settings > Global Configuration`
and is written to :file:`typo3conf/LocalConfiguration.php`. The settings can be
overridden in the file :file:`typo3conf/AdditionalConfiguration.php`.

More information:
    * :ref:`Global Configuration <typo3ConfVars>`

Links to the code:
    * Defaults: `EXT:core/Configuration/DefaultConfiguration.php <https://github.com/TYPO3/TYPO3.CMS/blob/master/typo3/sysext/core/Configuration/DefaultConfiguration.php>`__
    * Descriptions: `EXT:core/Configuration/DefaultConfigurationDescription.yaml <https://github.com/TYPO3/TYPO3.CMS/blob/master/typo3/sysext/core/Configuration/DefaultConfigurationDescription.yaml>`__

Extension Configuration
-----------------------

A subset of the :php:`$GLOBALS['TYPO3_CONF_VARS']` array is
:ref:`Extension Configuration <extension-options>` (:php:`$GLOBALS['TYPO3_CONF_VARS']['EXTENSIONS']`).
It is used for configuration specific to one extension. An API (:php:`ExtensionConfiguration->get()`)
is used to read Extension Configuration. The schema is defined in :ref:`ext_conf_template.txt` in the
extension. The settings can be changed in the backend in :guilabel:`Settings > Extension Configuration`
(only for system maintainers).

More information: :ref:`Extension Configuration <extension-options>`

TCA
---

:php:`GLOBALS['TCA']` is the backbone of database tables displayed in the backend, it configures
how data is stored if editing records in the backend, how fields are displayed,
relations to other tables and much more. It is a huge array loaded in almost all
access contexts.

The array contains a subarray for the respective database table using the
same name as key (e.g. `pages`). You can view the entire array in the
backend module :guilabel:`SYSTEM > Configuration`.

TCA, that is set in the core can be overridden by extensions. This is done in the
following files:

* In order to set TCA: :file:`Configuration/TCA/<tablename>.php`
* In order to override TCA: :file:`Configuration/TCA/Overrides/<tablename>.php`

You may still find extensions that directly set :php:`$GLOBALS['TCA'] or even :php:`$TCA`
in :file:`ext_tables.php`. This is no longer correct. You should steer away from
examples and snippets (or extensions) that write TCA in :file:`ext_tables.php` or even
better notify the author about outdated examples.

:ref:`Doing this correctly <extending-tca>` is important due to how TYPO3 concatenates
and caches some configuration files!

More information:

* :ref:`TCA Reference <t3tca:start>` is a complete reference of all
  different `TCA` options, with bells and whistles. The document is a must-read for
  developers and is often used as a reference book on a daily basis.
* :ref:`Extending the TCA array in extensions <extending-tca>`


User settings
-------------

:ref:`User settings <user-settings>` :php:`$GLOBALS['TYPO3_USER_SETTINGS']`
defines configuration for backend users


TypoScript constants
--------------------

In TypoScript, there are constants and setup. The name constants may be a little
misleading as they can be set and overridden multiple times. Constants are defined
using the TypoScript constant declaration syntax. They can be set in the
:guilabel:`Web > Template` module in the backend or in an extension, typically in
the file :file:`Configuration/TypoScript/constants.typoscript`.

When constants are changed in the :guilabel:`Template` module of a page, they apply
to the page and all subpages. This makes it possible to configure individual sites
or pages differently within one TYPO3 installation.

TypoScript setup
----------------

TypoScript - or more precisely **TypoScript Templating** - is used in TYPO3 to steer
the frontend rendering (the actual website) of a TYPO3 instance.
It is based on :ref:`TypoScript syntax  <typoscript-syntax-start>`.

Frontend TypoScript is very powerful and has been the backbone of frontend rendering ever since.
However, with the rise of the Fluid templating engine, many parts of Frontend TypoScript are much less
often used. Nowadays, TypoScript in real life projects is often not much more than a way to
set a series of options for plugins, to set some global config options, and to act as a simple
pre processor between database data and Fluid templates.

More information:
    :ref:`t3tsref:start`

TSconfig
--------

:ref:`TSconfig <tsconfig>` is used to configure and **customize the backend** on a page (page TSconfig)
and a user or group basis (user TSconfig).
Using `TSconfig` it is possible to enable or
disable certain views, change the editing interfaces, and much more. All that without coding a single
line of PHP.

`TSconfig` uses the same syntax as `TypoScript Templating`, the syntax is outlined in detail in
:ref:`typoscript-syntax-start`. Other than that, TSconfig and TypoScript Templating
don't have much more in common - they consist of entirely different properties.

A full reference of properties as well as an introduction can be found in the :ref:`t3tsconfig:start`. While Developers
should have an eye on this document, it is mostly used as a reference for Integrators who make life as
easy as possible for backend users.


Flexforms
---------

FlexForms have a very narrow scope as they only apply to one content element. Editing Flexforms
is a part of editing content which is usually done by editors. So, we do not consider that part
configuration. But setting up the FlexForms in an extension can also be considered configuration too.

More information:
    :ref:`Flexform <flexforms>`

Feature toggles
---------------

Feature toggles are used to switch a specific functionality of TYPO3 on or off. The settings can
be changed in the backend module :guilabel:`Settings` in :guilabel:`Feature Toggles`.

More information:
    :ref:`feature-toggles`

YAML
----

Some system extensions use YAML for configuration:

* :ref:`Site <sitehandling>` configuration is stored in :file:`<project-root>/config/sites/<identifier>/config.yaml`
  and can be configured in the sites module.
* :ref:`form <form:concepts-configuration>`: Forms in the frontend
* :ref:`rte_ckeditor <ckedit:configuration>`: configure editing rich text editing
* :ref:`Event listeners <EventDispatcher>` in :file:`Configuration/Services.yaml`
* :ref:`Dependency injection <DependencyInjection>` information in :file:`Configuration/Services.yaml`

There is a :ref:`YamlFileLoader <yamlFileLoader>` which can be used to load YAML
files.

Configuration files
===================

For an overview of configuration files in an extension, see :ref:`extension-files-locations`.

