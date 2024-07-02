[Original by Easycore](https://rathena.org/board/topic/110692-guide-adding-custom-random-options/)  
**Introduction**

In this guide I will introduce you how to implement custom Random Options.  
I will use as an example the bonus "bAddEff".

![](../images/easycore_ropt.png)

For display our custom options must be added to `data\luafiles514\lua files\datainfo\enumvar.lub` and `data\luafiles514\lua files\datainfo\addrandomoptionnametable.lub

#### enumvar.lub
Find:  
`VAR_CRITICAL_RATE = { 254, 10 },`  
And add:  
`WEAPON_FREEZE = {255, 0 },`  
*The first number must be same that added in `db\re\item_randomopt_db.yml*

#### addrandomoptionnametable.lub
Find:  
`[EnumVAR.MDAMAGE_SIZE_LARGE_USER[1]] = "Magical resistance Large size monster +%d%%",`  
And add:  
`[EnumVAR.WEAPON_FREEZE[1]] = "Freeze an enemy when attacking +%d%%",`  
*%d% is equal to ROA_VALUE.* 

After completing all of the above your Random Option is ready to use.  
Remember that there is documentation of how to add random options to items and a sample npc.