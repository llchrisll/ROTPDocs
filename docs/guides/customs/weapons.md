
Note: This will only explain the client side.
___

Adding a custom Weapon can be done with it's own animation files or without.  
But you only have deal with the `weapontable.lub` if you have those.  
  
   1. Open the `data\luafiles514\lua files\datainfo\weapontable.lub`  
     (See explanation below)  
      Note: Add your entries always after the last entry and to add a `,` after the previous one.
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

##### Explanation
- Weapon_IDs = Table for each weapon type  
  These values are used for the `ClassNum` argument in your `itemInfo.lub` entry, as well as your ViewID in your item db.
- WeaponNameTable = Table for the file name
- Expansion_Weapon_IDs = Table to assign the weapon to a weapon type
- WeaponHitWaveNameTable = Table which .wav file should be played for your custom weapon type
- BowTypeList = Table for Bows