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

-- Load the additional files
-- Example: (Yes you could add kRO itemInfo itself, but prepare for lua errors)
--dofile("System/itemInfo_true.lub")
```

* `require` is most important and loads the function, which were split from the original iteminfo.  
This allows me to only have one global itemInfo.lua with all arguments,  
which are normally read by newer clients only, like `EffectID` and `costume`.  
* `dofile` loads files additionally to the `itemInfo.lua`.  
Yes, it is possible to add multiple iteminfos, like what I do:  
```
-- Load the additional files
-- Example: (Yes you could add kRO itemInfo itself, but prepare for lua errors)
--dofile("System/itemInfo_true.lub")
dofile("SystemEN/item_kro.lua")
dofile("SystemEN/item_jro.lua")
dofile("SystemEN/item_iro.lua")
dofile("SystemEN/item_bro.lua")
dofile("SystemEN/item_idro.lua")
dofile("SystemEN/item_ghhro.lua")
dofile("SystemEN/item_twro.lua")
```
![](../images/itemInfo_dofile.png)  
But to actually merge them into the main `tbl` via the `itemInfoMerge` function, you still need add a few lines which is explained at the end.  

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
-- The item id will be automically parsed at the end of 'DbUrl'
-- example: 'https://www.divine-pride.net/database/item/512'
DisplayDatabase = true
DbURL = 'https://www.divine-pride.net/database/item/'
DbDisplay = 'Divine-Pride.net'

---------------- Additional Configs for custom items ----------------
-- Display server name
-- 0 = disable/1 = in Item Name/2 = top of description/3 = bottom of description
DisplayCustomServer = 1

-- Defines how the item id will be shown in item name, doesn't take effect in other settings
CustomTagStart = '['
CustomTagEnd = ']'

-- Server Name for your custom items
CServerName = 'ExampleRO'

-- Define the colour in which the custom Server Name should be shown (custom items)
-- Format: '^<RRGGBB>'
-- '' = same color as "Server: " (^0000CC = blue)
-- '^FFFFFF' = white
CServerColour = '^00FF00'

-- Database link for custom items, like fluxcp (true/false)
-- The item id will be automically parsed at the end of 'CustomDbUrl'
-- example: 'http://127.0.0.1/?module=item&action=view&id=512'
DisplayCustomDB = false
CustomDbUrl = 'http://127.0.0.1/?module=item&action=view&id='
CustomDbDisplay = 'Database'
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
* `DisplayDatabase (true/false)` adds an URL (opens in your webbrowser) to a database.
![](../images/itemInfo_Link.png)  
* `DbURL` defines the base url to the database like divine-pride
* `DbDisplay` defines how the link will be displayed  
![](../images/itemInfo_Link2.png)  
* `CServerName` holds the name of your Server and works with `DisplayCustomServer`
##### itemInfoMerge function
```
function itemInfoMerge(src, state)
	if src == nil then
		return
	end
	for ItemID,DESC in pairs(src) do
		if state == false then
			if not tbl[ItemID] then
				tbl[ItemID] = {}
				tbl[ItemID] = DESC
			end
		else
			tbl[ItemID] = DESC
		end
		if src == tbl_custom then
			tbl[ItemID].Custom = true
		end
	end
	return
end

-- itemInfoMerge(src, state)
-- @src = table for merge into tbl
-- @state = overwrite existing entries (true) or not (false)

--itemInfoMerge(tbl_override, true) -- official overrides
--itemInfoMerge(tbl_custom, false) -- custom items
--itemInfoMerge(tbl, false) -- original kRO iteminfo
```
**DON'T TOUCH** the function `itemInfoMerge` unless you know what you are doing.  
I don't take responsiblity, if you change it without my knowledge.  

Like stated above, you also need to add a new function call with the new table, but be sure that it holds a different name than any present ones.  
See the commented one as example, which would merge the original kRO iteminfo into the global `tbl`.

My lines mentioned above:  
```
-- itemInfoMerge(src, state)
-- @src = table for merge into tbl
-- @state = overwrite existing entries (true) or not (false)

itemInfoMerge(tbl_override, true) -- official overrides
itemInfoMerge(tbl_custom, false) -- custom items
--itemInfoMerge(tbl, false) -- original kro iteminfo

itemInfoMerge(tbl_kro, false) -- kro
itemInfoMerge(tbl_jro, false) -- jro
itemInfoMerge(tbl_iro, false) -- iro
itemInfoMerge(tbl_idro, false) -- idro
itemInfoMerge(tbl_bro, false) -- bro
itemInfoMerge(tbl_ghhro, false) -- ghhro
itemInfoMerge(tbl_twro, false) -- twro
```
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