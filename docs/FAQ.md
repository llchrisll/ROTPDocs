# Frequently Asked Questions
If you have question that's not listed here, feel free to post it on the Discord (Link at main site), otherwise go to [rAthena Forum](https://rathena.org/board/forum/19-client-side-support/) for support.

___
**Q**: I recieve an **Error** window with gibberish in it.

**A1**: That might be related to the Official Anti-Cheat Program used in your client. For that you need to use the **fixed** CDClient.dll from [Nemo](https://gitlab.com/4144/Nemo/-/blob/master/Input/CDClient.dll) or from [WARP](https://github.com/Neo-Mind/WARP/blob/rock_win32/Inputs/CDClient.dll) and overwrite the one in your folder, which prevents the loading of such program.
___
**Q**: My client exe's still using Korean text/gibberish text?

**A1**: All files from **data** folder of this project must be packed in **grf** format (ex: english.grf) and listed in .ini file (default: data.ini) in your client folder.

**A2**: Make sure ``Load custom lua file instead itemInfo*.lub`` diff is targeting the correct itemInfo.lua
___

**Q**: I can't see My headgear when equipped?

**A1**: Check your server item_db.txt, The viewID is must set to the correct value based on accessoryid.lub, or you can check the value in itemInfo.lua under "ClassNum" for reference.

**A2**: Your client data.grf doesn't have it or the file is corrupt.
___
**Q**: I can't see My garment(Wings) costume?

**A1**: Update your kRO client, otherwise that garment was came from other official RO, like jRO.

**A2**: Check your server item_db.txt, The viewID is must set to the correct value based on spriterobeid.lub, or you can check the value in itemInfo.lua under "ClassNum" for reference.
___
**Q**: My weapon isn't showing during attack?

**A1**: Update your kRO client, there are new weapon sprites update for Doram race and some from event.

**A2**: Probably its "ClassNum" value in itemInfo.lua is 0, please report it on issue page.
___
**Q**: My client.exe crashes when I try to open it?

Note: All files from project have been tested and don't caused any crash.

**A1**: Install DirectX 9.0c from Microsoft.

**A2**: These files must be present in your client folder: aossdk.dll, binkw32.dll, CDClient.dll, cps.dll, granny2.dll, ijl15.dll, libcurl.dll, Mss32.dll and Mp3dec.asi

**A3**: There is file that's missing/corrupt in your data.grf (related to login screen).

**A4**: Check your client diffs, probably there is diff that causes client to crash.
___
**Q**: My client has small font?

**A1**: [Solution](https://rathena.org/board/topic/117647-guide-fixing-small-font-on-ragnarok-online-client/)
___
**Q**: Where are item sprites and textures that usually included in translation project?

**A1**: This project only deals with translation, post question on rA forum if you have any missing item resource.
___
**Q**: Why item/skill/map names different from iRO version?

**A1**: Read the project description.
___
**Q**: Why there are still many gibberish texts in itemInfo.lua?

**A1**: Almost each week kRO added many new items, new quests and skill revisions, and only 1 active translator in this project. Too much to do, too little time.
___
**Q**: I have issue with criatura academy maps (1st and 2nd floor), it becomes black/unwalkable?

**A**: rAthena still using old version of Criatura academy quests, thus older version of criatura maps are needed. ([Download](https://mega.nz/#!b2J12AyA!9e_HSXRuS7Ae778hanXq-PoW0TTkaiLmu1GNk7kSKn8))
___
**Q**: Which emulator I should use with this project?

**A1**: I'm using rAthena only, but it also might work Hercules. 
___
**Q**: What version of rAthena that I can use with this project?

**A1**: Pretty much ever version, but recommended is the latest one, as there are updates included which might not match older rAthena versions.
___
**Q**: I found many grammatical errors in your translation.

**A1**: Glad to hear, feel free to submit Pull request or just report it on the discord.
___