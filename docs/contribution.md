#Contribution
You are free to help me with any kind of translation/work.  
Finding typos, mistranslations or even making me notice that there are missing items in the project itself.  
I welcome everything (less work for me).  
Be sure to post it in the Discord in the #feedback channel.

## Text Editor Settings
Most files here, including itemInfo.lua, were edited by using [Notepad++](https://notepad-plus-plus.org/).  
If you're interested in translating, the default settings of NPP aren't suited for editing itemInfo.lua,  
because there are 4 type of fonts that came from 4 main official servers (kRO, jRO, twRO and iRO) that could break items' resource names.

Thus, you need to set up your NPP to:  
1. Open Tab **Settings** > **Preferences** > **New Document**, then change **Encoding** to ANSI  
2. Open Tab **Settings** > **Preferences** > **MISC.**, then DESELECT **Autodetect character encoding**

That way, when you open itemInfo.lua for the first time, it should look like this:
![sample1](https://i.ibb.co/wMH3Hyh/Sample1.jpg)

Other things, like choice of font or style, are up to you.

## Translation Layout
In case you still want to participate and got your Notepad++ or similar ready to go.  
I would like to ask you to pretty much follow this format: 

## itemInfo
```
  * Elements:
    ^FF0000 = Fire
	^0000BB = Water
	^CC5500 = Earth
	^33CC00 = Wind
	^663399 = Poison
	^777777 = Ghost, Undead, Holy, Shadow and Neutral = iteminfo
	^009999 = Ghost, Undead, Holy, Shadow and Neutral = skillinfo
  	
  * Misc
    ^CC6600 = Status (STR,AGI,...)/Base Level
	^0000FF = Numbers
	^663399 = Debuff (Curse, Freeze,...)
	^0033CC = Location
	^FF0000 = Race/Size
	^0033CC = Job Classes

   * Google Translation of Elements:
    fury = Fire
	cancer = Shadow
	castle = Holy
	immortality = Undead
	flame = Ghost

    unidentifiedDescriptionName = { "Can be identified by using a ^990099Magnifier^000000." },
	
	- Stats Codings:
	"Base ^CC6600AGI^000000 at least ^FF000070^000000:",
	"Bonus ^CC6600STR^000000 at least ^FF0000+10^000000:",
	"^CC6600Base Level^000000 at least ^FF0000100^000000:",
	"^CC6600Base Level^000000 is ^FF000099^000000 or less:",
	"^CC6600Base Level^000000 between ^FF0000100~169^000000:",
	"^CC6600Base Level^000000 less than ^FF0000175^000000:",
	"For each ^0000FF20^000000 base ^CC6600STR^000000:",
	"For each ^0000FF50 ^CC6600Base Level^000000:",
	"For each ^0000FF20^000000 combined sum of base ^CC6600AGI^000000 and ^CC6600VIT^000000:",
	"When total combined sum of base ^CC6600VIT^000000 and ^CC6600STR^000000 is ^0000FF250^000000:",
	
	"STR +",
	"AGI +",
	"VIT +",
	"INT +",
	"DEX +",
	"LUK +",
	"ATK +", "ATK +%",
	"MATK +", "MATK +%",
	"DEF +", "DEF +%",
	"MDEF +", "MDEF +%",
	"HIT +", "FLEE +",
	"Perfect Dodge +",
	"Perfect HIT +", "Perfect HIT +%",
	"MaxHP +", "MaxHP +%",
	"MaxSP +", "MaxSP +%",
	"Increases HP Recovery Rate by %.",
	"Increases SP Recovery Rate by %.",
	"Attack Range: x cells",
	"Prevents ^663399<Status^000000 status.",
	"Increases resistance to ^663399<Status>^000000 status by %.",
	"Increases Attack Speed (decreases After Attack Delay by %).",
	"All Basic Stats +",
	
	> 4th Classes:
	"POW +",
	"STA +",
	"WIS +",
	"SPL +",
	"CON +",
	"CRT +",
	"P.ATK +",
	"S.MATK +",
	"H.PLUS +",
	"C.RATE +",
	"RES +",
	"MRES +",
	"All Trait Stats +",
	
	- Damage Descriptions:
	"Inflict % more damage on ^0033CC<Monster>^000000.",
	
	"Increases Magical Damage with ^<Element>^000000 element by %.",
	"Increases Magical Damage with every element by %.",
	"Increases continuous Magical Damage by %.", > Damage Over Time (DOT)
	
	"Increases Physical Damage against monsters of ^FF0000<Race/Size/Class>^000000 race/size/class by %.",
	"Increases Physical Damage against monsters of every race/size/class by %.",
	"Increases Physical Damage against monsters of ^<Element>^000000 element by %.",
	"Increases Physical Damage against enemies of every race/size/class by %.",
	
	"Increases Magical Damage against monsters of ^FF0000<Race/Size/Class>^000000 race/size/class by %.",
	"Increases Magical Damage against monsters of every race/size/class by %.",
	"Increases Magical Damage against monsters of ^<Element>^000000 element by %.",
	"Increases Magical Damage against enemies of every race/size/class by %.",
	
	"Increases Damage against monsters of ^FF0000<Race/Size/Class>^000000 race/size/class by %.",
	"Increases Damage against monsters of every race/size/class by %.",
	"Increases Damage against monsters of ^<Element>^000000 element by %.",
	"Increases Damage against monsters in Memorial Dungeon's ^0033CC<Instance Name>^000000 by 15%.",
	
	"Decreases damage taken from monsters of ^FF000<Race/Size/Class>^000000 race/size/class by %.",
	"Decreases damage taken from monsters of every race/size/class by %.",
	"Decreases damage taken from monsters of ^<Element>^000000 element by %.",
	"Decreases damage taken from ranged physical attacks by 20%.",
	
	"Increases experience gained from defeating ^FF0000<Race>^000000 race monsters by %.",
	"Increases experience gained from defeating ^<Element>^000000 elemental monsters by %.",
	"Increases experience gained by 100% and item drop chance by 50%.",
	
	"Ignores physical and magical defense of every race, except ^FF0000Players^000000, by %.",
	
	- Consumable Items:
	^0033CC = Specific Recovery Item
	^990099Recovery Items^000000
	"^0000CCEffect:^000000", > Used at buff/heal items
	
	"<STAT> +1 multiplied with total skill level of ^0033CC<Class>^000000's exclusive/related skills:",
	"^009900<Skill List> and <Last Skill>^000000",
	
	- Skill Codings:
	"For each Level of ^009900<Skill>^000000:",
	"Increases damage of ^009900<Skill>^000000 by %.",
	"Enables the use of ^0000FF<Skill>^000000.",
	"Enables the use of Level X ^0000FF<Skill>^000000.",
	"Enables the use of ^0000FF<Skill>^000000 at the same level as the ^0000FFRefine Level^000000.",
	"When ^009900<Skill>^000000 is used:",
	"When ^009900<Skill>^000000 is mastered:",
	"When Level X ^009900<Skill>^000000 is learned:",
	"Gain following effects when Level X ^009900<Skill>^000000 is learned:",
	"When ^0033CC<Base Class>^000000 classes uses ^009900<Skill List>^000000 or ^009900<Last Skill>^000000:",
	
	"Skill casting cannot be interrupted.",
	"Nullifies Gemstone Requirement of certain skills.",
	"Nullifies Weapon Size Penalty.",
	
	"Increases damage of ^009900<Skill>^000000 by %."
	
	"Decreases ^009900<Skill>^000000 skill cooldown by seconds.",
	"Decreases ^009900<Skill>^000000 skill cooldown by second.",
	"Decreases ^009900<Skill>^000000 skill cooldown by %.",
	
	"Decreases SP Consumption by .",
	"Decreases SP Consumption of ^009900<Skill>^000000 by .",
	
	"Decreases After Skill Delay by  %.",
	"Decreases After Skill Delay of ^009900<Skill>^000000 by %.",
	
	"Decreases Variable Casting Time by %.",
	"Decreases Variable Casting Time of ^009900<Skill>^000000 by %.",
	
	"Decreases Fixed Casting Time by %.",
	"Decreases Fixed Casting Time of ^009900<Skill>^000000 by %.",
	
	"For the highest Level of either ^009900<Skill>^000000, ^009900<Skill>^000000 or ^009900<Skill>^000000,",
	"increase damage dealt with ^009900<Skill>^000000 by % per skill Level.",
	
	"Physical attacks have a certain chance to auto cast Level X ^009900<Skill>^000000. (If you learned a higher Level, it will auto cast that Level instead.)",

	- Equipment Combination:
	"When equipped with ^990099<Equipment>^000000:",
	"When equipped with 2 types of ^990099<Class> Shadow^000000, ^990099<Class> Shadow^000000 or ^990099<Class> Shadow^000000 Equipment:",
	"When equipped by ^0033CC<Base Class>^000000 classes:",
	"When equipped by ^0033CC<Certain Class>^000000:",
	"When equipped as ^990099Accessory Right^000000:", -> Accessory (1)
	"When equipped as ^990099Accessory Left^000000:", -> Accessory (2)
	"If ^990099Weapon^000000 type is a ^990099Two-Handed Sword, Two-Handed Spear, Two-Handed Staff, Two-Handed Axe, Katar, Bow, Huuma Shuriken^000000 or any ^990099Firearm^000000 class weapon:",
	
	"^663399Indestructible in battle^000000",
	
	- Compounding/Enchantment:
	"When compounded on ^990099<Equipment>^000000:",
	"When enchanted with ^990099<Equipment>^000000:",
	"When ^990099Pet ^000000 is active:",
	
	- Weapon/Armor Level:
	"When ^990099Armor Level^000000 of compounded equipment is ^0000FF<X>^000000:",
	"When ^990099Weapon Level^000000 of compounded equipment is ^0000FF<X>^000000:",
	
	- Refine:
	"^000088Cannot be refined normally.^000000",
	
	"^0000FFFor each Refine Level^000000:",
	"^0000FFFor each Refine Level^000000 of ^990099<Equipment>^000000:",
	"^0000FFFor each Refine Level^000000 equal or above ^0000FF+9^000000 of ^990099<Equipment>^000000 and ^990099<Equipment>^000000:",
	"^0000FFFor each Refine Level^000000 equal or above ^0000FF+6^000000:",
	"^0000FFFor each Refine Level^000000 above ^0000FF+6^000000:",
	"^0000FFFor each 2 Refine Levels^000000 of equipped ^990099<Equipment Type>^000000:",
	"^0000FFFor each 2 Refine Levels^000000:",
	"^0000FFRefine Level +7^000000:",
	"^0000FFUp to max +5 Refine Level^000000:",
	"^0000FFRefine Level^000000 of equipped ^990099<Equipment Type>^000000 is ^0000FF+7 or higher^000000:",
	"^0000FFRefine Level^000000 of ^990099<Equipment>^000000 is ^0000FF+7 or higher^000000:",
	
	> Refine Combinations:
	"^0000FFTotal Refine Level^000000 of ^990099<Equipment>^000000, ^990099<Equipment>^000000 and ^990099<Equipment>^000000 is ^0000FF+27 or higher^000000:",
	"^0000FFTotal Refine Level of entire set^000000 is at least ^0000FF+14^000000:",
	"^0000FFFor each Refine Level^000000 of ^0000FFentire set^000000:",
	"^0000FFFor each 5 Refine Levels^000000 of ^0000FFentire set^000000:",
	
	- Player died:
	"If you are incapacitated, the mercenary will disappear.",
	"If you are incapacitated or hit by the Dispell skill, the item effect will disappear.",
	"If you are incapacitated, the item effect will disappear.",
	"^000088When player's character KO'd, the buff effect will wear off.^000000",
	
	"Warning - After using it, unless you choose the destination in 1 minute it will be useless",
	
	- Rental Items:
	"^000088Rental Item^000000",
	"^ff0000This item is not refundable.^000000",
	"^ff0000If you open this item, it is not refundable anymore.^000000",
	"^ff0000This item cannot be traded with other accounts.^000000",
	"^ff0000This item cannot be traded or moved to storage.^000000",
	
	"^ff0000This item can only be sold to NPCs and moved to storage.^000000",
	"^ff0000This item can only be sold to NPCs.",
	"^ff0000This item will not be used in future events.^000000",
	
Equipment Info Layout:
			"_______________________",
			"^0000CCType:^000000 ",
			"^0000CCAttack:^000000 ",
			"^0000CCDefense:^000000 ", - Removed for Accessories/Costumes
			"^0000CCPosition:^000000 ",
			- Accessory Positions:
			> kRO:
			  - ¾×¼¼¼­¸®(¿ÞÂÊ) = Accessory Left
			  - ¾×¼¼¼­¸®(¿À¸¥ÂÊ) = Accessory Right
			> jRO:
			  - ƒAƒNƒZƒTƒŠ[(1) = Accessory Left
			  - ƒAƒNƒZƒTƒŠ[(2) = Accessory Right
			"^0000CCElement:<Element Color Code> ", > Look at the beginning of this file
			"^0000CCWeight:^000000 ",
			"^0000CCArmor Level:^000000 ",
			"^0000CCWeapon Level:^000000 ",
			"^0000CCRefineable:^000000 No", > Only used when the item is NOT refinable
			"^0000CCEnchantable:^000000 Yes",
			"_______________________",
			"^0000CCRequirement:^000000",
			"Base Level X",
			"<Job Classes>"
	
Shadow Thump Box:
	"If you combine x of any of the following Shadow Equipments which are refined to +5 or higher, you can obtain <Reward>.",
	"If you combine x of any of the following Shadow Equipments which are refined to +7 or higher, you can obtain <Reward>.",
	"<List>",
	"_______________________",
	"^ff0000The Refine Level of the materials does not affect the result.^000000",

Boxes:
	"[Required Materials]",
	"[Obtainable Items]",
	"[Selectable Items]",
	"[Target Items]",
	
	
WoE/PvP:
	"*Effects in WoE TE area",
	"Increases physical damage against ^FF0000Players^000000 by 40%.",
	"Increases magical damage against ^FF0000Players^000000 by 40%.",
	"Random chance to inflict ^663399Bleeding^000000 status when dealing physical damage.",
	"Random chance to inflict ^663399Bleeding^000000 status when dealing magical damage.",
	"Decreases damage taken from ^FF0000Players^000000 by 10%.",
	
	"Decreases the target's SP by 10% on each physical attack. (This effect does not work with skills.)",
	"Has a chance to reflect damage back to the enemy as well as casting ^009900Magic Mirror^000000.",
	"Physical attacks have a certain chance to increase ATK by 200 for 3 seconds.",

Exchange NPC Locations:
	"<NAVI>[Designer Heidam]<INFO>mal_in01,20,124,0,100,0,0</INFO></NAVI> can exchange it with Costume Enchant Stone Box <X>.",
		
	"X can be obtained from",
	"<NAVI>[Cat Salesman Nyarom]<INFO>itemmall,41,50,0,100,0,0</INFO></NAVI>,",
	"by using Silvervine Cat Fruit or Zeny.",
	
	"<NAVI>[Richard]<INFO>malangdo,220,160,0,101,0</INFO></NAVI>",
	"<NAVI>[Jeeky]<INFO>itemmall,31,70,0,100,0,0</INFO></NAVI>.",
	"<NAVI>[Centro]<INFO>prontera,166,300,0,100,0,0</INFO></NAVI>",
	"<NAVI>[Yves]<INFO>malangdo,152,136,0,100,0,0</INFO></NAVI>",
	"<NAVI>[RS26-1]<INFO>sp_cor,98,136,0,100,0,0</INFO></NAVI>",
	
	"<NAVI>[Lace La Zard]<INFO>mal_in01,20,107,0,100,0,0</INFO></NAVI>",
	"<NAVI>[Aver De Dosh]<INFO>mal_in01,23,113,0,100,0,0</INFO></NAVI>",
	"<NAVI>[Gregio Grumani]<INFO>mal_in01,24,121,0,100,0,0</INFO></NAVI>",
	"<NAVI>[Nyan Time]<INFO>malangdo,208,163,0,100,0,0</INFO></NAVI>]",
	"<NAVI>[Nyan Time]<INFO>moc_para01,26,174,0,100,0,0</INFO></NAVI>]",
	"<NAVI>[Prontera Family Relations Guide]<INFO>prt_in,285,171,0,100,0,0</INFO></NAVI>",
	"<NAVI>[Lasagna Independent Helper]<INFO>lasagna,100,200,0,100,0,0</INFO></NAVI>",
	"<NAVI>[Beginner's Weapon Manager]<INFO>prontera,157,191,0,100,0,0</INFO></NAVI>",
	"Please visit <NAVI>[Gratin Gracias]<INFO>prontera,88,332,0,100,0,0</INFO></NAVI> with this.",
	"Take it to <NAVI>[Equipment Support Manager]<INFO>prontera,157,279,0,100,0,0</INFO></NAVI>.",
	"Take it to <NAVI>[Centro]<INFO>prontera,148,282,0,100,0,0</INFO></NAVI> and exchange it for one of the items below:",
	"Go to <NAVI>[Special Equipment Researcher]<INFO>rgsr_in,136,171,0,100,0,0</INFO></NAVI> to upgrade your helmet.",
	"Enchanter: <NAVI>[Jumping Enchant Specialist]<INFO>prontera,151,187,0,100,0,0</INFO></NAVI>^000000.",
	
	"^32CD32This item can't receive additional enchantment from Piercing Brosnan.^000000",
	
Shadow Equipment:
	> Armor: 
	"A suit of armor worn on top of normal armor for additional defense. Needs a complete set to have bonus effect.",
	
	> Weapon: 
	"A pair of gloves that can draw the wearer's potential ability.",
	
	> Pendant: 
	"A sacred necklace which is believed to protect its wearer. It also draws the wearer's potential abilities.",
	
	> Earring: 
	"A sacred earring which is believed to protect its wearer. It also draws the wearer's potential abilities.",
	
	> Shield: 
	"A small shield worn on the arm for additional defense. Needs a complete set to have bonus effect.",
	
	> Shoes: 
	"A pair of shoes worn on top of normal shoes for additional defense. Needs a complete set to have bonus effect.",

Unidentified Item Display Names when certain Resource Name is given:
	¸®º» = Ribbon
	¸Ó¸®¶ì = Hairband
	Ä¸ / ÇÞ = Hat
	±Û·¡½º = Glasses
	¸¶½ºÅ© = Mask
	Çï¸§ = Helmet
	°¡µå = Shield
	½´Áî = Shoes
	ÈÄµå = Garment
	Å¬¸³ = Accessory
	¹Ù½ºÅ¸µå¼Òµå = Sword
	ÄÚÆ°¼ÅÃ÷ = Clothing

Enchant Stones:
	Item Display Names:
	Upper
	Mid
	Lower
	Garment
	Dual

	Descriptions:
	"A stone that awakens the potential of <Class>.",
	"Gives the following effects when compounded on a slot of an Costume Upper Headgear.",
	"Gives the following effects when compounded on a slot of an Costume Middle Headgear.",
	"Gives the following effects when compounded on a slot of an Costume Lower Headgear.",
	"Gives the following effects when compounded on a slot of an Costume Garment.",

Grade Options:
	"If ^990099<Weapon>^000000's Grade is ^CC3D3DC^000000 or higher:",
	"If the ^990099<Equipment>^000000's Grade is ^CC3D3DC^000000 or higher:",
	"If enchanted ^990099Armor^000000's Grade is ^CC3D3DD^000000:",
	"If enchanted ^990099Equipment^000000's Grade is ^CC3D3DD^000000 or higher:",
	"<Bonus> for each Grade of the enchanted Weapon."
	"Depending on the Grade of the enchanted ^990099<Equipment>^000000:",
	
	"^CC3D3D[Bonus by Grade]^000000",
	"^CC3D3D[Bonus by <Equipment> Grade]^000000",
	"^CC3D3D[Bonus by Equipment's Grade]^000000",
	"[Grade D]: Effect",

	Refine Level:
	<Effect> per ^0000FF2 Refine Levels^000000
	
	Stats:
	<Effect> per ^0000FF15^000000 base ^CC6600INT^000000

Equipped Effect:
	"^006400Since it is an equipped effect, it still will be displayed even when the effect (/effect) is turned off.^000000",
	
	"^006400This item is equipped with special effects:",
	"- When the effect (/effect) is switched, the display does not change immediately, so it is necessary to re-equip the item after entering the command.",
	"- When using a disappearing skill such as \"Hiding\", the effect will not be visible to other players.",
	"- Even when equipped with an adopted character, the same effect as a normal character will be displayed.^000000",
	
	"^000088The graphic is reflected on the character.^000000",
	
jRO Egg Description:
			"A magical egg that pops out outfits when opened.",
			"_______________________",
			"Any of the following costume equipment will appear at random.^0000FF",
			"- Costume ",
			"- Costume ",
			"- Costume ",
			"- Costume ",
			"- Costume ",
			"- Costume ",
			"- Costume ",
			"- Costume ",
			"- Costume ",
			"- Costume ^000000",
			"_______________________",
			"^0000CCWeight:^000000 1"
```
## ItemReformSystem
```
	- InformationString:
	<B>Á¶ÇÕ °á°ú Á¤º¸ ¾È³»</B>
	> <B>Combination Result</B>
	
	Á¦·Ãµµ :
	> Refine Level:
	
	·£´ý ¿É¼Ç Á¤º¸ :
	·£´ý¿É¼Ç :
	> Random Options:
	
	Ä«µå ¹× ÀÎÃ¦Æ® Á¤º¸ :
	> Cards:
	
	µî±Þ Á¤º¸ :
	> Grade Rating:
	
	Á¾ºÎ¿© = types granted
	
	ÀÌÀüµÊ = Transfered
	À¯ÁöµÊ = Transfered
	Á¦°ÅµÊ = Removed
	Á¦°Å = Removed
	ÃÊ±âÈ­ = Reset
	»èÁ¦µÊ = Deleted
```
## EnchantList
```	
	- SetCaution:
	±âº» ¼º°øÈ®·ü > Success Chance:
	ÀÎÃ¦Æ® ¼º°øÈ®·ü > Success Chance:
	ÀÎÃ¦Æ® ÃÊ±âÈ­ È®·ü: > Reset Chance:
	ÃÊ±âÈ­ È®·ü > Reset Chance:
	 ½ÇÆÐ½Ã ÆÄ±«¾ÈµÊ > , will not be destroyed on failure 
	 ÀÎÃ¦Æ® ÃÊ±âÈ­ °¡´É > Enchantments can be reset
	 ÀÎÃ¦Æ® ÃÊ±âÈ­ ºÒ°¡ > Enchantments cannot be reset
```
## SkillDescript
```
    ^0000FF = Skill Names + Status (Hiding,...)/Elementals/Machines/Creatures
    ^990099 = Item Names + Skill Requirements (Spirit Spheres, Mounts,...)
    ^00A100 = Race/Class/Size
	
    "Max Level:
 
    "^CC3399Requirement: Divine Protection 5^000000",
     with Job ID before:
    "4^CC3399Requirement: Heal 2^000000",
	
    "Skill Form: ^6666CCPassive^000000",
    "Skill Form: ^3F0099Active^000000",
    "Skill Form: ^3F0099Active (Toggle)^000000"
	
    "Type: ^339900Supportive^000000",
    "Type: ^339900Recovery^000000",
    "Type: ^339900Designation^000000",
    "Type: ^339900Crafting^000000",
    "Type: ^339900FAW^000000",
    "Type: ^339900Summon^000000",
	
    "Type: ^000099Trap (Hidden)^000000",
    "Type: ^000099Trap (Visible)^000000",
    "Type: ^000099Trap^000000",
    "Type: ^000099Planting^000000",
    "Type: ^000099Song Skill^000000",
    "Type: ^000099Dance Skill^000000",
    "Type: ^000099Ensemble Skill^000000",
    "Type: ^000099Stance Skill^000000",
	
    "Type: ^FF0000Debuff^000000",
    "Type: ^FF0000Physical Melee^000000",
    "Type: ^FF0000Physical Ranged^000000",
    "Type: ^FF0000Special^000000",
    "Type: ^FF0000Special Physical^000000",
    "Type: ^FF0000Special Physical Ranged^000000",
	
    "Type: ^FF0000Magical^000000",
    "Type: ^FF0000Magical, AoE^000000",
    "Type: ^FF0000Magical, Debuff^000000",
	
    "Range: ^7777779x9 AoE^000000",
    "Range: ^777777^000000",
	
    "Target: ^6666CCHomunculus^000000",
    "Target: ^6666CCSummon^000000",
    "Target: ^6666CCElemental^000000", = Sorcerer Summon
    "Target: ^6666CCCaster^000000",
    "Target: ^6666CCGround^000000",
    "Target: ^6666CC1 Character^000000",
    "Target: ^6666CCEnemies on the screen^000000",
    "Target: ^6666CCEnemies around the caster^000000",
    "Target: ^6666CCAround the caster^000000",
    "Target: ^6666CCCaster's View Range^000000",
    "Target: ^6666CCCaster and Party Members^000000",
    "Target: ^6666CC1 Party Member^000000",
	
	"Description: ^777777 ^000000",

	- Damage Modifications:
	"Inflicts more damage when under the ^0000FFAxe Stomp^777777 effect.",
	
	"Damage is additionaly increased according",
	"to the caster's ^CC6600Base Level^777777 and ^CC6600POW^777777.",
	
	"Damage additionally increases according",
	"to the caster's ^CC6600Base Level^777777 and ^CC6600STR^777777,",
	"can inflict half of the total ^CC6600Critical Damage^777777",
	"based on the caster's ^CC6600Critical^777777 chance.",
	
	"Damage additionally increases according",
	"to the caster's ^CC6600Base Level^777777 and ^CC6600POW^777777,",
	"can inflict ^CC6600Critical Damage^777777",
	"based on the caster's ^CC6600Critical^777777 chance.",
	
	"Damage additionally increases according",
	"to the caster's ^CC6600Base Level^777777 and ^CC6600POW^777777,",
	"can inflict half of the total ^CC6600Critical Damage^777777",
	"based on half of the caster's ^CC6600Critical^777777 chance.^000000",
	
	- 4th Classes:
	"Skill Form: ^3F0099Active(AP)^000000",
	"AP Recovery: ^0054FF^000000",
	"AP Cost: ^FF0000^000000",
	
	- Level Descriptions with modifiers:
	> Race if it doesn't fit in one line:
	"[Lv 1]: ^777777ATK 950%,",
	"^0033CCDemi-Human/Angel^777777: ATK 1400%^000000",
	
	> Race if it fit one line:
	"[Lv 1]: ^777777ATK 1750%/2000% (^0033CCPlant/Insect^000000)^000000",
	
	> Skill/Effects:
	"[Lv 1]: ^777777MATK 320+(Mastery Lv x5)%",
	"^0000FFHoly Shield^777777: MATK 450+(Mastery Lv x10)%",
```
If you have suggestions regarding the colorization, you can do that.