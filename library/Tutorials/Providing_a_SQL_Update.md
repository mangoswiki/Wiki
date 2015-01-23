#### This guide is to provide assistance for those wishing to commit updates to the MaNGOS databases.

## Database Numbering System

The DB version is made up of four parts, a typical commit file is named as:

<PRE>20003_17_Molten_Core_Portal_Fix.sql</PRE>

`20` is the release version.

`003` is the base core version.

`17` is the sequence number of the update (this number increments for each update on a base core version).

The last part is a description of what the update does.

### Base Core update or revision update ?

The rules that decide whether the update is a base core version update are as follows:

* If the DB change requires a core change.
* If there are DB Structure changes.


Otherwise it would be a revision update:

* a typical DB `Update`, `Insert` or `Delete` change

#### A typical Revision update

The file would be called:
<pre>20003_18_Silithus_Rock_Stalkers_Set_To_Elite.sql</pre>

and contains the following:
<pre>/*
	This sets the Rock Stalkers in Silithus to Elite (Rank)
	They did not have their elite status removed until patch 2.3
*/

-- Add the Revision update into the revision column
INSERT IGNORE INTO db_version SET `Version` = 'MaNGOSZero Database 2.0.11 Rev 18';

UPDATE creature_template SET `Rank`='1' WHERE `Entry`='11739';
</pre>

#### A Typical Base Core Update

This is a bit more involved as it requires changes in the server repo as well

To start with, the file would be called:
<pre>/*
	This fixes the portal inside of Molten Core. Before you were ported to Blackrock Depths when you wanted to leave Molten Core through the portal.
	Now you will get ported to Blackrock Mountain (beside the Elv which ports you inside Molten Core).
*/

ALTER TABLE db_version CHANGE COLUMN required_20003_16_Molten_Core_Creature_Cleanup required_20003_17_Molten_Core_Portal_Fix  BIT;

UPDATE `areatrigger_teleport` SET 
`target_map` = '0',
`target_position_x` = '-7506.95',
`target_position_y` = '-1040.91',
`target_position_z` = '180.91',
`target_orientation` = '3.35' 
WHERE `areatrigger_teleport`.`id` =2890;
</pre>

The `ALTER TABLE` statement changes the column name from the existing one to the new filename prefixed with `required_`

In the server repo, the file `src/shares/revision_sql.h`

The line:
<pre>#define REVISION_DB_MANGOS "required_20003_16_Molten_Core_Creature_Cleanup"</pre>
Needs to be changed to:
<pre>#define REVISION_DB_MANGOS "required_20003_17_Molten_Core_Portal_Fix"</pre>

Once this is complete, both changes will need to be pushed to their respective repo's.

