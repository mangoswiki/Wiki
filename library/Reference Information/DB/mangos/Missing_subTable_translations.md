[![](/wiki/icons/home.gif)](/wiki/Home.md)
[![](/wiki/icons/back.gif)](/wiki/Progress.md)

-----

#### Description of the MaNGOSZero Missing Translations

----

##### Please Note that the | symbol is a field separator and the symbols < and > are justification flags. None of these should be removed or altered.

<br/>
<table border='1' cellspacing='0' cellpadding='4' bgcolor='#f0f0f0' width='100%'>
<tr>
<td>SubtableId</td>
<td>SubtableName</td>
<td>English</td>
<td>Localised</td>
</tr>
<tr bgcolor='#FFFFEE'><td>10</td>
<td>Battlegrounds</td>
<td>Value|<Battleground Name
1|Alterac Valley
2|Warsong Gulch
3|Arathi Basin</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>11</td>
<td>BG - Min players per team</td>
<td>Tier|Level Ranges
1|10-19
2|20-29
3|30-39
4|40-49
5|50-59
6|60-69
7|70</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>12</td>
<td>Conditions</td>
<td>ID|<Type|<Description
-3|CONDITION_NOT|Used to evaluate if another condition is NOT true.
-2|CONDITION_OR|Used to evaluate if condition OR condition is true.
-1|CONDITION_AND|Used to evaluate if condition AND condition is true.
0|CONDITION_NONE|This condition is not used at all.
1|CONDITION_AURA|Checks target currently has the specified aura on him/her.
2|CONDITION_ITEM|Checks if the player has the required amount (value2) of items in his/hers inventory.
3|CONDITION_ITEM_EQUIPPED|Checks if the player has the specified item equipped.
4|CONDITION_AREAID|Checks if the player is within the specified area.
5|CONDITION_REPUTATION_RANK_MIN|Checks if the player has the minimum required reputation rank with a specific faction.
6|CONDITION_TEAM|Checks what team the target is a member of.
7|CONDITION_SKILL|Checks if the player has the required minimum skill value of the specified skill.
8|CONDITION_QUESTREWARDED|Checks if the player has been rewarded for the specified quest.
9|CONDITION_QUESTTAKEN|Checks if the player has taken the quest (as in has it in his/hers quest log.)
10|CONDITION_AD_COMMISSION_AURA|TODO
11|CONDITION_NO_AURA|Checks if the target DOES NOT currently have the specified aura on him/her.
12|CONDITION_ACTIVE_GAME_EVENT|Checks if a game event is currently active.
13|CONDITION_AREA_FLAG|Checks if area_flag is present in current area (if area_flag set != 0) AND if not_have_flag is not present in current area (if not_have_flag != 0)
14|CONDITION_RACE_CLASS|Checks if the target is a certain race AND/OR class.
15|CONDITION_LEVEL|Checks the targets level.
16|CONDITION_NOITEM|Checks if the player DOES NOT have the required amount (value2) of items in his/hers inventory.
17|CONDITION_SPELL|Checks if the target has or hasn’t (value2) the specified spell.
18|CONDITION_INSTANCE_SCRIPT|TODO
19|CONDITION_QUESTAVAILABLE|Checks if the specified quest is available (can start it) for the player.
20|CONDITION_RESERVED_1|Reserved for later usage
21|CONDITION_RESERVED_2|Reserved for later usage
22|CONDITION_QUEST_NONE|Checks if the player has NOT taken the quest AND has NOT been rewarded for the quest.
23|CONDITION_ITEM_WITH_BANK|Checks if the player has the required amount (value2) of items in his/hers inventory OR bank.
24|CONDITION_NOITEM_WITH_BANK|Checks if the player DOES NOT have count (value2) of items in his/hers inventory OR bank.
25|CONDITION_NOT_ACTIVE_GAME_EVENT|Checks if a game event is currently NOT active.
26|CONDITION_ACTIVE_HOLIDAY|Checks if a holiday is active
27|CONDITION_NOT_ACTIVE_HOLIDAY|Checks if a holiday is not active
28|CONDITION_LEARNABLE_ABILITY|Checks if the player can learn ability (using minimum skill value from SkillLineAbility.dbc.) If the player has spell or has item (when defined) the condition will evaluate to false.
29|CONDITION_SKILL_BELOW|TODO
30|CONDITION_REPUTATION_RANK_MAX|Checks if the player has a higher reputation rank than specified a faction.
31|CONDITION_RESERVED_3|Reserved for later usage
32|CONDITION_SOURCE_AURA|Checks if the source of the condition (like looted npc) has an aura.
33|CONDITION_LAST_WAYPOINT|Checks the waypoint-state of the source of the condition.
34|CONDITION_RESERVED_4|Reserved for later usage
35|CONDITION_GENDER|Checks the gender of a player.
36|CONDITION_DEAD_OR_AWAY|Checks if a player, a player’s group, all players in an instance, or a creature is dead or left the map.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>13</td>
<td>Sheath state</td>
<td>Value|<State
0|All weapons sheathed
1|Melee weapon unsheathed
2|Ranged weapon unsheathed</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>14</td>
<td>Movement Animation</td>
<td>Value|<Movement Animation
0x00000000|MOVEFLAG_NONE
0x00000001|MOVEFLAG_FORWARD
0x00000002|MOVEFLAG_BACKWARD
0x00000004|MOVEFLAG_STRAFE_LEFT
0x00000008|MOVEFLAG_STRAFE_RIGHT
0x00000010|MOVEFLAG_TURN_LEFT
0x00000020|MOVEFLAG_TURN_RIGHT
0x00000040|MOVEFLAG_PITCH_UP
0x00000080|MOVEFLAG_PITCH_DOWN
0x00000100|MOVEFLAG_WALK_MODE
0x00000400|MOVEFLAG_LEVITATING
0x00000800|MOVEFLAG_ROOT
0x00002000|MOVEFLAG_FALLING
0x00004000|MOVEFLAG_FALLINGFAR
0x00200000|MOVEFLAG_SWIMMING
0x00400000|MOVEFLAG_ASCENDING
0x00800000|MOVEFLAG_CAN_FLY
0x01000000|MOVEFLAG_FLYING
0x02000000|MOVEFLAG_ONTRANSPORT
0x04000000|MOVEFLAG_SPLINE_ELEVATION
0x08000000|MOVEFLAG_SPLINE_ENABLED
0x10000000|MOVEFLAG_WATERWALKING
0x20000000|MOVEFLAG_SAFE_FALL
0x40000000|MOVEFLAG_HOVER</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>15</td>
<td>Example Auras</td>
<td>Value|<Result
'16380 0'|Makes the creature_template invisible
'18950 0 18950 1'|Makes the creature_template detect invisible creatures and players</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>16</td>
<td>Item Class</td>
<td>ID|<Name
0|Consumable
1|Container
2|Weapon
4|Armor
5|Reagent
6|Projectile
7|Trade Goods
9|Recipe
11|Quiver
12|Quest
13|Key
15|Miscellaneous</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>17</td>
<td>Item SubClass</td>
<td>Class ID|Subclass ID|<Subclass
0|0|Consumable
1|0|Container, Bag
1|1|Container, Soul bag
1|2|Container, Herb bag
1|3|Container, Enchanting bag
1|4|Container, Engineering bag
2|0|Weapon, Axe 1H
2|1|Weapon, Axe 2H
2|2|Weapon, Bow
2|3|Weapon, Gun
2|4|Weapon, Mace 1H
2|5|Weapon, Mace 2H
2|6|Weapon, Polearm
2|7|Weapon, Sword 1H
2|8|Weapon, Sword 2H
2|10|Weapon, Staff
2|13|Weapon, Fist weapon
2|14|Weapon, Miscellaneous
2|15|Weapon, Dagger
2|16|Weapon, Thrown
2|17|Weapon, Spear
2|18|Weapon, Crossbow
2|19|Weapon, Wand
2|20|Weapon, Fishing pole
4|0|Armor, Miscellaneous
4|1|Armor, Cloth
4|2|Armor, Leather
4|3|Armor, Mail
4|4|Armor, Plate
4|6|Armor, Shield
4|7|Armor, Libram
4|8|Armor, Idol
4|9|Armor, Totem
5|0|Reagent
6|2|Projectile, Arrow
6|3|Projectile, Bullet
7|0|Trade goods, Trade goods
7|1|Trade goods, Parts
7|2|Trade goods, Explosives
7|3|Trade goods, Devices
9|0|Recipe, Book
9|1|Recipe, Leatherworking
9|2|Recipe, Tailoring
9|3|Recipe, Engineering
9|4|Recipe, Blacksmithing
9|5|Recipe, Cooking
9|6|Recipe, Alchemy
9|7|Recipe, First aid
9|8|Recipe, Enchanting
9|9|Recipe, Fishing
11|2|Quiver
11|3|Ammo pouch
12|0|Quest
13|0|Key
13|1|Lockpick
15|0|Miscellaneous, Junk</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>18</td>
<td>Inventory Type</td>
<td>Value|<Slot name
0|Not equipable
1|Head
2|Neck
3|Shoulders
4|Body
5|Chest
6|Waist
7|Legs
8|Feet
9|Wrists
10|Hands
11|Finger
12|Trinket
13|Weapon
14|Shield
15|Ranged
16|Cloak
17|2H weapon
18|Bag
19|Tabard
20|Robe
21|Weapon, main hand
22|Weapon, offhand
23|Holdable
24|Ammo
25|Thrown
26|Ranged, right
27|Quiver
28|Relic</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>19</td>
<td>Material Type</td>
<td>Value|<Material
1|Metal
2|Wood
3|Liquid
4|Jewelry
5|Chain
6|Plate
7|Cloth
8|Leather</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>20</td>
<td>Sheath Type</td>
<td>Value|<Type|<Description
0|None|No sheathing
1|Main hand|On the back, pointing down
2|Off hand|On the back, pointing up
3|Large weapon left|&nbsp;
4|Large weapon right|&nbsp;
5|Hip weapon left|To the side
6|Hip weapon right|To the side
7|Shield|On the back, in the middle</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>21</td>
<td>Text Substitution</td>
<td>Value|<Description
%s|Creature name
$n|Character name
$r|Character race
$c|Character class</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>22</td>
<td>Emotes</td>
<td>Value|<Emote Name
10|EMOTE_STATE_DANCE
12|EMOTE_STATE_SLEEP
13|EMOTE_STATE_SIT
26|EMOTE_STATE_STAND
28|EMOTE_STATE_WORK
64|EMOTE_STATE_STUN
64|EMOTE_STATE_DEAD
68|EMOTE_STATE_KNEEL
70|EMOTE_ONESHOT_WAVE_NOSHEATHE
71|EMOTE_ONESHOT_CHEER_NOSHEATHE
92|EMOTE_ONESHOT_EAT_NOSHEATHE
173|EMOTE_STATE_WORK_NOSHEATHE
379|EMOTE_STATE_FISHING
380|EMOTE_ONESHOT_FISHING
381|EMOTE_ONESHOT_LOOT
382|EMOTE_STATE_WHIRLWIND
392|EMOTE_STATE_LAUGH
398|EMOTE_STATE_CANNIBALIZE
400|EMOTE_STATE_DANCESPECIAL
412|EMOTE_STATE_EXCLAIM
415|EMOTE_STATE_SIT_CHAIR_MED</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>23</td>
<td>AI ScriptType</td>
<td>Value|<Description
NullAI|Do nothing. Same as empty string.
AggressorAI|Creature attacks when entering aggro radius.
ReactorAI|Creature attacks only if aggroed by spell.
GuardAI|Creature is a zone guard.
PetAI|Creature is a pet.
TotemAI|Creature casts spell from spell1.
EventAI|Creature uses event based AI.</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>24</td>
<td>Creature Rank Type</td>
<td>Value|Name|<Description
0|Normal|Default type
1|Elite|Increased health, damage, better loot
2|Rare elite|Like Elite but with increased respawn time
3|World boss|Highest rank, best loot, highest respawn time
4|Rare|Increased respawn time, better loot</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>25</td>
<td>Creature Family</td>
<td>ID|Family|
1|Wolf
2|Cat
3|Spider
4|Bear
5|Boar
6|Crocolisk
7|Carrion Bird
8|Crab
9|Gorilla
11|Raptor
12|Tallstrider
15|Felhunter
16|Voidwalker
17|Succubus
19|Doomguard
20|Scorpid
21|Turtle
23|Imp
24|Bat
25|Hyena
26|Owl
27|Wind Serpent
28|Remote Control</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>26</td>
<td>Creature Type</td>
<td>ID|Family|
0|None
1|Beast
2|Dragonkin
3|Demon
4|Elemental
5|Giant
6|Undead
7|Humanoid
8|Critter
9|Mechanical
10|Not Specified
11|Totem
12|Non-combat pet
13|Gas Cloud</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>27</td>
<td>GameObject Type DataFields</td>
<td>>GameObject Type|<Field|<Meaning
DOOR = 0|&nbsp;|&nbsp;
&nbsp;|data0|startOpen (Boolean flag)
&nbsp;|data1|open (LockId from Lock.dbc)
&nbsp;|data2|autoClose (65536 * seconds) (e.g. open after 5min = 19660800)
&nbsp;|data3|noDamageImmune (Boolean flag)
&nbsp;|data4|openTextID (Unknown Text ID)
&nbsp;|data5|closeTextID (Unknown Text ID)
BUTTON = 1|&nbsp;|&nbsp;
&nbsp;|data0|startOpen (State)
&nbsp;|data1|open (LockId from Lock.dbc)
&nbsp;|data2|autoClose (65536 * seconds)
&nbsp;|data3|linkedTrap (gameobject_template.entry (Spawned GO type 6))
&nbsp;|data4|noDamageImmune (Boolean flag)
&nbsp;|data5|large? (Boolean flag)
&nbsp;|data6|openTextID (Unknown Text ID)
&nbsp;|data7|closeTextID (Unknown Text ID)
&nbsp;|data8|losOK (Boolean flag)
QUESTGIVER = 2|&nbsp;|&nbsp;
&nbsp;|data0|open (LockId from Lock.dbc)
&nbsp;|data1|questList (unknown ID)
&nbsp;|data2|pageMaterial (PageTextMaterial.dbc)
&nbsp;|data3|gossipID (unknown ID)
&nbsp;|data4|customAnim (unknown value from 1 to 4)
&nbsp;|data5|noDamageImmune (Boolean flag)
&nbsp;|data6|openTextID (Unknown Text ID)
&nbsp;|data7|losOK (Boolean flag)
&nbsp;|data8|allowMounted (Boolean flag)
&nbsp;|data9|large? (Boolean flag)
CHEST = 3|&nbsp;|&nbsp;
&nbsp;|data0|open (LockId from Lock.dbc)
&nbsp;|data1|chestLoot (gameobject_loot_template.entry) *This field is obtained from WDB data and is not to be changed*
&nbsp;|data2|chestRestockTime (time in seconds)
&nbsp;|data3|consumable (State - Boolean flag)
&nbsp;|data4|minRestock (Min successful loot attempts for Mining, Herbalism etc)
&nbsp;|data5|maxRestock (Max successful loot attempts for Mining, Herbalism etc)
&nbsp;|data6|lootedEvent (unknown ID)
&nbsp;|data7|linkedTrap (gameobject_template.entry (Spawned GO type 6))
&nbsp;|data8|questID (quest_template.entry of completed quest)
&nbsp;|data9|level (minimal level required to open this gameobject)
&nbsp;|data10|losOK (Boolean flag)
&nbsp;|data11|leaveLoot (Boolean flag)
&nbsp;|data12|notInCombat (Boolean flag)
&nbsp;|data13|log loot (Boolean flag)
&nbsp;|data14|openTextID (Unknown ID)
&nbsp;|data15|use group loot rules (Boolean flag)
BINDER = 4|&nbsp;|&nbsp;
&nbsp;||Object type not used
GENERIC = 5|&nbsp;|&nbsp;
&nbsp;|data0|floatingTooltip (Boolean flag)
&nbsp;|data1|highlight (Boolean flag)
&nbsp;|data2|serverOnly? (Always 0)
&nbsp;|data3|large? (Boolean flag)
&nbsp;|data4|floatOnWater (Boolean flag)
&nbsp;|data5|questID (Required active quest_template.entry to work)
TRAP = 6|&nbsp;|&nbsp;
&nbsp;|data0|open (LockId from Lock.dbc)
&nbsp;|data1|level (npc equivalent level for casted spell)
&nbsp;|data2|diameter (so radius*2)
&nbsp;|data3|spell (Spell Id from spell.dbc)
&nbsp;|data4|charges (0 or 1)
&nbsp;|data5|cooldown (time in seconds)
&nbsp;|data6|autoClose (unknown)
&nbsp;|data7|startDelay? (time in seconds)
&nbsp;|data8|serverOnly? (always 0)
&nbsp;|data9|stealthed (Boolean flag)
&nbsp;|data10|large? (Boolean flag)
&nbsp;|data11|stealthAffected (Boolean flag)
&nbsp;|data12|openTextID (Unknown ID)
CHAIR = 7|&nbsp;|&nbsp;
&nbsp;|data0|chairslots (number of players that can sit down on it)
&nbsp;|data1|chairorientation? (number of usable side?)
SPELLFOCUS = 8|&nbsp;|&nbsp;
&nbsp;|data0|spellFocusType (from SpellFocusObject.dbc)
&nbsp;|data1|diameter (so radius*2)
&nbsp;|data2|linkedTrap (gameobject_template.entry (Spawned GO type 6))
TEXT = 9|&nbsp;|&nbsp;
&nbsp;|data0|pageID (page_text.entry)
&nbsp;|data1|language (from Languages.dbc)
&nbsp;|data2|pageMaterial (PageTextMaterial.dbc)
GOOBER = 10|&nbsp;|&nbsp;
&nbsp;|data0|open (LockId from Lock.dbc)
&nbsp;|data1|questID (Required active quest_template.entry to work)
&nbsp;|data2|eventID (The id of the event that the gameobject will activate)
&nbsp;|data3|autoClose (most be the same like doors (65536 * seconds))
&nbsp;|data4|customAnim (unknown)
&nbsp;|data5|consumable (Boolean flag controling if gameobject will despawn or not)
&nbsp;|data6|cooldown (time in seconds)
&nbsp;|data7|pageID (page_text.entry)
&nbsp;|data8|language (from Languages.dbc)
&nbsp;|data9|pageMaterial (PageTextMaterial.dbc)
&nbsp;|data10|spell (Spell Id from spell.dbc)
&nbsp;|data11|noDamageImmune (Boolean flag)
&nbsp;|data12|linkedTrap (gameobject_template.entry (Spawned GO type 6))
&nbsp;|data13|large? (Boolean flag)
&nbsp;|data14|openTextID (Unknown ID)
&nbsp;|data15|closeTextID (Unknown ID)
&nbsp;|data16|losOK (Boolean flag)
TRANSPORT = 11|&nbsp;|&nbsp;
&nbsp;||No data data used, all are always 0
AREADAMAGE = 12|&nbsp;|&nbsp;
&nbsp;||Object type not used
CAMERA = 13|&nbsp;|&nbsp;
&nbsp;|data0|open (LockId from Lock.dbc)
&nbsp;|data1|camera (Cinematic entry from CinematicCamera.dbc)
MAPOBJECT = 14|&nbsp;|&nbsp;
&nbsp;||No data data used, all are always 0
MOTRANSPORT = 15|&nbsp;|&nbsp;
&nbsp;|data0|taxiPathID (Id from TaxiPath.dbc)
&nbsp;|data1|moveSpeed
&nbsp;|data2|accelRate
DUELFLAG = 16|&nbsp;|&nbsp;
&nbsp;||Only one Gameobject with this type (21680) and no data data
FISHINGNODE = 17|&nbsp;|&nbsp;
&nbsp;||Only one Gameobject with this type (35591) and no data data
RITUAL = 18|&nbsp;|&nbsp;
&nbsp;|data0|casters?
&nbsp;|data1|spell (Spell Id from spell.dbc)
&nbsp;|data2|animSpell (Spell Id from spell.dbc)
&nbsp;|data3|ritualPersistent (Boolean flag)
&nbsp;|data4|casterTargetSpell (Spell Id from spell.dbc)
&nbsp;|data5|casterTargetSpellTargets (Boolean flag)
&nbsp;|data6|castersGrouped (Boolean flag)
MAILBOX = 19|&nbsp;|&nbsp;
&nbsp;||No data data used, all are always 0
AUCTIONHOUSE = 20|&nbsp;|&nbsp;
&nbsp;|data0|actionHouseID (From AuctionHouse.dbc ?)
GUARDPOST = 21|&nbsp;|&nbsp;
&nbsp;||Object type not used
SPELLCASTER = 22|&nbsp;|&nbsp;
&nbsp;|data0|spell (Spell Id from spell.dbc)
&nbsp;|data1|charges
&nbsp;|data2|partyOnly (Boolean flag, need to be in group to use it)
MEETINGSTONE = 23|&nbsp;|&nbsp;
&nbsp;|data0|minLevel
&nbsp;|data1|maxLevel
&nbsp;|data2|areaID (From AreaTable.dbc)
FLAGSTAND = 24|&nbsp;|&nbsp;
&nbsp;|data0|open (LockId from Lock.dbc)
&nbsp;|data1|pickupSpell (Spell Id from spell.dbc)
&nbsp;|data2|radius (distance)
&nbsp;|data3|returnAura (Spell Id from spell.dbc)
&nbsp;|data4|returnSpell (Spell Id from spell.dbc)
&nbsp;|data5|noDamageImmune (Boolean flag)
&nbsp;|data6|openTextID
&nbsp;|data7|losOK (Boolean flag)
FISHINGHOLE = 25|&nbsp;|&nbsp;
&nbsp;|data0|radius (distance)
&nbsp;|data1|chestLoot (gameobject_loot_template.entry)
&nbsp;|data2|minRestock
&nbsp;|data3|maxRestock
FLAGDROP = 26|&nbsp;|&nbsp;
&nbsp;|data0|open (LockId from Lock.dbc)
&nbsp;|data1|eventID (Unknown Event ID)
&nbsp;|data2|pickupSpell (Spell Id from spell.dbc)
&nbsp;|data3|noDamageImmune (Boolean flag)
MINIGAME = 27|&nbsp;|&nbsp;
&nbsp;||Object type not used
&nbsp;||Reused in core for CUSTOM_TELEPORT
|** data0|areatrigger_teleport.id
LOTTERYKIOSK = 28|&nbsp;|&nbsp;
&nbsp;||Object type not used
CAPTUREPOINT = 29|&nbsp;|&nbsp;
&nbsp;|data0|radius (Distance)
&nbsp;|data1|spell (Unknown ID, not a spell id in dbc file, maybe server only side spell)
&nbsp;|data2|worldState1
&nbsp;|data3|worldstate2
&nbsp;|data4|winEventID1 (Unknown Event ID)
&nbsp;|data5|winEventID2 (Unknown Event ID)
&nbsp;|data6|contestedEventID1 (Unknown Event ID)
&nbsp;|data7|contestedEventID2 (Unknown Event ID)
&nbsp;|data8|progressEventID1 (Unknown Event ID)
&nbsp;|data9|progressEventID2 (Unknown Event ID)
&nbsp;|data10|neutralEventID1 (Unknown Event ID)
&nbsp;|data11|neutralEventID2 (Unknown Event ID)
&nbsp;|data12|neutralPercent
&nbsp;|data13|worldstate3
&nbsp;|data14|minSuperiority
&nbsp;|data15|maxSuperiority
&nbsp;|data16|minTime (in seconds)
&nbsp;|data17|maxTime (in seconds)
&nbsp;|data18|large? (Boolean flag)
AURAGENERATOR = 30|&nbsp;|&nbsp;
&nbsp;|data0|startOpen (Boolean flag)
&nbsp;|data1|radius (Distance)
&nbsp;|data2|auraID1 (Spell Id from spell.dbc)
&nbsp;|data3|conditionID1 (Unknown ID)
DUNGEONDIFFICULTY = 31|&nbsp;|&nbsp;
&nbsp;|data0|mapID (From Map.dbc)
&nbsp;|data1|difficulty (0 or 1)
BARBER_CHAIR = 32|&nbsp;|&nbsp;
&nbsp;||Used for barber chairs.
DESTRUCTIBLE_BUILDING = 33|&nbsp;|&nbsp;
&nbsp;||Object type not used
GUILD_BANK = 34|&nbsp;|&nbsp;
&nbsp;||No data data used, all are always 0</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>28</td>
<td>GameObject Types</td>
<td>>GameObject Identifier|<Value
GAMEOBJECT_TYPE_DOOR|0
GAMEOBJECT_TYPE_BUTTON|1
GAMEOBJECT_TYPE_QUESTGIVER|2
GAMEOBJECT_TYPE_CHEST|3
GAMEOBJECT_TYPE_BINDER|4
GAMEOBJECT_TYPE_GENERIC|5
GAMEOBJECT_TYPE_TRAP|6
GAMEOBJECT_TYPE_CHAIR|7
GAMEOBJECT_TYPE_SPELLFOCUS|8
GAMEOBJECT_TYPE_TEXT|9
GAMEOBJECT_TYPE_GOOBER|10
GAMEOBJECT_TYPE_TRANSPORT|11
GAMEOBJECT_TYPE_AREADAMAGE|12
GAMEOBJECT_TYPE_CAMERA|13
GAMEOBJECT_TYPE_MAPOBJECT|14
GAMEOBJECT_TYPE_MOTRANSPORT|15
GAMEOBJECT_TYPE_DUELFLAG|16
GAMEOBJECT_TYPE_FISHINGNODE|17
GAMEOBJECT_TYPE_RITUAL|18
GAMEOBJECT_TYPE_MAILBOX|19
GAMEOBJECT_TYPE_AUCTIONHOUSE|20
GAMEOBJECT_TYPE_GUARDPOST|21
GAMEOBJECT_TYPE_SPELLCASTER|22
GAMEOBJECT_TYPE_MEETINGSTONE|23
GAMEOBJECT_TYPE_FLAGSTAND|24
GAMEOBJECT_TYPE_FISHINGHOLE|25
GAMEOBJECT_TYPE_FLAGDROP|26
GAMEOBJECT_TYPE_MINIGAME|27
GAMEOBJECT_TYPE_LOTTERYKIOSK|28
GAMEOBJECT_TYPE_CAPTUREPOINT|29
GAMEOBJECT_TYPE_AURAGENERATOR|30
GAMEOBJECT_TYPE_DUNGEONDIFFICULTY|31
GAMEOBJECT_TYPE_BARBER_CHAIR|32
GAMEOBJECT_TYPE_DESTRUCTIBLE_BUILDING|33
GAMEOBJECT_TYPE_GUILD_BANK|34</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>29</td>
<td>GameObject Flags</td>
<td>Value|<Meaning
1|in use (can’t interact with the object)
2|Makes chests/doors locked (requiring a key, spell, event to open)
4|Untargetable
8|Transport (Object can transport (elevator, boat, car))
16|Player cant interact with the object.
32|No despawn (never despawn, typically for doors, they just change state)
64|Triggered (typically, summoned objects. Triggered by spell or other events)</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>30</td>
<td>Movement Types</td>
<td>ID|<Type
0|Idle; stay in one place 
1|Random movement inside the spawndist radius 
2|Waypoint movement</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>31</td>
<td>Inhabit Type</td>
<td>ID|<Type
1|Ground only 
2|Water only 
3|Both ground and water 
4|Flying</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>32</td>
<td>Unit Flags</td>
<td>Flag|<Name|<Comments
1|UNIT_FLAG_UNK_0|&nbsp;
2|UNIT_FLAG_NON_ATTACKABLE|&nbsp;
4|UNIT_FLAG_DISABLE_MOVE|&nbsp;
8|UNIT_FLAG_PVP_ATTACKABLE|(allow apply pvp rules to attackable state in addition to faction dependent state)
16|UNIT_FLAG_RENAME|&nbsp;
32|UNIT_FLAG_RESTING|&nbsp;
64|UNIT_FLAG_UNK_6|&nbsp;
128|UNIT_FLAG_NOT_ATTACKABLE_1|(??) ((UNIT_FLAG_PVP_ATTACKABLE + UNIT_FLAG_NOT_ATTACKABLE_1) is NON_PVP_ATTACKABLE) 
256|UNIT_FLAG_OOC_NOT_ATTACKABLE|(2.0.8 – Can not be attacked when not in combat. Removed if unit for some reason enter combat.) (2.4.3, Seems to make the unit unattackable) 
512|UNIT_FLAG_PASSIVE|(makes unable to attack everything. Almost identical to "civilian". Will not engage in combat unless "called upon" or engaged by another unit.) 
1024|UNIT_FLAG_LOOTING|(loot animation) 
2048|UNIT_FLAG_PET_IN_COMBAT|(in combat?, 2.0.8) 
4096|UNIT_FLAG_PVP|Allows item spells to be casted upon (?) 
8192|UNIT_FLAG_SILENCED|Can’t cast spells 
16384|UNIT_FLAG_UNK_14|(2.0.8) 
32768|UNIT_FLAG_UNK_15|&nbsp;
65536|UNIT_FLAG_UNK_16|&nbsp;
131072|UNIT_FLAG_PACIFIED|&nbsp;
262144|UNIT_FLAG_DISABLE_ROTATE|(stunned, 2.1.1) 
524288|UNIT_FLAG_IN_COMBAT|&nbsp;
1048576|UNIT_FLAG_TAXI_FLIGHT|(disable casting at client side spell not allowed by taxi flight (mounted?), probably used with 0×4 flag) 
2097152|UNIT_FLAG_DISARMED|(disable melee spells casting…, "Required melee weapon" added to melee spells tooltip.) 
4194304|UNIT_FLAG_CONFUSED|&nbsp;
8388608|UNIT_FLAG_FLEEING|&nbsp;
16777216|UNIT_FLAG_PLAYER_CONTROLLED|(used in spell Eyes of the Beast for pet…) 
33554432|UNIT_FLAG_NOT_SELECTABLE|Can’t be selected by mouse 
67108864|UNIT_FLAG_SKINNABLE|&nbsp;
134217728|UNIT_FLAG_MOUNT|(the client seems to handle it perfectly) 
268435456|UNIT_FLAG_UNK_28|&nbsp;
536870912|UNIT_FLAG_UNK_29|(used in Feign Death spell) 
1073741824|UNIT_FLAG_SHEATHE|&nbsp;
2147483648|UNIT_FLAG_UNK_31|(set skinnable icon and also changes color of portrait) </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>33</td>
<td>Script Target Type</td>
<td>Value|<Description
0|Game object
1|Creature template
2|Dead creature template</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>34</td>
<td>Vendor Conditions</td>
<td>Value|<Condition|<Comments  
0|CONDITION_NONE|Regular drop  
1|CONDITION_AURA|Player looting must have an aura active  
2|CONDITION_ITEM|Player must have a number of items in his/her inventory  
3|CONDITION_ITEM_EQUIPPED|Player must have an item equipped  
4|CONDITION_ZONEID|Player must be in a certain zone  
5|CONDITION_REPUTATION_RANK|Player must have a certain reputation rank with a certain faction  
6|CONDITION_TEAM|Player must be part of the specified team (Alliance or Horde)  
7|CONDITION_SKILL|Player must have a certain skill value  
8|CONDITION_QUESTREWARDED|Player must have completed a quest first  
9|CONDITION_QUESTTAKEN|Players must have the quest in the quest log and not completed yet  
10|CONDITION_AD_COMMISSION_AURA|
11|CONDITION_NO_AURA|Player looting must have no aura active mentioned in condition_value1  
12|CONDITION_ACTIVE_EVENT|The loot with that condition can be looted only while the Event (condition_value1) is active  </td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>35</td>
<td>Item Quality</td>
<td>ID|Color|<Quality
0|Grey|Poor
1|White|Common
2|Green|Uncommon
3|Blue|Rare
4|Purple|Epic
5|Orange|Legendary
6|Red|Artifact</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>36</td>
<td>Quest Method</td>
<td>Value|<Description
0|Quest will auto-complete. Objectives/details will be skipped.
1|Quest is disabled.
2|Quest is enabled.</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>37</td>
<td>Quest Type</td>
<td>Value|<Description
0|Normal
1|Elite
21|Life
41|PvP
62|Raid
81|Dungeon
82|World Event
83|Legendary</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>38</td>
<td>Creature Regen Stats</td>
<td>Value|<Description
0|No regeneration
1|Regenerate health
2|Regenerate power</td>
<td></td>
</tr>
<tr bgcolor='#FEFEFF'><td>39</td>
<td>Creature Racial Leader</td>
<td>Value|<Description
0|Normal creature
1|Racial leader</td>
<td></td>
</tr>
<tr bgcolor='#FFFFEE'><td>40</td>
<td>Creature Dynamic Flags</td>
<td>Value|<Description|<Comments
0|None|&nbsp;
1|Lootable|&nbsp;
2|Track unit|&nbsp;
4|Other tagger|Makes creature name tag appear grey
8|Rooted|&nbsp;
16|Specialinfo|Show basic creature stats in tooltip
32|Dead|Make creature appear dead without tag
64|Tapped by all threat list|&nbsp;</td>
<td></td>
</tr>
</table>
<br />
