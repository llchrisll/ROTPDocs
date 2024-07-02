Adding custom headgears requires 4 additional files and 2 more lua files to adjust.  
Headgear Sprite Files consist of `gender_name.act` and `gender_name.spr`, meaning 2 files per gender.  
##### Files  
There are 2 folders, which are for the gender.

*  `data\sprite\¾Ç¼¼»ç¸®\³²` (Male)
*  `data\sprite\¾Ç¼¼»ç¸®\¿©` (Female)
 
##### Lua Files
* `data\luafiles514\lua files\datainfo\accessoryid.lub`  
	Contains the ViewID/ClassNum of your headgear.
  > View ID for Item DB  
  > ClassNum for itemInfo.lub
   
	Note: Clients have a hardcoded View ID limit, depending on client, it might vary.  
	2018-06-20 as example has 2000 (I think), so to use a value higher than that  
	you need to apply the client patch "Increase Headgear ViewID".  
	Like you want to use 6000 as start then input 7000 or more in the patch.  

* `data\luafiles514\lua files\datainfo\accname.lub`  
	File Name Entry, only consisting of `_name`, meaning the client will automatically add the gender at the front.

### Costume Headgears
Adding Costume Headgears is no different from regular heagears,  
you just change the `Locations` node (YML) in the item database on your server and  
change the `costume = false` to `costume = true` in the `itemInfo.lub`, tho the lua part is optional.