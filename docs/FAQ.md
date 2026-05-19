# Frequently Asked Questions
If you have question that's not listed here,  
feel free to post it on the [Discord][discord], otherwise go to [rAthena Forum][rathena] for support.

___
!!! question "I recieve an **Error** window with gibberish in it"
	=== "Answer 1"
	These errors could mean anything without knowing the message itself.  
	You can ++ctrl+c++ (Copy) into your clipboard and use ++ctrl+v++ (Paste) to provide the error message.
	=== "Answer 2"
	That might be related to the Official Anti-Cheat Program used in your client. For that you need to use the **fixed** CDClient.dll from [Nemo](https://gitlab.com/4144/Nemo/-/blob/master/Input/CDClient.dll) or from [WARP](https://github.com/Neo-Mind/WARP/blob/rock_win32/Inputs/CDClient.dll) and overwrite the one in your folder, which prevents the loading of such program.
___
!!! question "My client exe's still using Korean text/gibberish text?"
	You might have missed a step in the setup.  
	Please revisit the [Installation Guide][guide] and recheck the steps.
___

!!! question "I can't see My headgear when equipped?"
	=== "Answer 1"
	Check your server item_db_equip.yml, the `View` field must be set to the correct value based on accessoryid.lub, or you can check the value in itemInfo.lua under "ClassNum" for reference.
	=== "Answer 2"
	Your client data.grf doesn't have it or the file is corrupt.
___
!!! question "I can't see My garment(Wings) costume?"
	=== "Answer 1"
	Update your kRO client, otherwise that garment was came from other official RO, like jRO.
	=== "Answer 2"
	Check your server item_db_equip.yml, the `View` field must be set to the correct value based on spriterobeid.lub, or you can check the value in itemInfo.lua under "ClassNum" for reference.
___
!!! question "My weapon isn't showing during attack?"
	=== "Answer 1"
	Update your kRO client, there are new weapon sprites update for Doram race and some from event.
	=== "Answer 2"
	Probably its `ClassNum` value in itemInfo.lua is 0, please report it on issue page.
___
!!! question "My client.exe crashes when I try to open it?"
	!!! note
		All files from the project have been tested, but without further information, nobody can help.
	=== "Answer 1"
	Install DirectX 9.0c from Microsoft.
	=== "Answer 2"
	These files must be present in your client folder: aossdk.dll, binkw32.dll, CDClient.dll, cps.dll, granny2.dll, ijl15.dll, libcurl.dll, Mss32.dll and Mp3dec.asi
	=== "Answer 3"
	There is file that's missing/corrupt in your data.grf (related to login screen).
	=== "Answer 4"
	Check your client diffs, probably there is diff that causes client to crash.
___
!!! question "My client has small font?"
	=== "Answer 1"
	[Solution](https://rathena.org/board/topic/117647-guide-fixing-small-font-on-ragnarok-online-client/)
	=== "Answer 2"
	Change the `<langtype>` in your s/clientinfo.xml, read more [here](https://llchrisll.github.io/ROTPDocs/guides/webservice//#langtype-list).
___
!!! question "Where are item sprites and textures that usually included in translation project?"
	=== "Answer 1"
	This project only deals with translation, post questions on rA forum if you have any missing item resource.
	=== "Answer 2"
	Additional sprites and textures can be taken from my `official_data.grf`,  
		which can be downloaded from my [Discord][discord] server.
___
!!! question "Why item/skill/map names different from iRO version?"
	Read the project description.
___
!!! question "Why there are still many gibberish texts in itemInfo.lua?"
	Almost each week kRO (and other servers) adds many new items, new quests and more,  
	but only 1 active translator in this project. Too much to do, too little time.  
	Also I consider this a hobby, not a paied job. If I feel like doing translations, I do it.
	!!! warning "Important"
	I don't do paied jobs, my work is free for everyone.
___
!!! question "I have issue with criatura academy maps (1st and 2nd floor), it becomes black/unwalkable?"
	rAthena still using old version of Criatura academy quests, thus older version of criatura maps are needed. ([Download](https://mega.nz/#!b2J12AyA!9e_HSXRuS7Ae778hanXq-PoW0TTkaiLmu1GNk7kSKn8))
___
!!! question "Which emulator I should use with this project?"
	This project is not restricted to any emulator, it all depends on which client date you are choosing.  
	The emulator is only responsible to provide support for your chosen client date.
___
!!! question "What version of rAthena that I can use with this project?"
	Pretty much ever version, but recommended is the latest one, as there are updates included which might not match older rAthena versions.
___
!!! question "I found many grammatical errors in your translation."
	Glad to hear, feel free to submit Pull request or just report it on the [Discord][discord] server.

[guide]: ../guides/install/
[discord]: https://discord.gg/sagbPhH
[rathena]: https://rathena.org/board/forum/19-client-side-support/