[![](/wiki/icons/home.gif)](/wiki/Home.md)
[![](/wiki/icons/back.gif)](/wiki/Progress.md)

-----

#### Description of the MaNGOSZero Missing Translations

----

<br/>
<table border='1' cellspacing='0' cellpadding='4' bgcolor='#f0f0f0' width='100%'>
<tr>
<td>TableId</td>
<td>TableName</td>
<td>English</td>
<td>Localised</td>
</tr>
<tr bgcolor='#FFFFEE'><td>1</td>
<td>areatrigger_involvedrelation</td>
<td>The areatrigger_involvedrelation table holds connections between triggers and quests.

If there is a record in the table for a quest, the quest will not be completed until the player activates the areatriger. The quest is not necessarily finished after that, but that one condition of the quest is satisfied. If the only condition of the quest is to explore an area, then the quest will be complete.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>2</td>
<td>areatrigger_tavern</td>
<td>Enable a trigger when player enters a city or tavern. This causes the player to enter a resting state.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>3</td>
<td>areatrigger_teleport</td>
<td>Contains all the teleport triggers definition. This table is used to complete .dbc file information.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>4</td>
<td>battleground_events</td>
<td>This table contains the description of battleground events.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>5</td>
<td>battleground_template</td>
<td>Contains information about the different battlegrounds, like how many players are needed to start, how many can be inside the same one, and the locations where each side starts.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>6</td>
<td>battlemaster_entry</td>
<td>Holds information on which NPC can start what battleground or arena.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>7</td>
<td>command</td>
<td>Holds help and security information for commands.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>8</td>
<td>conditions</td>
<td>With this table and the new conditions it is possible to create tree like and very complicated combined conditions (like HasAura && (HasItem || HasQuest))

Used in:

DBScript
gossip_menu
gossip_menu_option
npc_spellclick_spells
spell_area</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>9</td>
<td>creature</td>
<td>Contains individual creature spawn data. Spawn of a creature is an instance of the creature object in the world.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>10</td>
<td>creature_addon</td>
<td>The creature_addon and creature_template_addon tables define different things that are applied on creatures when they are loaded. These "different things" can be for example to have the creature be mounted, to have it emote something, to have it display an aura effect, etc. Through the use of the fields in this table, many things can be changed about the outward visual appearance of the creature. The creature_template_addon table affects all creatures with that creature template ID while the creature_addon table affects individually spawned creatures (so that two creatures using the same template can look different).

NOTES: 
A creature_addon record will override a creature_template_addon record should they overlap on the same creature.<br />
<br />
The data for this table is largely incomplete and is mostly just a regurgitation of what the client receives from the server. This article is a WIP as to what all the possible values are.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>11</td>
<td>creature_ai_scripts</td>
<td>This table specifies the actions that a creature script will do. 
A basic eventAI script works with and requires only two pieces of information: What to do and When to do it.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>12</td>
<td>creature_ai_summons</td>
<td>This table is used to provide NPC support for an event using action 32 = ACTION_T_SUMMON as one of its Actions</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>13</td>
<td>creature_ai_texts</td>
<td>This table holds all the texts used within the eventai (ACID) scripts. This table handles the actual text, display type (say/yell/emote) and corresponding sounds or emote (if any).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>14</td>
<td>creature_battleground</td>
<td>This table contains the description of creatures spawned on battlegrounds.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>15</td>
<td>creature_equip_template</td>
<td>This table contains all equipment mobs can wear.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>16</td>
<td>creature_equip_template_raw</td>
<td>The creature_equip_template_raw table holds information on items that creatures should wear.<br/ >
<br/ >
<b>Note:</b> This table is deprecated. Do not use it, as it will be removed in a future update and is just here to ease transition to the new creature_equip_template table.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>17</td>
<td>creature_involvedrelation</td>
<td>Holds NPC quest ender relations on which NPCs finishes which quests.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>19</td>
<td>creature_linking</td>
<td>This table holds details of how creatures linked to a master creature should act in combat and non-combat situations.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>20</td>
<td>creature_linking_template</td>
<td>This table holds details on how creature templates linked to a master creature template should act in combat and non-combat situations.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>21</td>
<td>creature_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>22</td>
<td>creature_model_info</td>
<td>This table contains all models of mobs, their gender and other information that are model related. This means that when a creature uses another model, this information will change as well.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>23</td>
<td>creature_movement</td>
<td>This table holds all the information on each creature's waypoints. In essence, a waypoint just defines a path that the creature will follow by going from point to point. More specifically, once the creature arrives at a point, it can do different things like cast a spell, do an emote, etc. Usually this table is filled through the .wp command (and its various subcommands) in the world. 

Please note that for a creature to use waypoints, its MovementType must be 2.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>24</td>
<td>creature_movement_template</td>
<td>This table holds informations on paths for creature_template entries and allows the behaviour to be defined along the movement path.<br />
<br />
Template movement is usually applied to creature templates spawned by scripts, or for templates which are unique and have only one spawn.<br />
<br />
<b>Note:</b> Movement attached to a creature template will be applied to all spawns of this template, unless there is a unique movement defined for the creature entry.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>25</td>
<td>creature_onkill_reputation</td>
<td>This table controls the reputation given by creatures when killed by other players.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>26</td>
<td>creature_questrelation</td>
<td>This table holds NPC quest giver relations on which NPCs start which quests.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>27</td>
<td>creature_template</td>
<td>This table contains the description of creatures. Each spawned creature is an instance of a template present in this table, this means every creature MUST be defined in this table.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>28</td>
<td>creature_template_addon</td>
<td>The creature_addon and creature_template_addon tables define different things that are applied on creatures when they are loaded. These "different things" can be for example to have the creature be mounted, to have it emote something, to have it display an aura effect, etc. Through the use of the fields in this table, many things can be changed about the outward visual appearance of the creature. The creature_template_addon table affects all creatures with that creature template ID while the creature_addon table affects individually spawned creatures (so that two creatures using the same template can look different).

NOTES: 
A creature_addon record will override a creature_template_addon record should they overlap on the same creature.<br />
<br />
The data for this table is largely incomplete and is mostly just a regurgitation of what the client receives from the server. This article is a WIP as to what all the possible values are.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>29</td>
<td>creature_template_classlevelstats</td>
<td>This table contains the base values for creatures' health, mana and armor.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>30</td>
<td>creature_template_spells</td>
<td>This table holds information on the spells to which a Creature (See creature_template) has access.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>32</td>
<td>db_script_string</td>
<td>This table holds texts for scripts.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>33</td>
<td>db_version</td>
<td>This table holds the current version of the MaNGOS world database</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>34</td>
<td>dbdocsfields</td>
<td>This table is part of the implementation of the 'Mangos Database Documentation' (MDD) Project.

An entry in this table provides a link to the table and field to allow additional notes to describe the field in the Wiki.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>35</td>
<td>dbdocsprogressquests</td>
<td>This table is part of the dbdocs project and is not used by the mangos server. 

It holds details on the completion status of each quest in MaNGOS, as well as any notes about the quest.<br />
<br />
<b>Note:</b> By default the progress value is set to 0% by dbdocs.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>36</td>
<td>dbdocssubtables</td>
<td>This table is part of the implementation of the 'Mangos Database Documentation' (MDD) Project.

An entry in this table provides a table which directly replaces the link in the fieldnotes.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>37</td>
<td>dbdocstable</td>
<td>This table is part of the implementation of the 'Mangos Database Documentation' (MDD) Project.

An entry in this table provides a notes field to describe the database in the Wiki.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>38</td>
<td>dbscripts_on_creature_death</td>
<td>This table holds scripts activated when a creature dies. (Source: creature)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>39</td>
<td>dbscripts_on_creature_movement</td>
<td>This table holds scripts activated while a npc is moving. (Source: creature)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>40</td>
<td>dbscripts_on_event</td>
<td>This table holds scripts activated whenever an event is activated, be it by an object or as the spell effect SPELL_EFFECT_SEND_EVENT (61)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>41</td>
<td>dbscripts_on_go_template_use</td>
<td>This table holds possible scripts activated by gameobjects of type GAMEOBJECT_TYPE_BUTTON (1). (Source: user)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>42</td>
<td>dbscripts_on_go_use</td>
<td>This table holds possible scripts activated by gameobjects of type GAMEOBJECT_TYPE_BUTTON (1). (Source: user)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>43</td>
<td>dbscripts_on_gossip</td>
<td>This table holds scripts activated on gossip_menu_option – use.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>44</td>
<td>dbscripts_on_quest_end</td>
<td>This table holds scripts activated when a player finishes a quest. (Source: quest taker)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>45</td>
<td>dbscripts_on_quest_start</td>
<td>This table holds scripts activated when a player accepts a quest. (Source: quest giver)</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>46</td>
<td>dbscripts_on_spell</td>
<td>This table holds scripts that can be activated by spells with effect SPELL_EFFECT_SCRIPT_EFFECT (77). (Source: caster)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>47</td>
<td>disenchant_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>48</td>
<td>exploration_basexp</td>
<td>This table controls the XP gained by characters when they explore new zones.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>49</td>
<td>fishing_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>50</td>
<td>game_event</td>
<td>This table is contains definitions for all game events that are activated or deactivated automatically by the Game Event System in the core.

Game events are not necessarily events related to events introduced by patches (e.g. The Ahn’Qiraj opening). 

Game events include things such as the Stockades riots, or the Pyrewood Village event for the Worgen curse.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>51</td>
<td>game_event_creature</td>
<td>Contains all creature instances that have to be spawned/unspawned during defined game events.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>52</td>
<td>game_event_creature_data</td>
<td>Contains all creature instances that need to change display id and/or equipment during defined game events.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>53</td>
<td>game_event_gameobject</td>
<td>Contains all gameobjects instances that participate to any game event.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>54</td>
<td>game_event_mail</td>
<td>This table holds definitions for mails sent out during game events and conditions for when to send the mail.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>55</td>
<td>game_event_quest</td>
<td>This table contains the mapping of a quest in a world event to the condition that it will fulfill. It also contains how much a given quest will add to a condition once that quest is completed by a player.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>56</td>
<td>game_graveyard_zone</td>
<td>This table contains information about which zones are connected to the world’s graveyards.

This table set if character die in zone ghost_zone and graveyard with id accept his team (HORDE or ALIANCE or both) and this is nearest graveyard then character’s ghost will be teleported to graveyard id.

For a list of all existing graveyard zones and their respective IDs, check out WorldSafeLocs.dbc</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>57</td>
<td>game_tele</td>
<td>This table contains a list of teleport locations that can be used with the .tele command in-game. Entries in this table can be added/deleted manually or with the .addtele/.deltele commands.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>58</td>
<td>game_weather</td>
<td>This table holds the percentages for weather changes in various zones. Not all zones can have their weather changed. For any given zone the percentage of all weather types for each season should total, and not exceed 100%.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>59</td>
<td>gameobject</td>
<td>This table holds the individual object data on each spawned game object in the world. This data along with the object’s template data is read and used to instantiate the objects in the world.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>60</td>
<td>gameobject_battleground</td>
<td>This table contains the events of gameobjects which are spawned on battlegrounds.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>61</td>
<td>gameobject_involvedrelation</td>
<td>This table holds game object quest taker relations. The game objects in this table should all be of type QUESTGIVER (2).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>62</td>
<td>gameobject_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>63</td>
<td>gameobject_questrelation</td>
<td>This table holds game object quest giver relations. The game objects in this table should all be of type QUESTGIVER (2).</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>64</td>
<td>gameobject_template</td>
<td>This table contains templates of all the world’s objects</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>65</td>
<td>gossip_menu</td>
<td>This table is used for displaying gossip when a player talks to an NPC.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>66</td>
<td>gossip_menu_option</td>
<td>This table holds infos about menu options a gossip NPC can have. 
Examples of options: "Train me!" or "I want to unlearn my talents".</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>68</td>
<td>instance_template</td>
<td>This table has all the templates for every instance. When a group enters an instance, a new copy of that instance is made from the values in these fields.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>69</td>
<td>item_enchantment_template</td>
<td>This table holds enchantment chance information for items that should have either a random property or a random suffix attached to them.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>70</td>
<td>item_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>71</td>
<td>item_required_target</td>
<td>These spell effects require a specific target in either alive or dead state (for creatures).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>72</td>
<td>item_template</td>
<td>Holds information on every item that exists in the game. All items are created from the template stored in this table.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>73</td>
<td>locales_creature</td>
<td>This table is used to provide to localized clients with localized string for creatures.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>74</td>
<td>locales_gameobject</td>
<td>This table is used to provide to localized clients with localized string for gameobjects.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>75</td>
<td>locales_gossip_menu_option</td>
<td>This table is used to provide localized clients with localized string for gossip_menu_option.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>76</td>
<td>locales_item</td>
<td>This table is used to provide to localized clients with localized string for items.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>77</td>
<td>locales_npc_text</td>
<td>This table is used to provide localized clients with localized string for npc_texts.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>78</td>
<td>locales_page_text</td>
<td>This table is used to provide localized clients with localized string for page_texts.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>79</td>
<td>locales_points_of_interest</td>
<td>This table is used to provide to localized clients with localized string for points_of_interest.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>80</td>
<td>locales_quest</td>
<td>This table is used to provide to localized clients with localized string for quest templates.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>81</td>
<td>mail_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>82</td>
<td>mangos_string</td>
<td>This table holds all of the strings used internally by the server. This table is provided with the main purpose of translation in mind.

NOTE: The % arguments need to stay in the exact same order as they are provided by default in the English translation.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>83</td>
<td>npc_gossip</td>
<td>THIS TABLE IS OUTDATED. DO NOT USE
<br/> 
It should have been removed around 2009, but for some bad reasons it wasn’t..

Use table gossip_menu instead.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>84</td>
<td>npc_text</td>
<td>This table contains the texts that are used for gossip. 
<br />
More research needs to be done on this table !
<br />
Text is shown in the start of the talk window.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>85</td>
<td>npc_trainer</td>
<td>This table holds all the information on training NPCs. All spells listed in the table are learning spells. This means that the main effect of the spells listed here is to teach spells to the target (which is the player in this case). Any other spell that is not a learning spell will be ignored and an error message will be shown in the console window. Learning spells usually have the same name as their actual spell counterparts and are listed as Uncategorized in Wowhead.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>86</td>
<td>npc_trainer_template</td>
<td>This table holds all the information on training NPCs. All spells listed in the table are learning spells. This means that the main effect of the spells listed here is to teach spells to the target (which is the player in this case). Any other spell that is not a learning spell will be ignored and an error message will be shown in the console window. Learning spells usually have the same name as their actual spell counterparts and are listed as Uncategorized in Wowhead.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>87</td>
<td>npc_vendor</td>
<td>This table holds the vendor data for all NPCs that sell items. The gold price for each item is in its item template as BuyPrice.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>88</td>
<td>npc_vendor_template</td>
<td>This table holds the vendor data for all NPCs that sell items. The gold price for each item is in its item template as BuyPrice.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>89</td>
<td>page_text</td>
<td>This table holds the text for letter items or any items that when moused-over turn the cursor into a magnifying glass and on right-click will open up a window where you can read the contents of the letter.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>90</td>
<td>pet_levelstats</td>
<td>This table holds information on individual pet base stats based on level.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>91</td>
<td>pet_name_generation</td>
<td>This table holds pieces of names (first and last half) that are use for pet name generation.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>92</td>
<td>petcreateinfo_spell</td>
<td>This table holds spells which are assigned to tameable creatures.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>93</td>
<td>pickpocketing_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>94</td>
<td>player_classlevelstats</td>
<td>This table holds information on the base health and mana of characters when they level up. Each class has different level stats. All of the values in this table signify only the base health and mana of the class at a specific level.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>95</td>
<td>player_levelstats</td>
<td>This table holds information on what stats are gained by characters when they level up. Each race-class combination has different level stats. All of the values in this table signify only the base stats of the race-class combination at a specific level.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>96</td>
<td>player_xp_for_level</td>
<td>Includes information on how much experience needed for next level.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>97</td>
<td>playercreateinfo</td>
<td>This table holds the start positions of each class-race combinations for all newly created characters.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>98</td>
<td>playercreateinfo_action</td>
<td>This table holds information on what default actions a brand new character should start out with. Each race-class combination can have a different default starting setup.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>99</td>
<td>playercreateinfo_item</td>
<td>This table holds information on what items each race-class combination of a new character starts out with.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>100</td>
<td>playercreateinfo_spell</td>
<td>This table holds information on what spells newly created characters should start out with. A character in this table is defined by his/her race and class combination.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>101</td>
<td>points_of_interest</td>
<td>This table holds definitions for points of interests in various locations.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>102</td>
<td>pool_creature</td>
<td>Contains all pool instances that participate to any game event.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>103</td>
<td>pool_creature_template</td>
<td>Contains all pool instances that participate to any game event.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>104</td>
<td>pool_gameobject</td>
<td>Contains all pool instances that participate to any game event.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>105</td>
<td>pool_gameobject_template</td>
<td>Contains all pool instances that participate to any game event.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>106</td>
<td>pool_pool</td>
<td>This is the pool of pools table. You can create a pool with a chance of a range of pools in that pool being activated.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>107</td>
<td>pool_template</td>
<td>Contains all pool instances that participate to any game event.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>108</td>
<td>quest_template</td>
<td>Contains all basic definitions of quests available.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>109</td>
<td>reference_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>110</td>
<td>reputation_reward_rate</td>
<td>Holds reputation multipliers for specific factions.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>111</td>
<td>reputation_spillover_template</td>
<td>This table holds information for alternative factions which can be awarded reputation, if the faction originally rewarded to is already at the highest reachable level.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>112</td>
<td>reserved_name</td>
<td>This table serves as a simple list of names that players (gmlevel == 0) cannot use when naming their characters.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>115</td>
<td>scripted_areatrigger</td>
<td>This table links areatriggers to C++ scripts.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>116</td>
<td>scripted_event</td>
<td>This table links events to C++ scripts.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>117</td>
<td>sd2_db_version</td>
<td>This table holds the current version of the Scripts database</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>118</td>
<td>skill_fishing_base_level</td>
<td>This table controls the minimum skill level required in fishing to fish in a certain area.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>119</td>
<td>skinning_loot_template</td>
<td>This table format is used to generate different loot items. Loot templates define only items in the loot.
See comments about money drop in corpse, pickpocketing and luggage loot in creature_template and item_template.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>120</td>
<td>spell_affect</td>
<td>This table holds information on what spells are affected by what spell mods. All spells in this table need to apply an aura that either adds a flat modifier to other spells or adds a percent modifier to other spells. Also, a single row in this table only holds information on a single spell effect that applies the aura. Therefore since a spell may have up to three effects, a maximum of 3 rows per spell is allowed. However, only the spell effects that apply the flat or percent auras will be used.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>121</td>
<td>spell_area</td>
<td>This table holds information on what spells are applied to npcs/players in some areas.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>122</td>
<td>spell_bonus_data</td>
<td>Table used for storing custom damage/healing bonus coefficients.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>123</td>
<td>spell_chain</td>
<td>This table defines spell chains. A spell chain is a series of spells which all share the same name and all do the same thing; however, each has a different rank and as the rank increases, so does the spell damage/heal/etc values. This table also controls what spells are replaced by their more powerful later ranks; however, that is also decided by other factors as well (if mana costs for both spells are the same, etc). All fields in this table except rank are spell IDs from Spell.dbc.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>124</td>
<td>spell_elixir</td>
<td>This table holds elixir information to be used to properly stack the elixirs.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>125</td>
<td>spell_facing</td>
<td>This table holds information indicating whether a caster needs to face the target when casting a spell.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>126</td>
<td>spell_learn_spell</td>
<td>This table holds information on spells that should be learned at the same time a player learns another spell. For example the few spells that are automatically learned when a player first learns a new profession. All fields in this table use spell IDs from Spell.dbc

NOTE: Spells with spell effects SPELL_EFFECT_LEARN_SPELL should NOT be included in this table.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>127</td>
<td>spell_linked</td>
<td>This table provides data for spell linking system, telling it what spells trigger what, and under what conditions.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>128</td>
<td>spell_pet_auras</td>
<td>This table holds information for connecting pet creatures to spells and auras.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>129</td>
<td>spell_proc_event</td>
<td>This table holds information on what events (or procs) certain spells are activated. All spells in this table must have apply a SPELL_AURA_PROC_TRIGGER_SPELL (42) aura. Any entries in this table will overwrite the existing proc settings in the spell’s DBC entry.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>130</td>
<td>spell_proc_item_enchant</td>
<td>This table holds information for proc chances of spells which enchant weapons.<br/>
<br/>
This also includes shaman weapon enchants.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>131</td>
<td>spell_script_target</td>
<td>Used to control SpellEffect with ImplicitTargetA-B == 7|8|38|40|46|52.

These spell effects require a specific target in either alive or dead state (for creatures).</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>132</td>
<td>spell_target_position</td>
<td>This table holds coordinate information on where the player should be teleported to when a spell with effect SPELL_EFFECT_TELEPORT_UNITS.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>133</td>
<td>spell_threat</td>
<td>This table holds threat values on all spells that should either give or take away threat.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>134</td>
<td>transports</td>
<td>This table contains all type 15 transports (Boats and Zeppelins). 
<br />
All other transport types have their frame time read from TransportAnimation.dbc.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>135</td>
<td>world_template</td>
<td>This table holds informations for connection world continents to scripts from the script library.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>186</td>
<td>dbdocsfields_localised</td>
<td>This table is part of the implementation of the 'Mangos Database Documentation' (MDD) Project.


An entry in this table provides a link to the table and field to allow additional notes to describe the field in the Wiki for localised entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>187</td>
<td>dbdocslanguage</td>
<td>This table is part of the implementation of the 'Mangos Database Documentation' (MDD) Project.


This table provides a list of supported languages, based on the entries provided in the core.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>188</td>
<td>dbdocssubtables_localised</td>
<td>This table is part of the implementation of the 'Mangos Database Documentation' (MDD) Project.


An entry in this table provides a table which dirctly replaces the link in the fieldnotes for localised entries.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>189</td>
<td>dbdocstable_localised</td>
<td>This table is part of the implementation of the 'Mangos Database Documentation' (MDD) Project.


An entry in this table provides a additional localised notes field to describe the database in the Wiki in that language.</td>
<td></td>
</tr>
</table>
<br />
