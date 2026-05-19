This list is based on the list from [RateMyServer.net](https://ratemyserver.net/index.php?page=riot_bible_main),  
but only provides the base folders and class names.  

You can download it in as a .txt file [here](../downloads/spritelist.txt){:download="spritelist.txt"} as well.

---
## Folders
All sprites are located in the `data\sprite\` folder, which contains the following sub-folders:  
I provide the korean (EUC-KR) and "gibberish" (ANSI) version.
!!! note
	=== "`<Class>`"
	If `<Class>` is mentioned, it needs to be replaced with the respective name.
	=== "(?)"
	Entries marked with a (?) I'm not sure of when or where they are used.  
	Maybe legacy placeholder files.

!!! info "Folders"
	=== "Korean"
		* 몬스터 = Monster Sprites
		* 도람족 = Doram Class related sprites (Wedding/Weapon,etc)
		* 로브 = Robes/Custome Garmnents
		* 아이템 = Skill Icons + Item Drop Sprites
		* 악세사리 = Headgears
			* /여 = Female
			* /남 = Male
		* 방패 = Shields
			* /<Class> = Folders for Shields per Class
		* 인간족 = Class Sprites
			* /<Class> = Folders for Weapons and attack animations per Class
			* /머리통 = Head Sprites
				* /여 = Female
				* /남 = Male
			* /몸통 = Body Sprites (Files: See below)
				* /여 = Female
				* /남 = Male  
				Files: /`<Class>`_`<Gender>`.act/spr (See at the end for complete list)
		* 이팩트 = Skill and Hat Effects
		* npc = NPC Sprites
	
	=== "ANSI"
		* ¸ó½ºÅÍ = Monster Sprites
		* µµ¶÷Á· = Doram Class related sprites (Wedding/Weapon,etc)
		* ·Îºê = Robes/Custome Garmnents
		* ¾ÆÀÌÅÛ = Skill Icons + Item Drop Sprites
		* ¾Ç¼¼»ç¸® = Headgears
			* /¿© = Female
			* /³² = Male
		* ¹æÆÐ = Shields
			* /<Class> = Folders for Shields per Class
		* ÀÎ°£Á· = Class Sprites
			* /<Class> = Folders for Weapons and attack animations per Class
			* /¸Ó¸®Åë = Head Sprites
				* /¿© = Female
				* /³² = Male
			* /¸öÅë = Body Sprites  
				* /¿© = Female
				* /³² = Male  
				Files: /`<Class>`_`<Gender>`.act/spr (See at the end for complete list)
		* ÀÌÆÑÆ® = Skill and Hat Effects
		* npc = NPC Sprites
---
## Layout for Classes
!!! info 
	=== "Folders"
	`/<Class>/`
	=== "Files"
	`/<Class>_<Gender>.act/.spr`

!!! info
	=== "Korean"
		* abyss_chaser = Abyss Chaser
		* arch_mage = Arch Mage
		* biolo = Biolo
		* cardinal = Cardinal
		* dragon_knight = Dragon Knight
		* elemetal_master = Elemental Master
		* hyper_novice = Hyper Novice
		* imperial_guard = Imperial Guard
		* inquisitor = Inquisitor
		* kagerou = Kagerou
		* meister = Meister
		* night_watch = Night Watch
		* oboro = Oboro
		* rebellion = Rebellion
		* shadow_cross = Shadow Cross
		* shinkiro(남)/shiranui(여) = Shinkiro/Shiranui
		* sky_emperor2 = Sky Emperor (Fusion)
		* sky_emperor = Sky Emperor
		* soul_ascetic = Soul Ascetic
		* troubadour(남)/trouvere(여) = Troubadour/Trouvere
		* windhawk = Wind Hawk
		* 가드 = Royal Guard
		* 건너 = Gunslinger
		* 검사 = Swordsman
		* 결혼 = Tuxedo/Wedding Dress
		* 검용병 = Novice (Alternative?)
		* 궁수 = Archer
		* 권성 = Star Gladiator
		* 권성융합 = Star Gladiator (Fusion)
		* 기사_h = Knight(?)
		* 기사 = Knight
		* 길로틴크로스 = Guillotine Cross
		* 닌자 = Ninja
		* 도둑 = Thief
		* 드래곤나이트 = Rune Knight
		* 레인져 = Ranger
		* 로그_h = Rogue(?)
		* 로그 = Rogue
		* 로드나이트 = Lord Knight
		* 로드페코 = Lord Knight (Peco)
		* 룬나이트 = Rune Knight(?)
		* 리벨리온 = Rebellion
		* 마도기어 = Madogear
		* 마도아머 = Madogear 2
		* 마법사 = Magician
		* 몽크_h = Monk(?)
		* 몽크 = Monk
		* 무희 = Dancer
		* 무희바지 = Dancer(?) - Found in 남 folder
		* 미케닉 = Mechanic
		* 민스트럴 = Minstrel
		* 바드_h = Bard(?)
		* 바드 = Bard
		* 산타 = Santa Suit
		* 상인 = Merchant
		* 팔라딘 = Paladin
		* 성제 = Star Emperor
		* 성제융합 = Star Emperor (Fusion)
		* 성직자_h = Acolyte(?)
		* 성직자 = Acolyte
		* 성투사2 = High Priest
		* 성투사 = Priest(?)
		* 세이지_h = Sage(?)
		* 세이지 = Sage
		* 소서러 = Sorcerer
		* 소울리퍼 = Soul Reaper
		* 소울링커 = Soul Linker
		* 쉐도우체이서 = Shadow Chaser
		* 슈라 = Sura
		* 슈퍼노비스 = Super Novice
		* 스나이퍼 = Sniper
		* 스토커 = Stalker
		* 아크비숍 = Arch Bishop
		* 어세신_h = Assassin(?)
		* 어세신 = Assassin
		* 어쌔신크로스 = Assassin Cross
		* 여름2 = Summer Suit 2
		* 여름 = Summer Suit
		* 연금술사_h = Alchemist(?)
		* 연금술사 = Alchemist
		* 옥토버패스트 = Oktoberfest Suit
		* 운영자2 = Madogear for GMs? or alternative GM Sprite as Madogear
		* 운영자 = Game Master
		* 워록 = Warlock
		* 위저드_h = Wizard(?)
		* 위저드 = Wizard
		* 인퀴지터 = Sura(?)
		* 제네릭 = Genetic
		* 제철공_h = Blacksmith(?)
		* 제철공 = Blacksmith
		* 창용병 = Spear Mercenary
		* 용병 = Sword Mercenary
		* 챔피온 = Champion
		* 초보자 = Novice
		* 크루세이더_h = Crusader(?)
		* 크루세이더 = Crusader
		* 크리에이터 = Creator
		* 클라운 = Clown/Gypsy
		* 태권소년 = Taekwon
		* 턱시도 = Tuxedo(?)
		* 프로페서 = Professor
		* 프리스트_h = Priest(?)
		* 프리스트 = Priest
		* 하이위저드 = High Wizard
		* 하이프리 = High Priest
		* 한복 = Hanbok Suit
		* 헌터_h = Hunter(?)
		* 헌터 = Hunter
		* 화이트스미스 = Whitesmith
	
	=== "ANSI"
		* abyss_chaser = Abyss Chaser
		* arch_mage = Arch Mage
		* biolo = Biolo
		* cardinal = Cardinal
		* dragon_knight = Dragon Knight
		* elemetal_master = Elemental Master
		* hyper_novice = Hyper Novice
		* imperial_guard = Imperial Guard
		* inquisitor = Inquisitor
		* kagerou = Kagerou
		* meister = Meister
		* night_watch = Night Watch
		* oboro = Oboro
		* rebellion = Rebellion
		* shadow_cross = Shadow Cross
		* shinkiro(³²)/shiranui(¿©) = Shinkiro/Shiranui
		* sky_emperor2 = Sky Emperor (Fusion)
		* sky_emperor = Sky Emperor
		* soul_ascetic = Soul Ascetic
		* troubadour(³²)/trouvere(¿©) = Troubadour/Trouvere
		* windhawk = Wind Hawk
		* °¡µå = Royal Guard
		* °Ç³Ê = Gunslinger
		* °Ë»ç = Swordsman
		* °áÈ¥ = Tuxedo/Wedding Dress
		* °Ë¿ëº´ = Novice (Alternative?)
		* ±Ã¼ö = Archer
		* ±Ç¼º = Star Gladiator
		* ±Ç¼ºÀ¶ÇÕ = Star Gladiator (Fusion)
		* ±â»ç_h = Knight(?)
		* ±â»ç = Knight
		* ±æ·ÎÆ¾Å©·Î½º = Guillotine Cross
		* ´ÑÀÚ = Ninja
		* µµµÏ = Thief
		* µå·¡°ï³ªÀÌÆ® = Rune Knight
		* ·¹ÀÎÁ® = Ranger
		* ·Î±×_h = Rogue(?)
		* ·Î±× = Rogue
		* ·Îµå³ªÀÌÆ® = Lord Knight
		* ·ÎµåÆäÄÚ = Lord Knight (Peco)
		* ·é³ªÀÌÆ® = Rune Knight(?)
		* ¸®º§¸®¿Â = Rebellion
		* ¸¶µµ±â¾î = Madogear
		* ¸¶µµ¾Æ¸Ó = Madogear 2
		* ¸¶¹ý»ç = Magician
		* ¸ùÅ©_h = Monk(?)
		* ¸ùÅ© = Monk
		* ¹«Èñ = Dancer
		* ¹«Èñ¹ÙÁö = Dancer(?) - Found in ³² folder
		* ¹ÌÄÉ´Ð = Mechanic
		* ¹Î½ºÆ®·² = Minstrel
		* ¹Ùµå_h = Bard(?)
		* ¹Ùµå = Bard
		* »êÅ¸ = Santa Suit
		* »óÀÎ = Merchant
		* ÆÈ¶óµò = Paladin
		* ¼ºÁ¦ = Star Emperor
		* ¼ºÁ¦À¶ÇÕ = Star Emperor (Fusion)
		* ¼ºÁ÷ÀÚ_h = Acolyte(?)
		* ¼ºÁ÷ÀÚ = Acolyte
		* ¼ºÅõ»ç2 = High Priest
		* ¼ºÅõ»ç = Priest(?)
		* ¼¼ÀÌÁö_h = Sage(?)
		* ¼¼ÀÌÁö = Sage
		* ¼Ò¼­·¯ = Sorcerer
		* ¼Ò¿ï¸®ÆÛ = Soul Reaper
		* ¼Ò¿ï¸µÄ¿ = Soul Linker
		* ½¦µµ¿ìÃ¼ÀÌ¼­ = Shadow Chaser
		* ½´¶ó = Sura
		* ½´ÆÛ³ëºñ½º = Super Novice
		* ½º³ªÀÌÆÛ = Sniper
		* ½ºÅäÄ¿ = Stalker
		* ¾ÆÅ©ºñ¼ó = Arch Bishop
		* ¾î¼¼½Å_h = Assassin(?)
		* ¾î¼¼½Å = Assassin
		* ¾î½Ø½ÅÅ©·Î½º = Assassin Cross
		* ¿©¸§2 = Summer Suit 2
		* ¿©¸§ = Summer Suit
		* ¿¬±Ý¼ú»ç_h = Alchemist(?)
		* ¿¬±Ý¼ú»ç = Alchemist
		* ¿ÁÅä¹öÆÐ½ºÆ® = Oktoberfest Suit
		* ¿î¿µÀÚ2 = Madogear for GMs? or alternative GM Sprite as Madogear
		* ¿î¿µÀÚ = Game Master
		* ¿ö·Ï = Warlock
		* À§Àúµå_h = Wizard(?)
		* À§Àúµå = Wizard
		* ÀÎÄûÁöÅÍ = Sura(?)
		* Á¦³×¸¯ = Genetic
		* Á¦Ã¶°ø_h = Blacksmith(?)
		* Á¦Ã¶°ø = Blacksmith
		* Ã¢¿ëº´ = Spear Mercenary
		* ¿ëº´ = Sword Mercenary
		* Ã¨ÇÇ¿Â = Champion
		* ÃÊº¸ÀÚ = Novice
		* Å©·ç¼¼ÀÌ´õ_h = Crusader(?)
		* Å©·ç¼¼ÀÌ´õ = Crusader
		* Å©¸®¿¡ÀÌÅÍ = Creator
		* Å¬¶ó¿î = Clown/Gypsy
		* ÅÂ±Ç¼Ò³â = Taekwon
		* ÅÎ½Ãµµ = Tuxedo(?)
		* ÇÁ·ÎÆä¼­ = Professor
		* ÇÁ¸®½ºÆ®_h = Priest(?)
		* ÇÁ¸®½ºÆ® = Priest
		* ÇÏÀÌÀ§Àúµå = High Wizard
		* ÇÏÀÌÇÁ¸® = High Priest
		* ÇÑº¹ = Hanbok Suit
		* ÇåÅÍ_h = Hunter(?)
		* ÇåÅÍ = Hunter
		* È­ÀÌÆ®½º¹Ì½º = Whitesmith
---
### Mount Sprites
!!! info  
	!!! info "Cash Mounts"
		=== "Korean"
			* `<Class>_riding_` = Halter Sprites for 4th Classes
			* frog_kagerou = Frog Mount for Kagerou
			* frog_oboro = Frog Mount for Oboro
			* peco_rebellion = Bike Mount for Rebellion (why Peco?)
			___
			* `<Class>포링` = Poring Halter Sprites (Novice/Super Novice+Taekwon)
			* `<Class>알파카` = Alpaca Halter Sprites (Acolyte Classes)
			* `<Class>멧돼지` = Savage Halter Sprites (Merchant Classes)
			* `두꺼비<Class>` = Frog Halter Sprites (Ninja/Soul Linker)
			* `사자<Class>` = Lion Halter Sprites (Knight Classes)
			* `여우<Class>`= Fox Halter Sprites (Magician Classes)
			* `켈베로스<Class>` = Hyuena Halter Sprites (Thief Classes)
			* `타조<Class>` = Ostrich Halter Sprites (Archer Classes)
			* `해태<Class>` = Haetae Halter Sprites (Star Emperor/Soul Reaper)
		
		=== "ANSI"
			* `<Class>`_riding_ = Halter Sprites for 4th Classes
			* frog_kagerou = Frog Mount for Kagerou
			* frog_oboro = Frog Mount for Oboro
			* peco_rebellion = Bike Mount for Rebellion (why Peco?)
			___
			* `<Class>`Æ÷¸µ = Poring Halter Sprites (Novice/Super Novice+Taekwon)
			* `<Class>`¾ËÆÄÄ« = Alpaca Halter Sprites (Acolyte Classes)
			* `<Class>`¸äµÅÁö = Savage Halter Sprites (Merchant Classes)
			* µÎ²¨ºñ`<Class>` = Frog Halter Sprites (Ninja/Soul Linker)
			* »çÀÚ`<Class>` = Lion Halter Sprites (Knight Classes)
			* ¿©¿ì`<Class>`= Fox Halter Sprites (Magician Classes)
			* ÄÌº£·Î½º`<Class>` = Hyuena Halter Sprites (Thief Classes)
			* Å¸Á¶`<Class>` = Ostrich Halter Sprites (Archer Classes)
			* ÇØÅÂ`<Class>` = Haetae Halter Sprites (Star Emperor/Soul Reaper)
	
	!!! info "Regular Mounts"
		=== "Korean"
			* `<Class>_chicken_` = Mount Sprites for Dragon Knight and Imperial Guard
			* meister_madogear1 = Old Madogear for Meister
			* meister_madogear2 = New Madogear for Meister
			* wolf_windhawk = Wind Hawk (Wolf)
			___
			* 레인져늑대 = Ranger (Wolf)
			* 신페코크루세이더_h = Crusader (Peco - Alternative)(?)
			* 신페코크루세이더 = Crusader (Peco - Alternative)
			* 페코rebellion = Rebellion on Peco
			* 페코건너 = Gunslinger (Bike)
			* 페코페코_기사_h = Knight (Peco)(?)
			* 페코페코_기사 = Knight (Peco)
			* 구페코크루세이더 = Crusader (Peco)
			* 그리폰가드 = Royal Guard (Gryphon)
			* 룬나이트쁘띠2 = Rune Knight (Violet Dragon)
			* 룬나이트쁘띠3 = Rune Knight (White Dragon)
			* 룬나이트쁘띠4 = Rune Knight (Blue Dragon)
			* 룬나이트쁘띠5 = Rune Knight (Red Dragon)
			* 룬나이트쁘띠 = Rune Knight (Dragon)
		
		=== "ANSI"
			* `<Class>_chicken_` = Mount Sprites for Dragon Knight and Imperial Guard
			* meister_madogear1 = Old Madogear for Meister
			* meister_madogear2 = New Madogear for Meister
			* wolf_windhawk = Wind Hawk (Wolf)
			___
			* ·¹ÀÎÁ®´Á´ë = Ranger (Wolf)
			* ½ÅÆäÄÚÅ©·ç¼¼ÀÌ´õ_h = Crusader (Peco - Alternative)(?)
			* ½ÅÆäÄÚÅ©·ç¼¼ÀÌ´õ = Crusader (Peco - Alternative)
			* ÆäÄÚrebellion = Rebellion on Peco
			* ÆäÄÚ°Ç³Ê = Gunslinger (Bike)
			* ÆäÄÚÆäÄÚ_±â»ç_h = Knight (Peco)(?)
			* ÆäÄÚÆäÄÚ_±â»ç = Knight (Peco)
			* ±¸ÆäÄÚÅ©·ç¼¼ÀÌ´õ = Crusader (Peco)
			* ±×¸®Æù°¡µå = Royal Guard (Gryphon)
			* ·é³ªÀÌÆ®»Ú¶ì2 = Rune Knight (Violet Dragon)
			* ·é³ªÀÌÆ®»Ú¶ì3 = Rune Knight (White Dragon)
			* ·é³ªÀÌÆ®»Ú¶ì4 = Rune Knight (Blue Dragon)
			* ·é³ªÀÌÆ®»Ú¶ì5 = Rune Knight (Red Dragon)
			* ·é³ªÀÌÆ®»Ú¶ì = Rune Knight (Dragon)