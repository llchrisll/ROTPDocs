Adding your own cards is no different than an regular ETC item.  
Like explained in the [Basic Setup](../basic_custom/#basic-setup), you need the basic description in your itemInfo.lub.  

They only have a global sprites/texture files by official means,  
if you have custom card sprites, of course you are free to use those instead.  

 ANSI encoding:   
  * `unidentifiedResourceName = "ÀÌ¸§¾ø´ÂÄ«µå",`  
  * `identifiedResourceName = "ÀÌ¸§¾ø´ÂÄ«µå",`  
  
 EUC-KR encoding:  
  * `unidentifiedResourceName = "이름없는카드",`  
  * `identifiedResourceName = "이름없는카드",`  
  
Additionally to the itemInfo.lua, there are 4 .txt files in the data folder, which are responsible for the cards.  
Without those, you cards won't be recognized by the client as cards, but regular ETC items.

  * `carditemnametable.txt`  
	This file is the most important, in here each Card has it's own entry and  
	tells the client, the following IDs are Cards.  
	Format: `<ID>#` per card
  * `cardpostfixnametable.txt`  
	This file is responsible if you want your "prefix" before the Item Name, like `Bloody` for a Hydra Card.  
	Format: `<ID>#` per Card
  * `cardprefixnametable.txt`  
	This file is for the prefixes, by default they are placed after the Item Name,  
	unless you put an entry in `cardpostfixnametable.txt`.  
	Format: `<ID>#<Prefix>#` per Card
  * `num2cardillustnametable.txt`  
	If you have an illustration aka image, this is the file for it.  
	In case, you don't have one, don't worry, just use `sorry` (`<ID>#sorry#`) as placeholder.  
	Format: `<ID>#<File Name>#` per Card (without .bmp)