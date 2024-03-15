If you have trouble using this translation project, here is a tutorial how to do so.

## Downloading
I recommend you to use TortoiseGit to download this project.

* [Git for Windows](https://git-scm.com/download/win)  
* [TortoiseGit](https://tortoisegit.org/download/)

Optional is that you download the repository, in a Zip format, but then you have to download the whole project again when I make updates, not just the updated files.

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

## NEMO Profiles and WARP Sessions
Requires one of these programs:

* [NEMO (by 4144)](https://gitlab.com/4144/Nemo/)
* [WARP (by Neo-Mind)](https://github.com/Neo-Mind/WARP)

The easiest way to use this project is by taking advantage of the NEMO Profile/WARP Session feature.

* Nemo [Profiles](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/NEMO%20Profiles)
* WARP [Sessions](https://github.com/llchrisll/ROenglishRE/tree/master/Addons/WARP%20Sessions)

| Profile/Session | Usage for |
| --- | --- |
| 2015 | Any client in 2015 until you reach a certain date |
| 2019-06 | 2019-06 and higher |

Each profile/session has the patches with the required values already pre-defined,  
like itemInfo.lub -> itemInfo_EN.lub, so you only have to press "OK" to confirm the patches  
in Nemo while in WARP it applies automatically.

NEMO Example - Client 2018-06-20 until the next profile

1.) "Load Profile" and select `2018_Translation.log` > Confirm patches  
2.) "Select Recommended" after applying any profile.  
3.) Now you can select your custom changes you want, like "Custom Windows Title" and so on.  
4.) "Apply Selected" and test your client.

WARP Example - Client 2018-06-20 until next profile

1.) "Load Session file" and select `2018_Translation.yml` > Confirm patches  
2.) "Select Recommended" after applying any session.  
3.) Now you can select your custom changes you want, like "Custom Windows Title" and so on.  
4.) "Apply Patches" and test your client.

Note - Quest List:  
RecommendedQuestInfoList_True_EN contains the latest kRO content which are mostly not implemented yet by rAthena.  
So you can stick to the RecommendedQuestInfoList_EN if you want as well.