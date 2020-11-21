.. include:: /Includes.rst.txt


.. _links+references-intro:

============
Introduction
============

This page gives an introduction into links and references in TYPO3, how they
are created and maintained and how to extend TYPO3 core functionality in this
regard. Most of the information is relevant for developers only, but this
introduction should also give you a better understanding of how TYPO3 works
internally.

Links and references are both used to define a relation between two entities.

Examples
========

*file reference*

The TYPO3 content element "textmedia" can be used to display content blocks
consisting of images as well as text. When editing a "textmedia" element
in the backend, images can be added to the element.

This is a:

* file reference
* of TCA type "inline"
* for the field :db:`tt_content.assets`
* where the relation is stored in the table :db:`sys_file_reference`
* n to n relation - a file can be related to 0 or more records and a record
  can contain 0 or more files.

The relation is defined with TCA:




*language reference*

This is more commonly called language overlay.

Another example


Definition of terms
===================

reference:
   A reference (in this context) is a relation between 2 entries in the
   database and usually consists of the table name, field name and uid
   of both entries. Examples for references are content elements with
   images or pages of type "shortcut" with redirect to another page.

link:
   A link is also a kind of reference but has a special syntax, e.g.
   :html:`<a href="t3://page?uid=1">anchor text</a>` is a a page link
   to the page with uid=1.

IRRE:
   Inline-Relational-Record-Editing

soft reference:

reference index:

link browser:

file abstraction layer:

More information
================

You can find more information in the following chapters, but also in

* :ref:`fal`
* :ref:`TCA column type "inline" <t3tca:columns-inline>`
* :ref:`TCA column type "group" <t3tca:columns-group>`
