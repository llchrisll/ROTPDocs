## Web Service  
The year 2020 had a major change regarding Emblems and Hotkeys.  
You need a extra Web Service, where all those informations are saved to and loaded from.
___
_Client Setup_  
If you need more info about these service_ folders, see [below](#service_-folder).

1. Open up the `service_ExternalSettings_.lub` and go to the following lines
```
AssistAddr = 0.0.0.03000
-----------------------------------------
-- Old client compatibility [Secret]
-- (Just change the AssistAddr to your IP)
-----------------------------------------
Url = { TwitterUrl = 'http'..AssistAddr }
AccountLinkedUserDataUrl = {
	Save = 'http'..AssistAddr..'userconfigsave',
	Load = 'http'..AssistAddr..'userconfigload'
}
TwitterDataUrl = {
	Auth = 'http'..AssistAddr..'twitteruser-auth',
	Upload = 'http'..AssistAddr..'twitterupload'
}
EmblemDataUrl = {
	Upload = 'http'..AssistAddr..'emblemupload',
	Download = 'http'..AssistAddr..'emblemdownload'
}
```
2. Now edit the IP+Port in `AssistAddr` to your server IP and Port (8888) from the web service.
3. Save and close it.
4. Test it.
___ 
Note  
For Clients older than 2020-08 you also need to apply the patch `Fix HTTP Emblems in clients` when diffing your client.
___
## service_ folder
The files in the service_ folder is basically responsible for the EmblemHotkeys for 2020 Clients as well as the Doram class creation.
It also is responsible for displaying the Aura based on the class and level.
(Still requires the server side changes to send the packets to the client)

Based on the langtype set from below, it reads a certain folder, but you can also force the client to read only the [service_korea](https://github.com/llchrisll/ROenglishRE/tree/master/Renewal/data/luafiles514/lua%20files/service_korea) folder with the patch Always load Korea ExternalSettings lua file.

In case that patch doesn't work or is not available, you need to rename the service_korea folder,
depending on the langtype.
As for the file names, just replace the _kr and _kr_sak with the respective values from ```File Postfix```.

## Langtype List
Here you can find a list of avaiable langtypes, used are the values.

| langtype | language/folder name | File Postfix | Issues | 
| --- | --- | --- | --- |
| 0   | korea | _kr<br>_kr_sak | |
| 1   | usa | _usa<br>_usa_sak | |
| 2   | japan | _jp<br>_jp_sak | |
| 3   | china | _ch<br>_ch_sak | |
| 4   | taiwan | _tw<br>_tw_sak | |
| 5   | thailand | _th<br>_th_sak | |
| 6   | indonesia | _id<br>_id_sak | |
| 7   | philippine | _ph<br>_ph_sak | uses different login packets thenrAthena handles,<br />requires https://github.com/OpenKore/openkore |
| 12  | brazil | _br<br>_br_sak | |
| 14  | russia/ru | _ru<br>_ru_sak | I experienced that clients up to 2018-06-20<br /> and starting with 2020-08-19 are working |
| 15  | vietnam | _vn<br>_vn_sak | |
| 18  | france | _fr<br>_fr_sak | |

 _kr = Read by Ragexe.exe Clients  
 _kr_sak = Read by RagexeRE.exe Clients

What else does the langtype define

* Font the client uses  
* Login packets, most are supported by rAthena.

Note A detailed list of the langtypes and other important values in sclientinfo.xml, can be found [here](https://github.com/rathena/rathena/wiki/Clientinfo.xml)