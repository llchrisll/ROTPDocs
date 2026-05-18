
Note: This will only explain the client side, please visit the original topic for more information about the server-side of it, if it's explained.  

Disclaimer  
I don't take any credit for the copied guide.
___

[Original by iraciz](https://rathena.org/board/topic/97954-guide-adding-custom-icons-to-skills/#comment-268363)

First of all you need the data files, those are:

* Sprite and Act of your custom icon.
* Item Bmp of your custom Icon.

### Step 1
Place your custom Icon Sprite and Act in `data/sprite/¾ÆÀÌÅÛ`  

**IMPORTANT**  
The icon need to be named exactly as the skill name displayed in the DB,  
if you don't know it, you have 2 choices, open skill_db.txt or login into your server  
and use the command @skillid "name" to confirm.  
RO data.grf brought 3 party icons as default, but the name was changed and I had to rename it according to the Skill Name in the skill_db.yml

### Step 2
Place the Custom Icon BMP in `data/texture/À¯ÀúÀÎÅÍÆäÀÌ½º/item`  

**IMPORTANT**  
As step #1, It need to be named exactly as the skill name, also need to be bmp size 24x24  

Editing Lua Files  
Some Skills do not exist in the lua files, and the must be added because files are conected and they take each other names as reference to read information, for example if you only add the sprites and bmp, it does'nt guarantee that your skill will show the icon, just because you added files with the name.

### Step 3
Go to `data\luafiles514\lua files\skillinfoz`

* skillid.lub  
  In this file you need to check if your current skill exist! if not, you need to add a new one according to the skill name, and skillid number.
* skilldescript.lub  
  In this file if your customized icon belong to a non-included skill in this file, you will have to add or include the new skill, because a name need to be taken as reference there.

	For Example: Party Skills are not included in the txt skilldescript.lub, in order to recognize the custom icon, the skill must be created or added into that file.  
	You can do the same for other skills such as Darkstrike, Dragon Fear, etc, respecting the lime formats of the luafiles " ",

* skillinfolist.lub  
  This file include a list of every skill registered, of course if you use an icon for a new skill, you need to add the skill in this file.  
  This file also display son information in the game skill window.

**Structure**  
This information do not affect the skill sctructure in game, but it is necessary  
because its used to display information when scrolling mouse over the skill icon,  
and casting ranged skills, if you cast a skill no included in this file,  
maybe the range will not be recognized and it will pop up a warning of cant get skill range. 

```
[sKID. "the exactly name of the skill must be added there, don't mess with that."] = {  
"ICON NAME";  
SkillName = "This is the text that the character will display when casting the skill",  
MaxLv = the max level of the skill existing in the skilldb.txt.  
SpAmount = { sp consumed by level according to the skilldb structure, this will be showed in the player skill window}  
bSeperateLv = true for seperated skill leves such as warmwind, teleport, gospel etc, false to fix the skill to the last level applied,  
AttackRange = {Range of the skill according to the skill level range of skills in the skill_db.txt}  
```