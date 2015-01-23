[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------

##The dbdocs system

The db docs system is made up of three core tables

* dbdocstable
* dbdocsfields
* dbdocssubtables

The World database also has an additional table:-

* dbdocsprogressquests

I will attempt to explain how the dbdocs system links everything together below

###dbdocstable - DB Docs Table

---

This table contains two fields:

####Field 'tableName'
This field contains the table name to link the additional notes to.

####Field 'tableNotes'
This field is the description of the table, since this is a text field the text can be quite lengthy if required and contain html.

###dbdocsfields - DB Docs Fields

---

This table contains three fields:

####Field 'tableName'
This field contains the table name to link the additional notes to.

####Field 'fieldName'
This field contains the field name in the table to link the additional notes to.

####Field 'fieldComment'
This field contains a short description of the field.

####Field 'fieldNotes'
This field is the description of the field, since this is a text field the text can be quite lengthy if required and contain html.

You can also add subtable directives at any point through the text. The directive takes the format: <pre>¬subtable:x¬</pre> Where x is the subtable Id.

<pre>What follows is a list of allowed races:
¬subtable:1¬
* Remember that some races are not available on earlier expansions
</pre>

This literally means add subtable Id 1 into the text at this point

###dbdocssubtables - DB Docs SubTables

---

This table contains two fields:

####Field 'subtableId'
This field contains the table name to link the additional notes to.

####Field 'subtablecontent'
This field contains the markup for the subtable, since this is a text field the text can be quite lengthy if required and contain html. This directly replaces the subtable directives used in field notes.

####Field 'subtableNotes'
This field is the short description of the subtable is.


The last of the tables is:

###dbdocsprogressquests - DB Docs ProgressQuests

---
This table contains three fields:

####Field 'QuestId'
This field contains the quest Id.

####Field 'Progress'
This field contains the percentage complete this quest is. By default the dbdocs system assumes that this is 0% if unmatched.

####Field 'QuestNotes'
This field is the a note regarding the state of the quest, since this is a text field the text can be quite lengthy if required and contain html. 

---

All the current wiki Database and DBC reference information page are now built using the above system.