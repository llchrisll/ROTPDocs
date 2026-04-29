This page should help you understand the dependencies of certain lua files in the `data/luafiles514/lua files/` folder.  
This page is also not complete and changes and/or corrections can be requested via Discord.  

First the main file, then the files it's required in.  
Example:  
> `Enchant/Enchant.lub` and `ItemReform/ItemReformSystem.lub` both require `ItemDBNameTbl.lub`
___
 * ItemDBNameTbl.lub:  
    » Enchant/Enchant.lub  
    » ItemReform/ItemReformSystem.lub
 * hateffectinfo/ [2024-04-17]
     * hateffectids.lub  
        » hateffectinfo.lub  
	    » effecthatitemtable.lub  
	    » footprinteffectinfo.lub
 * datainfo/
    * accessoryid.lub  
        » accname.lub  
        » TB_Layer_Priority.lub
    * npcidentity.lub  
        » jobName.lub  
        » petinfo.lub  
        » shadowtable.lub
    * spriterobeid.lub  
        » spriterobename.lub  
        » transparentItem\transparentItem.lub
    * EnumVAR.lub  
        » AddRandomOptionNameTable.lub
 * skillinfoz/
    * skillid.lub  
        » skillinfolist.lub  
        » skilldescript.lub  
        » skilltreeview.lub  
        » skilldelaylist.lub
 * stateicon/
    * efstids.lub  
        » stateiconinfo.lub  
        » stateiconimginfo.lub
 * worldviewdata\
    * worldviewdata_language.lub  
        » worldviewdata_list.lub  
        » worldviewdata_table.lub