# WACCA Asset Definition Table Map

This page defines what the role of each `.uasset` file in `/WindowsNoEditor/Mercury/Content/Table` is.

> WARNING: This page is currently a work in progress, it may be missing information or be incorrect in some way. 
> 
> Please contribute if you can!

### AnnounceTable
Old announcements, unused in modern version past WACCA S, last announcement dated to December 15th, 2020 (10AM JST)
#### Structure
| Name              | Type                          | Example Value   | Notes |
| ----------------- | ----------------------------- | --------------- | ----- |
| AnnounceStartDate | *UInt64Property* (WACCA Date) | `2018121310`    |       |
| AnnounceEndDate   | *UInt64Property* (WACCA Date) | `0`             |       |
| ImageFileName     | *StrProperty*                 | `uT_AN_S00_000` |       |

### BackMovieSettingTable
Setting, Background Movie (ask/ON/OFF)

### BarLineTable
Setting, toggle display of measure lines (ON/OFF)

### BGMVolumeTable
Setting, BGM Volume (0-10), increments of 10 in-game (0, 10, 20, etc.)

### BingoAllClearResultTable
Contains rewards for bingo sheet clears.
Lists season ID, sheet number, reward item ID and item number (amount?)
#### Structure
| Name         | Type           | Example Value | Notes |
| ------------ | -------------- | ------------- | ----- |
| ID           | *IntProperty*  | `42`          |       |
| MainSeasonId | *ByteProperty* | `3`           |       |
| SubSeasonId  | *Int8Property* | `0`           |       |
| SheetNumber  | *IntProperty*  | `42`          |       |
| ItemId       | *IntProperty*  | `206001`      |       |
| ItemNumber   | *IntProperty*  | `1`           |       |

### BingoLineResultTable
Rewards for hitting bingos? 1-9, probably granted in order per sheet.
Contains data in the same format as [BingoAllClearResultTable](#bingoallclearresulttable), WP rewards are denoted by item ID 0.
#### Structure
| Name            | Type                  | Example Value | Notes |
| --------------- | --------------------- | ------------- | ----- |
| ID              | *IntProperty*         | `7`           |       |
| MainSeasonId    | *ByteProperty*        | `3`           |       |
| SubSeasonId     | *Int8Property*        | `0`           |       |
| SheetNumberList | *Array\<IntProperty>* | `42`          |       |
| ItemId          | *IntProperty*         | `0`           |       |
| ItemNumber      | *IntProperty*         | `1500`        |       |

### BingoMissionConditionTable
List of every possible condition for a bingo to have.
Lists difficulty, condition genre (class), condition type, and any associated values with that condition. As of 3.07.01, there are 375 conditions
#### Structure
| Name            | Type                  | Example Value | Notes |
| --------------- | --------------------- | ------------- | ----- |
| ID              | *IntProperty*         | `7`           |       |
| MainSeasonId    | *ByteProperty*        | `3`           |       |
| SubSeasonId     | *Int8Property*        | `0`           |       |
| SheetNumberList | *Array\<IntProperty>* | `42`          |       |
| ItemId          | *IntProperty*         | `0`           |       |
| ItemNumber      | *IntProperty*         | `1500`        |       |

### BingoMissionSheetTable
Defines what difficulties of conditions should appear on each sheet, specified as a range of sheets, that has a list of levels and amount of conditions per level.

### BingoMissionSkipSettingTable
Bingo Skip setting (ON/OFF)

### BonusEffectSettingTable
Setting, Bonus Note Effect (ON/OFF)

### BonusEffectVolumeTable
Setting, Volume for Bonus Note Effect, same values as [BGMVolumeTable](#bgmvolumetable)

### BoostItemTable
List of boost items, such as EXP, WP, or Gate boosts, as well as Daily Bonus boosts.

### BossStageTable
List of boss songs, their start and end dates, appear conditions, and unlock conditions. Requires more research, unsure of what each appear and unlock condition is.

### CenterInfoTable
Setting, Center Display (0-7), has options to change to combo, score, -score, and all score borders

### ChainNoteVolumeTable
Setting, Chain Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### CharacterVoiceTable
Setting, Character Voice (ON/OFF), I think this is for character voices in-game

### ClearRateTable
List of every letter grade (MASTER, SSS, C, AAA, etc.) and their requirements. Requirements listed in either note hit count or minimum score.

### ColorTable
RGBA color definitions for WACCA Console UI elements. Unsure if it's on-screen colors or LED colors.

### ConditionTable
Massive table of conditions (776 as of 3.07.01), has IDs similar to IDs seen in [BossStageTable](#bossstagetable), could be related.

### CoopNormaTable
List of multiplayer co-op handicaps, based on averaged level of all players

### CoopTable
Multiplayer configurations relating to "boost rate" and "penalty note rates", unsure of what this does yet.

### CountrySettingTable
Defines the displayed country code for each region, the maximum amount of songs per set, if the coin blocker setting should be displayed, and optionally the password required to be able to change the songs per set.

### DemoMusicTable
List of songs that will be played in attract mode, cycled through in order of appearance.
Lists song ID, difficulty, and play time in seconds.

### EMoneyBrandTable
List of EMoney providers.
Lists brand ID, an icon for the provider, as well as success and error sounds for electronic payment. Most of this functionality is disabled since sometime in Lily R?

### ErrorTable
List of WACCA-specific errors that can be triggered.
Lists error number and sub error number (e.g. 1904-1)

### EventTable
List of in-game events. Lists the following:

- Event ID
- Start and end times
- "title balloon widget path", appears to alter the appearance of the dialog shown on the title screen
- Title Message Tag, shown before action on the title screen
- Title Action Message Tag, shown after action, when start button is visible
- A list of navigator IDs, used to force nav to specific one, for example, the April Fools events
- A list of endcards to show for "rank in"
- A list of endcards to show for "random"
- The conditions to display the above endcards, or to not display any
- The event music tag, for specific conditions
- A list of valid "cultures" for the event
- A misspelled "titla call voice character ID" list, appears to be unused
- A "class voice message" list, appears to be unused

### GameScoreTable
Configurations related to ratings, somehow, as well as the max allowed score

### GateSkipSettingTable
Setting, Gate Skip (ON/OFF)

### GiveupSettingTable
Setting, Give Up Border (0-5), autofail when selected condition is no longer reachable

### GradePartsTable
A list of every Title Part, used to construct custom Titles.
Lists part ID, part type(?), part string, part explanation (unused), start/end times, and if it's an initial item

### GradeTable
A list of every Title.
Lists title ID, IDs of up to 3 title parts (0 is used for unused parts), title rarity, title string, explanation tag, start/end times, if it's an initial item, and how many WP you gain for earning the title

### GuideLineIntervalTable
Setting, Guide Line Interval (0-7), labeled as None/A-G in-game.

### GuideLineMaskTable
Setting, Guide Line Mask (0-5), adjusts transparency of guide lines.

### GuideVolumeTable
Setting, Guide volume, same values as [BGMVolumeTable](#bgmvolumetable)

### HoldNoteVolumeTable
Setting, Hold Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### IconTable
A list of every Icon.
Lists icon ID, icon texture name (relative to `UI/Textures/USERICON/`), title rarity, icon name tag, explanation tag, start/end times, if it's an initial item, and how many WP you gain for earning the icon

### JudgeInfoDetailPositionTable
Setting, show FAST/LATE indicator  (ON/OFF)

### JudgeInfoPositionTable
Setting, Judgement Info Position (0-3), 3 is OFF

### JudgeLineSettingTable
Offset (0-200), -10 to+10 in increments of .1, default 100

### JudgeParameterTable
Judgement timing table for each note type, unsure of how the values are used.
Contains fast/late timings for each judgement type and adjustments for front/rear

### KeyBeamEffectTable
Setting, Key Beam Effect (ON/OFF)

### LaunchDateTable
List of the launch dates of every major version of the game, might be used for rate calculations.

### LevelUpTable
List of experience requirements for levels.
Lists starting level and required EXP for a level up. Only levels where it changes are defined.

### LevelUpWaccaPointTable
Same as [LevelUpTable](#leveluptable), except lists WP reward for finishing each level.

### LimitationTimeTable
A list of all of the UI timers used in the game, and how long their time limits are. Time limits bug out over 999.

### LoginRandomMessageTable
A list of random login messages.
Lists a message tag, the conditions for the random message, 2 values, probably related to the condition, and a priority number.

### MessageTagTable
Appears to be a list of message tag string replacements. Unused since Lily R, may however still be active. Lists a tag, a replacement string, and start/end times.

### MirrorSettingTable
Setting, Mirror Notes (ON/OFF), mirrors notes across Y axis.

### MultiPlayPointTable
Appears to be a list of WP bonus multipliers for multiplayer games. Has 4 ranks? Not sure how this works.

### MultiRankInfoTable
Setting, Multiplayer Rank display (ON/OFF), controls the display of current multiplayer placement in-game.

### MusicParameterTable
List of all music selectable in the game. This is where you can add songwheel definitions.
This is a very dense table, will do a separate write-up about details later.

### MusicSelectOptionBeginner
List of option presets displayed for beginners.

### MusicSelectOptionDesignSetting
List that defines design options.

### MusicSelectOptionDisplayInfoSetting
List that defines display options.

### MusicSelectOptionGameSetting
List that defines game options.

### MusicSelectOptionNoteColorTable
List of note color options. Maps parameter to [NotesColorTable](#notescolortable) (note color ID). Custom note colors may be possible?

### MusicSelectOptionSoundSetting
List of sound options.

### MusicSelectOptionTop
List of option menus.

### MyRoomTopMenu
List of My Room options.

### NavigateCharacterTable
List of navigator characters in the game. Lists the following:

- Navigator ID
- Validity in every culture
- Character type (mapped to fixed C++ enum)
- if the character is original
- default and stage up textures
- monitor texture
- end card normal, "rank in", and stage up textures
- VIP joined texture
- VIP joined background material
- VIP joined light material
- VIP joined front material
- Voice start/end times
- name and explanation tags
- Navigator start/end times
- if is an initial item

### NaviPanelTable
List of UI button visual appearances.
Lists button text tag A and B, help text tag (unused since WACCA S iirc), text sizes for each tag, button icon type, texture size, texture position, button widget type, and button widget color.

### NormaTable
List of gauge (health) points gained/lost for each judgement on each type of note. Referred to by the old terms SuperJust/Just/Good/Miss.

### NoteDesignTable
Mask setting (0-4), used to control the background dimming.

### NotesColorTable
List of note color definitions, used by [MusicSelectOptionNoteColorTable](#musicselectoptionnotecolortable).
Lists note color ID, note color type (may be hardcoded D:), color parameter name, color name tag, if the color is a support color, and the hold color ID

### PlayerLevelInfoTable
Player Level Info setting (ON/OFF), toggles the display of the player's level.

### RateInfoTable
Rate Info setting (ON/OFF), toggles the display of the player's rate.

### RhythmGameAppearanceTable
Miscellaneous settings regarding in-game effects.
Lists "required combo for effect", song pass effect wait time, "change guide lane appearance combo border", the brightness/gradation of the mask in songs with and without a video, hold note division length, and hold note division lane width

### RhythmGamePosTable
Defines the XYZ coordinates of where the notes appear, as well as effects.

### RhythmGameRuleTable
Defines "protect involve rock frame number", default note speed, amount of misses considered missless, "basic experience", and "adapted start dash level".

### ScoreInfoTable
Setting, Score Info (ON/OFF)

### SeeYouRandomMessageTable
Same as [LoginRandomMessageTable](#loginrandommessagetable), except for endcards

### SESetTable
List of every sound effect set. Lists the following:

- marvelous and good SE
- swipe (slide) marvelous and good SE
- snap marvelous and good SE
- hold marvelous SE
- hold constant SE
- dropped hold constant SE
- chain SE
- name and explanation tag
- start/end times
- if is an initial item
- how many WP you gain for earning the effect pack

### SkillTable
list of skills, seems to be unused, translation keys no longer exist, and IDs only refer to 1.xx.xx

### SlideBonusTimingTable
A list of timing leniency windows for swipes (slides) based on the BPM, measured in beats.

### SlideNoteColorSupportTable
Setting, Swipe (Slide) Inverted Color (ON/OFF)

### SlideNoteVolumeTable
Setting, Swipe (Slide) Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### SnapNoteColorSupportTable
Setting, Snap Note Inverted Color (ON/OFF)

### SnapNoteVolumeTable
Setting, Snap Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### SNoteEffectTable
Setting, R Note Effect setting (ON/OFF)

### SNoteVolumeTable
Setting, R Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### StageupIconTable
Setting, Stage Up Emblem (ON/OFF), toggles the display of the player's stage up emblem.

### StageUpTable
List of every stage in the game. You can create your own stages, so long as you are running on a server that supports it.
This is a very dense table, will do a separate write-up about details later.

### StoreMenu
List of items available to buy from the Shop. Lists the following:

- Goods ID
- Item category
- Item ID
- Item amount
- Boost item category
- Boost item ID
- Boost item amount
- Payable type (credits or WP)
- Price
- Store item name and description
- Store character message
- Item texture
- start/end times
- "exclusion target goods ID"

### SugorokuStageParameterTable
Gate page definitions, fill in later

### SugorokuUniqueParameterTable
List of Gates, fill in later

### TapBonusTimingTable
A list of timing leniency windows for touch notes based on the BPM, measured in beats.

### TicketItemTable
List of ticket items.

### TotalResultItemJudgementTable
List of times that specific conditions can occur when passing certain songs based on conditions defined in [ConditionTable](#conditiontable). This is very confusing and I don't quite fully understand it.

### TotalResultRandomItemTable
List of random drop conditions after playing a song. Related to [TotalResultItemJudgementTable](#totalresultitemjudgementtable) in some way.

### TouchEffectShootTable
Setting, Touch Effect Shoot (ON/OFF)

### TouchEffectTable
Setting, Touch Effect ON/OFF before Reverse, now contains an touch effect ID.

### TouchNoteVolumeTable
Setting, Touch Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### TouchPanelSymbolColorTable
List of console colors.

### TrophyTable
List of trophies.

### UnlockInfernoTable
List of unlock requirements for INFERNO charts.

### UnlockMusicTable
List of unlock requirements for every song. Can have multiple entries for different unlock conditions over time.

### UserPlateBackgroundTable
List of all user plates.

### UserRateCoefficientTable
Lists correlations between minimum scores and rate coefficients.

### UserRateStepTable
Lists every rate level achievable in the game.

### UserRateTargetTable
Defines where the new/old song cutoff is for rate, how many songs apply, and the coefficient of the type of song.

### VolumeStepListTable
A list of the volume steps in increments of 10 as full-width strings. Unsure where it's used.

### WaccaPointTable
List of how many WP you earn for each letter grade depending on the level of the song.

### WidgetTranslucencyTable
Setting, Widget Translucency (0-5). Impacts life bar, judgement, etc. visibility.