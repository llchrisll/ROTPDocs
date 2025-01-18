With the pull request [PR #67](https://github.com/llchrisll/ROenglishRE/pull/67), I have implemented [NeoMind](https://rathena.org/board/topic/98148-guide-how-to-use-a-secondary-iteminfo-file/)'s Multi-Iteminfo Support  
into the project, which also changed the iteminfo location and definition.  

#### SystemEN\itemInfo.lua  
This file contains now the table for your custom entries,   
as well as the possbility to override offical items, like in Neo's original version.  
  
Below I will try to explain the configs which are possible, let's start with core of it:
##### Importing files
```
-- Load the splited function file
require("SystemEN/LuaFiles514/itemInfo_f")

-- Load the translation file
dofile("SystemEN/LuaFiles514/itemInfo.lua")

-- Load the file for custom items and overrides
-- dofile("SystemEN/itemInfo_C.lua")

-- Load additional files, like custom items, overrides and others
-- New tables needs unique names, to import them you need to copy a "itemInfoMerge"
-- line at the end and adjust it accordingly.

-- Place all files in the "SystemEN" folder, the rest will be automatically added.
ImportFiles = {
	"itemInfo_C.lua", -- custom items
}
-- Just define the table postfix, 'tbl_' will be automatically added
-- Note: The "tbl_override" is handled separately at the end.
ImportTables = {
	"custom",
}
```

* `require` is most important and loads the function, which were split from the original iteminfo.  
This allows me to only have one global itemInfo.lua with all arguments,  
which are normally read by newer clients only, like `EffectID` and `costume`.  
* `dofile` loads files additionally to the `itemInfo.lua`.  
Yes, it is possible to add multiple iteminfos, like what I do:  
```
-- Place all files in the "SystemEN" folder, the rest will be automatically added.
ImportFiles = {
	"rotp_c.lua", -- custom items
	"item_kro.lua", -- untranslated kRO items
	"item_jro.lua", -- untranslated jRO items
	"item_iro.lua", -- untranslated iRO items
	"item_idro.lua", -- untranslated idRO items
	"item_bro.lua", -- untranslated bRO items
	"item_twro.lua", -- untranslated twRO items
	"item_thro.lua" -- untranslated thRO items
}
-- Just define the table postfix, 'tbl_' will be automatically added
ImportTables = {
	"custom",
	"kro",
	"jro",
	"iro",
	"idro",
	"bro",
	"twro",
	"thro"
}
```
![](../images/itemInfo_dofile.png)

**Note**  
These files contain missing and untranslated items from each server and are able to download from my discord in the [contribution](https://discord.com/channels/632937952997277696/721722941464903741/1159571115790827641) channel.
##### Ingame Display
There are two sets of variables, one for the translation file and one for your custom items,  
except the `CServerName` which is only for custom items.  
The 2nd set of variables all contain the word `Custom` in some way.
```
---------------- Additional Configs for translation file ----------------
-- Display origin server based on translation file's Server argument
-- 0 = disable/1 = in Item Name/2 = top of description/3 = bottom of description
DisplayServer = 1

-- Defines how the item id will be shown in item name, doesn't take effect in other settings
TagStart = '('
TagEnd = ')'

-- Define the colour in which the Server Name should be shown (affects official)
-- Format: '^<RRGGBB>'
-- '' = same color as "Server: " (^0000CC = blue)
-- '^FFFFFF' = white
ServerColour = '^FF0000'

-- Show ItemID at bottom (affects custom items as well)
-- 0 = disable/1 = top of description/2 = bottom of description
DisplayItemID = 2

-- Display a database link at bottom of description (true/false)
DisplayDatabase = true

---------------- Additional Configs for custom items ----------------
-- Display server name
-- 0 = disable/1 = in Item Name/2 = top of description/3 = bottom of description
DisplayCustomServer = 1

-- Defines how the item id will be shown in item name, doesn't take effect in other settings
CustomTagStart = '['
CustomTagEnd = ']'

-- Server Name for your custom items
CServerName = 'ROTP'

-- Define the colour in which the custom Server Name should be shown (custom items)
-- Format: '^<RRGGBB>'
-- '' = same color as "Server: " (^0000CC = blue)
-- '^FFFFFF' = white
CServerColour = '^00FF00'

-- Database link for custom items, like fluxcp (true/false)
DisplayCustomDB = false

----- Table for Database Links -------------------
ItemDatabase = {
	["Divine-Pride"] = {
		Name = "Divine-Pride.net",
		URL = "https://www.divine-pride.net/database/item/"
	},
	["iRO"] = {
		Name = "iRO Wiki",
		URL = "https://db.irowiki.org/db/item-info/"
	},
	["Custom"] = {
		Name = "Database",
		URL = "http://127.0.0.1/?module=item&action=view&id="
	}
}
```

* `DisplayServer` reads the custom `Server` argument and displays it based on the value you put it on, like this:  
![](../images/itemInfo_Server.png)  
* `TagStart` and `TagEnd` defines how the server name is seperated from the Item Name and can be anything (tested with [] and () )  
![](../images/itemInfo_Server2.png) ![](../images/itemInfo_Server3.png)  
* `ServerColour` defines in which color your name will be highlighted.  
Example:  
`ServerColour = '^FF0000'`  
![](../images/itemInfo_Color.png)  
* `DisplayItemID` displays the Item ID based on the value you put, like this:  
![](../images/itemInfo_ID.png)  
* `CServerName` holds the name of your Server and works with `DisplayCustomServer`  
* `DisplayDatabase (true/false)` adds an URL (opens in your webbrowser) to a database.
  ![](../images/itemInfo_Link.png)  
   The actual links are saved in the `ItemDatabase` table.  
   `["Divine-Pride"]` being default, but you can also use whatever you want.  
   Like this project supports items from other servers,  
   like iRO, we can refer to the iRO Wiki only for iRO items with `["iRO"]`  
   `Name` defines how the link will be displayed  
   `URL ` defines the base url to the database like divine-pride
  ![](../images/itemInfo_Link2.png)  

##### The `DO NOT TOUCH` lines
```
---------------- DON'T TOUCH THE LINES BELOW unless you know what you are doing ----------------
require('SystemEN/LuaFiles514/rotp_f')

-- Loop through each file in the "ImportFiles" table and load them
for _, v in ipairs(ImportFiles) do
	dofile('SystemEN/'..v)
end

-- Loop through each table in the "ImportTables" table
-- and merge them into the main table "tbl" 
for _, v in ipairs(ImportTables) do
	F_itemInfoMerge(_G['tbl_'..v], false)
end

F_itemInfoMerge(tbl_override, true) -- official overrides
---------------------------------------------------
```
Technically, please **DON'T TOUCH** them.  
The only thing you can touch or adjust is the last line of it, `F_itemInfoMerge(tbl_override, true)`.  
This only defines if entries in the `tbl_override` should override or not.  
Of course , you can add more files the same way.  

#### SystemEN\itemInfo_C.lua  
To keep changing configs easier, I split the tables for custom items and overrides into it's own file: `itemInfo_C.lua`  
You can rename it as you like as long as you change the name in the first part.
```
--[[ Template
	[ID] = {
		unidentifiedDisplayName = "Unknown Item",
		unidentifiedResourceName = "",
		unidentifiedDescriptionName = { "" },
		identifiedDisplayName = "Item",
		identifiedResourceName = "",
		identifiedDescriptionName = {
			"Line 1",
			"Line 2"
		},
		slotCount = 0,
		ClassNum = 0,
		costume = false
	},
]]

-- Table for Custom Items
tbl_custom = {
}

-- Table for Official Overrides
tbl_override = {
	
}
```

* `tbl_custom` holds the entries for your custom items.  
* `tbl_override` holds items you want to change,  
   overriding the official ones without touching the translation file directly.

#### SystemEN\LuaFiles514\itemInfo.lua  
This is now the itemInfo for translated items, just like the itemInfo_EN.lua before.  
The only difference is that it now contains every argument (costume and EffectID).  
	
#### SystemEN\LuaFiles514\itemInfo_f.lua  
This contains the function lines for the itemInfo and will now be the key to overwrite  
depending on the client you are using.

#### SystemEN\LuaFiles514\rotp_f.lua  
This is a file, which was added recently ([11th January 2025](https://github.com/llchrisll/ROenglishRE/commit/23073800ac14156cfc6393f5e7892045302e79d6)) to the project.  
It contains the important and globalized `F_itemInfoMerge` function,
as well as another functions required for the [Custom Lua Support](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/Custom%20Lua%20Support).  
In all cases, it's a **DO NOT TOUCH** file, you have been warned.