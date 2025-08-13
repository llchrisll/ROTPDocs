## [Navigation Legacy](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/Navigation%20Legacy)
As of commit [3rd April 2022](https://github.com/llchrisll/ROenglishRE/commit/4b8cc693b6491bc9edea70b7622364ba0750acf0) I moved the previous Navigation files into `Addons/Navigation Legacy`.
Because this commit removes them of the Renewal folder and introduces an modified `navi_f_krpri.lub` and `navi_f_krsak.lub` in combination of an extra file: `SystemEN/Navi_Data.lub`
This file contains the korean text and the translated counterpart for it.

The result of the whole process is that I can skip then tiring process of syncing the ID's kRO uses for their navigation, which mostly changes with each update they do regarding it and only focus on translating the words.
But that also means that the client also reads the kRO files instead, which might not match the emulator content.

For this reason I moved the previous navigation files into `Addons/Navigation Legacy` folder.
Just place those files in the `data/luafiles514/lua files/navigation/` folder again and you have the previous setup. But still use the new `SystemEN/Navi_Data.lub` as well.

## [Signboard Legacy](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/Signboard%20Legacy)
As I removed the `signboard.lub` file from the project with [8th April 2022](https://github.com/llchrisll/ROenglishRE/commit/e85d3883a7822308008bcbef3877d5ab25fff21f) and  
implemented the `SystemEN/Sign_Data.lub` as well as the edited `signboard_f.lub` file,  
I decided recently ([22 March 2023](https://github.com/llchrisll/ROenglishRE/commit/6e08f70384572d64af25eea6176ca4a69999cf05)) to re-upload the old `signboardlist.lub` separatly as well.

## [Non-kRO Lua Entries](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/NonkROLuaEntries)
These files only contain non-kro entries I used to have in the Additions folder in the respective files.  
So you would need to copy the entries in them yourself, so use with caution!  
To keep some legacy out of them, I split them apart to avoid issues users had when using them duo those non-kro entries in them.

## [Legacy Pre-Renewal Skill Info](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/Legacy%20Pre-Re%20Skillinfoz)
This skilldescript.lub contains the old and original skilldescription for pre-renewal skills.  
Since the community voted to use Sandalphon's version which is more detailed and corrected,  
I decided to keep the old file here for legacy purposes.
---
#### Disclaimer
In most cases the original files only have to be overwritten, if not stated otherwise.  
Remember, always make backups!