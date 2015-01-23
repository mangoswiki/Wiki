[![](/wiki/icons/home.gif)](/wiki/Home.md)
[![](/wiki/icons/back.gif)](/wiki/Progress.md)

-----

#### Description of the MaNGOSZero Missing Translations

----

<br/>
<table border='1' cellspacing='0' cellpadding='4' bgcolor='#f0f0f0' width='100%'>
<tr>
<td>FieldId</td>
<td>FieldName</td>
<td>English</td>
<td>Localised</td>
</tr>
<tr bgcolor='#FFFFEE'><td>1</td>
<td>id</td>
<td>The ID of the trigger (See AreaTrigger.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>2</td>
<td>quest</td>
<td>The entry of the quest (see quest_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>3</td>
<td>id</td>
<td>The ID of the trigger (See AreaTrigger.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>4</td>
<td>name</td>
<td>Name of town or tavern.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>5</td>
<td>id</td>
<td>The ID of the trigger (See AreaTrigger.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>6</td>
<td>name</td>
<td>The name of the teleport areatrigger.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>7</td>
<td>required_item</td>
<td>Requested an item (See item_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>8</td>
<td>required_item2</td>
<td>Requested an item (See item_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>9</td>
<td>required_level</td>
<td>The player needs to be at least this level.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>10</td>
<td>required_quest_done</td>
<td>Requires quest (See quest_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>11</td>
<td>target_map</td>
<td>The destination map id. The value has to match with a map identifier defined (see Map.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>12</td>
<td>target_orientation</td>
<td>The orientation of the player at the destination, This is measured in radians (North = 0.0, South = 3.14159).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>13</td>
<td>target_position_x</td>
<td>The x location of the player at the destination.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>14</td>
<td>target_position_y</td>
<td>The y location of the player at the destination.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>15</td>
<td>target_position_z</td>
<td>The z location of the player at the destination.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>16</td>
<td>description</td>
<td>Description of the event. If possible specify name, location, and schedule in the comment.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>17</td>
<td>event1</td>
<td>The identifier for the event node in the battleground. Event nodes usually are defined in the battleground’s script.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>18</td>
<td>event2</td>
<td>The state of the event node. Node status is defined differently in every battleground script.
<br />
NOTE:<br />
If you update battleground scripts and make changes to node status values ensure that you provide database update scripts which update the battleground events accordingly.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>19</td>
<td>map</td>
<td>The map id of the location of the event (See map.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>20</td>
<td>AllianceStartLoc</td>
<td>The location where the alliance players get teleported to when the battleground first starts (See WorldSafeLocs.dbc).
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>21</td>
<td>AllianceStartO</td>
<td>The orientation of the alliance players upon teleport into the battleground. North is 0, south is Pi (3.14159). </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>22</td>
<td>HordeStartLoc</td>
<td>The location where the horde players get teleported to when the battleground first starts (See WorldSafeLocs.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>23</td>
<td>HordeStartO</td>
<td>The orientation of the horde players upon teleport into the battleground. North is 0, south is Pi (3.14159). </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>24</td>
<td>id</td>
<td>The battleground ID. (See BattlemasterList.dbc).

¬subtable:10¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>25</td>
<td>MaxLvl</td>
<td>The maximum level that players need to be in order to join the battleground.<br />
If left at 0, mangos will use the default value (See map.dbc).
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>26</td>
<td>MaxPlayersPerTeam</td>
<td>Controls how many players from each team can join the battleground.<br />
If left at 0, mangos will use the default DBC value.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>27</td>
<td>MinLvl</td>
<td>The minimum level that players need to be in order to join the battleground.<br />
If left at 0, mangos will use the default value (See map.dbc)
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>28</td>
<td>MinPlayersPerTeam</td>
<td>Controls the minimum number of players that need to join the battleground on each faction side for the battleground to start. For the battleground to start, all characters (between min and max player values) must be in the same tier. Tiers are set up in ranges of 10 levels except for level 70.

¬subtable:11¬

If characters of different tiers all join the queue, they will join their respective tier's queue and wait for more players of their tier to join the queue. Characters in different tiers can never join the same battleground. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>29</td>
<td>bg_template</td>
<td>The battleground template ID (See Battleground_template).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>30</td>
<td>entry</td>
<td>The unique identifier of the item template entry.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>31</td>
<td>help</td>
<td>The help text for the command which explains it's use and parameters.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>32</td>
<td>name</td>
<td>The Command Name.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>33</td>
<td>security</td>
<td>The minimum security level to use the command (See account.gmlevel) in the realm database.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>34</td>
<td>condition_entry</td>
<td>Identifier</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>35</td>
<td>type</td>
<td>Type of the condition:<br />

¬subtable:33¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>36</td>
<td>value1</td>
<td>Data field One for the condition.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>37</td>
<td>value2</td>
<td>Data field Two for the condition.<br />
<br />
Condition Types:<br />
<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th align='right'><b>Condition Type</b></th>
<th align='left'><b>Value1</b></th>
<th align='left'><b>Value2</b></th>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_NOT</td><td align='left' valign='middle'>Reference to another condition_entry</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_OR</td><td align='left' valign='middle'>Reference to another condition_entry</td><td align='left' valign='middle'>Reference to another condition_entry</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_AND</td><td align='left' valign='middle'>Reference to another condition_entry</td><td align='left' valign='middle'>Reference to another condition_entry</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_NONE</td><td align='left' valign='middle'>0</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_AURA</td><td align='left' valign='middle'>Spell Id (See Spell.dbc)</td><td align='left' valign='middle'>Spell effect index to aura effect.</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_ITEM</td><td align='left' valign='middle'>Item Template Id (See item-template.id)</td><td align='left' valign='middle'>count (number of items required)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_ITEM_EQUIPPED</td><td align='left' valign='middle'>Item Template Id (See item-template.id)</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_AREAID</td><td align='left' valign='middle'>AreaTable ID (See AreaTable.dbc)</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_REPUTATION_RANK_MIN</td><td align='left' valign='middle'>Faction Id (See Faction.dbc)</td><td align='left' valign='middle'>Reputation rank (defined in SharedDefines.h, enum ReputationRank)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_TEAM</td><td align='left' valign='middle'>Team ID: 469 for Alliance, 67 for Horde</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_SKILL</td><td align='left' valign='middle'>SkillLine Id (See SkillLine.dbc)</td><td align='left' valign='middle'>Skill value</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_QUESTREWARDED</td><td align='left' valign='middle'>Quest Template ID (See quest_template.id)</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_QUESTTAKEN</td><td align='left' valign='middle'>Quest Template ID (See quest_template.id)</td><td align='left' valign='middle'>0, 1 or 2 (0 any state, 1 if quest incomplete, 2 if quest completed).</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_AD_COMMISSION_AURA</td><td align='left' valign='middle'>0</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_NO_AURA</td><td align='left' valign='middle'>Spell Id (See Spell.dbc)</td><td align='left' valign='middle'>Spell effect index to aura effect.</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_ACTIVE_GAME_EVENT</td><td align='left' valign='middle'>Game Event ID (See game_event.id)</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_AREA_FLAG</td><td align='left' valign='middle'>Area flag</td><td align='left' valign='middle'>Unwanted area flag</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_RACE_CLASS</td><td align='left' valign='middle'>Races Mask (See ChrRaces.dbc)</td><td align='left' valign='middle'>Classes Mask (See ChrClasses.dbc)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_LEVEL</td><td align='left' valign='middle'>Character level</td><td align='left' valign='middle'>0, 1 or 2 (0: equal to, 1: equal or higher than, 2: equal or less than)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_NOITEM</td><td align='left' valign='middle'>Item Template Id (See item-template.id</td><td align='left' valign='middle'>Count (number of items)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_SPELL</td><td align='left' valign='middle'>Spell Id (See Spell.dbc)</td><td align='left' valign='middle'>0 or 1 (0: has spell, 1: hasn’t spell)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_INSTANCE_SCRIPT</td><td align='left' valign='middle'>TODO</td><td align='left' valign='middle'>TODO: Currently Unknown</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_QUESTAVAILABLE</td><td align='left' valign='middle'>Quest Template ID (See quest_template.id)</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_RESERVED_1</td><td align='left' valign='middle'>Reserved for later usage</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_RESERVED_2</td><td align='left' valign='middle'>Reserved for later usage</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_QUEST_NONE</td><td align='left' valign='middle'>Quest Template ID (See quest_template.id)</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_ITEM_WITH_BANK</td><td align='left' valign='middle'>Item Template Id (See item-template.id)</td><td align='left' valign='middle'>Count (number of items required)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_NOITEM_WITH_BANK</td><td align='left' valign='middle'>Item Template Id (See item-template.id)</td><td align='left' valign='middle'>Count (number of items required)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_NOT_ACTIVE_GAME_EVENT</td><td align='left' valign='middle'>Game Event ID (See game_event.id)</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_ACTIVE_HOLIDAY</td><td align='left' valign='middle'>Holiday ID</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_NOT_ACTIVE_HOLIDAY</td><td align='left' valign='middle'>Holiday ID</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_LEARNABLE_ABILITY</td><td align='left' valign='middle'>Spell Id (See Spell.dbc)</td><td align='left' valign='middle'>0 or Item Template Id (See item-template.id) (item entry can be used if you want to check if the player has one (1) item in his/hers inventory or bank)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_SKILL_BELOW</td><td align='left' valign='middle'>SkillLine Id (See SkillLine.dbc)</td><td align='left' valign='middle'>Skill value</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_REPUTATION_RANK_MAX</td><td align='left' valign='middle'>Faction Id (See Faction.dbc</td><td align='left' valign='middle'>Reputation rank (defined in SharedDefines.h, enum ReputationRank)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_RESERVED_3</td><td align='left' valign='middle'>Reserved for later usage</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_SOURCE_AURA</td><td align='left' valign='middle'>Spell Id (See Spell.dbc)</td><td align='left' valign='middle'>Spell effect index to aura effect</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_LAST_WAYPOINT</td><td align='left' valign='middle'>Waypoint ID</td><td align='left' valign='middle'>0: exact, 1: wp <= waypointId, 2: wp > waypointId</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_RESERVED_4</td><td align='left' valign='middle'>Reserved for later usage</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>CONDITION_GENDER</td><td align='left' valign='middle'>0: male, 1: female, 2: none</td><td align='left' valign='middle'>0</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>CONDITION_DEAD_OR_AWAY</td><td align='left' valign='middle'>0: player, 1: group, 2: instance, 3: creature</td><td align='left' valign='middle'>0 or range</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>38</td>
<td>curhealth</td>
<td>The current health of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>39</td>
<td>curmana</td>
<td>The current mana of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>40</td>
<td>currentwaypoint</td>
<td>The current waypoint of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>41</td>
<td>DeathState</td>
<td>The creature's death state. A boolean, 0 = Alive, 1 = Corpse lying dead around (no gossip possible when dead, if you need corpse-gossip use dynamicflags|32) 
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>42</td>
<td>equipment_id</td>
<td>The ID of the equipment that the creature is using (See creature_equip_template.entry).
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>43</td>
<td>guid</td>
<td>A unique identifier given to each creature to distinguish one creature from another. Two creatures can NOT have same GUID. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>44</td>
<td>id</td>
<td>The id of the template that is used when instantiating this creature (See creature_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>45</td>
<td>map</td>
<td>The map id of the location of the creature (See map.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>46</td>
<td>modelid</td>
<td>The model id of the the creature. </td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>47</td>
<td>MovementType</td>
<td>The movement type associated with this creature. Usually the same as creature_template.MovementType but can be different.

The creature default movement type.

¬subtable:30¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>48</td>
<td>orientation</td>
<td>The orientation of the creature. (North = 0.0; South = pi (3.14159))</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>49</td>
<td>position_x</td>
<td>The x position of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>50</td>
<td>position_y</td>
<td>The y position of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>51</td>
<td>position_z</td>
<td>The z position of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>52</td>
<td>spawndist</td>
<td>The maximum distance that the creature should spawn from its spawn point. Also controls how far away the creature can walk from its spawn point if its MovementType = 1. </td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>53</td>
<td>spawntimesecs</td>
<td>The respawn time of the creature in seconds. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>54</td>
<td>auras</td>
<td>This field controls any auras to be applied on the creature (both in effect and visually). The syntax for for an individual aura entry is "&lt;spell ID&gt; &lt;index&gt;". An aura is defined not just by the spell that applies it but also by the individual spell affect that applies it. Therefore, the effect index must be specified along with the spell ID. Each spell can have a maximum of three spell effects, so the effect index can only be 0, 1, or 2. To apply multiple auras, you can add more aura entries, separating each entry by a space. Remember that if a spell applies multiple auras, you need to specify an aura entry for each effect index if you want to apply more than one aura from the same spell. 

List of useful aura entries:<br />

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Aura Entry</b></th>
<th align='left'><b>Meaning</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>16380 0</td><td align='left' valign='middle'>Makes the creature invisible.</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>18950&nbsp;0&nbsp;18950&nbsp;1</td><td align='left' valign='middle'>Makes the creature detect other invisible units (players or creatures).</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>55</td>
<td>b2_0_sheath</td>
<td>SheathState.<br />
<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value1</b></th>
<th align='left'><b>State</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>0</td><td align='left' valign='middle'>All Weapons Sheathed by Default</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>1</td><td align='left' valign='middle'>Melee Weapon NOT Sheathed by Default (Melee Weapon In Hand)</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>2</td><td align='left' valign='middle'>Ranged Weapon NOT Sheathed by Default (Ranged Weapon In Hand)</td></tr>
</table>

</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>56</td>
<td>b2_1_flags</td>
<td>The value here overrides the value for the creature's unit field UNIT_FIELD_BYTES_2.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>57</td>
<td>bytes1</td>
<td>The value here overrides the value for the creature's unit field UNIT_FIELD_BYTES_1. 

List of known values and what their visual effects on the creature 

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value</b></th>
<th align='left'><b>Meaning</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>1</td><td align='left' valign='middle'>Sitting on Ground</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>
2</td><td align='left' valign='middle'>Creature that can fly and are not on the ground appear to have this flag. If they are on the ground, flag is not present.</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>
3</td><td align='left' valign='middle'>Sleep</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>
4</td><td align='left' valign='middle'>Untrackable</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>
7</td><td align='left' valign='middle'>Makes the mob lying dead (combined with empty health bar (dynamicflags = 32) and gray name (dynamicflags = 4) makes the mob to appear dead)</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>
8</td><td align='left' valign='middle'>Makes the mob kneel (need bytes2 = 1)</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>
9</td><td align='left' valign='middle'>Submerges the creature below the ground</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>58</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.

¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>59</td>
<td>guid</td>
<td>Signifies a unique creature guid (See creature.guid). It will affect just that creature whose GUID matches the one specified here.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>60</td>
<td>mount</td>
<td>The model ID of the mount to be used to make the creature appear mounted (See creature_model_info.modelid). The value here overrides the value for the creature's unit field UNIT_FIELD_MOUNTDISPLAYID.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>61</td>
<td>moveflags</td>
<td>Flags controlling how the creature will behave animation-wise while moving. This table is 100% wrong as of 3.1. It is still here for a period of time for reference and to convert values in DB. 

See the proper table under this one 

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value</b></th>
<th><b>Name</b></th>
<th align='left'><b>Comment</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>0</td><td align='center' valign='middle'>MOVEMENTFLAG_NONE</td><td align='left' valign='middle'>Do Nothing</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>1</td><td align='center' valign='middle'>MOVEMENTFLAG_FORWARD</td><td align='left' valign='middle'>instantly teleport creature, then creature move forward animation but no real movement</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>2</td><td align='center' valign='middle'>MOVEMENTFLAG_BACKWARD</td><td align='left' valign='middle'>instantly teleport creature, then creature move back animation but no real movement</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>4</td><td align='center' valign='middle'>MOVEMENTFLAG_STRAFE_LEFT</td><td align='left' valign='middle'>instantly teleport creature, then creature move left animation but no real movement</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>8</td><td align='center' valign='middle'>MOVEMENTFLAG_STRAFE_RIGHT</td><td align='left' valign='middle'>instantly teleport creature, then creature move right animation but no real movement</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>16</td><td align='center' valign='middle'>MOVEMENTFLAG_LEFT</td><td align='left' valign='middle'>creature spin left animation</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>32</td><td align='center' valign='middle'>MOVEMENTFLAG_RIGHT</td><td align='left' valign='middle'>then creature spin right animation</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>64</td><td align='center' valign='middle'>MOVEMENTFLAG_PITCH_UP</td><td align='left' valign='middle'>no effect on creature</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>128</td><td align='center' valign='middle'>MOVEMENTFLAG_PITCH_DOWN</td><td align='left' valign='middle'>no effect on creature</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>256</td><td align='center' valign='middle'>MOVEMENTFLAG_WALK_MODE</td><td align='left' valign='middle'>If flag is not set then player runs</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>512</td><td align='center' valign='middle'>MOVEMENTFLAG_ONTRANSPORT</td><td align='left' valign='middle'>causes creatures to fly while moving (not include standing)</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>1024</td><td align='center' valign='middle'>MOVEMENTFLAG_LEVITATING</td><td align='left' valign='middle'>hovering animation at stand (not include moving)</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>2048</td><td align='center' valign='middle'>MOVEMENTFLAG_ROOT</td><td align='left' valign='middle'>Rooted</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>4096</td><td align='center' valign='middle'>MOVEMENTFLAG_JUMPING</td><td align='left' valign='middle'>Jump animation</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>8192</td><td align='center' valign='middle'>MOVEMENTFLAG_FALLING</td><td align='left' valign='middle'>Falling animation</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>16384</td><td align='center' valign='middle'>MOVEMENTFLAG_FALLINGFAR</td><td align='left' valign='middle'>Falling Great distance animation</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>32768</td><td align='center' valign='middle'>MOVEMENTFLAG_UNK2</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>65536</td><td align='center' valign='middle'>MOVEMENTFLAG_UNK3</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>131072</td><td align='center' valign='middle'>MOVEMENTFLAG_UNK4</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>262144</td><td align='center' valign='middle'>MOVEMENTFLAG_UNK5</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>524288</td><td align='center' valign='middle'>MOVEMENTFLAG_UNK6</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>1048576</td><td align='center' valign='middle'>MOVEMENTFLAG_UNK7</td><td align='left' valign='middle'>Causes creature to instantly appear at new position</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>2097152</td><td align='center' valign='middle'>MOVEMENTFLAG_SWIMMING</td><td align='left' valign='middle'>appears with fly flag also (causes creatures to fall to ground at stand state)</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>4194304</td><td align='center' valign='middle'>MOVEMENTFLAG_ASCENDING</td><td align='left' valign='middle'>no effect on creature</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>8388608</td><td align='center' valign='middle'>MOVEMENTFLAG_CAN_FLY</td><td align='left' valign='middle'>no effect on creature</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>16777216</td><td align='center' valign='middle'>MOVEMENTFLAG_FLYING</td><td align='left' valign='middle'>no effect on creature</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>33554432</td><td align='center' valign='middle'>MOVEMENTFLAG_ONTRANSPORT</td><td align='left' valign='middle'>Creature flying (not hover at stop moving)</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>67108864</td><td align='center' valign='middle'>MOVEMENTFLAG_SPLINE</td><td align='left' valign='middle'>probably wrong name (no effect on creature)</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>134217728</td><td align='center' valign='middle'>MOVEMENTFLAG_SPLINE2</td><td align='left' valign='middle'>no effect on creature</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>268435456</td><td align='center' valign='middle'>MOVEMENTFLAG_WATERWALKING</td><td align='left' valign='middle'>also prevent creature from falling under water</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>536870912</td><td align='center' valign='middle'>MOVEMENTFLAG_SAFE_FALL</td><td align='left' valign='middle'>active rogue safe fall spell (passive) (no effect on creature)</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>1073741824</td><td align='center' valign='middle'>MOVEMENTFLAG_HOVER</td><td align='left' valign='middle'>Causes creature to hover at stand state (not include moving)</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>2147483648</td><td align='center' valign='middle'>MOVEMENTFLAG_UNK10</td><td align='left' valign='middle'>Causes creature to roll to strange angle Note: MONSTER_MOVE_SPLINE_FLY = MONSTER_MOVE_WALK + MONSTER_MOVE_SPLINE and makes creature fly by points.</td></tr>
</table>


Note: MONSTER_MOVE_SPLINE_FLY = MONSTER_MOVE_WALK + MONSTER_MOVE_SPLINE and makes creature fly by points. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>62</td>
<td>action1_param1</td>
<td>Parameter 1 of the action1_type (See creature_ai_scripts.action1_type)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>63</td>
<td>action1_param2</td>
<td>Parameter 2 of the action1_type (See creature_ai_scripts.action1_type)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>64</td>
<td>action1_param3</td>
<td>Parameter 3 of the action1_type (See creature_ai_scripts.action1_type)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>65</td>
<td>action1_type</td>
<td>The first actiontype<br />

Before we start to list and explain the different actions that can be taken, we must first look at how the eventAI targeting system works. Due to technical reasons in how targetting is handled, the eventAI script cannot target anything or anyone that is not in its threat list or is not the scripted creature itself. It also can't currently target anyone specific in its threat list except by their position in the threat list. However, even then it can only target specifically the current victim, the second unit in its threat list, and the last unit in its threat list. It can also target units in its threat list at random and has two options for that: anyone in its threat list at random, or anyone in its threat list excluding the unit with the most threat. Aside from all of those external targets, the script can always target itself. More information on the target types can be found in the reference tables at the end of this guide.

One last note before we start looking at individual actions is about the texts. The eventAI script has support for localized text entries. Therefore, you can define what the mob will say in more than one language all in another table and the script will show the corresponding localized text to the corresponding client (english text to enUS/enGB clients, german text to deDE clients, etc). All of the localized text entries will have a unique text ID assigned to them and it is that text ID that will be used by any actions that require textual input.

<br />
<pre>
* *0 = ACTION&#95;T&#95;NONE*: Does nothing!

* *1 = ACTION&#95;T&#95;SAY*: Displays the -TextId as defined. In case -TextId2 and optionally -TextId3, the output will be randomized. Type text are defined in the "eventai_texts":eventai_texts table (say, yell, whisper, etc) along with other options for the text. All values are required to be negative.
** Parameter 1: The entry of the text that the NPC should use from "eventai_texts":eventai_texts table. Optionally a entry from other tables can be used (such as "custom_texts":custom_texts).Entry are required to be negative and exist in a &#42;&#95;texts-table. The type text to be displayed are defined in the texts-table itself (Say, Yell, Whisper, Emote Text, Boss Whisper, Boss Emote)Other options are also to be defined in the texts-table, such as a sound to be heard with the text and the language used in output (common, dwarvish, etc).In case this entry has a localized version of the text, the localized text will be displayed in client that support this locale.
** Parameter 2: Optional. TextId can be defined in addition. The same apply to this as explained above, however eventAI will randomize between the two.
** Parameter 3: Optional, if Parameter 2 exist. In this case, eventAI will randomize between three.

* *2 = ACTION&#95;T&#95;YELL*: UNUSED

* *3 = ACTION&#95;T&#95;TEXTEMOTE*: UNUSED

* *4 = ACTION&#95;T&#95;SOUND*: When activated, the creature will play the specified sound.
** Parameter 1: The sound ID to be played. Sound IDs are contained in the DBC files.

* *5 = ACTION&#95;T&#95;EMOTE*: When activated, the creature will perform a visual emote. Unlike a text emote, a visual emote is one where the creature will actually move or perform a gesture.
** Parameter 1: The emote ID that the creature should perform. Emote IDs are also contained in the DBC but they can be found in the mangos source as well.

* *6 = ACTION&#95;T&#95;RANDOM&#95;SAY*: UNUSED

* *7 = ACTION&#95;T&#95;RANDOM&#95;YELL*: UNUSED

* *8 = ACTION&#95;T&#95;RANDOM&#95;TEXTEMOTE*: UNUSED

* *9 = ACTION&#95;T&#95;RANDOM&#95;SOUND*: Similar to the ACTION&#95;T&#95;SOUND action, when this action is activated, it will choose at random a sound to play. This action needs all three parameters to be filled and it will pick a random entry from the three. NOTE: (1)
** Parameter 1: The sound ID to be played as choice one.
** Parameter 2: The sound ID to be played as choice two.
** Parameter 3: The sound ID to be played as choice three.

* *10 = ACTION&#95;T&#95;RANDOM&#95;EMOTE*: Similar to the ACTION&#95;T&#95;EMOTE action, when this action is activated, it will choose at random an emote ID to emote visually. This action needs all three parameters to be filled and it will pick a random entry from the three. NOTE: (1)
** Parameter 1: The emote ID that the creature should perform as choice one.
** Parameter 2: The emote ID that the creature should perform as choice two.
** Parameter 3: The emote ID that the creature should perform as choice three.

* *11 = ACTION&#95;T&#95;CAST*: When activated, the creature will cast a spell specified by a spell ID on a target specified by the target type.
** Parameter 1: The spell ID to use for the cast. The value used in this field needs to be a valid spell ID.
** Parameter 2: The target type defining who the creature should cast on. The value in this field needs to be a valid target type as specified in the reference tables below.
** Parameter 3: See "spell flags":creature_ai_scripts#cast-flags. If it is 1, then the spell cast will interrupt any spells that are already in the progress of being casted; otherwise if the creature is already casting a spell and this field is 0, then this action will be skipped.

* *12 = ACTION&#95;T&#95;SUMMON*: When activated, the creature will summon another creature at the same spot as itself that will attack the specified target.
** Parameter 1: The creature template ID to be summoned. The value here needs to be a valid creature template ID.
** Parameter 2: The target type defining who the summoned creature will attack. The value in this field needs to be a valid target type as specified in the reference tables below. NOTE: Using target type 0 will cause the summoned creature to not attack anyone.
** Parameter 3: The duration until the summoned creature should be unsummoned. The value in this field is in milliseconds or 0. If zero, then the creature will not be unsummoned until it leaves combat, but only works with t&#95;type !=0.

* *13 = ACTION&#95;T&#95;THREAT&#95;SINGLE&#95;PCT*: When activated, this action will modify the threat of a target in the creature's threat list by the specified percent.
** Parameter 1: Threat percent that should be modified. The value in this field can range from -100 to +100. If it is negative, threat will be taken away and if positive, threat will be added.
** Parameter 2: The target type defining on whom the threat change should occur. The value in this field needs to be a valid target type as specified in the reference tables below.

* *14 = ACTION&#95;T&#95;THREAT&#95;ALL&#95;PCT*: When activated, this action will modify the threat for everyone in the creature's threat list by the specified percent.
** Parameter 1: The percent that should be used in modifying everyone's threat in the creature's threat list. The value here can range from -100 to +100. NOTE: Using -100 will cause the creature to reset everyone's threat to 0 so that everyone has the same amount of threat. It does NOT make any changes as to who is in the threat list.

* *15 = ACTION&#95;T&#95;QUEST&#95;EVENT*: When activated, this action will satisfy the external completion requirement for the quest for the specified target defined by the target type. This action can only be used with player targets so it must be ensured that the target type will point to a player.
** Parameter 1: The quest template ID. The value here must be a valid quest template ID. Furthermore, the quest should have SpecialFlags &#124; 2 as it would need to be completed by an external event which is the activation of this action.
** Parameter 2: The target type defining whom the quest should be completed for. The value in this field needs to be a valid target type as specified in the reference tables below.

* *16 = ACTION&#95;T&#95;CASTCREATUREGO*: When activated, this action will call CastedCreatureOrGO() function for the player. It can be used to give quest credit for casting a spell on the creature.
** Parameter 1: The quest template ID. The value here must be a valid quest template ID.
** Parameter 2: The spell ID to use to simulate the cast. The value used in this field needs to be a valid spell ID.
** Parameter 3: The target type defining whom the quest credit should be given to. The value in this field needs to be a valid target type as specified in the reference tables below.

* *17 = ACTION&#95;T&#95;SET&#95;UNIT&#95;FIELD*: When activated, this action can change the target's unit field values. More information on the field value indeces can be found at "character data":character data.
** Parameter 1: The index of the field number to be changed. Use "character data":character data for a list of indeces and what they control. Note that a creature shares the same indeces with a player except for the PLAYER&#95;&#42; ones.
** Parameter 2: The new value to be put in the field.
** Parameter 3: The target type defining for whom the unit field should be changed. The value in this field needs to be a valid target type as specified in the reference tables below.

* *18 = ACTION&#95;T&#95;SET&#95;UNIT&#95;FLAG*: When activated, this action changes the target's "flags":https://github.com/cmangos/issues/wiki/Creature_template#unitflags by adding (turning on) more flags. For example, this action can make the creature unattackable/unselectable if the right flags are used.
** Parameter 1: The flag(s) to be set. Multiple flags can be set by using bitwise-OR on them (adding them together).
** Parameter 2: The target type defining for whom the flags should be changed. The value in this field needs to be a valid target type as specified in the reference tables below.

* *19 = ACTION&#95;T&#95;REMOVE&#95;UNIT&#95;FLAG*: When activated, this action changes the target's flags by removing (turning off) flags. For example, this action can make the creature normal after it was unattackable/unselectable if the right flags are used.
** Parameter 1: The flag(s) to be removed. Multiple flags can be set by using bitwise-OR on them (adding them together).
** Parameter 2: The target type defining for whom the flags should be changed. The value in this field needs to be a valid target type as specified in the reference tables below.

* *20 = ACTION&#95;T&#95;AUTO&#95;ATTACK*: This action controls whether or not the creature should stop or start the auto melee attack.
** Parameter 1: If zero, then the creature will stop its melee attacks. If non-zero, then the creature will either continue its melee attacks (the action would then have no effect) or it will start its melee attacks on the target with the top threat if its melee attacks were previously stopped.

* *21 = ACTION&#95;T&#95;COMBAT&#95;MOVEMENT*: This action controls whether or not the creature will always move towards its target.
** Parameter 1: If zero, then the creature will stop moving towards its victim (if its victim gets out of melee range) and will be stationary. If non-zero, then the creature will either continue to follow its victim (the action would have no effect) or it will start to follow the target with the top threat if its movement was disabled before.

* *22 = ACTION&#95;T&#95;SET&#95;PHASE*: When activated, this action sets the creature's event to the specified value.
** Parameter 1: The new phase to set the creature in. This number must be an integer between 0 and 31 inclusive.

* *23 = ACTION&#95;T&#95;INC&#95;PHASE*: When activated, this action will increase (or decrease) the current creature's phase.
** Parameter 1: The number of phases to increase or decrease. Use negative values to decrease the current phase. After increasing or decreasing the phase by this action, the current phase must not be lower than 0 or exceed 31.

* *24 = ACTION&#95;T&#95;EVADE*: When activated, the creature will immediately exit out of combat, clear its threat list, and move back to its spawn point. Basically, this action will reset the whole encounter.

* *25 = ACTION&#95;T&#95;FLEE*: When activated, the creature will try to flee from combat. Currently this is done by it casting a fear-like spell on itself called &quot;Run Away&quot;.

* *26 = ACTION&#95;T&#95;QUEST&#95;EVENT&#95;ALL*: This action does the same thing as the ACTION&#95;T&#95;QUEST&#95;EVENT does but it does it for all players in the creature's threat list. Note that if a player is not in its threat list for whatever reason, he/she won't get the quest completed.
** Parameter 1: The quest ID to finish for everyone.

* *27 = ACTION&#95;T&#95;CASTCREATUREGO&#95;ALL*: This action does the same thing as the ACTION&#95;T&#95;CASTCREATUREGO does but it does it for all players in the creature's threat list. Note that if a player is not in its threat list for whatever reason, he/she won't receive the cast emulation.
** Parameter 1: The quest template ID.
** Parameter 2: The spell ID used to simulate the cast.

* *28 = ACTION&#95;T&#95;REMOVEAURASFROMSPELL*: This action will remove all auras from a specific spell from the target.
** Parameter 1: The target type defining for whom the unit field should be changed. The value in this field needs to be a valid target type as specified in the reference tables below.
** Parameter 2: The spell ID whose auras will be removed.

* *29 = ACTION&#95;T&#95;RANGED&#95;MOVEMENT*: This action changes the movement type generator to ranged type using the specified values for angle and distance. Note that specifying zero angle and distance will make it just melee instead.
** Parameter 1: The distance the mob should keep between it and its target.
** Parameter 2: The angle the mob should use.

* *30 = ACTION&#95;T&#95;RANDOM&#95;PHASE*: Randomly sets the phase to one from the three parameter choices. NOTE: (1)
** Parameter 1: A possible random phase choice.
** Parameter 2: A possible random phase choice.
** Parameter 3: A possible random phase choice.

* *31 = ACTION&#95;T&#95;RANDOM&#95;PHASE&#95;RANGE*: Randomly sets the phase between a range of phases controlled by the parameters.
** Parameter 1: The minimum of the phase range.
** Parameter 2: The maximum of the phase range. The number here must be greater than the one in parameter 1.

* *32 = ACTION&#95;T&#95;SUMMON*: Summons a creature using the data specified in the separate "summons":creature_ai_summons table.
** Parameter 1: The creature template ID to be summoned. The value here needs to be a valid creature template ID.
** Parameter 2: The target type defining who the summoned creature will attack. The value in this field needs to be a valid target type as specified in the reference tables below. NOTE: Using target type 0 will cause the summoned creature to not attack anyone.
** Parameter 3: The summon ID from the eventai&#95;summons table controlling the position (and spawntime) where the summoned mob should be spawned at.

* *33 = ACTION&#95;T&#95;KILLED&#95;MONSTER*: When activated, this action will call KilledMonster() function for the player. It can be used to give creature credit for killing a creature (note that it can be ANY creature including certain quest specific triggers). In general if the quest is set to be accompished on different creatures (e.g. &quot;Credit&quot; templates).
** Parameter 1: The creature template ID. The value here must be a valid creature template ID.
** Parameter 2: The target type defining whom the quest kill count should be given to. The value in this field needs to be a valid target type as specified in the reference tables below.

* *34 = ACTION&#95;T&#95;SET&#95;INST&#95;DATA*: Sets data for the instance. Note that this will only work when the creature is inside an instantiable zone that has a valid script (ScriptedInstance) assigned.
** Parameter 1: The field to change in the instance script. Again, this field needs to be a valid field that has been already defined in the instance's script.
** Parameter 2: The value to put at that field index. The number here must be a valid 32 bit number.

* *35 = ACTION&#95;T&#95;SET&#95;INST&#95;DATA64*: Sets GUID (64 bits) data for the instance based on the target. Note that this will only work when the creature is inside an instantiable zone that has a valid script (ScriptedInstance) assigned.
** Parameter 1: The field to change in the instance script. Again, this field needs to be a valid field that has been already defined in the instance's script.
** Parameter 2: The target type to use to get the GUID that will be stored at the field index. The value in this field needs to be a valid target type as specified in the reference tables below.

* *36 = ACTION&#95;T&#95;UPDATE&#95;TEMPLATE*: This function temporarily changes creature entry to new entry, display is changed, loot is changed, but AI is not changed. At respawn creature will be reverted to original entry.
** Parameter 1: The creature template ID. The value here must be a valid creature template ID.
** Parameter 2: Use model&#95;id from team : Alliance(0) or Horde (1).

* *37 = ACTION&#95;T&#95;DIE*: Kills the creature

* *38 = ACTION&#95;T&#95;ZONE&#95;COMBAT&#95;PULSE*: Places all players within the instance into combat with the creature. Only works in combat and only works inside of instances.

* *39 = ACTION&#95;T&#95;CALL&#95;FOR&#95;HELP*: Call any friendly creatures (if its not in combat/etc) in radius attack creature target.
** Parameter 1: Radius from creature.

* *40 = ACTION&#95;T&#95;SET&#95;SHEATH*: Let set sheath state for creature (0-no weapon show (not used mostly by creatures), 1-melee weapon show, 2-ranged weapon show)
** Parameter 1: Sheath state of the creature.

* *41 = ACTION&#95;T&#95;FORCE&#95;DESPAWN*: Despawns the creature.
** Parameter 1: Despawn delay.
</pre>
(1) = Use -1 to specify that if this param is picked to do nothing. Random is constant between actions within an event. So if you have a random Yell and a random Sound they will match up (ex: param2 with param2)
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>66</td>
<td>action2_param1</td>
<td>Parameter 1 of action2_type (See creature_ai_scripts.action2_type)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>67</td>
<td>action2_param2</td>
<td>Parameter 2 of action2_type (See creature_ai_scripts.action2_type)zzzz</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>68</td>
<td>action2_param3</td>
<td>Parameter 3 of action2_type (See creature_ai_scripts.action2_type)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>69</td>
<td>action2_type</td>
<td>The Second actiontype (See creature_ai_scripts.action2_type)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>70</td>
<td>action3_param1</td>
<td>Parameter 1 of action3_type (See creature_ai_scripts.action3_type)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>71</td>
<td>action3_param2</td>
<td>Parameter 2 of action3_type (See creature_ai_scripts.action3_type)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>72</td>
<td>action3_param3</td>
<td>Parameter 3 of action3_type (See creature_ai_scripts.action3_type)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>73</td>
<td>action3_type</td>
<td>The Third actiontype (See creature_ai_scripts.action3_type)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>74</td>
<td>comment</td>
<td>Documents what an event script is supposed to do. It has been defined that comments should use the form: ‘Creature/GameObject name - Cast Spellname’.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>75</td>
<td>creature_id</td>
<td>This references the Unique ID in the Creature Template table (See creature_template.id) for which the entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>76</td>
<td>event_chance</td>
<td>The percentage chance for this event to happen. Values have to be between 1 and 100.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>77</td>
<td>event_flags</td>
<td>Event flags allow you to modify how events are executed.<br />

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value</b></th>
<th><b>Type</b></th>
<th align='left'><b>Description</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>1</td><td align='center' valign='middle'>EFLAG_REPEATABLE</td><td align='left' valign='middle'>Event repeats (Does not repeat if this flag is not set)</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>2</td><td align='center' valign='middle'>EFLAG_RESERVED_1</td><td align='left' valign='middle'>Unused</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>4</td><td align='center' valign='middle'>EFLAG_RESERVED_2</td><td align='left' valign='middle'>Unused</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>8</td><td align='center' valign='middle'>EFLAG_RESERVED_3</td><td align='left' valign='middle'>Unused</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>16</td><td align='center' valign='middle'>EFLAG_RESERVED_4</td><td align='left' valign='middle'>Unused</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>32</td><td align='center' valign='middle'>EFLAG_RANDOM_ACTION</td><td align='left' valign='middle'>At event occur execute one random action from event actions instead all actions.</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>64</td><td align='center' valign='middle'>EFLAG_RESERVED_6</td><td align='left' valign='middle'>Unused</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>128</td><td align='center' valign='middle'>EFLAG_DEBUG_ONLY</td><td align='left' valign='middle'>Event only occurs in debug builds</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>79</td>
<td>event_param1</td>
<td>Parameter Value 1 for the eventtype (See creature_ai_scripts.event_type).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>80</td>
<td>event_param2</td>
<td>Parameter Value 2 for the eventtype (See creature_ai_scripts.event_type).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>81</td>
<td>event_param3</td>
<td>Parameter Value 3 for the eventtype (See creature_ai_scripts.event_type).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>82</td>
<td>event_param4</td>
<td>Parameter Value 4 for the eventtype (See creature_ai_scripts.event_type).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>83</td>
<td>event_type</td>
<td>Event Type ID, from one of the Events below:

<hr />
<pre>
* *0 = EVENT&#95;T&#95;TIMER*: COMBAT ONLY! - Expires first between (Param1) and (Param2) and then between every (Param3) and (Param4).
** Parameter 1: InitialMin
** Parameter 2: InitialMax
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *1 = EVENT&#95;T&#95;TIMER&#95;OOC*: OUT OF COMBAT - Expires first between (Param1) and (Param2) and then between every (Param3) and (Param4).
** Parameter 1: InitialMin
** Parameter 2: InitialMax
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *2 = EVENT&#95;T&#95;HP*: Expires when HP is between (Param1) and (Param2). Will repeat every (Param3) and (Param4).
** Parameter 1: HPMax%
** Parameter 2: HPMin%
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *3 = EVENT&#95;T&#95;MANA*: Expires once Mana% is between (Param1) and (Param2). Will repeat every (Param3) and (Param4).
** Parameter 1: ManaMax%
** Parameter 2: ManaMin%
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *4 = EVENT&#95;T&#95;AGGRO*: Expires upon initial aggro (does not repeat).

* *5 = EVENT&#95;T&#95;KILL*: Expires upon killing a player. Will repeat every (Param1) and (Param2).
** Parameter 1: RepeatMin
** Parameter 2: RepeatMax

* *6 = EVENT&#95;T&#95;DEATH*: Expires upon Death.

* *7 = EVENT&#95;T&#95;EVADE*: Expires upon creature EnterEvadeMode().

* *8 = EVENT&#95;T&#95;SPELLHIT*: Expires upon Spell hit. If (param1) is set will only expire on that spell. If (param2) will only expire on spells of that school. Will repeat every (Param3) and (Param4) .
** Parameter 1: SpellID
** Parameter 2: School
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *9 = EVENT&#95;T&#95;RANGE*: Expires when the highest threat target distance is greater than (Param1) and less than (Param2). Will repeat every (Param3) and (Param4) .
** Parameter 1: MinDist
** Parameter 2: MaxDist
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *10 = EVENT&#95;T&#95;OOC&#95;LOS*: Expires when a Player moves within visible distance to creature. Does not expire for Hostile Players if (Param1) is not 0. Does not expire for Friendly Players if (Param2) is not 0. Will repeat every (Param3) and (Param4) . Does not expire for creatures or pet or when the creature is in combat.
** Parameter 1: NoHostile
** Parameter 2: NoFriendly
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *11 = EVENT&#95;T&#95;SPAWNED*: Expires at initial spawn and at creature respawn (useful for setting ranged movement type)

* *12 = EVENT&#95;T&#95;TARGET&#95;HP*: Expires when Current Target's HP is between (Param1) and (Param2). Will repeat every (Param3) and (Param4) .
** Parameter 1: HPMax%
** Parameter 2: HPMin%
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *13 = EVENT&#95;T&#95;TARGET&#95;CASTING*: Expires when the player is casting a spell. Will repeat every (Param1) and (Param2) .
** Parameter 1: RepeatMin
** Parameter 2: RepeatMax

* *14 = EVENT&#95;T&#95;FRIENDLY&#95;HP*: Expires when a friendly unit in radius(param2) has at least (param1) hp missing. Will repeat every (Param3) and (Param4) .
** Parameter 1: HPDeficit
** Parameter 2: Radius
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *15 = EVENT&#95;T&#95;FRIENDLY&#95;IS&#95;CC*: Expires when a friendly unit is Crowd controlled within the given radius (param2). Will repeat every (Param3) and (Param4) .
** Parameter 1: DispelType
** Parameter 2: Radius
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *16 = EVENT&#95;T&#95;MISSING&#95;BUFF*: Expires when a friendly unit is missing aura's given by spell (param1) within radius (param2). Will repeat every (Param3) and (Param4) .
** Parameter 1: SpellId
** Parameter 2: Radius
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *17 = EVENT&#95;T&#95;SUMMONED&#95;UNIT*: Expires after creature with entry(Param1) is spawned or for all spawns if param1 = 0. Will repeat every (Param2) and (Param3) .
** Parameter 1: CreatureId
** Parameter 2: RepeatMin
** Parameter 3: RepeatMax

* *18 = EVENT&#95;T&#95;TARGET&#95;MANA*:
** Parameter 1: ManaMax%
** Parameter 2: ManaMin%
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *21 = EVENT&#95;T&#95;REACHED&#95;HOME*: Expires when creature reach it's home(spawn) location after Evade.

* *22 = EVENT&#95;T&#95;RECEIVE&#95;EMOTE*: Expires when creature receive emote with text emote id(enum TextEmotes). Condition can be defined. If set, then most conditions has additional value <font color="blue">(see table enum ConditionType below.)</font>
** Parameter 1: EmoteId
** Parameter 2: Condition
** Parameter 3: CondValue1
** Parameter 4: CondValue2

* *23 = EVENT&#95;T&#95;BUFFED*: Expires when creature have spell (Param1) auras applied stack greater or equal provided in Param2 amount. Will repeat every (Param3) and (Param4).
** Parameter 1: SpellId
** Parameter 2: AmmountInStack
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *24 = EVENT&#95;T&#95;TARGET&#95;BUFFED*: Expires when target unit have spell (Param1) auras applied stack greater or equal provided in Param2 amount. Will repeat every (Param3) and (Param4).
** Parameter 1: SpellId
** Parameter 2: AmmountInStack
** Parameter 3: RepeatMin
** Parameter 4: RepeatMax

* *25 = EVENT&#95;T&#95;SUMMONED&#95;JUST&#95;DIED*: Expires after creature with entry(Param1) is die or for all spawns if param1 = 0. Will repeat every (Param2) and (Param3) .
** Parameter 1: CreatureId
** Parameter 2: RepeatMin
** Parameter 3: RepeatMax

* *26 = EVENT&#95;T&#95;SUMMONED&#95;JUST&#95;DESPAWN*: Expires before creature with entry(Param1) is despawned or for all spawns if param1 = 0. Will repeat every (Param2) and (Param3) .
** Parameter 1: CreatureId
** Parameter 2: RepeatMin
** Parameter 3: RepeatMax
</pre>
Now that all of the supported events have been listed and described, we shall now move on to the actions that can be performed. Each event can take up to three actions. The actions will all be performed when the event is triggered and they will be performed in the order that they have been defined. This means that, for a certain event, action 1 will be performed first, followed by action 2, then lastly by action 3. Just like event definitions, each action can use up to three different parameters but not all actions will use all three parameters. If a parameter isn't mentioned for an action, then that action does not need that parameter.
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>84</td>
<td>id</td>
<td>The unique identifier for the AI script entry. To ease development, it has been defined that the identifier always equals the creature_template.entry * 100 (See creature_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>85</td>
<td>comment</td>
<td>Documents what kind of creature will be summoned. Currently it is common to use the summoned creature’s Creature Template Entry value (See creature_template.entry) to describe what is summoned.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>86</td>
<td>id</td>
<td>This references the third action parameter in the Creature_ai_scripts table entry (See creature_ai_scripts.entry) with a summon action assigned.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>87</td>
<td>orientation</td>
<td>The orientation for the creature to be spawned.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>88</td>
<td>position_x</td>
<td>The X position for the creature to be spawned.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>89</td>
<td>position_y</td>
<td>The Y position for the creature to be spawned.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>90</td>
<td>position_z</td>
<td>The Z position for the creature to be spawned.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>91</td>
<td>spawntimesecs</td>
<td>The despawn timer for the summoned creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>92</td>
<td>comment</td>
<td>This documents the creature text. Currently there are no hard or fast rules for the format of the comment. 
It should help identifying who and why does perform the emote.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>93</td>
<td>content_default</td>
<td>Contains the text presented in the default language English. Strings may contain special variables which are replaced with creature or character data. The following table lists available variables.
¬subtable:21¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>94</td>
<td>content_loc1</td>
<td>Korean localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>95</td>
<td>content_loc2</td>
<td>French localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>96</td>
<td>content_loc3</td>
<td>German localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>97</td>
<td>content_loc4</td>
<td>Chinese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>98</td>
<td>content_loc5</td>
<td>Taiwanese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>99</td>
<td>content_loc6</td>
<td>Spanish (Spain) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>100</td>
<td>content_loc7</td>
<td>Spanish (Latin America) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>101</td>
<td>content_loc8</td>
<td>Russian localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>102</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.
¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>103</td>
<td>entry</td>
<td>This references a script using an action of the type ACTION_T_TEXT in the Creature AI Scripts table tables entry (See creature_ai_scripts).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>104</td>
<td>language</td>
<td>A language identifier. The value has to match with a language identifier (See Languages.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>105</td>
<td>sound</td>
<td>A sound identifier. The value has to match with a sound identifier (See SoundEntries.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>106</td>
<td>type</td>
<td>The type of message to display. The following table lists all valid types.

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value</b></th>
<th align='left'><b>Description</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>0</td><td align='left' valign='middle'>Say</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>1</td><td align='left' valign='middle'>Yell</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>2</td><td align='left' valign='middle'>Text emote</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>3</td><td align='left' valign='middle'>Boss emote</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>4</td><td align='left' valign='middle'>Whisper</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>5</td><td align='left' valign='middle'>Boss whisper</td></tr>
</table></td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>107</td>
<td>event1</td>
<td>Main Event.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>108</td>
<td>event2</td>
<td>Sub Event.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>109</td>
<td>guid</td>
<td>A unique identifier given to each creature to distinguish one creature from another. Two creatures can NOT have same GUID. This GUID is linked to the creature-table.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>110</td>
<td>entry</td>
<td>Unique Id of the equipment, no link with any official data. This id is free. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>111</td>
<td>equipentry1</td>
<td>This is the item of the equipment used in the right hand (See Item.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>112</td>
<td>equipentry2</td>
<td>This is the item of the equipment used in the left hand (See Item.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>113</td>
<td>equipentry3</td>
<td>This is the item of the equipment used in the distance slot (See Item.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>114</td>
<td>entry</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>115</td>
<td>equipinfo1</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>116</td>
<td>equipinfo2</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>117</td>
<td>equipinfo3</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>118</td>
<td>equipmodel1</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>119</td>
<td>equipmodel2</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>120</td>
<td>equipmodel3</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>121</td>
<td>equipslot1</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>122</td>
<td>equipslot2</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>123</td>
<td>equipslot3</td>
<td>Deprecated Table</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>124</td>
<td>id</td>
<td>The ID of the creature (See creature_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>125</td>
<td>quest</td>
<td>The quest ID that the creature finishes (See quest_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>126</td>
<td>class</td>
<td>The class of the item template.<br /><br />
¬subtable:16¬

</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>127</td>
<td>displayid</td>
<td>A display model identifier for the Item. 
This references an DisplayInfo entry (See itemDisplayInfo.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>128</td>
<td>entry</td>
<td>The unique identifier of the item template entry (See item_template).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>129</td>
<td>inventory_type</td>
<td>Defines if and in which slot an item can be equipped. The following table shows all allowed values.<br /><br />
¬subtable:18¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>130</td>
<td>material</td>
<td>The material that the item is made of. The value here affects the sound the item uses when moved in bags. Use -1 for consumable items like food, reagents, etc. This references a material identifier (See Material.dbc).<br />
<br />
The following table contains valid material identifiers.<br />
¬subtable:19¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>131</td>
<td>sheath_type</td>
<td>The value of this field controls how characters will show or hide items worn, e.g. for weapons. The following table shows a list of supported sheath types.<br />
<br />
¬subtable:20¬
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>132</td>
<td>subclass</td>
<td>The subclass of the item template.<br /><br/>
¬subtable:17¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>133</td>
<td>flag</td>
<td>This flag determines how a linked creature will act, when the master is changing it’s combat state. 
Flags provide support for combat state, non combat state and life state.

The following flags determine the behaviour if the master is in combat state.

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value</b></th>
<th align='left'><b>Flag Name</b></th>
<th align='left'><b>Description</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>1</td><td align='left' valign='middle'>FLAG_AGGRO_ON_AGGRO</td><td align='left' valign='middle'>the slave aggroes when the master aggroes</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>2</td><td align='left' valign='middle'>FLAG_TO_AGGRO_ON_AGGRO</td><td align='left' valign='middle'>the master aggroes when the slave aggroes</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>4</td><td align='left' valign='middle'>FLAG_RESPAWN_ON_EVADE</td><td align='left' valign='middle'>the slave respawns when the master evades</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>8</td><td align='left' valign='middle'>FLAG_TO_RESPAWN_ON_EVADE</td><td align='left' valign='middle'>the master respawns when the slave evades</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>16</td><td align='left' valign='middle'>FLAG_DESPAWN_ON_DEATH</td><td align='left' valign='middle'>the slave despawns when the master dies</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>32</td><td align='left' valign='middle'>FLAG_SELFKILL_ON_DEATH</td><td align='left' valign='middle'>the slave goes suicide when the master dies</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>64</td><td align='left' valign='middle'>FLAG_RESPAWN_ON_DEATH</td><td align='left' valign='middle'>the slave respawn when the master dies</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>128</td><td align='left' valign='middle'>FLAG_RESPAWN_ON_RESPAWN</td><td align='left' valign='middle'>the slave respawns on master respawn</td></tr>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>256</td><td align='left' valign='middle'>FLAG_DESPAWN_ON_RESPAWN</td><td align='left' valign='middle'>the slave despawns on master respawn</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>4096</td><td align='left' valign='middle'>FLAG_DESPAWN_ON_EVADE</td><td align='left' valign='middle'>the slave despawn after the master evade</td></tr>
<tr bgcolor='#FFFFEE'></tr>
</table>

<br />
The following flags determine the behaviour if the master is out of combat state.

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value</b></th>
<th align='left'><b>Flag Name</b></th>
<th align='left'><b>Description</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>512</td><td align='left' valign='middle'>FLAG_FOLLOW</td><td align='left' valign='middle'>the slave follows the master</td></tr>
<tr bgcolor='#FEFEFF'></tr>
<tr bgcolor='#FFFFEE'></tr>
</table>

<br />
The following flags determine the behaviour for any combat state.

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th><b>Value</b></th>
<th align='left'><b>Flag Name</b></th>
<th align='left'><b>Description</b></th>
<tr bgcolor='#FFFFEE'><td align='center' valign='middle'>1024</td><td align='left' valign='middle'>FLAG_CANT_SPAWN_IF_BOSS_DEAD</td><td align='left' valign='middle'>the slave cannot respawn while boss is dead</td></tr>
<tr bgcolor='#FEFEFF'><td align='center' valign='middle'>2048</td><td align='left' valign='middle'>FLAG_CANT_SPAWN_IF_BOSS_ALIVE</td><td align='left' valign='middle'>the slave cannot respawn while boss is alive</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>134</td>
<td>guid</td>
<td>This references the “creature” table tables unique ID for which the entry is valid (See creature.entry). 
<br />This is a creature spawn bound to the master creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>135</td>
<td>master_guid</td>
<td>This references the “creature” table tables unique ID for which the entry is valid (See creature.entry).
<br />This is the master creature which defines behaviour for the linked creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>136</td>
<td>entry</td>
<td>creature_template.entry of the slave mob that is linked (See creature_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>137</td>
<td>flag</td>
<td>This flag determines how a linked creature will act, when the master is changing it’s combat state. Flags provide support for combat state, non combat state and life state.

The following flags determine the behaviour if the master is in combat state.

<table border="1" cellpadding="3" cellspacing="0">
<caption>Possible values</caption>
<tr><th>Value</th><th>Flag Name</th><th>Comment</th></tr>
<tr><td align="center" valign="middle">1</td><td align="center" valign="middle">FLAG&#95;AGGRO&#95;ON&#95;AGGRO</td><td align="left" valign="middle">The &quot;slave&quot; aggroes when the &quot;master&quot; aggroes</td></tr>
<tr><td align="center" valign="middle">2</td><td align="center" valign="middle">FLAG&#95;TO&#95;AGGRO&#95;ON&#95;AGGRO</td><td align="left" valign="middle">The master aggroes when the slave aggroes</td></tr>
<tr><td align="center" valign="middle">4</td><td align="center" valign="middle">FLAG&#95;RESPAWN&#95;ON&#95;EVADE</td><td align="left" valign="middle">The slave respawns when the master evades</td></tr>
<tr><td align="center" valign="middle">8</td><td align="center" valign="middle">FLAG&#95;TO&#95;RESPAWN&#95;ON&#95;EVADE</td><td align="left" valign="middle">the master respawns when the slave evades</td></tr>
<tr><td align="center" valign="middle">16</td><td align="center" valign="middle">FLAG&#95;DESPAWN&#95;ON&#95;DEATH</td><td align="left" valign="middle">the slave despawns when the master dies</td></tr>
<tr><td align="center" valign="middle">32</td><td align="center" valign="middle">FLAG&#95;SELFKILL&#95;ON&#95;DEATH</td><td align="left" valign="middle">the slave goes suicide when the master dies</td></tr>
<tr><td align="center" valign="middle">64</td><td align="center" valign="middle">FLAG&#95;RESPAWN&#95;ON&#95;DEATH</td><td align="left" valign="middle">the slave respawn when the master dies</td></tr>
<tr><td align="center" valign="middle">128</td><td align="center" valign="middle">FLAG&#95;RESPAWN&#95;ON&#95;RESPAWN</td><td align="left" valign="middle">the slave respawns on master respawn</td></tr>
<tr><td align="center" valign="middle">256</td><td align="center" valign="middle">FLAG&#95;DESPAWN&#95;ON&#95;RESPAWN</td><td align="left" valign="middle">the slave despawns on master respawn (TODO: check for slave != master)</td></tr>
<tr><td align="center" valign="middle">512</td><td align="center" valign="middle">FLAG&#95;FOLLOW</td><td align="left" valign="middle">the slave follows the master, very basic, see TODO notes in commit, or post below</td></tr>
<tr><td align="center" valign="middle">1024</td><td align="center" valign="middle">FLAG&#95;CANT&#95;SPAWN&#95;IF&#95;BOSS&#95;DEAD</td><td align="left" valign="middle">the slave cannot respawn while boss is dead</td></tr>
<tr><td align="center" valign="middle">2048</td><td align="center" valign="middle">FLAG&#95;CANT&#95;SPAWN&#95;IF&#95;BOSS&#95;ALIVE</td><td align="left" valign="middle">the slave cannot respawn while boss is alive</td></tr>
<tr><td align="center" valign="middle">4096</td><td align="center" valign="middle">FLAG&#95;DESPAWN&#95;ON&#95;EVADE</td><td align="left" valign="middle">the slave despawn after the master evade</td></tr>
<tr><td align="center" valign="middle">8192</td><td align="center" valign="middle">FLAG&#95;DESPAWN&#95;ON&#95;DESPAWN</td><td align="left" valign="middle">the slave despawn after the master despawns</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>138</td>
<td>map</td>
<td>Id of map of the mobs</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>139</td>
<td>master_entry</td>
<td>master entry to trigger events</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>140</td>
<td>search_range</td>
<td>IF given != 0 only mobs with spawn-dist <= search_range around the master_entry will be linked to the master. Use this to model group behaviour.<br />
<br />
IF = 0 all mobs on the map are linked to the master.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>141</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>142</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

¬subtable:34¬

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>143</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>144</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be defined for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>145</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>146</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>147</td>
<td>mincountOrRef</td>
<td>This field defines 

¦when positive: the minimum number of copies of the item that can drop in a single loot 
¦when negative: a reference to another template. 
Zero value makes no sense and should not be used. 

Meaning of positive values is quite clear and requires no additional comments. References can point to either a whole template or to single group of a template and decribed below. 

Template reference
mincountOrRef < 0, group = 0 

Template reference asks core to process another loot template (having entry equal to "-mincountOrRef") and to include all items dropped for that template into current loot. Simple idea. 

Value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. So if the referenced template can produce 3 to 10 items (depending on luck) and value of maxcount is '5' then after processing of that reference 15 to 50 items will be added to the loot. An awful example, isn't it? Actually no good example for whole template reference repetition is known, but it is quite useful for group references sometimes. 

Be careful. Self references (loot template includes reference to itself) and loop references (loot template A includes reference to entire template B, loot template B includes reference to entire template A) are completely different from internal references. If you make a self-reference like 

<pre>INSERT INTO `creature_loot_template` (`entry`,`item`,`mincountOrRef`) VALUES ('21215','0','-21215'); </pre>

then the core will crash due to stack overflow at first attempt of loot 21215 processing. That is why self references and loop references are strictly forbidden. 

Group reference
mincountOrRef < 0, group > 0 

Group reference asks core to process another loot template (having entry equal to "-mincountOrRef") only in the part of one group - with id equal to value of `groupid` field of the reference entry. So this reference may add only none or 1 item into the loot (provided maxcount is equal to 1). 

Meaning of maxcount field value is the same as described in Template reference. 

Note that there is no way to have a reference as a part of a group as such grouped reference would have the same format as reference to group described here. 

There are two types of group references: 

¦external reference when group reference row has entry different from entry of the referenced group 
¦internal reference when group reference row has the same entry as the referenced group. 
Basic usage of group references is to avoid repetition of group definitions when several loot sources have common parts of the loot. In this case it is possible: 

¦to define groups with the same contents (items/drop chances) again and again. The simpliest way, but very RAM consumable. 
¦to define the group once as a part of one of loot source loot definition and to include group references in loot definitions of the other loot sources instead of repeating group definition. 
¦to define the group once as a part of an artificial loot definition (having entry not corresponding to any source) and to include group references in loot definitions for every related loot source. 
The first way is deprecated, both second and third use external references. UDB recommends to use the third way. 

As references have chance to be processed it is possible to use them effiently for zone or world drop definitions. Those drops often have different chances for different loot sources (low/high skill gameobjects, non-elite/elite creatures etc) while having the same contents of the loot. The recommended way to define such drops is as following: 

¦to set up a group with 100% group chance in an artificial loot template (using equal-chanced entries when possible) 
¦to include references to that group into loot definition of every related loot source setting the drop chance for the reference. 
Some bosses drop more than one tier item (two or three). Loot statistics looks like the same group is rolled 2 or 3 times and every time an item (possible the same) is chosen. It is simple to define a group for single item, but how to define drop for the second and the third? We can: 

¦repeat group definition 2 (or 3) times with change of group id 
¦define the group once and include 1 (or 2) internal references. 
¦define the group once as a part of an artificial loot definition and include 2 (or 3) external group references. 
¦define the group once as a part of an artificial loot definition and include an external group reference with repetition factor of 2 (or 3). 
The in-game results will be the same. But again - the first way is very inefficient and then deprecated. We recommends to use the forth way. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>148</td>
<td>bounding_radius</td>
<td>This is the distance the creature stands from the player to attack him while in melee.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>149</td>
<td>combat_reach</td>
<td>This is the maximum distance the creature can reach the player in ranged attack.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>150</td>
<td>gender</td>
<td><table border="1" cellpadding="3" cellspacing="0">
<caption>Gender of the creature</caption>
<tr><th>Value</th><th>Gender</th></tr>
<tr><td align="center" valign="middle">0</td><td align="center" valign="middle">Male</td></tr>
<tr><td align="center" valign="middle">1</td><td align="center" valign="middle">Female</td></tr>
<tr><td align="center" valign="middle">2</td><td align="center" valign="middle">None</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>151</td>
<td>modelid</td>
<td>The Display ID (See CreatureDisplayInfo.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>152</td>
<td>modelid_other_gender</td>
<td>Point to Creature_model_info.modelid. When the entry is gender male (0) or female (1), this value can point to the display id of the other gender (See Creature_model_info.modelid)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>153</td>
<td>modelid_other_team</td>
<td>If the model information entry has different display information for the other faction, this references the “creature_model_info” table's unique ID for the entry of the other faction’s model information (See CreatureDisplayInfo.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>154</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.
¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>155</td>
<td>id</td>
<td>This references the creature table table's unique ID (See Creature.ID).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>156</td>
<td>model1</td>
<td>A display model identifier activated on the waypoint. This references the "creature_model_info" table tables unique ID for which this entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>157</td>
<td>model2</td>
<td>An alternative display model identifier activated on the waypoint. This references the "creature_model_info" table tables unique ID for which this entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>158</td>
<td>orientation</td>
<td>The orientation for the creature's movement point. Measured in radians, where 0 is north on the mini-map and pi is south on the mini-map.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>159</td>
<td>point</td>
<td>An index count for all movement points attached to a creature spawn. Starts with 1 and increments by one.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>160</td>
<td>position_x</td>
<td>The X position for the creature's movement point.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>161</td>
<td>position_y</td>
<td>The Y position for the creature's movement point.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>162</td>
<td>position_z</td>
<td>The Z position for the creature's movement point.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>163</td>
<td>script_id</td>
<td>If a script should be executed, this references the "dbscripts_on_creature_movement" table tables unique ID for which the entry is valid. If not, set the value to zero.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>164</td>
<td>spell</td>
<td>The spell identifier. The value has to match with a spell identifier defined in Spell.dbc. This refers to a spell which should be cast on this waypoint.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>165</td>
<td>textid1</td>
<td>If a text should be emoted, this references the “db_script_string” table tables unique ID for which the entry is valid. If not, set the value to zero.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>166</td>
<td>textid2</td>
<td>If a text should be emoted, this references the “db_script_string” table tables unique ID for which the entry is valid. If not, set the value to zero.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>167</td>
<td>textid3</td>
<td>If a text should be emoted, this references the “db_script_string” table tables unique ID for which the entry is valid. If not, set the value to zero.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>168</td>
<td>textid4</td>
<td>If a text should be emoted, this references the “db_script_string” table tables unique ID for which the entry is valid. If not, set the value to zero.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>169</td>
<td>textid5</td>
<td>If a text should be emoted, this references the “db_script_string” table tables unique ID for which the entry is valid. If not, set the value to zero.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>170</td>
<td>waittime</td>
<td>If the creature should wait at the movement point, set this to the time in milliseconds. Otherwise set to zero for the creature to immediately proceed to the next movement point.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>171</td>
<td>wpguid</td>
<td>A unique identifier for this waypoint.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>172</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.
¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>173</td>
<td>entry</td>
<td>Creature ID from creature_template (See creature_template.id)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>174</td>
<td>model1</td>
<td>A display model identifier activated on the waypoint. This references the unique ID in the “creature_model_info” table (See creature_model_info.ID) for which this entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>175</td>
<td>model2</td>
<td>An alternative display model identifier activated on the waypoint. This references the unique ID in the “creature_model_info” table (See creature_model_info.ID) for which this entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>176</td>
<td>orientation</td>
<td>The orientation for the creature's movement point. Measured in radians, 0 is north on the mini-map and pi is south on the mini-map.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>177</td>
<td>point</td>
<td>An index count for all movement points attached to a creature spawn. Starts with 1 and increments by one.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>178</td>
<td>position_x</td>
<td>The X position for the creature's movement point.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>179</td>
<td>position_y</td>
<td>The Y position for the creature's movement point.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>180</td>
<td>position_z</td>
<td>The Z position for the creature's movement point.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>181</td>
<td>script_id</td>
<td>If a script should be executed, this references the unique ID in the “dbscripts_on_creature_movement” table (See dbscripts_on_creature_movement.Id) for which the entry is valid. If not, set the value to zero.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>182</td>
<td>spell</td>
<td>The spell identifier. The value has to match with a spell identifier defined (See Spell.dbc). This refers to a spell which should be cast on this waypoint.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>183</td>
<td>textid1</td>
<td>Obsolete, Do not use this Field</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>184</td>
<td>textid2</td>
<td>Obsolete, Do not use this Field</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>185</td>
<td>textid3</td>
<td>Obsolete, Do not use this Field</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>186</td>
<td>textid4</td>
<td>Obsolete, Do not use this Field</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>187</td>
<td>textid5</td>
<td>Obsolete, Do not use this Field</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>188</td>
<td>waittime</td>
<td>Delay time in milliseconds</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>189</td>
<td>wpguid</td>
<td>A unique identifier for this waypoint.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>190</td>
<td>creature_id</td>
<td>The template ID of the creature (See creature_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>191</td>
<td>IsTeamAward1</td>
<td><table border="1" cellpadding="3" cellspacing="0">
<caption>Boolean 0 or 1 that controls if the player receives the reputation not only to the faction but also the faction team.</caption>
<tr><th>Value</th><th>Gender</th></tr>
<tr><td align="center" valign="middle">0</td><td align="center" valign="middle">Player receives reputation only for the faction.</td></tr>
<tr><td align="center" valign="middle">1</td><td align="center" valign="middle">Player receives reputation both for the faction and the faction’s team.</td></tr>
</table>

NOTE: The reputation value that the player gains for the team (if the field is 1) is half of the value specified in RewOnKillRepValue

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>192</td>
<td>IsTeamAward2</td>
<td><table border="1" cellpadding="3" cellspacing="0">
<caption>Boolean 0 or 1 that controls if the player receives the reputation not only to the faction but also the faction team.</caption>
<tr><th>Value</th><th>Gender</th></tr>
<tr><td align="center" valign="middle">0</td><td align="center" valign="middle">Player receives reputation only for the faction.</td></tr>
<tr><td align="center" valign="middle">1</td><td align="center" valign="middle">Player receives reputation both for the faction and the faction’s team.</td></tr>
</table>

NOTE: The reputation value that the player gains for the team (if the field is 1) is half of the value specified in RewOnKillRepValue

</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>193</td>
<td>MaxStanding1</td>
<td>The maximum standing that the creature will award reputation until. If the player achieves standing higher than this, the creature will not award any reputation.<br />
<table border="1" cellpadding="3" cellspacing="0" width='100%'>
<tr><th>Value</th><th>Gender</th></tr>
<tr><td align="center" valign="middle">0</td><td align="center" valign="middle">Hated</td></tr>
<tr><td align="center" valign="middle">1</td><td align="center" valign="middle">Hostile</td></tr>
<tr><td align="center" valign="middle">2</td><td align="center" valign="middle">Unfriendly</td></tr>
<tr><td align="center" valign="middle">3</td><td align="center" valign="middle">Neutral</td></tr>
<tr><td align="center" valign="middle">4</td><td align="center" valign="middle">Friendly</td></tr>
<tr><td align="center" valign="middle">5</td><td align="center" valign="middle">Honored</td></tr>
<tr><td align="center" valign="middle">6</td><td align="center" valign="middle">Revered</td></tr>
<tr><td align="center" valign="middle">7</td><td align="center" valign="middle">Exalted</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>194</td>
<td>MaxStanding2</td>
<td>The maximum standing that the creature will award reputation until. If the player achieves standing higher than this, the creature will not award any reputation.<br />
<table border="1" cellpadding="3" cellspacing="0" width='100%'>
<tr><th>Value</th><th>Gender</th></tr>
<tr><td align="center" valign="middle">0</td><td align="center" valign="middle">Hated</td></tr>
<tr><td align="center" valign="middle">1</td><td align="center" valign="middle">Hostile</td></tr>
<tr><td align="center" valign="middle">2</td><td align="center" valign="middle">Unfriendly</td></tr>
<tr><td align="center" valign="middle">3</td><td align="center" valign="middle">Neutral</td></tr>
<tr><td align="center" valign="middle">4</td><td align="center" valign="middle">Friendly</td></tr>
<tr><td align="center" valign="middle">5</td><td align="center" valign="middle">Honored</td></tr>
<tr><td align="center" valign="middle">6</td><td align="center" valign="middle">Revered</td></tr>
<tr><td align="center" valign="middle">7</td><td align="center" valign="middle">Exalted</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>195</td>
<td>RewOnKillRepFaction1</td>
<td>The faction ID of the faction that the player will gain or lose points in (See Faction.dbc)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>196</td>
<td>RewOnKillRepFaction2</td>
<td>The faction ID of the faction that the player will gain or lose points in (See Faction.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>197</td>
<td>RewOnKillRepValue1</td>
<td>The reputation value that the player gains (or loses if it&amp;s negative) by killing the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>198</td>
<td>RewOnKillRepValue2</td>
<td>The reputation value that the player gains (or loses if it&amp;s negative) by killing the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>199</td>
<td>TeamDependent</td>
<td><table border="1" cellpadding="3" cellspacing="0">
<caption>Boolean 0 or 1.Boolean 0 or 1.</caption>
<tr><th>Value</th><th>Gender</th></tr>
<tr><td align="center" valign="middle">0</td><td align="center" valign="middle">The creature will give reputation to the any player from both fields (RewOnKillRepFaction1 and RewOnKillRepFaction2) if both fields are non-zero.</td></tr>
<tr><td align="center" valign="middle">1</td><td align="center" valign="middle">The creature will award alliance players the reputation from RewOnKillRepFaction1 and will award horde players the reputation from RewOnKillRepFaction2.</td></tr>
</table>

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>200</td>
<td>id</td>
<td>The ID of the creature (See creature_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>201</td>
<td>quest</td>
<td>The quest ID that the creature starts (See quest_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>202</td>
<td>AIName</td>
<td>This string determines which built-in AI script will be used for the creature template. By default and empty string will lead to the creature doing nothing. 
The following table lists all valid entries.<br />

¬subtable:23¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>203</td>
<td>Armor</td>
<td>The armor value of the creature. It controls how much damage reduction the creature gets from physical attacks.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>204</td>
<td>ArmorMultiplier</td>
<td>Setting this value to a value smaller or larger than 1 will modify the creature template’s armor by this factor.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>206</td>
<td>CreatureType</td>
<td>This Field Defines The Type Of Creature This NPC Is.<br /><br/>
¬subtable:26¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>207</td>
<td>CreatureTypeFlags</td>
<td>Type flags seem to control what actions a player can perform towards a creature template.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>210</td>
<td>DamageVariance</td>
<td>Setting this value to a value smaller or larger than 1 will modify the creature template’s damage by this factor.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>211</td>
<td>DynamicFlags</td>
<td>Dynamic flags are used to control the visual appearance of a creature template. The following table provides a list of valid values. Multiple flags may be combined.

¬subtable:40¬

</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>212</td>
<td>Entry</td>
<td>This is the Primary NPC Entry Number and is Also the Dungeon Normal Mode / Raid 10-Man Normal Mode Entry.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>216</td>
<td>FactionAlliance</td>
<td>The Faction If The Creature Is On The Alliance Side (See FactionTemplate.dbc).. Just Because More Than One Faction Has The Same Name, The Inter-Faction Relationships Can Be Different.<br />
<br />
Note: This Field Also Controls The Creature Family Assistance Mechanic. Only Creatures With The Same Faction Will Assist Each Other.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>217</td>
<td>FactionHorde</td>
<td>The Faction If The Creature Is On The Alliance Side (See FactionTemplate.dbc).. Just Because More Than One Faction Has The Same Name, The Inter-Faction Relationships Can Be Different.<br />
<br />
Note: This Field Also Controls The Creature Family Assistance Mechanic. Only Creatures With The Same Faction Will Assist Each Other.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>218</td>
<td>Family</td>
<td>This Defines The Family That This Creature Belongs To. This Is Only Used If CreatureType Is 1 (Beast).<br />
<br />
¬subtable:25¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>220</td>
<td>HealthMultiplier</td>
<td>Setting this value to a value smaller or larger than 1 will modify the creature template’s health by this factor.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>221</td>
<td>InhabitType</td>
<td>This Field Controls Where The Creature Can Move Into, Chase And Attack. 

The NPC Is Limited To ONLY This:

¬subtable:31¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>222</td>
<td>KillCredit1</td>
<td>If killing a creature should credit towards a different creature_template, this should be set to the creature template’s identifier.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>223</td>
<td>KillCredit2</td>
<td>If killing a creature should credit towards a different creature_template, this should be set to the creature template’s identifier.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>226</td>
<td>MaxLevel</td>
<td>The maximum level of the creature when it is spawned in-game. Must be higher than minlevel!</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>227</td>
<td>MaxLevelHealth</td>
<td>The maximum health of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>228</td>
<td>MaxLevelMana</td>
<td>The maximum mana of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>229</td>
<td>MaxLootGold</td>
<td>The money dropped by the creature in copper (1000 = 10s, 100000 = 1g, 111111 = 11g 11s 11c)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>231</td>
<td>MaxRangedDmg</td>
<td>Maximum damage the creature deals in ranged combat. This field is combined with the ranged attackpower field to calculate the damage.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>234</td>
<td>MeleeBaseAttackTime</td>
<td>A creature’s melee attack time in milliseconds.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>235</td>
<td>MinLevel</td>
<td>The minimum level of the creature when it is spawned in-game.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>236</td>
<td>MinLevelHealth</td>
<td>The minimum health of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>238</td>
<td>MinLootGold</td>
<td>Minimum money the creature drops when killed, in copper.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>241</td>
<td>ModelId1</td>
<td>A display model identifier for the creature_template. 
This references the unique ID in table "creature_model_info" (See creature_model_info) for which this entry is valid.
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>242</td>
<td>ModelId2</td>
<td>A display model identifier for the creature_template. 
This references the unique ID in table "creature_model_info" (See creature_model_info) for which this entry is valid.
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>244</td>
<td>Name</td>
<td>The creature’s name that will be displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>245</td>
<td>NpcFlags</td>
<td>The flags of the creature.
Note that most of these also require the "Gossip" [1] flag to work.
So if you want a NPC that is a quest giver, a vendor and can repair you just add the specific flags together: 1 + 2 + 128 + 4096 = 4227. 

<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th align='right'><b>Pure Flags</b></th>
<th><b>Decimal</b></th>
<th><b>Binary (32 Bit)</b></th>
<th align='left'><b>Remarks</b></th>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>UNIT_NPC_FLAG_NONE</td><td align='center' valign='middle'>0</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_GOSSIP</td><td align='center' valign='middle'>1</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0000 0001</td><td align='left' valign='middle'>(If NPC has more gossip options, add this flag to bring up a menu.)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_QUESTGIVER</td><td align='center' valign='middle'>2</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0000 0010</td><td align='left' valign='middle'>(Any NPC giving or taking quests needs to have this flag.)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_UNKNOWN1</td><td align='center' valign='middle'>4</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0000 0100</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_UNKOWN2</td><td align='center' valign='middle'>8</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0000 1000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_TRAINER</td><td align='center' valign='middle'>16</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0001 0000</td><td align='left' valign='middle'>(Allows the NPC to have a trainer list to teach spells, all trainers must have this flag)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_TRAINER_CLASS</td><td align='center' valign='middle'>32</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0010 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_TRAINER_PROF</td><td align='center' valign='middle'>64</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0100 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_VENDOR</td><td align='center' valign='middle'>128</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 1000 0000</td><td align='left' valign='middle'>(Any NPC selling items needs to have this flag)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_VENDOR_AMMO</td><td align='center' valign='middle'>256</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0001 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_VENDOR_FOOD</td><td align='center' valign='middle'>512</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0010 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_VENDOR_POISON</td><td align='center' valign='middle'>1024</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0100 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_VENDOR_REAGENT</td><td align='center' valign='middle'>2048</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 1000 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_ARMORER</td><td align='center' valign='middle'>4096</td><td align='center' valign='middle'>0000 0000 0000 0000 0001 0000 0000 0000</td><td align='left' valign='middle'>(NPC with this flag can repair items.)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_TAXIVENDOR</td><td align='center' valign='middle'>8192</td><td align='center' valign='middle'>0000 0000 0000 0000 0010 0000 0000 0000</td><td align='left' valign='middle'>(Any NPC serving as fly master has this.)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_SPIRITHEALER</td><td align='center' valign='middle'>16384</td><td align='center' valign='middle'>0000 0000 0000 0000 0100 0000 0000 0000</td><td align='left' valign='middle'>(Makes the NPC invisible to alive characters and has the resurrect function.)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_SPIRITGUIDE</td><td align='center' valign='middle'>32768</td><td align='center' valign='middle'>0000 0000 0000 0000 1000 0000 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_INNKEEPER</td><td align='center' valign='middle'>65536</td><td align='center' valign='middle'>0000 0000 0000 0001 0000 0000 0000 0000</td><td align='left' valign='middle'>(NPC with this flag can set hearthstone locations.)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_BANKER</td><td align='center' valign='middle'>131072</td><td align='center' valign='middle'>0000 0000 0000 0010 0000 0000 0000 0000</td><td align='left' valign='middle'>(NPC with this flag can show the bank)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_ARENACHARTER</td><td align='center' valign='middle'>262144</td><td align='center' valign='middle'>0000 0000 0000 0100 0000 0000 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_TABARDVENDOR</td><td align='center' valign='middle'>524288</td><td align='center' valign='middle'>0000 0000 0000 1000 0000 0000 0000 0000</td><td align='left' valign='middle'>(Allows the designing of guild tabards.)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_BATTLEFIELDPERSON</td><td align='center' valign='middle'>1048576</td><td align='center' valign='middle'>0000 0000 0001 0000 0000 0000 0000 0000</td><td align='left' valign='middle'>(NPC with this flag port players to battlegrounds. Like battlemasters, arena organzier etc.)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_AUCTIONEER</td><td align='center' valign='middle'>2097152</td><td align='center' valign='middle'>0000 0000 0010 0000 0000 0000 0000 0000</td><td align='left' valign='middle'>(Allows NPC to display auction list.)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_STABLE</td><td align='center' valign='middle'>4194304</td><td align='center' valign='middle'>0000 0000 0100 0000 0000 0000 0000 0000</td><td align='left' valign='middle'>(Has the option to stable pets for hunters.)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
UNIT_NPC_FLAG_GUILD_BANK</td><td align='center' valign='middle'>8388608</td><td align='center' valign='middle'>0000 0000 1000 0000 0000 0000 0000 0000</td><td align='left' valign='middle'></td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
UNIT_NPC_FLAG_SPELLCLICK</td><td align='center' valign='middle'>16777216</td><td align='center' valign='middle'>0000 0001 0000 0000 0000 0000 0000 0000</td><td align='left' valign='middle'>(Needs data on npc_spellclick_spells table)</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
Mailbox</td><td align='center' valign='middle'>67108864</td><td align='center' valign='middle'>0000 0100 0000 0000 0000 0000 0000 0000</td><td align='left' valign='middle'>(NPC will act like a mailbox, opens mailbox with right-click)</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
Guard</td><td align='center' valign='middle'>268435456</td><td align='center' valign='middle'>0001 0000 0000 0000 0000 0000 0000 0000</td><td align='left' valign='middle'>(Cityguards, must be scripted)</td></tr>
</table>
<br />
<table border='1' cellspacing='1' cellpadding='3' bgcolor='#f0f0f0'>
<tr bgcolor='#f0f0ff'>
<th align='right'><b>Flag Combinations</b></th>
<th><b>Decimal</b></th>
<th><b>Binary (32 Bit)</b></th>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>TRAINER_CLASS + TRAINER + GOSSIP</td><td align='center' valign='middle'>49</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 0011 0001</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
VENDOR + QUESTGIVER + GOSSIP</td><td align='center' valign='middle'>131</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 1000 0011</td></tr>
<tr bgcolor='#FFFFEE'><td align='right' valign='middle'>
VENDOR + TRAINER_CLASS + TRAINER + GOSSIP</td><td align='center' valign='middle'>177</td><td align='center' valign='middle'>0000 0000 0000 0000 0000 0000 1011 0001</td></tr>
<tr bgcolor='#FEFEFF'><td align='right' valign='middle'>
TABARDVENDOR + ARENACHARTER (GUILDMASTER)</td><td align='center' valign='middle'>786433</td><td align='center' valign='middle'>0000 0000 0000 1100 0000 0000 0000 0000</td></tr>
</table>
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>249</td>
<td>RacialLeader</td>
<td>A flag indicating wheather the creature is a racial leader. Killing racial leaders grants 100 honor.

¬subtable:39¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>250</td>
<td>RangedAttackPower</td>
<td>The attack power for the creature’s ranged attacks.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>251</td>
<td>RangedBaseAttackTime</td>
<td>The delay between ranged attacks, in milliseconds.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>252</td>
<td>Rank</td>
<td>The rank of a creature determines which border the game client will draw around the creature tooltip in the user interface. 
The following table lists all valid values:<br />

¬subtable:24¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>254</td>
<td>RegenerateStats</td>
<td>Controls if a creature template should regenerate it’s health or not.

¬subtable:38¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>255</td>
<td>ResistanceArcane</td>
<td>The Arcane resistance of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>256</td>
<td>ResistanceFire</td>
<td>The Fire resistance of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>257</td>
<td>ResistanceFrost</td>
<td>The Frost resistance of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>258</td>
<td>ResistanceHoly</td>
<td>The Holy resistance of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>259</td>
<td>ResistanceNature</td>
<td>The Nature resistance of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>260</td>
<td>ResistanceShadow</td>
<td>The Shadow resistance of the creature.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>261</td>
<td>Scale</td>
<td>The scale/size of the creature.<br />
Normal => 1 (100%)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>262</td>
<td>ScriptName</td>
<td>To assign a script from the script library to the creature_template, set this string to the script’s exported name.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>264</td>
<td>SpeedRun</td>
<td>Controls how fast the creature can move in running mode.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>265</td>
<td>SpeedWalk</td>
<td>Controls how fast the creature can move in walking mode.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>266</td>
<td>SubName</td>
<td>An optional tag, which will be shown below the creature’s name.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>268</td>
<td>TrainerRace</td>
<td>This field allows to restrict a riding trainer to a specific race. 
Players not from that race will require exalted reputation with the trainers race before being able to buy from him. 
Values in this field correspond with the content of ChrRaces.dbc (See ChrRaces.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>269</td>
<td>TrainerSpell</td>
<td>If set to a valid spell identifier from Spell.dbc (See Spell.dbc), this will restrict access to a profession trainer so that the player needs to already have access to the spell to access the trainer.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>273</td>
<td>UnitFlags</td>
<td>Allows the manual application of unit flags to creatures. Again this is a bitmask field and to apply more than one flag, just add the different numbers. Some possible flags are:

¬subtable:32¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>275</td>
<td>auras</td>
<td>Allows to attach auras to a creature_template entry. This includes visual auras and spell effects. The field is a string containing a spell identifier defined in Spell.dbc with an index to the spell effect.<br /><br />Multiple spells can be concatenated. Spells and effect indexes are separated by space characters.<br /><br />Examples<br /><br />¬subtable:15¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>276</td>
<td>b2_0_sheath</td>
<td>Defines the sheath state of the creature_template.<br /><br />¬subtable:13¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>277</td>
<td>b2_1_flags</td>
<td>The value here overrides the value for the creature's unit field UNIT_FIELD_BYTES_2.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>278</td>
<td>bytes1</td>
<td>TODO</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>279</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.
¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>280</td>
<td>entry</td>
<td>This references the unique ID in table “creature_template” (See creature_template.id) for which the entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>281</td>
<td>mount</td>
<td>A display model identifier used as mount for the creature_template. 
This references the “creature_model_info” table tables unique ID for which this entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>282</td>
<td>moveflags</td>
<td>The flag controls how a creature_template will be animated while moving.<br /><br />¬subtable:14¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>283</td>
<td>BaseArmor</td>
<td>Base armor value for any creature of this level and class.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>284</td>
<td>BaseDamageExp0</td>
<td>Base damage value for expansion 0 aka. vanilla WoW.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>285</td>
<td>BaseHealthExp0</td>
<td>Base health value for expansion 0 aka. vanilla WoW.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>286</td>
<td>BaseMana</td>
<td>Base mana value for any creature of this level and class.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>287</td>
<td>BaseMeleeAttackPower</td>
<td>Base melee attack power that has been factored for low level creatures.<br /><br />Note: This is raw base value to be used for all melee damage calculations.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>288</td>
<td>BaseRangedAttackPower</td>
<td>Base ranged attack power.<br /><br />Note: This is raw base value to be used for all ranged damage calculations.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>289</td>
<td>Class</td>
<td>A creature’s class. The following table describes the available classes.<br /><br />¬subtable:10¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>290</td>
<td>Level</td>
<td>Creature level for the stats.<br />Could Be MinLevel or MaxLevel or both, could Be Same if the creature only has a single level.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>291</td>
<td>entry</td>
<td>This references the unique ID in table “creature_template” (See creature_template.id) for which the entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>292</td>
<td>spell1</td>
<td>The spell identifier. The value has to match with a spell identifier defined (See Spell.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>293</td>
<td>spell2</td>
<td>The spell identifier. The value has to match with a spell identifier defined (See Spell.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>294</td>
<td>spell3</td>
<td>The spell identifier. The value has to match with a spell identifier defined (See Spell.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>295</td>
<td>spell4</td>
<td>The spell identifier. The value has to match with a spell identifier defined (See Spell.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>297</td>
<td>content_default</td>
<td>Contains the text presented in the default language English. Strings may contain special variables which are replaced with creature or character data. The following table lists available variables.
¬subtable:21¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>298</td>
<td>content_loc1</td>
<td>Korean localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>299</td>
<td>content_loc2</td>
<td>French localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>300</td>
<td>content_loc3</td>
<td>German localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>301</td>
<td>content_loc4</td>
<td>Chinese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>302</td>
<td>content_loc5</td>
<td>Taiwanese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>303</td>
<td>content_loc6</td>
<td>Spanish (Spain) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>304</td>
<td>content_loc7</td>
<td>Spanish (Latin America) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>305</td>
<td>content_loc8</td>
<td>Russian localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>306</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.
¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>312</td>
<td>content_default</td>
<td>Contains the text presented in the default language English. Strings may contain special variables which are replaced with creature or character data. The following table lists available variables.
¬subtable:21¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>313</td>
<td>content_loc1</td>
<td>Korean localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>314</td>
<td>content_loc2</td>
<td>French localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>315</td>
<td>content_loc3</td>
<td>German localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>316</td>
<td>content_loc4</td>
<td>Chinese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>317</td>
<td>content_loc5</td>
<td>Taiwanese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>318</td>
<td>content_loc6</td>
<td>Spanish (Spain) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>319</td>
<td>content_loc7</td>
<td>Spanish (Latin America) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>320</td>
<td>content_loc8</td>
<td>Russian localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>321</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.
¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>326</td>
<td>creature_ai_version</td>
<td>The Version of the Creature AI Database entries (ACID)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>327</td>
<td>required_20003_03_mangos_spell_bonus_data</td>
<td>The current fieldname of the Version of the Database.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>328</td>
<td>version</td>
<td>The Version string shown in game.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>329</td>
<td>fieldComment</td>
<td>A short Description of the Field.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>330</td>
<td>fieldName</td>
<td>The fieldname in the table to link the note to.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>331</td>
<td>fieldNotes</td>
<td>The Field Note text</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>332</td>
<td>tableName</td>
<td>The table name to link the note to.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>333</td>
<td>Progress</td>
<td>The percentage completeness of the project. By default the dbdocs system sets the percent complete of quests to 0 (Zero).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>334</td>
<td>QuestID</td>
<td>The Quest ID to link to (See Quest_template.entry).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>335</td>
<td>QuestNotes</td>
<td>Notes about issues with the quest.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>336</td>
<td>subTableContent</td>
<td>The Content of the subTable.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>337</td>
<td>subTableId</td>
<td>This is the Lookup Id of the subTable</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>338</td>
<td>subTableName</td>
<td>The Name of the SubTable</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>339</td>
<td>subTableTemplate</td>
<td>The SubTable Template, Used to create the SubTableContent field content</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>340</td>
<td>tableName</td>
<td>The table name to link the note to.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>341</td>
<td>tableNotes</td>
<td>The table note text.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>469</td>
<td>datalong</td>
<td>A multi-purpose field for storing data as an unsigned integer value.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>470</td>
<td>datalong2</td>
<td>A multi-purpose field for storing data as an unsigned integer value.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>473</td>
<td>o</td>
<td>The Orientation direction on the map for the command.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>475</td>
<td>x</td>
<td>The X position on the map for the command.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>476</td>
<td>y</td>
<td>The Y position on the map for the command.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>477</td>
<td>z</td>
<td>The Z position on the map for the command.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>495</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>496</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>497</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>498</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>499</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>500</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>504</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>505</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>506</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>507</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>508</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>509</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>512</td>
<td>end_time</td>
<td>A timestamp for the end date and time of the event. Try to keep start time related to the official World of Warcraft release on November 23rd 2004.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>514</td>
<td>holiday</td>
<td>If an event is related to an official in-game world event such as Winter Veil, etc. this contains the unique identifier as known by the game client.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>515</td>
<td>length</td>
<td>Defines the length of an event. The time is measured in minutes, and needs to be lower than the value set for occurence.

** Note **

If the length is greater thano occurence, an event will never stop.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>516</td>
<td>occurence</td>
<td>Defines the time span between occurrences of the game event. The time span is measured in minutes.

* 1440 minutes for a day,

* 2880 minutes for two days,

* etc.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>517</td>
<td>start_time</td>
<td>A timestamp for the start date and time of the event. Try to keep start time related to the official World of Warcraft release on November 23rd 2004.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>537</td>
<td>ghost_zone</td>
<td>The ID of the zone the graveyard is located in.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>538</td>
<td>id</td>
<td>incrementing ID.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>539</td>
<td>id</td>
<td>The id of the teleport location.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>540</td>
<td>map</td>
<td>The map id of the teleport location (See map.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>541</td>
<td>name</td>
<td>The name of the teleport location.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>542</td>
<td>orientation</td>
<td>The orientation of the player when teleported to the teleport location.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>543</td>
<td>position_x</td>
<td>The x location of the teleport location.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>544</td>
<td>position_y</td>
<td>The y location of the teleport location.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>545</td>
<td>position_z</td>
<td>The z location of the teleport location.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>562</td>
<td>map</td>
<td>The map id that the game object is located on (See map.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>563</td>
<td>orientation</td>
<td>The orientation of the game object.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>564</td>
<td>position_x</td>
<td>The x location of the game object.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>565</td>
<td>position_y</td>
<td>The y location of the game object.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>566</td>
<td>position_z</td>
<td>The z location of the game object.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>576</td>
<td>id</td>
<td>Entry ID of the gameobject that starts the quest</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>577</td>
<td>quest</td>
<td>Entry ID of the quest</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>578</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>579</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>580</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>581</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>582</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>583</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>585</td>
<td>id</td>
<td>Entry ID of the gameobject that starts the quest</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>587</td>
<td>data0</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>588</td>
<td>data1</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>589</td>
<td>data10</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>590</td>
<td>data11</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>591</td>
<td>data12</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>592</td>
<td>data13</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>593</td>
<td>data14</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>594</td>
<td>data15</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>595</td>
<td>data16</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>596</td>
<td>data17</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>597</td>
<td>data18</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>598</td>
<td>data19</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>599</td>
<td>data2</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>600</td>
<td>data20</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>601</td>
<td>data21</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>602</td>
<td>data22</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>603</td>
<td>data23</td>
<td>The content of the data fields depends on the gameobject type. See below

¬subtable:27¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>604</td>
<td>data3</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>605</td>
<td>data4</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>606</td>
<td>data5</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>607</td>
<td>data6</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>608</td>
<td>data7</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>609</td>
<td>data8</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>610</td>
<td>data9</td>
<td>The content of the data fields depends on the gameobject type. See below</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>611</td>
<td>displayId</td>
<td>A display model identifier for the Item. 
This references an DisplayInfo entry (See itemDisplayInfo.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>612</td>
<td>entry</td>
<td>Id of the gameobject template</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>613</td>
<td>faction</td>
<td>Object’s faction, if any. (See FactionTemplate.dbc)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>614</td>
<td>flags</td>
<td>This is a bitmask field describing the item. Mulitple flag may be combined. The following table lists the available flags:

¬subtable:29¬
<br />
<B>NOTE:</B> All chests that contain only quest loots need to have flag 4 set as the core will only allow players who have the quest in their questlog to loot them.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>617</td>
<td>name</td>
<td>Object's Name</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>618</td>
<td>ScriptName</td>
<td>To assign a script from the script library this template, set this string to the script’s exported name.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>619</td>
<td>size</td>
<td>Object’s size must be set because graphic models can be resample.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>620</td>
<td>type</td>
<td>¬subtable:28¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>639</td>
<td>content_default</td>
<td>Contains the text presented in the default language English. Strings may contain special variables which are replaced with creature or character data. The following table lists available variables.
¬subtable:21¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>640</td>
<td>content_loc1</td>
<td>Korean localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>641</td>
<td>content_loc2</td>
<td>French localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>642</td>
<td>content_loc3</td>
<td>German localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>643</td>
<td>content_loc4</td>
<td>Chinese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>644</td>
<td>content_loc5</td>
<td>Taiwanese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>645</td>
<td>content_loc6</td>
<td>Spanish (Spain) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>646</td>
<td>content_loc7</td>
<td>Spanish (Latin America) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>647</td>
<td>content_loc8</td>
<td>Russian localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>658</td>
<td>ScriptName</td>
<td>To assign a script from the script library this template, set this string to the script’s exported name.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>662</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>663</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>664</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>665</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>666</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>667</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>670</td>
<td>targetEntry</td>
<td>Depending on the type value this references the "creature_template" table tables unique ID, or the table "gameobject_template" unique ID (see  gameobject_template).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>688</td>
<td>displayid</td>
<td>A display model identifier for the Item. 
This references an DisplayInfo entry (See itemDisplayInfo.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>727</td>
<td>Quality</td>
<td>The Quality of the Item.

¬subtable:35¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>738</td>
<td>ScriptName</td>
<td>To assign a script from the script library this template, set this string to the script’s exported name.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1089</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1090</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1091</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1092</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1093</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1094</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1096</td>
<td>content_default</td>
<td>Contains the text presented in the default language English. Strings may contain special variables which are replaced with creature or character data. The following table lists available variables.
¬subtable:21¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1097</td>
<td>content_loc1</td>
<td>Korean localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1098</td>
<td>content_loc2</td>
<td>French localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1099</td>
<td>content_loc3</td>
<td>German localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1100</td>
<td>content_loc4</td>
<td>Chinese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1101</td>
<td>content_loc5</td>
<td>Taiwanese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1102</td>
<td>content_loc6</td>
<td>Spanish (Spain) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1103</td>
<td>content_loc7</td>
<td>Spanish (Latin America) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1104</td>
<td>content_loc8</td>
<td>Russian localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1108</td>
<td>em0_0</td>
<td>Emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1109</td>
<td>em0_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1110</td>
<td>em0_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1111</td>
<td>em0_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1112</td>
<td>em0_2</td>
<td>Third emote to play when text is displayed</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1113</td>
<td>em0_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1114</td>
<td>em1_0</td>
<td>emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1115</td>
<td>em1_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1116</td>
<td>em1_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1117</td>
<td>em1_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1118</td>
<td>em1_2</td>
<td>Third emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1119</td>
<td>em1_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1120</td>
<td>em2_0</td>
<td>emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1121</td>
<td>em2_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1122</td>
<td>em2_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1123</td>
<td>em2_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1124</td>
<td>em2_2</td>
<td>Third emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1125</td>
<td>em2_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1126</td>
<td>em3_0</td>
<td>emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1127</td>
<td>em3_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1128</td>
<td>em3_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1129</td>
<td>em3_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1130</td>
<td>em3_2</td>
<td>Third emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1131</td>
<td>em3_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1132</td>
<td>em4_0</td>
<td>emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1133</td>
<td>em4_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1134</td>
<td>em4_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1135</td>
<td>em4_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1136</td>
<td>em4_2</td>
<td>Third emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1137</td>
<td>em4_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1138</td>
<td>em5_0</td>
<td>emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1139</td>
<td>em5_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1140</td>
<td>em5_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1141</td>
<td>em5_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1142</td>
<td>em5_2</td>
<td>Third emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1143</td>
<td>em5_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1144</td>
<td>em6_0</td>
<td>emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1145</td>
<td>em6_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1146</td>
<td>em6_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1147</td>
<td>em6_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1148</td>
<td>em6_2</td>
<td>Third emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1149</td>
<td>em6_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1150</td>
<td>em7_0</td>
<td>emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1151</td>
<td>em7_0_delay</td>
<td>Time to wait before the first emote is played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1152</td>
<td>em7_1</td>
<td>Second emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1153</td>
<td>em7_1_delay</td>
<td>Time to wait after the first emote are played, before the second emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1154</td>
<td>em7_2</td>
<td>Third emote to play when text is displayed.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1155</td>
<td>em7_2_delay</td>
<td>Time to wait after the second emote are played, before the third emote gets played.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1156</td>
<td>ID</td>
<td>The unique identifier of the text entry. Please note that the identifier
is acquired from the game client by parsing the local *WDB* cache files.<br />

It is unknown if text identifiers required a specific identifier to work.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1157</td>
<td>lang0</td>
<td>The language of the text ingame.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1158</td>
<td>lang1</td>
<td>The language of the text in game.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1159</td>
<td>lang2</td>
<td>The language of the text in game.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1160</td>
<td>lang3</td>
<td>The language of the text in game.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1161</td>
<td>lang4</td>
<td>The language of the text in game.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1162</td>
<td>lang5</td>
<td>The language of the text in game.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1163</td>
<td>lang6</td>
<td>The language of the text in game.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1164</td>
<td>lang7</td>
<td>The language of the text in game.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1165</td>
<td>prob0</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1166</td>
<td>prob1</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1167</td>
<td>prob2</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1168</td>
<td>prob3</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1169</td>
<td>prob4</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1170</td>
<td>prob5</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1171</td>
<td>prob6</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1172</td>
<td>prob7</td>
<td>This is the probability that the creature will say this text.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1173</td>
<td>text0_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1174</td>
<td>text0_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1175</td>
<td>text1_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1176</td>
<td>text1_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1177</td>
<td>text2_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1178</td>
<td>text2_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1179</td>
<td>text3_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1180</td>
<td>text3_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1181</td>
<td>text4_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1182</td>
<td>text4_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1183</td>
<td>text5_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1184</td>
<td>text5_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1185</td>
<td>text6_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1186</td>
<td>text6_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1187</td>
<td>text7_0</td>
<td>This is the locale text that is displayed if the creature is male.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1188</td>
<td>text7_1</td>
<td>This is the locale text that is displayed if the creature is female.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1203</td>
<td>incrtime</td>
<td>This field decides how frequently a vendor will restock and item having a maximum count. 

The value is given in seconds, and for limited items, the BuyCount column of the “item_template” table is taken into account when restocking.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1209</td>
<td>item</td>
<td>Template ID of the item. </td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1233</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1234</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1235</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1236</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1237</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1238</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1241</td>
<td>basemana</td>
<td>Base mana value for any creature of this level and class.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1255</td>
<td>map</td>
<td>The map ID (See Map.dbc)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1306</td>
<td>CompleteScript</td>
<td>If a script should be executed on quest end, this references an entry in the “dbscripts_on_quest_end” table.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1317</td>
<td>entry</td>
<td>The unique identifier of the quest template entry.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1321</td>
<td>Method</td>
<td>This flag decides how a quest will handled by the client. The following table lists allowed values.

¬subtable:36¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1322</td>
<td>MinLevel</td>
<td>The lowest level allowed to accept the quest.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1345</td>
<td>QuestLevel</td>
<td>The quest’s level. Depending on the quest’s level, the experience rewarded for the quest will be awarded.

*If a character’s level is <= QuestLevel+5, full experience will be given.

*If QuestLevel is set to -1, the character’s level will be used as QuestLevel.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1425</td>
<td>StartScript</td>
<td>If a script should be executed on quest start, this references an entry in the “dbscripts_on_quest_start” table.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1428</td>
<td>Type</td>
<td>Classifies a quest’s difficulty. This references an entry from QuestInfo.dbc (see QuestInfo.dbc). 

The following table lists allowed values:

¬subtable:37¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1429</td>
<td>ZoneOrSort</td>
<td>Defines the category under which a quest will be listed in the in-game quest log. Depending on the sign of the value different category sources will be used.

* If the value is > 0, the value references an entry from AreaTable.dbc.

* If the value is < 0, the value references an entry from QuestSort.dbc. This is usually the case for class or skill related quests.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1430</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1431</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1432</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1433</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1434</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1435</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1456</td>
<td>content_default</td>
<td>Contains the text presented in the default language English. Strings may contain special variables which are replaced with creature or character data. The following table lists available variables.
¬subtable:21¬</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1457</td>
<td>content_loc1</td>
<td>Korean localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1458</td>
<td>content_loc2</td>
<td>French localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1459</td>
<td>content_loc3</td>
<td>German localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1460</td>
<td>content_loc4</td>
<td>Chinese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1461</td>
<td>content_loc5</td>
<td>Taiwanese localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1462</td>
<td>content_loc6</td>
<td>Spanish (Spain) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1463</td>
<td>content_loc7</td>
<td>Spanish (Latin America) localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1464</td>
<td>content_loc8</td>
<td>Russian localization of content_default</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1465</td>
<td>emote</td>
<td>Emote ID that the creature should continually perform.<br/>
<br />
List of often used emote IDs and what they do ie. 65 Makes the creature look dead by lying on the ground.
¬subtable:22¬</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1478</td>
<td>ScriptName</td>
<td>To assign a script from the script library this template, set this string to the script’s exported name.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1480</td>
<td>ScriptName</td>
<td>To assign a script from the script library this template, set this string to the script’s exported name.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1484</td>
<td>ChanceOrQuestChance</td>
<td>Meaning of that field is a bit different depending on its sign and the sign of mincountOrRef: 

Plain entry
ChanceOrQuestChance > 0, mincountOrRef > 0 

Absolute value of ChanceOrQuestChance (actuallu just the value as it's positive in this case) signifies the percent chance that the item has to drop. Any floating point number is allowed but indeed any value larger that 100 will make the same result as 100. 

Quest drop
ChanceOrQuestChance < 0, mincountOrRef > 0 

Just as for plain entries absolute value of ChanceOrQuestChance signifies the percent chance that the item has to drop. But in addition negative ChanceOrQuestChance informs the core that the item should be shown only to characters having appropriate quest. This means that even if item is dropped, in order to see it in the loot the player must have at least one quest that has the item ID in its ReqItemIdN fields or in its ReqSourceIdN fields. The player must also have less copies of the item than ReqItemCountN or ReqSourceCountN. 

Chanced references
mincountOrRef < 0 

For negative mincountOrRef (reference entries) ChanceOrQuestChance signifies the percent chance that the reference has to be used. So it is very similar to plain entries meaning, just note that entire reference is skipped if the chance is missed. 

Negative and zero values of ChanceOrQuestChance make no sense for that case and should not be used. 

Common remarks
Zero value of ChanceOrQuestChance is allowed for grouped entries only. 

(Non-zero) values of ChanceOrQuestChance in loot definition are multiplied by RATE_DROP_ITEMS (mangos config setting) during loot generation for references and non-reference entries, but not for grouped entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1485</td>
<td>condition_id</td>
<td>Value that represents a loot condition that must be filled in order for the item to drop. This field combined with condition_value1-2 fields can provide conditions on when an item can be dropped. 

Value  Condition  Comments  
0  CONDITION_NONE  Regular drop  
1  CONDITION_AURA  Player looting must have an aura active  
2  CONDITION_ITEM  Player must have a number of items in his/her inventory  
3  CONDITION_ITEM_EQUIPPED  Player must have an item equipped  
4  CONDITION_ZONEID  Player must be in a certain zone  
5  CONDITION_REPUTATION_RANK  Player must have a certain reputation rank with a certain faction  
6  CONDITION_TEAM  Player must be part of the specified team (Alliance or Horde)  
7  CONDITION_SKILL  Player must have a certain skill value  
8  CONDITION_QUESTREWARDED  Player must have completed a quest first  
9  CONDITION_QUESTTAKEN  Players must have the quest in the quest log and not completed yet  
10  CONDITION_AD_COMMISSION_AURA   
11  CONDITION_NO_AURA  Player looting must have no aura active mentioned in condition_value1  
12  CONDITION_ACTIVE_EVENT  The loot with that condition can be looted only while the Event (condition_value1) is active  

NOTE: For reference entries this field has no meaning, not used by the core in any way and should have the default value of 0. 

</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1486</td>
<td>entry</td>
<td>The ID of the loot definition (loot template). The rows with the same ID defines a single loot. 
It is often the same ID as the loot source (item, creature, etc) but when the link is made not on entry field of the Related table then ID can be different. For example, when several loot sources should provide the same loot, single loot definition can be used. In this case the loot sources have the same value in the link field. 

It is possible also to set up artificial loot templates which are not used directly at all as they have ID which are not referenced from the related source. Such "support templates" can be referenced from "normal" loot templates. 

When a common or artificial loot template is used a problem arises: what ID to use for that template? Depending on the loot table, different rules can be agreed on to simplify maintenance for the table. Moreover, such rules would be very handy but it seems at the moment there are very few rules explicitly defined. 

Agreements on entry field values are described there. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1487</td>
<td>groupid</td>
<td>A group is a set of loot definitions processed in such a way that at any given looting event the loot generated can receive only 1 (or none) item from the items declared in the loot definitions of the group. Groups are formed by loot definitions having the same values of entry and groupid fields. 

A group may consists of explicitly-chanced (having non-zero ChanceOrQuestChance) and equal-chanced (ChanceOrQuestChance = 0) entries. Every equal-chanced entry of a group is considered having such a chance that: 

¦all equal-chanced entries have the same chance 
¦group chance (sum of chances of all entries) is 100% 
Of course group may consist of 

¦only explicitly-chanced entries or 
¦only equal-chanced entries or 
¦entries of both type. 
The easies way to understand what are groups is to understand how core processes grouped entries: 

At loading time: 

¦groups are formed - all grouped entries with the same values of groupid and entry fields are gathered into two sets - one for explicitly-chanced entries and one for equal-chanced. Note that order of entries in the sets can not be defined by DB - you should assume that the entries are in an unknown order. But indeed every time core processes a group the entries are in some order, constant during processing. 
During loot generation: 

¦core rolls for explicitly-chanced entries (if any): 
¦a random number R is rolled in range 0 to 100 (floating point value). 
¦chance to drop is checked for every (explicitly-chanced) entry in the group: 
¦if R is less than absolute value of ChanceOrQuestChance of the entry then the entry 'wins': the item is included in the loot. Group processing stops, the rest of group entries are just skipped. 
¦otherwise the entry 'looses': the item misses its chance to get into the loot. R is decreased by the absolute value of ChanceOrQuestChance and next explicitly-chanced entry is checked. 
¦if none of explicitly-chanced entries got its chance then equal-chanced part (if any) is processed: 
¦a random entry is selected from the set of equal-chanced entries and corresponding item is included in the loot. 
¦If nothing selected yet (this never happens if the group has some equal-chanced entries) - no item from the group is included into the loot. 
Let us use term group chance as the sum of ChanceOrQuestChance (absolute) values for the group. Please note that even one equal-chanced entry makes group chance to be 100% (provided that sum of explicit chances does not exceed 100%). 

If you understand the process you can understand the results: 

¦Not more than one item from a group may drop at any given time. 
¦If group chance is at least 100 then one item will be dropped for sure. 
¦If group chance does not exceed 100 then every item defined in group entries has exactly that chance to drop as set in ChanceOrQuestChance. 
¦If group chance is greater than 100 then some entries will lost a part of their chance (or even not be checked at all - that will be the case for all equal-chanced entries) whatever value takes the roll R. So for some items chance to drop will be less than their ChanceOrQuestChance. That is very bad and that is why having group chance > 100 is strictly prohibited. 
¦Processing of equal-chanced part takes much less time then of explicitly-chanced one. So usage of equal-chanced groups is recommended when possible. 
So now basic applications of the groups are clear: 

¦Groups with group chance of 100% generate exactly one item every time. This is needed quite often, for example such behavior is needed to define a loot template for tier item drop from a boss. 
¦Groups with group chance < 100 generate one or zero items every time keeping chances of every item unchanged. Such behavior is useful to limit maximum number of items in the loot. 
¦A single group may be define
d for a set of items common for several loot sources. This could be very useful for decreasing DB size without any loss of data. See References for more details. 
There is no way to have a reference as a part of a group. 

Note: A group may contain definitions of non-quest drop, quest drop or both, but mixing non-quest and quest drop in a single group is not recommended. 

Note: The core has a limitation - only 16 non-quest items (money and items added into the loot for quests are not counted for this "16") may come into the loot. And this is not a caprice of core devs - the client has some constraints. As most of loots have much more than 16 possible items (sometimes several hundreds) so without groups there is a (little) chance that more than 16 items will be rolled for a given loot but player will be able to see (and take) only first 16 of them. With groups you can ensure that more than 16 items will never drop. If DB pretends to be a quality software it must have loot template definitions which ensure that not more than 16 plain entries and groups are defined for any loot template. This is just a note - such declaration is not issued by UDB developers yet. 

Note: The core has no limitation for number of groups (except 255 by DB field size), but according to the previous note there is no need to use values greater than 16. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1488</td>
<td>item</td>
<td>Template ID of the item which can be included into the loot. 

NOTE: For reference entries this field has no meaning and not used by the core in any way. Yet because of the PRIMARY KEY on the entry + item combination, this field will nonetheless need to be a unique number for each reference entry so that no indexing conflicts arise. </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1489</td>
<td>maxcount</td>
<td>For non-reference entries - the maximum number of copies of the item that can drop in a single loot. 

For references value of maxcount field is used as a repetition factor for references - the reference will be processed not just once but exactly maxcount times. This is designed to serve a single purpose: to make definition of tier token drops a bit simplier (tokens of a tier are defined as a 100%-chance group of an artificial template and bosses' loot templates include 100%-chanced reference to that group with repetition factor of 2 or 3 depending on the case). Using non-1 repetition factor for other things (references to a group with group chance less than 100% or chanced references with chance less than 100%) must be agreed with UDB devs first (and described here). 

Note: core rolls chance for any loot definition entry just one time - so if a references looses its chance it is skipped for the current loot completely whatever is maxcount value. 
</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1504</td>
<td>ap_bonus</td>
<td>Any value here will modify the spells attack power with the factor given here.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1552</td>
<td>inverseEffectMask</td>
<td>Takes a value for an effect, and shifts it.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1555</td>
<td>id</td>
<td>The spell identifier. The value has to match with a defined spell identifier (See Spell.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1556</td>
<td>target_map</td>
<td>The target map’s identifier. The value has to match with a defined map identifier (See Map.dbc).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1557</td>
<td>target_orientation</td>
<td>The orientation for the character on the target map. This is measured in radians, 0 is north on the mini-map and pi is south on the mini-map etc.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1558</td>
<td>target_position_x</td>
<td>The X position on the target map.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1559</td>
<td>target_position_y</td>
<td>The Y position on the target map.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1560</td>
<td>target_position_z</td>
<td>The Z position on the target map.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1561</td>
<td>ap_bonus</td>
<td>Any value here will modify the spells attack power with the factor given here.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1562</td>
<td>entry</td>
<td>The spell identifier. The value has to match with a spell identifier defined (See Spell.dbc).<br />
<br />
<h4>Note: Any spell referenced is required to be rank 1 in the spell chain, and has to have threat values set in the original spell definition.</h4></td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1563</td>
<td>multiplier</td>
<td>Any value here will modify the spells threat with the factor given here.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1564</td>
<td>Threat</td>
<td>The value of threat to add to the characters threat, or to remove from a characters threat. Negative values reduce threat, positive values increase threat.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1565</td>
<td>entry</td>
<td>This references the Gameobject Template table's unique ID (See gameobject_template.entry) of the game object of type 15 (boats and Zeppelins) for which the entry is valid.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1566</td>
<td>name</td>
<td>A name describing the transport. This is not used in-game, but only here to ease locking up data.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1567</td>
<td>period</td>
<td>This is the amount of time that it take for the transport to make one full pass through all the frames in the TaxiNodes (See TaxiNodes.dbc). When a client change occurs, usually this field must be updated. This values is set in milliseconds.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1568</td>
<td>map</td>
<td>The map ID (See Map.dbc)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>1569</td>
<td>ScriptName</td>
<td>To assign a script from the script library to the world continent, set this string to the script’s exported name.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>1764</td>
<td>languageId</td>
<td>dbdocsLanguageId to link to. (Normally 0 = English)</td>
<td></td>
</tr>
</table>
<br />
