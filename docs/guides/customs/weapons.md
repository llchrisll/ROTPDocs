!!! note
	This will only explain the client side.
___
Adding a custom Weapon can be done with it's own animation files or without.  
But you only have deal with the `weapontable.lub` if you have those. 
!!! info "Weapons without Animations"
	This is very simple, you just take existing values from the existing weapon type list:
	??? example "Weapon Type List"
		```lua
			WEAPONTYPE_NONE = 0,
			WEAPONTYPE_SHORTSWORD = 1,
			WEAPONTYPE_SWORD = 2,
			WEAPONTYPE_TWOHANDSWORD = 3,
			WEAPONTYPE_SPEAR = 4,
			WEAPONTYPE_TWOHANDSPEAR = 5,
			WEAPONTYPE_AXE = 6,
			WEAPONTYPE_TWOHANDAXE = 7,
			WEAPONTYPE_MACE = 8,
			WEAPONTYPE_TWOHANDMACE = 9,
			WEAPONTYPE_ROD = 10,
			WEAPONTYPE_BOW = 11,
			WEAPONTYPE_KNUKLE = 12,
			WEAPONTYPE_INSTRUMENT = 13,
			WEAPONTYPE_WHIP = 14,
			WEAPONTYPE_BOOK = 15,
			WEAPONTYPE_CATARRH = 16,
			WPCLASS_GUN_HANDGUN = 17,
			WPCLASS_GUN_RIFLE = 18,
			WPCLASS_GUN_GATLING = 19,
			WPCLASS_GUN_SHOTGUN = 20,
			WPCLASS_GUN_GRANADE = 21,
			WPCLASS_SYURIKEN = 22,
			WPCLASS_TWOHANDROD = 23,
			WEAPONTYPE_SHORTSWORD_SHORTSWORD = 25,
			WEAPONTYPE_SWORD_SWORD = 26,
			WEAPONTYPE_AXE_AXE = 27,
			WEAPONTYPE_SHORTSWORD_SWORD = 28,
			WEAPONTYPE_SHORTSWORD_AXE = 29,
			WEAPONTYPE_SWORD_AXE = 30,
			WEAPONTYPE_Main_Gauche = 31,
			WEAPONTYPE_Stiletto = 32,
			WEAPONTYPE_Gladius = 33,
			WEAPONTYPE_Zeny_Knife = 34,
			WEAPONTYPE_Poison_Knife = 35,
			WEAPONTYPE_Princess_Knife = 36,
			WEAPONTYPE_Sasimi = 37,
			WEAPONTYPE_Lacma = 38,
			WEAPONTYPE_Tsurugi = 39,
			WEAPONTYPE_Ring_Pommel_Saber = 40,
			WEAPONTYPE_Haedonggum = 41,
			WEAPONTYPE_Saber = 42,
			WEAPONTYPE_Jewel_Sword = 43,
			WEAPONTYPE_Gaia_Sword = 44,
			WEAPONTYPE_Twin_Edge_B = 45,
			WEAPONTYPE_Twin_Edge_R = 46,
			WEAPONTYPE_Priest_Sword = 47,
			WEAPONTYPE_Katana = 48,
			WEAPONTYPE_Bastard_Sword = 49,
			WEAPONTYPE_Broad_Sword = 50,
			WEAPONTYPE_Violet_Fear = 51,
			WEAPONTYPE_Lance = 52,
			WEAPONTYPE_Partizan = 53,
			WEAPONTYPE_Trident = 54,
			WEAPONTYPE_Halberd = 55,
			WEAPONTYPE_Crescent_Scythe = 56,
			WEAPONTYPE_Zephyrus = 57,
			WEAPONTYPE_Hammer = 58,
			WEAPONTYPE_Buster = 59,
			WEAPONTYPE_Brood_Axe = 60,
			WEAPONTYPE_Right_Epsilon = 61,
			WEAPONTYPE_Mace = 62,
			WEAPONTYPE_Sword_Mace = 63,
			WEAPONTYPE_Chain = 64,
			WEAPONTYPE_Stunner = 65,
			WEAPONTYPE_Golden_Mace = 66,
			WEAPONTYPE_Iron_Driver = 67,
			WEAPONTYPE_Spanner = 68,
			WEAPONTYPE_Arc_Wand = 69,
			WEAPONTYPE_Mighty_Staff = 70,
			WEAPONTYPE_Blessed_Wand = 71,
			WEAPONTYPE_Bone_Wand = 72,
			WEAPONTYPE_CrossBow = 73,
			WEAPONTYPE_Arbalest = 74,
			WEAPONTYPE_Kakkung = 75,
			WEAPONTYPE_Hunter_Bow = 76,
			WEAPONTYPE_Bow_Of_Rudra = 77,
			WEAPONTYPE_Waghnakh = 78,
			WEAPONTYPE_Knuckle_Duster = 79,
			WEAPONTYPE_Hora = 80,
			WEAPONTYPE_Fist = 81,
			WEAPONTYPE_Claw = 82,
			WEAPONTYPE_Finger = 83,
			WEAPONTYPE_Kaiser_Knuckle = 84,
			WEAPONTYPE_Berserk = 85,
			WEAPONTYPE_Rante = 86,
			WEAPONTYPE_Tail = 87,
			WEAPONTYPE_Whip = 88,
			WEAPONTYPE_Bible = 89,
			WEAPONTYPE_Book_Of_Billows = 90,
			WEAPONTYPE_Book_Of_Mother_Earth = 91,
			WEAPONTYPE_Book_Of_Blazing_Sun = 92,
			WEAPONTYPE_Book_Of_Gust_Of_Wind = 93,
			WEAPONTYPE_Book_Of_The_Apocalypse = 94,
			WEAPONTYPE_Girls_Diary = 95,
			WEAPONTYPE_Staff_Of_Soul = 96,
			WEAPONTYPE_Wizardy_Staff = 97,
			WEAPONTYPE_Spoon = 98,
			WEAPONTYPE_FOXTAIL_BROWN = 99,
			WEAPONTYPE_FOXTAIL_GREEN = 100,
			WEAPONTYPE_CandyCaneRod = 101,
			WEAPONTYPE_FOXTAIL_METAL = 102
		```
		Or look up similar weapons in either iteminfo.lub or server's item_equip.yml.
			
!!! info "Weapons with Animations"
	1. Open the `data\luafiles514\lua files\datainfo\weapontable.lub`
	2. `Weapon_IDs`  
      `WEAPONTYPE_CustomWeapon = 103`
	3. `WeaponNameTable`  
      `[Weapon_IDs.WEAPONTYPE_CustomWeapon] = "_customweapon"`
	4. `Expansion_Weapon_IDs`  
      `[Weapon_IDs.WEAPONTYPE_CustomWeapon] = Weapon_IDs.WEAPONTYPE_`  
       Assign a weapon type based on the `Weapon_IDs` table but only up to `WEAPONTYPE_SWORD_AXE = 30` are valid
	5. `BowTypeList`  
	`Weapon_IDs.WEAPONTYPE_CustomWeapon`
	This is only used for bows obviously.  
	6. Sprite Files  
	`data\sprite\ÀÎ°£Á·` = Main Folder for Weapon Sprites  
	Each class has it's own folder and requires 2 files (.act.spr) of your custom weapon per gender.  
	While you can duplicate them and just rename it for a different class and gender, but the animations won't match the class' movement at all.  
	The file name depends on your `WeaponNameTable` entry above.  
	See [Folder List](https://github.com/llchrisll/ROResourceCollection/blob/master/spritelist.md) for info.
	7. itemInfo.lua  
	Then you only have to assign the `ClassNum` to your custom weapon, which is the value of `WEAPONTYPE_CustomWeapon` you declared in `Weapon_IDs` table, like 103 as example.
	
	!!! note 
		Add your entries always after the last entry and to add a `,` after the previous one.
!!! info "Table Explanations"
	!!! info "`Weapon_IDs`"
		Defines weapon types and special weapons
		These values are used for the `ClassNum` argument in your `itemInfo.lub` entry, as well as your ViewID in your item db.
	!!! info "`WeaponNameTable`"
		Defines the file names
	!!! info "`Expansion_Weapon_IDs`"
		Assign the weapon to a weapon type
	!!! info "`WeaponHitWaveNameTable``"
		Defines which .wav file should be played for your custom weapon type
	!!! info "`BowTypeList`"
		Defines which weapons are considered Bows