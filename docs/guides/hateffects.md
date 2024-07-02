[Original by khyle650](https://rathena.org/board/topic/132752-guide-add-new-hateffect-aura-style/#comment-412723)

Note I will use `c_hateffect` and `HAT_EF_c_hateffect` as example

1. Open `data\texture\effect` folder
2. Move your files in a seperate folder in there
3. Open `data\luafiles514\lua files\hateffectinfo\hateffectinfo.lub`
4. Go the last entry of the `HatEFID` table (Example `HAT_EF_SERPENT_SHADOW = 180`)
5. Add a `,` after it and add in the same way your hateffect with an sequential ID (=Don't skip ID's)
6. Go to the last entry of `hatEffectTable`
7. Use the following layout entry as base (remember to put an `,` after the last entry)  
```
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
##### Explanation

- resourceFileName path to the datatextureeffect folder (effect nameeffect_name.str)  
- IsIgnoreRiding true makes the hateffect not to adjust to your mount  
- isRenderBeforeCharacter true makes the effect appear over the character  
- hatEffectPos Y Position (up and down) of the hateffect  
- hatEffectPosX X Position (left and right) of the hattect  
- isAdjustPositionWhenShrinkState put always true  
- isAdjustSizeWhenShrinkState put always true