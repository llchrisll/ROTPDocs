
Note: This will only explain the client side, please visit the original topic for more information about the server-side of it, if it's explained.  

Disclaimer  
I don't take any credit for the copied guide.
___
[Original by Shinsei](https://rathena.org/board/topic/122544-guide-fresh-all-in-one-guide-to-implementing-maps-with-worldmap/#comment-372759)

1. `datamappostable.txt`  
At the top of the file you should see #@ (probably 12@), change that to 13@ (That is the array size of the mappostable)
Scroll down to the bottom of the file and add the the map you want to add (as well as its coordinates on the map where it should appear) in the following format  
`[index]#[mapname].rsw#x¹#y¹#x²#y²#`
	- x¹, y¹, x², y² stand for the start and end coordinates of the map box which gets drawn on the world map.  
    Navigate to `data\luafiles514\lua files\worldviewdata\`  
    Find files `worldviewdata_table.lub` as well as `worldviewdata_language.lub`  
	(if your files are inside a GRF, extract them).  
       - Open your `worldviewdata_language.lub` and add the following line  
	   `MSI_###_[MAPNAME] = Map Display Name,`  
	   (if you’re adding it at the end of the array, don’t forget to remove the comma, as it’s the last element of the array.
       - Now open your `worldviewdata_table.lub` and add the following line  
	   `{###, [mapname].rsw, x¹, y¹, x², y², WORLD_MSGID.MSI_###_[MAPNAME],}`

	**IMPORTANT**  
	The ### number at the start of this array appears to be corresponding to a general “block” location on the map.  
	e.g. If you’re adding a map somewhere in the Payon area, you would want this number to be “111”,  
	however if you’re adding it in the area of Rachel, you’d want the number to be “105”.  
	In short, whenever you’re adding maps, always take a look at the numbers of the maps close to your new map,  
	use those numbers.  
	If your map doesnt appear on the worldmap, this is more than often the culprit behind it!

2. Go to `data\luafiles514\lua files\datainfo\` (Optional)  
This is where you will be adding the kafra teleporting service animations.  
Open the file `kaframovemapservicelist.lub` and add Kafra teleport service information to your map as well as KafraMinimapPos  
I am not certain what the parameters in this array do, if anyone has any idea, please let me know.

##### Navigation
**IMPORTANT**  
Remember to make a backup of it before you start working on it.  

Open the navigation folder and add your custom map to the `navi_map_krpri.lub`.  
To do that, open up the file, scroll all the way down the list and add your map in the following format `{ [mapname], Display name, ID, xSize, ySize }`

If you don't have any files, you can use the `navigenerator.bat` included in the server folder which is generator if you buildcompile it via your `rAthena.sln` and automatically generate them based on the NPC's and Maps which are available for you.

**NOTE**  
The Display name is going to be name displayed over your map  
There are 3 values for the IDs  
(I am not 100% certain about what they are exactly, will need to research it more - then I will update the information here)
  
* 5001 is used for standard maps, such as Towns, Fields, Dungeons.  
* 5002 appears to be used for maps which have clone counterparts  
* 5003 is used for indoor maps

xSize and ySize correspond to the values of gat.Width as well as gat.Height

	Adding connections between neighbouring maps  
	To do that, you want to open `navi_link.lub` and add connections to; as well as from the neighbouring maps in the following format  
	`{ [yourmap] , [index], 200, 99999, [yourmapname]_[destmapname]_[index], , xCoord, yCoord, payo2, destCoord_x, destCoord_y},`  
	e.g.  
	`{ pay_arche, 14056, 200, 99999, pay_arche_payon_706, , 81, 17, payon,  228, 327 },`  
	`{ payon, 15327, 200, 99999, payon_pay_arche_1977, , 228, 329, pay_arche, 81, 22 },`

##### Duplicate/Clone Maps  
Duplicating/cloning maps is very easy with the `dataresnametable.txt`,  
which is takes original files and redirects the client to them instead files for  your custom map which don't exist.
This makes copy & paste of original files unnecessary. 

**Layout**

	Custom Mapname.gnd#Original Mapname.gnd#  
	Custom Mapname.gat#Original Mapname.gat#  
	Custom Mapname.rsw#Original Mapname.rsw#  
	À¯ÀúÀÎÅÍÆäÀÌ½º\map\Custom Mapname.bmp#À¯ÀúÀÎÅÍÆäÀÌ½º\map\Original Mapname.bmp#  

Remember to either use a Map Cache Editor or the `mapcache.bat` from rAthena.