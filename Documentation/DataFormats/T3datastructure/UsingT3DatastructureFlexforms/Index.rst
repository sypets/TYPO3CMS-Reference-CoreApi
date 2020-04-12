.. include:: ../../../Includes.txt


.. _t3ds-flexforms:

==================================
Using T3DataStructure in Flexforms
==================================

The general T3DataStructure is explained in :ref:`t3ds-elements`.

This page explains how the elements of the T3DataStructure are
used in a Flexform definition file and gives some examples.

Elements
=========

<T3DataStructure>:
   *Required*

<meta>:
   *Optional*

<sheets>:
   *Required:* All of our sheets go inside this (<sheets>) tag. Sheets are tabs
   which allow different pages to be displayed to further separate our
   configuration options.

<sheet name>, e.g. sDEF:
   *Required:* This is the default sheet.

<ROOT>
   *Required*

<sheetTitle>
   *Required:* This defines a title for the sheet.



Example structure
=================


.. code-block:: none

   T3DataStructure/
   └── sheets
       ├── sDEF
       │   └── ROOT
       │       └── TCEforms
       │           ├── sheetTitle
       │           ├── type
       │           └── el
       │               └── setting1
       │               └── setting2
       │               └── ...
       └── s_redirect
           └── ROOT
               └── TCEforms
                   ├── sheetTitle
                   ├── type
                   └── el
                       └── setting1


.. _t3ds-elements-example:

Example
=======

Below is the (truncated) structure for the plugin options of
system extension "felogin". It shows an example of relative complex
data structure used in a FlexForm. More information about such usage
of FlexForms can be found in the :ref:`flexforms` page and the
:ref:`relevant section of the TCA reference <t3tca:columns-flex>`.

.. code-block:: xml

   <T3DataStructure>
      <meta>
         <langDisable>1</langDisable>
      </meta>
      <sheets>
         <sDEF>
            <ROOT>
               <TCEforms>
                  <sheetTitle>LLL:EXT:felogin/locallang_db.xml:tt_content.pi_flexform.sheet_general</sheetTitle>
               </TCEforms>
               <type>array</type>
               <el>
                  <showForgotPassword>
                     <TCEforms>
                        <label>LLL:EXT:felogin/locallang_db.xml:tt_content.pi_flexform.show_forgot_password</label>
                        <config>
                           <type>check</type>
                           <items type="array">
                              <numIndex index="1" type="array">
                                 <numIndex index="0">LLL:EXT:lang/locallang_core.xml:labels.enabled</numIndex>
                                 <numIndex index="1">1</numIndex>
                              </numIndex>
                           </items>
                        </config>
                     </TCEforms>
                  </showForgotPassword>
                  <showPermaLogin>
                     <TCEforms>
                        <label>LLL:EXT:felogin/locallang_db.xml:tt_content.pi_flexform.show_permalogin</label>
                        <config>
                           <default>1</default>
                           <type>check</type>
                           <items type="array">
                              <numIndex index="1" type="array">
                                 <numIndex index="0">LLL:EXT:lang/locallang_core.xml:labels.enabled</numIndex>
                                 <numIndex index="1">1</numIndex>
                              </numIndex>
                           </items>
                        </config>
                     </TCEforms>
                  </showPermaLogin>
                  // ...
               </el>
            </ROOT>
         </sDEF>
         <s_redirect>
            <ROOT>
               <TCEforms>
                  <sheetTitle>LLL:EXT:felogin/locallang_db.xml:tt_content.pi_flexform.sheet_redirect</sheetTitle>
               </TCEforms>
               <type>array</type>
               <el>
                  <redirectMode>
                     <TCEforms>
                        <label>LLL:EXT:felogin/locallang_db.xml:tt_content.pi_flexform.redirectMode</label>
                        <config>
                           <type>select</type>
                           <items type="array">
                              <numIndex index="0" type="array">
                                 <numIndex index="0">LLL:EXT:felogin/locallang_db.xml:tt_content.pi_flexform.redirectMode.I.0</numIndex>
                                 <numIndex index="1">groupLogin</numIndex>
                              </numIndex>
                              <numIndex index="1" type="array">
                                 <numIndex index="0">LLL:EXT:felogin/locallang_db.xml:tt_content.pi_flexform.redirectMode.I.1</numIndex>
                                 <numIndex index="1">userLogin</numIndex>
                              </numIndex>
                              // ...
                           </items>
                           <size>8</size>
                           <minitems>0</minitems>
                           <maxitems>8</maxitems>
                        </config>
                     </TCEforms>
                  </redirectMode>
               </el>
            </ROOT>
         </s_redirect>
         <s_messages>
            // ...
         </s_messages>
      </sheets>
   </T3DataStructure>

