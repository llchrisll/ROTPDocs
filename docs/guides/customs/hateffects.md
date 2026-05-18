!!! note
	This will only explain the client side, please visit the original topic for more information about the server-side of it, if it's explained.  

!!! abstract "Disclaimer"
	I don't take any credit for the copied guide.
___
[Original by khyle650](https://rathena.org/board/topic/132752-guide-add-new-hateffect-aura-style/#comment-412723)

!!! note
	I will use `c_hateffect` and `HAT_EF_c_hateffect` as example

!!! info "Guide"
	1. Open `data\texture\effect` folder
	2. Move your files in a seperate folder in there
	3. Open `data\luafiles514\lua files\hateffectinfo\hateffectinfo.lub`
	4. Go the last entry of the `HatEFID` table (Example `HAT_EF_SERPENT_SHADOW = 180`)
	5. Add a `,` after it and add in the same way your hateffect with an sequential ID (=Don't skip ID's)
	6. Go to the last entry of `hatEffectTable`
	7. Use the following layout entry as base (remember to put an `,` after the last entry)  
	```lua
		[HatEFID.HAT_EF_c_hateffect] = {
			resourceFileName = "c_hateffect\\c_hateffect.str",
			hatEffectPos = -1,
			hatEffectPosX = 0,
			isRenderBeforeCharacter = false,
			isIgnoreRiding = false,
			isAdjustPositionWhenShrinkState = true,
			isAdjustSizeWhenShrinkState = true
		}, 
	```
	!!! info "Explanation"
		!!! info "`resourceFileName`"
			Path to the `data\texture\effect\` folder (`nameeffect_name\nameeffect_name.str`)
		!!! info "`IsIgnoreRiding`"
			`true` makes the hateffect not to adjust to your mount
		!!! info "`isRenderBeforeCharacter`"
			`true` makes the effect appear over the character
		!!! info "`hatEffectPos`"
			Y Position (up and down) of the hateffect  
		!!! info "`hatEffectPosX`"
			X Position (left and right) of the hattect  
		!!! info "`isAdjustPositionWhenShrinkState`"
			Put this always on `true`
		!!! info "`isAdjustSizeWhenShrinkState`"
			Put this always on `true`