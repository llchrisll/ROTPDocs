[Original by khyle650](https://rathena.org/board/topic/132764-the-new-enchant-system-cannot-be-openedused-correctly/#comment-412806)  
You need to add an entry in `data\luafiles514\lua files\ItemDBNameTbl.lub` of your item  
and the enchant details in `data\luafiles514\lua files\Enchant\EnchantList.lub`.

### ItemDBNameTbl.lub Example
```
	F_Ein_Weapon_Hammer = 102124,
	Diabolus_Armor = 2375,
	Diabolus_Boots = 2433,
	Diabolus_Helmet = 5808,
	Diabolus_Manteau = 2537,
	Diabolus_Ring = 2729,
	Diabolus_Robe = 2374
```
### EnchantList.lub Example
```
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