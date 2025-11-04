This page contains information about the EquipmentProperties.lub I collected and tested myself to some degree.  
For advanced usage (like refine level) you need some basic lua knowledge as well, similar to NPC scripting in any emulator.

**Note: There might be mistakes and misunderstandings in there, if you have more information about it, let me know.**
___
## File Layout
```
[<ItemID>] = {
	Type = "",
	Stat = {
      20,
      0,
      0,
      0,
      0,
      0,
      0,
      0,
      0,
      0,
      1,
      0,
      0,
      0,
      0,
      0,
      0
	},
	OnStartEquip = function()
		<functions from below>
	end,
	OnStartPretendEquip = true, -- I don't have a clue what this is for
    Combiitem = { <ComboID>,... } -- Contains unique ID's representing an Combo, there is a separate table later one to declare the items and item effect. IDs start with 2000000000
},


Combiitem = {
	[<ComboID>] = {
		Item = { <ItemID>,<ItemID>,... }, -- contains the items which trigger the combo
		OnStartEquip = function()
			<functions>
		end
	},
}

SkillGroup = {
  [<SkillGroup>] = {<SkillID>},
}
```
### Types and Stat table
There are 5 `Type` entries:
 * `ammo`
 * `armor`
 * `Mweapon`
 * `Rweapon`
 * `card`

The `Stat` table contains only numeric values and using less values than noted, will end up in an error.  
So fill them with a 0.
#### Ammo
As far as I saw, it won't get displayed in the UI.  
Must contain 2 values.

	Type = "ammo",
	Stat = { 
		Element, Attack Damage
	}
#### Equipment
Must contain 17 values.

	Type = "armor",
	Stat = {
		DEF,
		STR,
		INT,
		VIT,
		DEX,
		AGI,
		LUK,
		MaxHP,
		MaxSP,
		<Armor Level>,
		MDEF,
		POW,
		SPL,
		STA,
		WIS,
		CON,
		CTR
	}
#### Melee Weapons
Must contain 17 values.

	Type = "Mweapon",
	Stat = {
		<Element>,
		<Weapon Type>,
		ATK,
		MATK,
		STR,
		INT,
		VIT,
		DEX,
		AGI,
		LUK,
		<Weapon Level>,
		POW,
		SPL,
		STA,
		WIS,
		CON,
		CTR
	}
#### Ranged Weapons
Must contain 15 values.

	Type = "Rweapon",
	Stat = {
		<Weapon Type>,
		ATK,
		STR,
		INT,
		VIT,
		DEX,
		AGI,
		LUK,
		<Weapon Level>,
		POW,
		SPL,
		STA,
		WIS,
		CON,
		CTR
	}
	
#### Cards
Does not require a `Stat` table, only the `OnStartEquip` function

	Type = "card",
	OnStartEquip = function()

### OnStartEquip = function()
This function handles all the effects outside of the `Stat` table, like refine effects and other parameters.  
After this you will find some notes about `<Element>`,`<Race` and so on.  
```
OnStartEquip = function()
	<functions>
end
```
#### Simple calls
| Function | Effect |
| ---- | ---- |
| AddExtParam(0, `<Parameter>`, `<Value>`) | Increases `<Parameter>` by `<Value>`</br>(% or flat amount based on `<Parameter>`) |
| SubExtParam(0, `<Parameter>`, `<Value>`) | Decreases `<Parameter>` by `<Value>`</br>(% or flat amount based on `<Parameter>`) |
| AddAttrTolerace(`<Element>`, `<Value>`) | Decreases damage taken from `<Element>` attacks by `<Value>`% |
| SubAttrTolerace(`<Element>`, `<Value>`) | Decreases resistance against `<Element>` attacks by `<Value>`% |
| addattrtolerace(`<Element>`, `<Value>`, 1) | Decreases damage taken from melee attacks of `<Element>` by `<Value>`% |
| subattrtolerace(`<Element>`, `<Value>`, 1) | Increases damage taken from melee attacks of `<Element>` by `<Value>`% |
| AddRaceTolerace(`<Race>`, `<Value>`) | Increases damage against `<Race>` enemies by `<Value>`% |
| SubRaceTolerace(`<Race>`, `<Value>`) | Increases damage taken from `<Race>` enemies by `<Value>`% |
| AddDamage_SKID(1, `<Skill ID>`, `<Value>`) | Increases damage of `<Skill>` by `<Value>`% |
| SubDamage_SKID | not setup |
| AddDamage_CRI(1, `<Value>`) | Increases Critical Damage by `<Value>`% |
| SubDamage_CRI(1, `<Value>`) | Decreases Critical Damage by `<Value>`% (not working) |
| AddCRIPercent_Race(`<Race>`, `<Value>`) | Increases Critical against `<Race>` enemies by `<Value>`/10% |
| SubCRIPercent_Race(`<Race>`, `<Value>`) | Decreases Critical against `<Race>` enemies by `<Value>`/10% |
| AddDamage_Size(1, `<Size>`, `<Value>`) | Increases physical damage against `<Size>` enemies by `<Value>`% |
| AddMDamage_Size(1, `<Size>`, `<Value>`) | Increases magical damage against `<Size>` enemies by `<Value>`% |
| AddDamage_Size(0, `<Size>`, `<Value>`) | Increases physical damage taken from `<Size>` by `<Value>`% |
| AddMDamage_Size(0, `<Size>`, `<Value>` | Increases magical damage taken from `<Size>` by `<Value>`% |
| SubDamage_Size(0, `<Size>`, `<Value>` | Decreases physical damage taken from `<Size>` enemies by `<Value>`% |
| SubMDamage_Size(0, `<Size>`, `<Value>` | Decreases magical damage taken from `<Size>` enemies by `<Value>`% |
| AddDamage_Property(1, `<Size>`, `<Value>` | Increases physical damage against `<Element>` enemies by `<Value>`% |
| AddMDamage_Property(1, `<Size>`, `<Value>` | Increases magical damage against `<Element>` enemies by `<Value>`% |
| AddDamage_Property(0, `<Size>`,`<Value>`) | Increases physical damage taken from `<Element>` by `<Value>`% |
| AddMDamage_Property(0, `<Size>`, `<Value>`) | Increases magical damage taken from `<Element>` by `<Value>`% |
| SubDamage_Property(0, `<Element>`, `<Value>`) | Decreases physical damage taken from `<Element>` enemies by `<Value>`% |
| SubMDamage_Property(0, `<Element>`, `<Value>`) | Decreases magical damage taken from `<Element>` enemies by `<Value>`% |
| SubDamage_Property(1, `<Element>`, `<Value>`) | Decreases physical damage against `<Element>` enemies by `<Value>`% |
| SubMDamage_Property(1, `<Element>`, `<Value>`) | Decreases magical damage against `<Element>` enemies by `<Value>`% |
| AddMdamage_Class(`<Class>`, `<Value>`) | Increases physical and magical damage against `<Class>` monsters by `<Value>`% |
| SubMdamage_Class(`<Class>`, `<Value>`) | Decreases physical and magical damage against `<Class>` monsters by `<Value>`% |
| AddMdamage_Race(`<Race>`, `<Value>`) | Increases magical damage against `<Race>` monsters by `<Value>`% |
| SubMdamage_Race(`<Race>`, `<Value>`) | Decreases magical damage against `<Race>` monsters by `<Value>`% |
| AddSkillMDamage(`<Element>`, `<Value>`) | Increases magical damage with `<Element>` by `<Value>`% |
| SubSkillMDamage(`<Element>`, `<Value>`) | Decreases magical damage with `<Element>` by `<Value>`% |
| AddMeleeAttackDamage(1, `<Value>`) | Increases melee attack damage by `<Value>`% |
| AddMeleeAttackDamage(0, `<Value>`) | Increases damage taken from melee attacks by `<Value>`% |
| SubMeleeAttackDamage(1, `<Value>`) | Decreases melee attack damage by `<Value>`% |
| AddRangeAttackDamage(1, `<Value>`) | Increases ranged attack damage by `<Value>`% |
| AddRangeAttackDamage(0, `<Value>`) | Increases damage taken from ranged attacks by `<Value>`% |
| SubRangeAttackDamage(1, `<Value>`) | Decreases ranged attack damage by `<Value>`% |
| AddBowAttackDamage(1, `<Value>`) | Increases damage with bow class weapons by `<Value>`% |
| SubBowAttackDamage(1, `<Value>`) | Decreases damage with bow class weapons by `<Value>`% |
| AddSpellDelay(`<Value>`) | Increases after skill delay by `<Value>`% |
| SubSpellDelay(`<Value>`) | Decreases after skill delay by `<Value>`% |
| AddSkillDelay(`<Skill ID>`, `<Value>`) | Increases skill cooldown of Skill by `<Value>` milliseconds |
| SubSkillDelay(`<Skill ID>`, `<Value>`) | Decreases skill cooldown of Skill by `<Value>` milliseconds |
| AddHealValue(`<Value>`) | Increases healing effectivness by `<Value>`% |
| SubHealValue(`<Value>`) | Decreases healing effectivness by `<Value>`% |
| AddHealModifyPercent(`<Value>`) | Increases recovery amount of restorative items by `<Value>`% |
| SubHealModifyPercent(`<Value>`) | Decreases recovery amount of restorative items by `<Value>`% |
| AddSpellCastTime(`<Value>`) | Increases Variable Casting Time by `<Value>`% |
| SubSpellCastTime(`<Value>`) | Decreases Variable Casting Time by `<Value>`% |
| ClassAddDamage(`<Class>`, 1, `<Value>`) | Increases physical damage against enemies of `<Class>` by `<Value>`% |
| ClassAddDamage(`<Class>`, 0, `<Value>`) | Increases physical damage taken from `<Class>` enemies by `<Value>`% |
| ClassSubDamage(`<Class>`, 0, `<Value>`) | Decreases damage taken from `<Class>` by `<Value>`% |
| ClassSubDamage(`<Class>`, 1, `<Value>`) | Decreases physical damage against `<Class>` enemies by `<Value>`% |
| RaceAddDamage(`<Race>`, `<Value>`) | Increases physical damage against enemies of `<Race>` by `<Value>`% |
| RaceSubDamage(`<Race>`, `<Value>`) | Decreases physical damage against enemies of `<Race>` by `<Value>`% |
| RaceAddDamageSelf(`<Race>`, `<Value>`) | Increases physical damage taken from `<Race>` enemies by `<Value>`% |
| RaceSubDamageSelf(`<Race>`, `<Value>`) | Decreases physical damage taken from `<Race>` enemies by `<Value>`% |
| SetIgnoreDefRace_Percent(`<Race>`, `<Value>`) | ignores `<Value>`% def of `<Race>` enemies |
| SetIgnoreMdefRace_Percent(`<Race>`, `<Value>`) | ignores `<Value>`% mdef of `<Race>` enemies |
| SetIgnoreDefClass_Percent(`<Class>`, `<Value>`) | ignores `<Value>`% def of `<Class>` enemies |
| SetIgnoreMdefClass(`<Class>`, `<Value>`) | ignores % mdef of `<Class>` enemies |
| SetIgnoreDEFRace(`<Race>`) | ignores 100% def of `<Race>` enemies |
| SetIgnoreMdefRace(`<Race>`, `<Value>`) | ignores `<Value>`% mdef of `<Race>` enemies |
| AddIgnore_RES_RacePercent(`<Race>`, `<Value>`) | ignores `<Value>`% RES of `<Race>` enemies |
| SubIgnore_RES_RacePercent(`<Race>`, `<Value>`) | Decreases the `<Value>`% of ignored RES of `<Race>` enemies |
| AddIgnore_MRES_RacePercent(`<Race>`, `<Value>`) | ignores `<Value>`% MRES of `<Race>` enemies |
| SubIgnore_MRES_RacePercent(`<Race>`, `<Value>`) | Decreases the `<Value>`% of ignored MRES of `<Race>` enemies |
| AddSpecificSpellCastTime(`<Skill ID>`, `<Value>`) | Decreases Variable Casting Time of Skill by `<Value>`% (does not overlapp with similar effects) |
| SubSpecificSpellCastTime(`<Skill ID>`, `<Value>`) | Decreases Variable Casting Time of Skill by `<Value>`% |
| AddSFCTEquipPermill | not setup |
| SubSFCTEquipPermill(`<Item ID>`, `<Value>`, `<Skill Group>`) | Decreases Fixed Casting Time by `<Value>`%, 3rd is optional and can be 0 (not acculmative with effects of other items) |
| SubSFCTEquipAmount(`<Item ID>`, `<Value>`, `<Skill Group>`) | Decreases Fixed Casting Time by `<Value>` milliseconds, 3rd is optional and can be 0 (not acculmative with effects of other items) |
| EnableSkill(`<Skill ID>`, `<Skill Level>`) | Gives `<Skill ID>` with Level `<Skill Level>` |
| DisableSkill | not setup |
| AddEXPPercent_KillRace(`<Race>`, `<Value>`) | Increases experience gained for Race monsters by `<Value>`% |
| SubEXPPercent_KillRace(`<Race>`, `<Value>`) | Decreases experience gained for Race monsters by `<Value>`% (will not go negative) |
| AddHPdrain(`<Chance>`, `<Value>`) | Increases the chance to absorb HP of `<Value>`% inflicted damage by `<Chance>`% |
| SubHPdrain(`<Chance>`, `<Value>`) | Decreases the chance to absorb HP of `<Value>`% inflicted damage by `<Chance>`% (chance will not go negative, 2nd value is optional but will be added to existing values) |
| AddSPdrain(`<Chance>`, `<Value>`) | Increases the chance to absorb SP of `<Value>`% inflicted damage by `<Chance>`%
| SubSPdrain(`<Chance>`, `<Value>`) | Decreases the chance to absorb SP of `<Value>`% inflicted damage by `<Chance>`% (chance will not go negative, 2nd value is optional but will be added to existing values)) |
| AddGuideAttack(`<Value>`) | Increases Perfect Hit chance by `<Value>` |
| SubGuideAttack(`<Value>`) | Decreases Perfect Hit chance by `<Value>` (will not go negative) |
| AddSPconsumption(`<Value>`) | Increases SP Consumption by `<Value>`% |
| SubSPconsumption(`<Value>`) | Decreases SP Consumption by `<Value>`% |
| addspconsumption(`<Value>`, `<Skill ID>`) | Increases SP Consumption of `<Skill ID>` by `<Value>`% |
| subspconsumption(`<Value>`, `<Skill ID>`) | Decreases SP Consumption of `<Skill ID>` by `<Value>`% |
| AddSkillSP(`<Skill ID>`, `<Value>`) | Increases SP Consumption of `<Skill ID>` by `<Value>` |
| SubSkillSP(`<Skill ID>`, `<Value>`) | Decreases SP Consumption of `<Skill ID>` by `<Value>` |
| AddDamage_HIT(1,`<Value>`) | Increases Hit Physical Damage (Normal Physical Damage) by `<Value>`% |
| SubDamage_HIT(1,`<Value>`) | Decreases received Hit Physical Damage (Normal Physical Damage) by `<Value>`% |
| AddReflectMagic(`<Value>`) | Increases the chance to reflect magic damage by `<Value>`% |
| SubReflectMagic(`<Value>`) | Decreases the chance to reflect magic damage by `<Value>`% (will not go negative) |
| AddReflectTolerace(`<Value>`) | Increases damage taken from reflected damage by `<Value>`% |
| SubReflectTolerace(`<Value>`) | Decreases damage taken from reflected damage by `<Value>`% |
| AddMeleeAttackReflect(`<Value>`) | Increases the chance to reflect physical damage by `<Value>`% |
| SubMeleeAttackReflect(`<Value>`) | Decreases the chance to reflect physical damage by `<Value>`% (will not go negative) |
| AddReceiveItem_Equip(`<Value>`) | Increases item drop rate by `<Value>`% |
| SubReceiveItem_Equip(`<Value>`) | Decreases item drop rate by `<Value>`% (will not go negative) |
| AddNeverknockback(1) | Prevents Knockback effect (1 = true) |
| SubNeverknockback(1) | not setup |
| NoDispell(1) | Skill casting can't be interrupted (1 = true) |
| PerfectDamage(1) | Nullifies weapon size penalty (1 = true) |
| SplashAttack(1) | Enables splash damage (1 = true) |
| Clairvoyance(1) | Enables to see hidden enemeis (1 = true) |
| Magicimmune(1) | Nullifies Magical Damage/Effects (1 = true) |
| NoJamstone(1) | Removes gemstone requirements |
| NoMadogearfuel(1) | Removes Magic Gear Fuel consumption |
| Reincarnation(1) | Recovers 100% hp/sp on resurrection |
| SetInvestigate() | Enchants weapon with "Investigate" skill effect (Thanatos Card/Ice Pick)! |
| IndestructibleArmor | not setup |
| IndestructibleWeapon | not setup |
| Condition(14, 9999, 100) | Increased Movement Speed |
| Condition(13, 9999, 100) | Endure Effect |

#### Advanced function calls
These functions are useable in combination with others, like Refine Level based effects.

| Function | Effect |
| ---- | ---- |
| GetEquipArmorLv(`<Equip Slot>`) | Retreives Armor Level (mostly used with GetLocation()) |
| GetEquipWeaponLv(`<Equip Slot>`) | Retreives Weapon Level; `<Equip Slot>` is normally 4 |
| GetItemIDLocation(`<Equip Slot>`) | Retreives item id on `<Equip Slot>` |
| GetWeaponClass(`<Equip Slot>`) | Retreives Weapon Type; `<Equip Slot>` is normally 4 |
| GetPetRelationship() | pet loyal level (0/2~4) |
| IsPremiumPcCafe() | VIP status (seen 2/10/65 as values so far) |
| SetEquipTempValue(`<Slot>`, `<Value>`) | `<Slot>` is a placeholder term, I saw up to 5 so far; it's used to temporary save values to the equipment |
| GetRefineLevel(`<Equip Slot>`) | Retreives Refine Level of `<Equip Slot>` |
| GetEquipGradeLevel(`<Equip Slot>`) | Retreives Grade Level of `<Equip Slot>` |
| GetLocation() | Retreives `<Equip Slot>` of the item is in |
| GetSkillLevel(`<Skill ID>`) | Retreives Skill Level |
| GetPureJob() | Base Job |
| GetMapName | not tested yet |
| CheckJobGroup2 | not tested yet |
| GetCategoryJob | not tested yet |
| get(`<Value>`) | Values:</br>7 = SP</br>8 = MaxSP</br>11 = Base Level</br>19 = Job ID</br>32 = STR</br>33 = AGI</br>34 = VIT</br>35 = INT</br>36 = DEX</br>37 = LUK</br>55 = Job Level</br>255 = POW</br>256 = STA</br>257 = WIS</br>258 = SPL</br>259 = CON</br>260 = CRT | get(11) |

##### Notes
| Argument | Values (If it's too much, I just refer to a source.) |
| ---- | ---- |
| `<Weapon Type>` | refers to weapontable.lub ID, can't be 0 |
| `<Parameter>` | refers to enumvar.lub's second value of each entry,</br>like `VAR_MAXHPAMOUNT = { 1, 109 },` > `109` |
| `<Element>` | 0 = Nothing</br>1 = Water</br>2 = Ground</br>3 = Fire</br>4 = Wind</br>5 = Poison</br>6 = Saint</br>7 = Darkness</br>8 = Telekinesis</br>9 = Undead</br>10 = All |
| `<Race>` | 0 = Nothing</br>1 = Undead</br>2 = Animal</br>3 = Plant</br>4 = Insect</br>5 = Fish</br>6 = Demon</br>7 = Human</br>8 = Angel</br>9 = Dragon</br>10 = HumanPlayer</br>11 = DoramPlayer</br>9999 = All |
| `<Class>` | 0 = Normal</br>1 = Boss</br>2 = Guardian |
| `<Size>` | 0 = Small</br>1 = Medium</br>2 = Large |
| `<Skill Group>` | refers to EquipmentProperties.lub "SkillGroup" table,</br> `[X]` is the skill group itself, can be 0 for all |
| `<Equip Slot>` | 1 = Lower Headgear</br>2 = Armor</br>3 = Shield</br>4 = Weapon</br>5 = Garment</br>6 = Shoes</br>7 = Right Accessory</br>8 = Left Accessory</br>10 = Upper Headgear</br>11 = Middle Headgear</br>30 = Shadow Armor</br>31 = Shadow Weapon</br>32 = Shadow Shield</br>33 = Shadow Shoes</br>34 = Shadow Right Accessory</br>35 = Shadow Left Accessory |

## Basic Lua
To make use of the more advanced function calls, you need to understand lua to some degree.  
[Lua 5.3 Reference Manual](https://www.lua.org/manual/5.3/manual.html)

Example from ID `2169` - Kalasag:

	itemInfo Entry:
		"^0000FFFor each 3 Refine Levels^000000:",  
		"Decreases damage taken from ^FF0000Boss^000000 class by 1%.",
	
```
OnStartEquip = function()
    local temp, temp2 = 0, 0
    temp = GetRefineLevel(3)
    temp2 = math.floor(temp / 3)
    ClassSubDamage(1, 0, temp2)
end

```
Explanation:

* `local` is used to declare a variable, `temp` and `temp2` in this case, as "local",  
which means the variable is only accessable in the `OnStartEquip` function, so it's not accidently used/overwritten by other calls.  
So `temp = 0` and `local temp = 0` are two different instances.
* `GetRefineLevel(3)` retreives the Refine Level of the Shield, like noted above
* `math.floor` returns the largest integral value smaller than or equal to x  
 (to round down/up, no decimals allowed (based on my understanding))
* ClassSubDamage(1, 0, `temp2`): 1 = Class (Boss), and `temp2` being the calucated value

