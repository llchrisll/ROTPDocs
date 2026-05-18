!!! note
	This will only explain the client side.
___

The Enchant UI was introduced with 2021-10-28 and first used with Episode 18 content.  
In 2023-09-20 it was updated to allow duplicate entries and new texture files,  
which moves the Random and Perfect Enchant into tabs in the first tab.

## File Dependencies
!!! info "Dependencies"
    * `ItemDBNameTbl.lub` is required for string values and the respective item id  
    To be safe, please avoid using `'` and similar in these, like `Bear's_Power` (ID 4875) > `Bears_Power`
    * `Enchant/EnchantList.lub` contains the actual Enchant details and has restrictions to follow.  
    If you use my edited [EnchantList_f.lub (2021-10-28)](https://github.com/llchrisll/ROenglishRE/blob/master/Translation/Compatibility/2021-10-28/data/luafiles514/lua%20files/Enchant/EnchantList_f.lub) | [EnchantList_f.lub (2023-09-20)](https://github.com/llchrisll/ROenglishRE/blob/master/Translation/Compatibility/2023-09-20/data/luafiles514/lua%20files/Enchant/EnchantList_f.lub), the errors are translated there.

## File Format
!!! info "General Info"
    * `ID` must match the server-side ID declared in item_enchant.yml
	* `Slot` refers to the card slots start
    * `"Item_String"` refers to the entry in ItemDBNameTbl.lub and must be in quotes
    * Refine refers the refine level
    * Grade refers to grade as a value:  
        * None = 0 (only accepted in SetEnchant)
	    * D = 1
	    * C = 2
	    * B = 3
	    * A = 4
     * Zeny refers to the actual value not payment type
     * Chance is to multiplied by 1000 (Example: 100% > 100*1000 = 100000)  
     * Values in [ ] are optional, mostly for item requirements  
     I didn't test the limit, but `MAX_MATERIAL_NUM` is called in `EnchantList_f.lub` (I guess hardcoded).  
	 But calling it manually it gave me `8`.
	 
!!! info "Table[ID] = CreateEnchantInfo()"
	This is a funtion call and is required for each entry.
	
	!!! info "`Table[ID]:`"
		The `:` attaches key words like `AddTargetItem` to the table and these are considered like global values for this entry.
   
	!!! info annotate "SetSlotOrder (1)"
		 Defines the order(2) in which enchantments will be placed, starts at the last slot by default.  
		 I don't know what happens if you change that...  
		   
	1. SetSlotOrder(0) | SetSlotOrder(3, 2, 1)
	2. * 0 = Disabled : SetSlotOrder(0) | 1 = 2nd Card Slot | 2 = 3rd Card Slot | 3 = 4th Card Slot

	!!! info annotate "AddTargetItem (1)"
		 Adds an item to this enchant table.
	1. AddTargetItem("Item_String")

	!!! info annotate "SetCondition (1)"
		Defines minimum refine and grade levels, can both be 0 and must both be given.
	1. SetCondition(Refine, Grade)

	!!! info annotate "ApproveRandomOption(1)"
		Based on my estimation, this declares if items with Random Options are allowed, untested tho.
	1. ApproveRandomOption(true)

	!!! info annotate "SetReset(1)"
		Defines if enchantments can be reset.
	1. SetReset(true/false, Chance, Zeny, [{"Item_String", Amount}])

	!!! info annotate "SetCaution(1)"
		 Should be self-explantory, but provides a description, `\n` should be used for new lines.  
		 Also keep it 2 lines if you don't want a ugly scroll bar.
	1. SetCaution("Info Text")

!!! info annotate "Table[].Slot[]:(1)"
    Now it attaches the table `Slot[]` to `Table[]` which also adds separate keywords to it.
	!!! info annotate "SetRequire(2)"
		TAX amount

	!!! info annotate "SetSuccessRate(3)"
		Official default is 100000 = 100%.

	!!! info annotate "SetGradeBonus(4)"
		Defines a bonus per Grade (1~4), Chance is 0 by default since `SetSuccessRate` is always 100% officially.

	!!! info annotate "SetEnchant(5)"
		Adds an random enchant to a certain Grade (0~4), 0 refers to No Grade.
		!!! warning 
			The max calucated chance of all items in the same slot must be exactly `100000`. 	
		
	!!! info annotate "AddUpgradeEnchant(6)"
		Upgrade an enchantment

	!!! info annotate "AddPerfectEnchant(7)"
		Adds an perfect enchantment (no fail chances), but mostly more resources required.
	
	!!! abstract "Changes with 2023-09-20"
		The changes mostly adds new versions of `AddUpgradeEnchant`,  
		when upgrades were 100%, but not anymore.  
		Exception are Perfect Enchants, so basically `AddUpgradeEnchant` > `AddPerfectUpgradeEnchant`.
		!!! info "`Table[ID]:`"
			!!! info annotate "AddTargetItem_Duplicate (8)"
				Allows duplicate entries in the global enchant table, if needed.

		!!! info "`Table[ID].Slot[Slot]`:"
			!!! info annotate "SetRandomUpgradeRequire (9)"
				Defines the price to upgrade an "random" enchantment
				 
			!!! info annotate "AddRandomUpgradeEnchant (10)"
				Defines the chance to the upgrade

			!!! info annotate "AddPerfectUpgradeEnchant (11)"
				Same as AddUpgradeEnchant but for Perfect Enchants only
				
	
1. Table[ID].Slot[Slot]:
2. SetRequire(Zeny)
3. SetSuccessRate(100000)
4. SetGradeBonus(Grade, Chance)
5. SetEnchant(Grade, "Item_String", Chance)
6. AddUpgradeEnchant("Item_String", "Item_String", Zeny[, { "Item_String", Amount}])
7. AddPerfectEnchant("Item_String", Zeny[, {"Item_String", Amount}])
8. 	AddTargetItem_Duplicate("Item_String")
9.	SetRandomUpgradeRequire("Item_String", Zeny[, {"Item_String", Amount}])
10. AddRandomUpgradeEnchant("Item_String", "Item_String", Chance)   
11. AddPerfectUpgradeEnchant("Item_String", "Item_String", Zeny[, {"Item_String", Amount}])  

## Example - Diabolus Set
!!! info "Credits"
	[Original by khyle650](https://rathena.org/board/topic/132764-the-new-enchant-system-cannot-be-openedused-correctly/#comment-412806)

??? example "ItemDBNameTbl.lub"

    ```lua
		Diabolus_Armor = 2375,
		Diabolus_Boots = 2433,
		Diabolus_Helmet = 5808,
		Diabolus_Manteau = 2537,
		Diabolus_Ring = 2729,
		Diabolus_Robe = 2374
    ```
??? example "EnchantList.lub"

    ```lua
	Table[68] = CreateEnchantInfo()
	Table[68]:SetSlotOrder(3, 2, 1)
	Table[68]:AddTargetItem("Diabolus_Armor")
	Table[68]:AddTargetItem("Diabolus_Boots")
	Table[68]:AddTargetItem("Diabolus_Helmet")
	Table[68]:AddTargetItem("Diabolus_Manteau")
	Table[68]:AddTargetItem("Diabolus_Ring")
	Table[68]:AddTargetItem("Diabolus_Robe")
	Table[68]:SetCondition(0, 0)
	Table[68]:ApproveRandomOption(true)
	Table[68]:SetReset(true, 100000, 3000000)
	Table[68]:SetCaution("Diabolus Set Enchantment\nSuccess Chance: 100%\nReset Chance: 100%, will not be destroyed on failure")
	Table[68].Slot[3]:SetRequire(100000)
	Table[68].Slot[3]:SetSuccessRate(100000)
	Table[68].Slot[3]:SetGradeBonus(1, 0)
	Table[68].Slot[3]:SetGradeBonus(2, 0)
	Table[68].Slot[3]:SetGradeBonus(3, 0)
	Table[68].Slot[3]:SetGradeBonus(4, 0)
	Table[68].Slot[3]:SetEnchant(0, "Èû1", 12460)
	Table[68].Slot[3]:SetEnchant(0, "ÀÎÆ®1", 12470)
	Table[68].Slot[3]:SetEnchant(0, "¾îÁú1", 12470)
	Table[68].Slot[3]:SetEnchant(0, "¹ÙÅ»1", 12470)
	Table[68].Slot[3]:SetEnchant(0, "·°1", 12460)
	Table[68].Slot[3]:SetEnchant(0, "µ¦1", 12470)
	Table[68].Slot[3]:SetEnchant(0, "Èû2", 3500)
	Table[68].Slot[3]:SetEnchant(0, "ÀÎÆ®2", 3500)
	Table[68].Slot[3]:SetEnchant(0, "¾îÁú2", 3500)
	Table[68].Slot[3]:SetEnchant(0, "¹ÙÅ»2", 3500)
	Table[68].Slot[3]:SetEnchant(0, "·°2", 3500)
	Table[68].Slot[3]:SetEnchant(0, "µ¦2", 3500)
	Table[68].Slot[3]:SetEnchant(0, "Èû3", 700)
	Table[68].Slot[3]:SetEnchant(0, "ÀÎÆ®3", 700)
	Table[68].Slot[3]:SetEnchant(0, "¾îÁú3", 700)
	Table[68].Slot[3]:SetEnchant(0, "¹ÙÅ»3", 700)
	Table[68].Slot[3]:SetEnchant(0, "·°3", 700)
	Table[68].Slot[3]:SetEnchant(0, "µ¦3", 700)
	Table[68].Slot[3]:AddPerfectEnchant("Èû1", 500000)
	Table[68].Slot[3]:AddPerfectEnchant("ÀÎÆ®1", 500000)
	Table[68].Slot[3]:AddPerfectEnchant("¾îÁú1", 500000)
	Table[68].Slot[3]:AddPerfectEnchant("¹ÙÅ»1", 500000)
	Table[68].Slot[3]:AddPerfectEnchant("·°1", 500000)
	Table[68].Slot[3]:AddPerfectEnchant("µ¦1", 500000)
	Table[68].Slot[3]:AddPerfectEnchant("Èû2", 1000000)
	Table[68].Slot[3]:AddPerfectEnchant("ÀÎÆ®2", 1000000)
	Table[68].Slot[3]:AddPerfectEnchant("¾îÁú2", 1000000)
	Table[68].Slot[3]:AddPerfectEnchant("¹ÙÅ»2", 1000000)
	Table[68].Slot[3]:AddPerfectEnchant("·°2", 1000000)
	Table[68].Slot[3]:AddPerfectEnchant("µ¦2", 1000000)
	Table[68].Slot[3]:AddPerfectEnchant("Èû3", 3000000)
	Table[68].Slot[3]:AddPerfectEnchant("ÀÎÆ®3", 3000000)
	Table[68].Slot[3]:AddPerfectEnchant("¾îÁú3", 3000000)
	Table[68].Slot[3]:AddPerfectEnchant("¹ÙÅ»3", 3000000)
	Table[68].Slot[3]:AddPerfectEnchant("·°3", 3000000)
	Table[68].Slot[3]:AddPerfectEnchant("µ¦3", 3000000)
	Table[68].Slot[3]:AddUpgradeEnchant("Èû1", "Èû2", 500000)
	Table[68].Slot[3]:AddUpgradeEnchant("Èû2", "Èû3", 1000000)
	Table[68].Slot[3]:AddUpgradeEnchant("ÀÎÆ®1", "ÀÎÆ®2", 500000)
	Table[68].Slot[3]:AddUpgradeEnchant("ÀÎÆ®2", "ÀÎÆ®3", 1000000)
	Table[68].Slot[3]:AddUpgradeEnchant("¾îÁú1", "¾îÁú2", 500000)
	Table[68].Slot[3]:AddUpgradeEnchant("¾îÁú2", "¾îÁú3", 1000000)
	Table[68].Slot[3]:AddUpgradeEnchant("¹ÙÅ»1", "¹ÙÅ»2", 500000)
	Table[68].Slot[3]:AddUpgradeEnchant("¹ÙÅ»2", "¹ÙÅ»3", 1000000)
	Table[68].Slot[3]:AddUpgradeEnchant("·°1", "·°2", 500000)
	Table[68].Slot[3]:AddUpgradeEnchant("·°2", "·°3", 1000000)
	Table[68].Slot[3]:AddUpgradeEnchant("µ¦1", "µ¦2", 500000)
	Table[68].Slot[3]:AddUpgradeEnchant("µ¦2", "µ¦3", 1000000)
	Table[68].Slot[2]:SetRequire(200000)
	Table[68].Slot[2]:SetSuccessRate(100000)
	Table[68].Slot[2]:SetGradeBonus(1, 0)
	Table[68].Slot[2]:SetGradeBonus(2, 0)
	Table[68].Slot[2]:SetGradeBonus(3, 0)
	Table[68].Slot[2]:SetGradeBonus(4, 0)
	Table[68].Slot[2]:SetEnchant(0, "Èû1", 12460)
	Table[68].Slot[2]:SetEnchant(0, "ÀÎÆ®1", 12470)
	Table[68].Slot[2]:SetEnchant(0, "¾îÁú1", 12470)
	Table[68].Slot[2]:SetEnchant(0, "¹ÙÅ»1", 12470)
	Table[68].Slot[2]:SetEnchant(0, "·°1", 12460)
	Table[68].Slot[2]:SetEnchant(0, "µ¦1", 12470)
	Table[68].Slot[2]:SetEnchant(0, "Èû2", 3500)
	Table[68].Slot[2]:SetEnchant(0, "ÀÎÆ®2", 3500)
	Table[68].Slot[2]:SetEnchant(0, "¾îÁú2", 3500)
	Table[68].Slot[2]:SetEnchant(0, "¹ÙÅ»2", 3500)
	Table[68].Slot[2]:SetEnchant(0, "·°2", 3500)
	Table[68].Slot[2]:SetEnchant(0, "µ¦2", 3500)
	Table[68].Slot[2]:SetEnchant(0, "Èû3", 700)
	Table[68].Slot[2]:SetEnchant(0, "ÀÎÆ®3", 700)
	Table[68].Slot[2]:SetEnchant(0, "¾îÁú3", 700)
	Table[68].Slot[2]:SetEnchant(0, "¹ÙÅ»3", 700)
	Table[68].Slot[2]:SetEnchant(0, "·°3", 700)
	Table[68].Slot[2]:SetEnchant(0, "µ¦3", 700)
	Table[68].Slot[2]:AddPerfectEnchant("Èû1", 500000)
	Table[68].Slot[2]:AddPerfectEnchant("ÀÎÆ®1", 500000)
	Table[68].Slot[2]:AddPerfectEnchant("¾îÁú1", 500000)
	Table[68].Slot[2]:AddPerfectEnchant("¹ÙÅ»1", 500000)
	Table[68].Slot[2]:AddPerfectEnchant("·°1", 500000)
	Table[68].Slot[2]:AddPerfectEnchant("µ¦1", 500000)
	Table[68].Slot[2]:AddPerfectEnchant("Èû2", 1000000)
	Table[68].Slot[2]:AddPerfectEnchant("ÀÎÆ®2", 1000000)
	Table[68].Slot[2]:AddPerfectEnchant("¾îÁú2", 1000000)
	Table[68].Slot[2]:AddPerfectEnchant("¹ÙÅ»2", 1000000)
	Table[68].Slot[2]:AddPerfectEnchant("·°2", 1000000)
	Table[68].Slot[2]:AddPerfectEnchant("µ¦2", 1000000)
	Table[68].Slot[2]:AddPerfectEnchant("Èû3", 3000000)
	Table[68].Slot[2]:AddPerfectEnchant("ÀÎÆ®3", 3000000)
	Table[68].Slot[2]:AddPerfectEnchant("¾îÁú3", 3000000)
	Table[68].Slot[2]:AddPerfectEnchant("¹ÙÅ»3", 3000000)
	Table[68].Slot[2]:AddPerfectEnchant("·°3", 3000000)
	Table[68].Slot[2]:AddPerfectEnchant("µ¦3", 3000000)
	Table[68].Slot[2]:AddUpgradeEnchant("Èû1", "Èû2", 500000)
	Table[68].Slot[2]:AddUpgradeEnchant("Èû2", "Èû3", 1000000)
	Table[68].Slot[2]:AddUpgradeEnchant("ÀÎÆ®1", "ÀÎÆ®2", 500000)
	Table[68].Slot[2]:AddUpgradeEnchant("ÀÎÆ®2", "ÀÎÆ®3", 1000000)
	Table[68].Slot[2]:AddUpgradeEnchant("¾îÁú1", "¾îÁú2", 500000)
	Table[68].Slot[2]:AddUpgradeEnchant("¾îÁú2", "¾îÁú3", 1000000)
	Table[68].Slot[2]:AddUpgradeEnchant("¹ÙÅ»1", "¹ÙÅ»2", 500000)
	Table[68].Slot[2]:AddUpgradeEnchant("¹ÙÅ»2", "¹ÙÅ»3", 1000000)
	Table[68].Slot[2]:AddUpgradeEnchant("·°1", "·°2", 500000)
	Table[68].Slot[2]:AddUpgradeEnchant("·°2", "·°3", 1000000)
	Table[68].Slot[2]:AddUpgradeEnchant("µ¦1", "µ¦2", 500000)
	Table[68].Slot[2]:AddUpgradeEnchant("µ¦2", "µ¦3", 1000000)
	Table[68].Slot[1]:SetRequire(300000)
	Table[68].Slot[1]:SetSuccessRate(100000)
	Table[68].Slot[1]:SetGradeBonus(1, 0)
	Table[68].Slot[1]:SetGradeBonus(2, 0)
	Table[68].Slot[1]:SetGradeBonus(3, 0)
	Table[68].Slot[1]:SetGradeBonus(4, 0)
	Table[68].Slot[1]:SetEnchant(0, "Èû1", 12460)
	Table[68].Slot[1]:SetEnchant(0, "ÀÎÆ®1", 12470)
	Table[68].Slot[1]:SetEnchant(0, "¾îÁú1", 12470)
	Table[68].Slot[1]:SetEnchant(0, "¹ÙÅ»1", 12470)
	Table[68].Slot[1]:SetEnchant(0, "·°1", 12460)
	Table[68].Slot[1]:SetEnchant(0, "µ¦1", 12470)
	Table[68].Slot[1]:SetEnchant(0, "Èû2", 3500)
	Table[68].Slot[1]:SetEnchant(0, "ÀÎÆ®2", 3500)
	Table[68].Slot[1]:SetEnchant(0, "¾îÁú2", 3500)
	Table[68].Slot[1]:SetEnchant(0, "¹ÙÅ»2", 3500)
	Table[68].Slot[1]:SetEnchant(0, "·°2", 3500)
	Table[68].Slot[1]:SetEnchant(0, "µ¦2", 3500)
	Table[68].Slot[1]:SetEnchant(0, "Èû3", 700)
	Table[68].Slot[1]:SetEnchant(0, "ÀÎÆ®3", 700)
	Table[68].Slot[1]:SetEnchant(0, "¾îÁú3", 700)
	Table[68].Slot[1]:SetEnchant(0, "¹ÙÅ»3", 700)
	Table[68].Slot[1]:SetEnchant(0, "·°3", 700)
	Table[68].Slot[1]:SetEnchant(0, "µ¦3", 700)
	Table[68].Slot[1]:AddPerfectEnchant("Èû1", 500000)
	Table[68].Slot[1]:AddPerfectEnchant("ÀÎÆ®1", 500000)
	Table[68].Slot[1]:AddPerfectEnchant("¾îÁú1", 500000)
	Table[68].Slot[1]:AddPerfectEnchant("¹ÙÅ»1", 500000)
	Table[68].Slot[1]:AddPerfectEnchant("·°1", 500000)
	Table[68].Slot[1]:AddPerfectEnchant("µ¦1", 500000)
	Table[68].Slot[1]:AddPerfectEnchant("Èû2", 1000000)
	Table[68].Slot[1]:AddPerfectEnchant("ÀÎÆ®2", 1000000)
	Table[68].Slot[1]:AddPerfectEnchant("¾îÁú2", 1000000)
	Table[68].Slot[1]:AddPerfectEnchant("¹ÙÅ»2", 1000000)
	Table[68].Slot[1]:AddPerfectEnchant("·°2", 1000000)
	Table[68].Slot[1]:AddPerfectEnchant("µ¦2", 1000000)
	Table[68].Slot[1]:AddPerfectEnchant("Èû3", 3000000)
	Table[68].Slot[1]:AddPerfectEnchant("ÀÎÆ®3", 3000000)
	Table[68].Slot[1]:AddPerfectEnchant("¾îÁú3", 3000000)
	Table[68].Slot[1]:AddPerfectEnchant("¹ÙÅ»3", 3000000)
	Table[68].Slot[1]:AddPerfectEnchant("·°3", 3000000)
	Table[68].Slot[1]:AddPerfectEnchant("µ¦3", 3000000)
	Table[68].Slot[1]:AddUpgradeEnchant("Èû1", "Èû2", 500000)
	Table[68].Slot[1]:AddUpgradeEnchant("Èû2", "Èû3", 1000000)
	Table[68].Slot[1]:AddUpgradeEnchant("ÀÎÆ®1", "ÀÎÆ®2", 500000)
	Table[68].Slot[1]:AddUpgradeEnchant("ÀÎÆ®2", "ÀÎÆ®3", 1000000)
	Table[68].Slot[1]:AddUpgradeEnchant("¾îÁú1", "¾îÁú2", 500000)
	Table[68].Slot[1]:AddUpgradeEnchant("¾îÁú2", "¾îÁú3", 1000000)
	Table[68].Slot[1]:AddUpgradeEnchant("¹ÙÅ»1", "¹ÙÅ»2", 500000)
	Table[68].Slot[1]:AddUpgradeEnchant("¹ÙÅ»2", "¹ÙÅ»3", 1000000)
	Table[68].Slot[1]:AddUpgradeEnchant("·°1", "·°2", 500000)
	Table[68].Slot[1]:AddUpgradeEnchant("·°2", "·°3", 1000000)
	Table[68].Slot[1]:AddUpgradeEnchant("µ¦1", "µ¦2", 500000)
	Table[68].Slot[1]:AddUpgradeEnchant("µ¦2", "µ¦3", 1000000)
	```
## Example - Temporal Boots[0]
??? example "ItemDBNameTbl.lub"
	```lua
		Temporal_STR_Boots = 22000,
		Temporal_INT_Boots = 22001,
		Temporal_AGI_Boots = 22002,
		Temporal_VIT_Boots = 22003,
		Temporal_DEX_Boots = 22004,
		Temporal_LUK_Boots = 22005,
		Modify_Str_Boots = 22107,
		Modify_Int_Boots = 22108,
		Modify_Agi_Boots = 22109,
		Modify_Vit_Boots = 22110,
		Modify_Dex_Boots = 22111,
		Modify_Luk_Boots = 22112,
		Fighting_Spirit4 = 4808,
		Fighting_Spirit5 = 4820,
		Fighting_Spirit6 = 4821,
		Fighting_Spirit7 = 4822,
		Expert_Archer1 = 4832,
		Expert_Archer2 = 4833,
		Expert_Archer3 = 4834,
		Expert_Archer4 = 4835,
		Spell2 = 4814,
		Spell3 = 4813,
		Spell4 = 4812,
		Spell5 = 4826,
		Vitality2 = 4741,
		Vitality3 = 4742,
		MHP1 = 4861,
		MHP2 = 4862,
		DelayafterAttack1Lv = 4869,
		DelayafterAttack2Lv = 4872,
		DelayafterAttack3Lv = 4873,
		DelayafterAttack4Lv = 4881,
		Luck3 = 4752,
		Luck4 = 4753,
		Luck5 = 4754,
		Luck6 = 4755,
		Bears_Power = 4875,
		Runaway_Magic = 4876,
		Speed_Of_Light = 4877,
		Muscle_Fool = 4878,
		Hawkeye = 4879,
		Lucky_Day = 4880,
		Coagulated_Spell = 6608
	```
??? example "EnchantList.lub"

    ```
	Table[164] = CreateEnchantInfo()
	Table[164]:SetSlotOrder(3, 2)
	Table[164]:AddTargetItem("Temporal_STR_Boots")
	Table[164]:AddTargetItem("Temporal_INT_Boots")
	Table[164]:AddTargetItem("Temporal_AGI_Boots")
	Table[164]:AddTargetItem("Temporal_VIT_Boots")
	Table[164]:AddTargetItem("Temporal_DEX_Boots")
	Table[164]:AddTargetItem("Temporal_LUK_Boots")
	Table[164]:AddTargetItem("Modify_Str_Boots")
	Table[164]:AddTargetItem("Modify_Int_Boots")
	Table[164]:AddTargetItem("Modify_Agi_Boots")
	Table[164]:AddTargetItem("Modify_Vit_Boots")
	Table[164]:AddTargetItem("Modify_Dex_Boots")
	Table[164]:AddTargetItem("Modify_Luk_Boots")
	Table[164]:SetCondition(0, 0)
	Table[164]:ApproveRandomOption(true)
	Table[164]:SetReset(false, 0, 0)
	Table[164]:SetCaution("Temporal Boots Enchantment\nSuccess Chance: 100% | Enchantment cannot be reset")
	Table[164].Slot[3]:AddPerfectEnchant("Fighting_Spirit4", 0, {"Coagulated_Spell", 1})
	Table[164].Slot[3]:AddUpgradeEnchant("Fighting_Spirit4", "Fighting_Spirit5", 0, {"Coagulated_Spell", 4})
	Table[164].Slot[3]:AddUpgradeEnchant("Fighting_Spirit5", "Fighting_Spirit6", 0, {"Coagulated_Spell", 15})
	Table[164].Slot[3]:AddUpgradeEnchant("Fighting_Spirit6", "Fighting_Spirit7", 0, {"Coagulated_Spell", 30})
	Table[164].Slot[3]:AddPerfectEnchant("Expert_Archer1", 0, {"Coagulated_Spell", 1})
	Table[164].Slot[3]:AddUpgradeEnchant("Expert_Archer1", "Expert_Archer2", 0, {"Coagulated_Spell", 4})
	Table[164].Slot[3]:AddUpgradeEnchant("Expert_Archer2", "Expert_Archer3", 0, {"Coagulated_Spell", 15})
	Table[164].Slot[3]:AddUpgradeEnchant("Expert_Archer3", "Expert_Archer4", 0, {"Coagulated_Spell", 30})
	Table[164].Slot[3]:AddPerfectEnchant("Spell2", 0, {"Coagulated_Spell", 1})
	Table[164].Slot[3]:AddUpgradeEnchant("Spell2", "Spell3", 0, {"Coagulated_Spell", 4})
	Table[164].Slot[3]:AddUpgradeEnchant("Spell3", "Spell4", 0, {"Coagulated_Spell", 15})
	Table[164].Slot[3]:AddUpgradeEnchant("Spell4", "Spell5", 0, {"Coagulated_Spell", 30})
	Table[164].Slot[3]:AddPerfectEnchant("Vitality2", 0, {"Coagulated_Spell", 1})
	Table[164].Slot[3]:AddUpgradeEnchant("Vitality2", "Vitality3", 0, {"Coagulated_Spell", 4})
	Table[164].Slot[3]:AddUpgradeEnchant("Vitality3", "MHP1", 0, {"Coagulated_Spell", 15})
	Table[164].Slot[3]:AddUpgradeEnchant("MHP1", "MHP2", 0, {"Coagulated_Spell", 30})
	Table[164].Slot[3]:AddPerfectEnchant("DelayafterAttack1Lv", 0, {"Coagulated_Spell", 1})
	Table[164].Slot[3]:AddUpgradeEnchant("DelayafterAttack1Lv", "DelayafterAttack2Lv", 0, {"Coagulated_Spell", 4})
	Table[164].Slot[3]:AddUpgradeEnchant("DelayafterAttack2Lv", "DelayafterAttack3Lv", 0, {"Coagulated_Spell", 15})
	Table[164].Slot[3]:AddUpgradeEnchant("DelayafterAttack3Lv", "DelayafterAttack4Lv", 0, {"Coagulated_Spell", 30})
	Table[164].Slot[3]:AddPerfectEnchant("Luck3", 0, {"Coagulated_Spell", 1})
	Table[164].Slot[3]:AddUpgradeEnchant("Luck3", "Luck4", 0, {"Coagulated_Spell", 4})
	Table[164].Slot[3]:AddUpgradeEnchant("Luck4", "Luck5", 0, {"Coagulated_Spell", 15})
	Table[164].Slot[3]:AddUpgradeEnchant("Luck5", "Luck6", 0, {"Coagulated_Spell", 30})
	Table[164].Slot[2]:SetRequire(0, {"Coagulated_Spell", 10})
	Table[164].Slot[2]:SetSuccessRate(100000)
	Table[164].Slot[2]:SetGradeBonus(1, 0)
	Table[164].Slot[2]:SetEnchant(0, "Bears_Power", 16667)
	Table[164].Slot[2]:SetEnchant(0, "Runaway_Magic", 16667)
	Table[164].Slot[2]:SetEnchant(0, "Speed_Of_Light", 16667)
	Table[164].Slot[2]:SetEnchant(0, "Muscle_Fool", 16667)
	Table[164].Slot[2]:SetEnchant(0, "Hawkeye", 16666)
	Table[164].Slot[2]:SetEnchant(0, "Lucky_Day", 16666)
	```