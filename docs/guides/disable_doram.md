[Original by Secret](https://rathena.org/board/topic/117041-tutorial-how-to-disable-creation-of-summoner-characters/#comment-351888)

Note Depending on the langtype and Ragexe type (Ragexe.exe or RagexeRE.exe), it will require you to edit different files.
Also it depends on if you have the NEMOWARP patch `Always load korea ExternalSettings lua file` available or not, if not see link to langtype.
But I will go by the default of `langtype 0` and `Ragexe.exe`

 1. Open the `data\luafiles514\lua files\service_korea\externalsettings_kr.lub`.
 2. Find and edit the following line `MakeableRace = { Doram = true }`
 3. Change it to `Doram = false`
 4. Save and close the file.