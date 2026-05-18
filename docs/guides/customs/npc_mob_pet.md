
Note: This will only explain the client side.
___
This is just a simple explanation, what each lua file is for.
##### Lua Files
 
- `data\luafiles514\lua files\datainfo\npcidentity.lub`  
	Holds the ID of the respective NPCMobPet
- `data\luafiles514\lua files\datainfo\jobname.lub`  
	Holds the resource file name of the respective NPCMobPet  
- `data\luafiles514\lua files\datainfo\jobidentity.lub`  
	Required for custom NPCs like `npcidentity.lub`, it holds the ID.  
- `data\luafiles514\lua files\datainfo\petinfo.lub`  
	Required for custom Pets, see below for a seperate explanation.  

##### Sprite Folders
 
- Mob and Pet: `data\sprite\¸ó½ºÅÍ`  
- NPC: `data\sprite\npc`

##### PetInfo.lub
 
- PetNameTable  
	Contains the resource file name of the pet
- PetIllustNameTable  
	Contains the file name for the image in the Pet Info window  
- PetIllustNameTable_Eng  
    English equivalent of the above one  
- PetAccIDs  
    Contains the Item ID for Pet Accessories  
- PetAccActNameTable  
    Contains the .act file name for Pet Accessories  
- PetAccActNameTable_Eng  
    English equivalent of the above one  
- PetStringTable  
    Contains the Pet Name  
- PetEggItemID_PetJobID  
    Assigns the Egg Item ID to a Pet
- PetFoodTable  
    Assigns the Food Item ID to a Pet