If you have trouble using this translation project, here is a tutorial how to do so.
___
## Downloading
I recommend you to use TortoiseGit to download this project.

* [Git for Windows](https://git-scm.com/download/win)  
* [TortoiseGit](https://tortoisegit.org/download/)

Optional is that you download the repository, in a Zip format, but then you have to download the whole project again when I make updates, not just the updated files.

## 2025 Full Clients and Ragexes
___
Disclaimer: This was written on 25th April 2026 and might/will change in the near future.
___
With the recent changes to the project and kRO clients (since 2025-07 and 2025-12-04),  
I will recommend one of these two full kRO clients, which were kindly provided by skylove:

 1. [2025-07-16](https://drive.google.com/file/d/1EAlnpYywf6ktli3v9DliDXMvrcFcClfq/view?usp=drive_link):  
    You will need to update this client, otherwise you will get a few lua errors duo the project being more up to date.  
	Or you'll get the files you error at from the `Tools\AdditionsGenerator.bat`.  
	Feel free to also download the `kro_data.grf` to get newer resource files.  
 2. [2026-02-19](https://drive.google.com/file/d/1NfZJb3WuDmeqfPGGcLzDlVJLnGKXWzXy/view):  
    You don't need my custom `kro_data.grf`, as it already contains files from it.
    Skylove told me to avoid updating this client as well. So you have been warned.  
	From what I have seen, the `data.grf` in there is fully accessable by GRF Editor,  
	but I might be wrong about that.
 
###Important kRO Client changes
 
 1. Clients/GRFs above 2025-07-16 implemented GRF v3 support, which increases the max size an GRF massively.  
    But this also requires newer clients. Clients like 2022-04-06 will not work anymore.  
	I didn't test which clients would still work with GRFs like that.
 2. Clients/GRFs above 2025-12-04 received a new GRF encryption, which are also not accessable to older clients.  
    Even GRF Editor (to this date) can't encrypt them.
   
## Translation Folder
With commit of [10th December 2023](https://github.com/llchrisll/ROenglishRE/commit/649d35f956a1a5cee088557194b99822d132a5ad), the default version of this project is 2015-10-29 again!
Therefore I added a few simple .bat files to generate the desired Client folder.

 * [ClientGenerator.bat](https://github.com/llchrisll/ROenglishRE/blob/master/Tools/ClientGenerator.bat)  
   Copies the necessary files based on selected type and client date into a generated Client folder.  
 * [AdditionsGenerator.bat](https://github.com/llchrisll/ROenglishRE/blob/master/Tools/AdditionsGenerator.bat)    
   Copies files from the Additions folder based on your selection into a generated Client folder  
 * [CLSGenerator.bat](https://github.com/llchrisll/ROenglishRE/blob/master/Tools/CLSGenerator.bat)  
   Copies the CLS (Custom Lua Support) based on your selection into a generated Client folder  
  
### Basic Files Setup
#### Data Version
Move the data folder in your Ragnarok root folder (where you're .exe is located)  
Be sure that your client is patched with "Read Data Folder First" (it's not recommended by default)

Note: The client will read everything else missing from the GRF's listed in DATA.ini afterwards!

#### GRF Version
Pack the data folder in a GRF and add your custom GRF in the DATA.ini as first entry.  
Example:  
```
[Data]
0=server.grf
1=data.grf
2=rdata.grf
```
Required Program - GRF Editor

 * [rAthena](https://rathena.org/board/files/file/2766-grf-editor/)  
 * [Hercules](https://board.herc.ws/files/file/138-grf-editor/)  

### System Folder
The System folder can't be placed in a GRF, so it goes also in the root folder.

## Client Patchers
To be able to patch an unpacked kRO Ragexe, you require one of these programs:
!!! note 
	I still need to test WARP2025 and WARP2026, if they are able to patch older clients.

 * [WARP](https://github.com/Neo-Mind/WARP) by Neo-Mind:  
   Original successor to NEMO, but hence dropped support by Neo for unknown reasons, maybe real-life.  
 * [WARP2025](https://github.com/hiphop9/Warp2025) by skylove:  
   For any Client newer than 2022-04-06, see more info in the [rAthena Forum](https://rathena.org/board/topic/144862-2025-06-04_ragexe-warp2025/).
 * [WARP0716](https://github.com/CrazyBebop/WARP0716) by CrazyBepop:  
   For **ONLY** the 2025-07-16 Ragexe, see more info in the [rAthena Forum](https://rathena.org/board/topic/149119-warp0716-%E2%86%92-forge-%E2%80%94-ragexe-2025-07-16-patches-customjobs-reforged-newest-client/).  
 * [WARP2026](https://github.com/zVictorHG/WARP2026-Project) by VictorHug0:  
   You can get an 2026-01-07 Ragexe in the [rAthena Forum](https://rathena.org/board/topic/149414-2026-01-07-ragexe-clientinfo-warp/).  
   I tested both with the 2026-02-19 kRO Full Client and the project files using `[27]` from the `ClientGenerator.bat` and didn't encounter any errors.
 * [FORGE](https://forge.legacygamers.net) by CrazyBepop:  
   This is still in development, but should be good alternative for NEMO and WARP in general once it's ready.

### Session & Profiles
The easiest way to use this project is by taking advantage of the NEMO Profile/WARP Session feature.

* WARP [Sessions](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/WARP%20Sessions)

| Profile/Session | Usage for |
| --- | --- |
| 2015 | Any client in 2015 until you reach a certain date |
| 2019-06 | 2019-06 and higher |

Each profile/session has the patches with the required values already pre-defined,  
like `System\itemInfo.lub` -> `SystemEN\iteminfo.lua`, so you only have to press "OK" to confirm the patches  
in Nemo while in WARP it applies automatically.

!!! example "Example - Client 2018-06-20 until next profile"

	1. "Load Session file" and select `2018_Translation.yml` > Confirm patches  
	2. "Select Recommended" after applying any session.  
	3. Now you can select your custom changes you want, like "Custom Windows Title" and so on.  
	4. "Apply Patches" and test your client.

!!! note "Recommended Quests"
    `SystemEN\RecommendedQuests.lub` contains the latest kRO content which are mostly not implemented yet by rAthena.  
    So you can stick to the `SystemEN\RecommendedQuests_basic.lub` if you want as well.