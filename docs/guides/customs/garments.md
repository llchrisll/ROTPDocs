!!! note 
	This will only explain the client side, please visit the original topic for more information about the server-side of it, if it's explained.  

!!! abstract "Disclaimer"
	I don't take any credit for the copied guide.
___
[Original by  Froost](https://rathena.org/board/topic/128738-guide-robewings-installation-guide-2021/#comment-398328)
!!! note "Guide Example"
	I will use `Angel_Wing` as example.  
	I'll use `Novice` (Male), the sprite name for that is `ÃÊº¸ÀÚ_³²`  
### Files
The Client requires for each class and per gender 2 files (.spr & .act).
  
!!! info "Sprites"
	!!! info "Male"
		`data\sprite\·Îºê\Angel_Wing\³²`
	!!! info "Female"
		`data\sprite\·Îºê\Angel_Wing\¿©`

	!!! note 
		You can copy&paste the male sprites into the female folder and rename them like mentioned above.

!!! info "Lua Files"
	Afterwards we need to add some entries in the `spriterobename.lub`, `spriterobeid.lub` as well as `transparentItem.lub`.
	!!! info "SpriteRobeID"  
		Add `ROBE_Angel_Wing = 84` at the end and a `,` after the last entry before yours.  

	!!! info "SpriteRobeName"
		1. Go to the end of the table `RobeNameTable` and `RobeNameTable_Eng`, add `[SPRITE_ROBE_IDs.ROBE_Angel_Wing ] = "Angel_Wing"` at the end and a `,` after the last entry before yours.
		2. At the end of `RobeTopLayer` add `SPRITE_ROBE_IDs.ROBE_Angel_Wing`  
		   (remember the `,` after the previous entry)

	!!! info "TransparentItem"
		If the Wing appears on the ALT+Q but does not appear on the character itself,  
		you need to make an additional edit in the `transparentItem\transparentItem.lub`.  
		It's an extra file that controls the transparency of the item,  
		this file's default for non-existent ids is 0 (transparent) so you just open it and add at the end  
		`{ 84, 255, 255, 0 },`  
		84 = is the ID

## Convert Custom Wings (Headgears) to Robes
[Original by madtoyz](https://rathena.org/board/topic/72734-guide-custom-wings-at-robe-place/#comment-148019)

Converting your custom Wings, which can be headgears is fairly simple  
Take the guide above in consideration, but instead of extra files for robes,  
you take the headgears files from `data\sprite\¾Ç¼¼»ç¸®\³²` and `data\sprite\¾Ç¼¼»ç¸®\¿©`  
as base and insert them the same way as above in the `·Îºê` folder.