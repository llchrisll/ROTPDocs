!!! abstract "Disclaimer"
	In most cases the original files only have to be overwritten, if not stated otherwise.  
	Remember, always make backups!
___
This is not something official but rather a QOL update, especially for those who wants to use the Nemo/WARP patch "Use icons from stateiconimginfo.lub".  
That patch resulted in ignoring hardcoded icons, therefore losing them all together as those are not mentioned in stateiconimginfo.lub at all.

## [Updated lub files](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/Stateiconimginfo%20Patch)
To make this work I added a new table in `stateiconimginfo.lub` > `StateIconImgList_HC = {` which lists all hardcoded icons.  
This table will be imported if the config below is on `true`:
```
---------------------------------------------------
-- Custom Setting to load re-import hardcoded entries when using "Use icons from stateiconimginfo.lub",
-- which disables hardcoded icons and only loads from this file.
-- This means these hardcoded ones are not shown anymore, which would be a lot of skill icons...
-- Valid values: true/false (yes/no)
ImportIcons = true
---------------------------------------------------
```

## Taekwon Skill Mild Wind (TK_SEVENWIND)
The next issue I encountered was the Mild Wind skill of Taekwon classes regarding the icons.  
Normally, they share the same `EFST_` like `EFST_PROPERTYFIRE` for all classes, but the client decided based on the job which icon to display.  
Therefore I had to create new custom entries in `efstids.lub`, `stateiconimginfo.lub` an `stateiconinfo.lub`.  
??? note "`efstids.lub`"
	```
	------ Custom Taekwon Mild Wind Entries ----
	EFST_PROPERTYFIRE_TK = 2000,
	EFST_PROPERTYWATER_TK = 2001,
	EFST_PROPERTYWIND_TK = 2002,
	EFST_PROPERTYGROUND_TK = 2003,
	EFST_PROPERTYHOLY_TK = 2004,
	------------------------------------------
	```
??? note "`stateiconimginfo.lub`"
	```
	-- StateIconList[EFST_IDs.EFST_PROPERTYFIRE_TK] = StateIconList[EFST_IDs.EFST_PROPERTYFIRE]
	StateIconList[EFST_IDs.EFST_PROPERTYFIRE_TK] = {
		haveTimeLimit = 1,
		posTimeLimitStr = 2,
		descript = {
			{ "Mild Wind [Fire]", COLOR_TITLE_BUFF },
			{ "%s", COLOR_TIME },
			{ "Enchant weapon with Fire element" },
			{ "Increases Fire elemental magic damage" }
		}
	}
	-- StateIconList[EFST_IDs.EFST_PROPERTYWATER_TK] = StateIconList[EFST_IDs.EFST_PROPERTYWATER]
	StateIconList[EFST_IDs.EFST_PROPERTYWATER_TK] = {
		haveTimeLimit = 1,
		posTimeLimitStr = 2,
		descript = {
			{ "Mild Wind [Water]", COLOR_TITLE_BUFF },
			{ "%s", COLOR_TIME },
			{ "Grants weapon with Water element" },
			{ "Increases Water elemental magic damage" }
		}
	}
	--StateIconList[EFST_IDs.EFST_PROPERTYWIND_TK] = StateIconList[EFST_IDs.EFST_PROPERTYWIND]
	StateIconList[EFST_IDs.EFST_PROPERTYWIND_TK] = {
		haveTimeLimit = 1,
		posTimeLimitStr = 2,
		descript = {
			{ "Mild Wind [Wind]", COLOR_TITLE_BUFF },
			{ "%s", COLOR_TIME },
			{ "Enchant weapon with Wind element" },
			{ "Increases Wind elemental magic damage" }
		}
	}
	-- StateIconList[EFST_IDs.EFST_PROPERTYGROUND_TK] = StateIconList[EFST_IDs.EFST_PROPERTYGROUND]
	StateIconList[EFST_IDs.EFST_PROPERTYGROUND_TK] = {
		haveTimeLimit = 1,
		posTimeLimitStr = 2,
		descript = {
			{ "Mild Wind [Earth]", COLOR_TITLE_BUFF },
			{ "%s", COLOR_TIME },
			{ "Enchant weapon with Earth element" },
			{ "Increases Earth elemental magic damage" }
		}
	}
	-- StateIconList[EFST_IDs.EFST_PROPERTYHOLY_TK] = StateIconList[EFST_IDs.EFST_ASPERSIO]
	StateIconList[EFST_IDs.EFST_PROPERTYHOLY_TK] = {
		haveTimeLimit = 1,
		posTimeLimitStr = 2,
		descript = {
			{ "Mild Wind [Holy]", COLOR_TITLE_BUFF },
			{ "%s", COLOR_TIME },
			{ "Grants weapon with Holy element" }
		}
	}
	```
??? note "`stateiconimginfo.lub`"
	```
	------ Custom Taekwon Mild Wind Entries ----
	[EFST_IDs.EFST_PROPERTYFIRE_TK] = "i_p_FIRE.tga",
	[EFST_IDs.EFST_PROPERTYWATER_TK] = "i_p_WATER.tga",
	[EFST_IDs.EFST_PROPERTYWIND_TK] = "i_p_WIND.tga",
	[EFST_IDs.EFST_PROPERTYGROUND_TK] = "i_p_EARTH.tga",
	[EFST_IDs.EFST_PROPERTYHOLY_TK] = "i_p_SAINT.tga",
	------------------------------------------
	```

### Patch File for rAthena
Of course the server also needed a update regarding that, so I made a [rAthena PR](https://github.com/rathena/rathena/pull/10054) too.  
The whole thing is controlled via a custom config called `buff_icons_tk` in `conf/battle/status.conf`.  

In case the PR is not accepted, [here](../../downloads/Stateicon.patch) a patch file to apply via Git.  
The ID's as well as the `EFST` names are adjustable as needed, just make sure to change server and client side.  

## Icon Description
Since I made custom descriptions, which mind not suit your taste, you can also redirect them to the normal version:  

Just uncomment this line:  
```
-- StateIconList[EFST_IDs.EFST_PROPERTYHOLY_TK] = StateIconList[EFST_IDs.EFST_ASPERSIO]
```
and comment-block the rest, like this:
!!! example
	```
	StateIconList[EFST_IDs.EFST_PROPERTYHOLY_TK] = StateIconList[EFST_IDs.EFST_ASPERSIO]
	--[[
	StateIconList[EFST_IDs.EFST_PROPERTYHOLY_TK] = {
		haveTimeLimit = 1,
		posTimeLimitStr = 2,
		descript = {
			{ "Mild Wind [Holy]", COLOR_TITLE_BUFF },
			{ "%s", COLOR_TIME },
			{ "Grants weapon with Holy element" }
		}
	}
	]]
	```
