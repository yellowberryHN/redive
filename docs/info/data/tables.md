# WACCA Asset Definition Table Map

This page defines what the role and structure of each `.uasset` file in `/WindowsNoEditor/Mercury/Content/Table`.

> WARNING: This page is currently a work in progress, it may be missing information or be incorrect in some way. 
> 
> Please contribute if you can!

### AnnounceTable
Old announcements, unused in modern version past WACCA S, last announcement dated to December 15th, 2020 (10AM JST)
<H4>Structure</H4>

| Name              | Type                              | Example Value   | Notes |
|-------------------|-----------------------------------|-----------------|-------|
| AnnounceStartDate | *UInt64Property*<br/>(WACCA Date) | `2018121310`    |       |
| AnnounceEndDate   | *UInt64Property*<br/>(WACCA Date) | `0`             |       |
| ImageFileName     | *StrProperty*                     | `uT_AN_S00_000` |       |

### BackMovieSettingTable
Setting, Background Movie (ask/ON/OFF)

### BarLineTable
Setting, toggle display of measure lines (ON/OFF)

### BGMVolumeTable
Setting, BGM Volume (0-10), increments of 10 in-game (0, 10, 20, etc.)

### BingoAllClearResultTable
Contains rewards for bingo sheet clears.
Lists season ID, sheet number, reward item ID and item number (amount?)
<H4>Structure</H4>

| Name         | Type           | Example Value | Notes |
|--------------|----------------|---------------|-------|
| ID           | *IntProperty*  | `42`          |       |
| MainSeasonId | *ByteProperty* | `3`           |       |
| SubSeasonId  | *Int8Property* | `0`           |       |
| SheetNumber  | *IntProperty*  | `42`          |       |
| ItemId       | *IntProperty*  | `206001`      |       |
| ItemNumber   | *IntProperty*  | `1`           |       |

### BingoLineResultTable
Rewards for clearing lines in a bingo sheet. Contains data in the same format as [BingoAllClearResultTable](#bingoallclearresulttable),
WP rewards are denoted by item ID 0.
<H4>Structure</H4>

| Name            | Type                       | Example Value                   | Notes                                      |
|-----------------|----------------------------|---------------------------------|--------------------------------------------|
| ID              | *IntProperty*              | `7`                             |                                            |
| MainSeasonId    | *ByteProperty*             | `3`                             |                                            |
| SubSeasonId     | *Int8Property*             | `0`                             |                                            |
| SheetNumberList | *Array&lt;IntProperty&gt;* | `[51, 52, 53, 54, 55, 56, ...]` | List of sheets that this reward applies to |
| ItemId          | *IntProperty*              | `0`                             | Item ID, or `0` for WP reward              |
| ItemNumber      | *IntProperty*              | `1500`                          | Quantity of items received                 |

### BingoMissionConditionTable
List of every possible condition for a bingo to have.
Lists difficulty, condition genre (class), condition type, and any associated values with that condition. As of 3.07.01, there are 375 conditions
<H4>Structure</H4>

| Name           | Type                                | Example Value                                          | Notes                                                           |
|----------------|-------------------------------------|--------------------------------------------------------|-----------------------------------------------------------------|
| ConditionId    | *IntProperty*                       | `248`                                                  |                                                                 |
| Difficulty     | *IntProperty*                       | `4`                                                    | Mission level                                                   |
| ConditionGenre | *Enum&lt;EConditionGenre&gt;*       | `EConditionGenre::MUSIC_SPECIFY`                       | Class of condition                                              |
| ConditionType  | *Enum&lt;EMissionConditionType&gt;* | `EMissionConditionType::MUSIC_CLEAR_ARTIST_DIFIICULTY` | Type of condition within class                                  |
| Value1         | *StrProperty*                       | `aran`                                                 | Data for condition, varies per condition                        |
| Value2         | *StrProperty*                       | `EXPERT`                                               | Data for condition, varies per condition, `null` if unspecified |
| Value3         | *StrProperty*                       | `3`                                                    | Data for condition, varies per condition, `null` if unspecified |
| Value4         | *StrProperty*                       | `null`                                                 | Data for condition, varies per condition, `null` if unspecified |
| Value5         | *StrProperty*                       | `null`                                                 | Data for condition, varies per condition, `null` if unspecified |


### BingoMissionSheetTable
Defines what level of missions should appear on each sheet, specified as a range of sheets,
that has a list of levels and amount of missions of each level per sheet.
<H4>Structure</H4>

| Name           | Type                       | Example Value | Notes                                                                                           |
|----------------|----------------------------|---------------|-------------------------------------------------------------------------------------------------|
| SheetStartNum  | *IntProperty*              | `6`           |                                                                                                 |
| SheetEndNum    | *IntProperty*              | `10`          |                                                                                                 |
| LevelList      | *Array&lt;IntProperty&gt;* | `[2, 3]`      | Level of missions that can appear on these sheets                                               |
| MissionNumList | *Array&lt;IntProperty&gt;* | `[5, 4]`      | Amount of each type of mission level per sheet<br/><br/>All values should sum up to 9, I think? |

### BingoMissionSkipSettingTable
Setting, Bingo Skip (ON/OFF)

### BonusEffectSettingTable
Setting, Bonus Note Effect (ON/OFF)

### BonusEffectVolumeTable
Setting, Volume for Bonus Note Effect, same values as [BGMVolumeTable](#bgmvolumetable)

### BoostItemTable
List of boost items, such as EXP, WP, or Gate boosts, as well as Daily Bonus boosts.
<H4>Structure</H4>

| Name                  | Type                             | Example Value           | Notes                                                  |
|-----------------------|----------------------------------|-------------------------|--------------------------------------------------------|
| BoostItemId           | *IntProperty*                    | `109002`                |                                                        |
| BoostItemType         | *IntProperty*                    | `1`                     | Types defined by *Enum&lt;EBoostItemType&gt;*          |
| IconTexturePath       | *StrProperty*                    | `CHANGE/uT_CH_SRicn_01` | Boost item icon texture name                           |
| BoostType01           | *IntProperty*                    | `-1`                    | Types defined by *Enum&lt;EBoostType&gt;*              |
| BoostValue01          | *StrProperty*                    | `null`                  | `null` if type is `-1`                                 |
| BoostType02           | *IntProperty*                    | `2`                     | Types defined by *Enum&lt;EBoostType&gt;*              |
| BoostValue02          | *StrProperty*                    | `2.1`                   | `null` if type is `-1`                                 |
| BoostType03           | *IntProperty*                    | `6`                     | Types defined by *Enum&lt;EBoostType&gt;*              |
| BoostValue03          | *StrProperty*                    | `2.1`                   | `null` if type is `-1`                                 |
| BoostType04           | *IntProperty*                    | `-1`                    | Types defined by *Enum&lt;EBoostType&gt;*              |
| BoostValue04          | *StrProperty*                    | `null`                  | `null` if type is `-1`                                 |
| BoostType05           | *IntProperty*                    | `-1`                    | Types defined by *Enum&lt;EBoostType&gt;*              |
| BoostValue05          | *StrProperty*                    | `null`                  | `null` if type is `-1`                                 |
| NameTag               | *StrProperty*                    | `BOOST_ITEM_NAME_002`   | Boost item name tag                                    |
| ExplanationTextTag    | *StrProperty*                    | `BOOST_ITEM_MES_002`    | Boost item description tag                             |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date) | `0`                     | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property*<br/>(WACCA Date) | `0`                     | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*                   | `False`                 | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*                    | `0`                     | How much additional WP to gain when getting this item? |

### BossStageTable
List of boss songs, their start and end dates, appear conditions, and unlock conditions. Requires more research, unsure of what each appear and unlock condition is.
<H4>Structure</H4>

| Name                 | Type                              | Example Value                             | Notes                                                                                  |
|----------------------|-----------------------------------|-------------------------------------------|----------------------------------------------------------------------------------------|
| MusicId              | *IntProperty*                     | `3062`                                    | Song ID of the boss song                                                               |
| bVipPreOpen          | *BoolProperty*                    | `True`                                    | Set if VIP users can access the boss song condition 1 day early                        |
| StartDate            | *UInt64Property*<br/>(WACCA Date) | `2022042807`                              | When the boss song condition starts                                                    |
| EndDate              | *UInt64Property*<br/>(WACCA Date) | `2022062107`                              | When the boss song condition ends                                                      |
| AppearConditionArray | *Array&lt;StrProperty&gt;*        | `["920000232", "920000233", "920000234"]` | Conditions to make the song appear. If empty, the song will not appear unless unlocked |
| UnlockConditionArray | *Array&lt;StrProperty&gt;*        | `["920000235"]`                           | Conditions to make the song unlock                                                     
### CenterInfoTable
Setting, Center Display (0-7), has options to change to combo, score, -score, and all score borders

### ChainNoteVolumeTable
Setting, Chain Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### CharacterVoiceTable
Setting, Character Voice (ON/OFF), I think this is for character voices in-game

### ClearRateTable
List of every letter grade (MASTER, SSS, C, AAA, etc.) and their requirements. Requirements listed in either note hit count or minimum score.
<H4>Structure</H4>

| Name             | Type             | Example Value | Notes |
|------------------|------------------|---------------|-------|
| RequiredScore    | *IntProperty*    | `850000`      |       |
| RequiredHitCount | *UInt32Property* | `0`           |       |

### ColorTable
RGBA color definitions for LED colors of various WACCA Console UI elements.
<H4>Structure</H4>

| Name  | Type           | Example Value | Notes |
|-------|----------------|---------------|-------|
| Red   | *ByteProperty* | `112`         |       |
| Green | *ByteProperty* | `48`          |       |
| Blue  | *ByteProperty* | `160`         |       |
| Alpha | *ByteProperty* | `255`         |       |

### ConditionTable
Massive table of conditions (776 as of 3.07.01), has IDs similar to IDs seen in [BossStageTable](#bossstagetable), could be related.
<H4>Structure</H4>

| Name                     | Type           | Example Value | Notes                                                           |
|--------------------------|----------------|---------------|-----------------------------------------------------------------|
| ConditionId              | *IntProperty*  | `920000235`   |                                                                 |
| bConditionLimitNowSeason | *BoolProperty* | `False`       |                                                                 |
| ConditionType            | *IntProperty*  | `64`          | Types defined by *Enum&lt;EConditionType&gt;*                   |
| Value1                   | *StrProperty*  | `3062`        | Data for condition, varies per condition                        |
| Value2                   | *StrProperty*  | `INFERNO`     | Data for condition, varies per condition, `null` if unspecified |
| Value3                   | *StrProperty*  | `CLEAR`       | Data for condition, varies per condition, `null` if unspecified |
| Value4                   | *StrProperty*  | `null`        | Data for condition, varies per condition, `null` if unspecified |
| Value5                   | *StrProperty*  | `null`        | Data for condition, varies per condition, `null` if unspecified |

### CoopNormaTable
List of multiplayer co-op handicaps, based on averaged level of all players
<H4>Structure</H4>

| Name                | Type            | Example Value | Notes |
|---------------------|-----------------|---------------|-------|
| AverageLevel        | *IntProperty*   | `6`           |       |
| NormaRate           | *FloatProperty* | `1.08`        |       |
| TargetNormaRate     | *FloatProperty* | `1.05`        |       |
| AdditionalMissNorma | *IntProperty*   | `-5`          |       |

### CoopTable
Multiplayer co-op configurations relating to "boost rate" and "penalty note rates", unsure of the specifics of the values.
<H4>Structure</H4>

| Name                   | Type            | Example Value | Notes |
|------------------------|-----------------|---------------|-------|
| BoostRate01            | *FloatProperty* | `1.1`         |       |
| BoostRate02            | *FloatProperty* | `1.25`        |       |
| BoostRate03            | *FloatProperty* | `1.35`        |       |
| BoostRate04            | *FloatProperty* | `1.45`        |       |
| BoostSuccessJudgeNum   | *IntProperty*   | `50`          |       |
| PenaltyMissJudgeNum    | *IntProperty*   | `5`           |       |
| PenaltyNoteRateNormal  | *FloatProperty* | `0.05`        |       |
| PenaltyNoteRateHard    | *FloatProperty* | `0.06`        |       |
| PenaltyNoteRateExpert  | *FloatProperty* | `0.08`        |       |
| PenaltyNoteRateInferno | *FloatProperty* | `0.09`        |       |

### CountrySettingTable
Defines the displayed country code for each region, the maximum amount of songs per set, if the coin blocker setting should be displayed, and optionally the password required to be able to change the songs per set.
<H4>Structure</H4>

| Name                      | Type           | Example Value | Notes                                                                      |
|---------------------------|----------------|---------------|----------------------------------------------------------------------------|
| CountryCode               | *StrProperty*  | `TWN`         |                                                                            |
| bEnableCoinblockerSetting | *BoolProperty* | `True`        |                                                                            |
| PlayMusicNumPassword      | *IntProperty*  | `7860`        | The password for changing the number of songs per set, `0` for no password |
| CompetitionModePassword   | *IntProperty*  | `-1`          | The password for enabling event mode, seem to always be set to `-1`        |

#### Password Reference
| Country | Password |
|---------|----------|
| JPN     | N/A      |
| CHN     | `6396`   |
| HKG     | `2244`   |
| KOR     | `2954`   |
| SGP     | `6198`   |
| TWN     | `7860`   |
| USA     | `1223`   |

### DemoMusicTable
List of songs that will be played in attract mode, cycled through in order of appearance.
Lists song ID, difficulty, and play time in seconds.
<H4>Structure</H4>

| Name          | Type             | Example Value | Notes |
|---------------|------------------|---------------|-------|
| MusicUniqueID | *UInt32Property* | `3011`        |       |
| Difficulty    | *IntProperty*    | `0`           |       |
| PlayTime      | *FloatProperty*  | `30`          |       |

### EMoneyBrandTable
List of EMoney providers.
Lists brand ID, an icon for the provider, as well as success and error sounds for electronic payment.
Most of this functionality was disabled since sometime in Lily R?
<H4>Structure</H4>

| Name             | Type          | Example Value                         | Notes |
|------------------|---------------|---------------------------------------|-------|
| BrandId          | *IntProperty* | `4`                                   |       |
| IconTexturePath  | *StrProperty* | `/Game/UI/Textures/EMoney/0008-01-00` |       |
| SuccessSoundPath | *StrProperty* | `/Game/Sound/Se/MER_SE_SYS_002`       |       |
| ErrorSoundPath   | *StrProperty* | `/Game/Sound/Se/MER_SE_SYS_002`       |       |

### ErrorTable
List of WACCA-specific errors that can be triggered.
Lists error number and sub error number (e.g. 1904-1)
<H4>Structure</H4>

| Name        | Type        | Example Value | Notes |
|-------------|-------------|---------------|-------|
| ErrorNum    | IntProperty | `1904`        |       |
| SubErrorNum | IntProperty | `1`           |       |

### EventTable
List of in-game events.
<H4>Structure</H4>

| Name                       | Type                                  | Example Value                                  | Notes                                                                                                     |
|----------------------------|---------------------------------------|------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| EventID                    | *IntProperty*                         | `1001`                                         |                                                                                                           |
| StartDateTime              | *Int64Property*<br/>(WACCA Date+Time) | `20210401070000`                               |                                                                                                           |
| EndDateTime                | *Int64Property*<br/>(WACCA Date+Time) | `20210408065959`                               |                                                                                                           |
| TitleBalloonWidgetPath     | *StrProperty*                         | `/Game/UI/Character/BP_Fukidasi.BP_Fukidasi_C` | Path to balloon widget, shown on the main menu                                                            |
| TitleEventMessageTag       | *StrProperty*                         | `TITLE_MESSAGE_EVENT__APRIL_FOOL_2021`         | Message in balloon before user interaction                                                                |
| TitleActionMessageTag      | *StrProperty*                         | `TITLE_ACTION_MESSAGE_EVENT__APRIL_FOOL_2021`  | Message in balloon after user interaction                                                                 |
| NavigateCharacterIds       | *Array&lt;IntProperty&gt;*            | `[210056, 210057, 210058, 210059]`             | Forces navigator for event? Or what navigators to get for playing?                                        |
| SeeYouCondition            | *Enum&lt;ESeeYouConditionType&gt;*    | `ESeeYouConditionType::Always`                 | Condition type for an event end card to be shown                                                          |
| EventMusicTag              | *Enum&lt;EMusicTagForUnlock&gt;*      | `EMusicTagForUnlock::INVALID`                  | Condition music tag for an event end card to be shown                                                     |
| RankInEndPlayCardInfoList  | *Array&lt;EndPlayCardInfo&gt;*        | [see below]                                    | End cards to show for "Rank In"                                                                           |
| RandomEndPlayCardInfoList  | *Array&lt;EndPlayCardInfo&gt;*        | [see below]                                    | End cards to randomly show                                                                                |
| ValidCultures              | *Map&lt;StrProperty,BoolProperty&gt;* | `{"ja-JP" => true, "ko-KR" => true, ...}`      | Key/Value map of what countries the event should be active in                                             |
| TitlaCallVoiceCharacterIds | *Array&lt;IntProperty&gt;*            | `[210001, 210002]`                             | Name is not a typo, unsure, sounds like it could play voice lines from selected navs on the title screen? |
| TitleCallVoiceMessages     | *Array&lt;StrProperty&gt;*            | `["TITLE_CALL_ANV_000"]`                       | Unsure, voice line to play from selected navs?                                                            |

#### `EndPlayCardInfo` Struct
| Name               | Type           | Example Value                                            | Notes              |
|--------------------|----------------|----------------------------------------------------------|--------------------|
| TexturePath        | *StrProperty*  | `/Game/UI/Textures/CHARACTER/chara056/uT_Chara056_SY000` |                    |
| NavigateCharaterId | *IntProperty*  | `210056`                                                 | Name is not a typo |
| MessageTag         | *StrProperty*  | `SEE_YOU_MSG_09`                                         |                    |
| IsPlayVoice        | *BoolProperty* | `True`                                                   |                    |

### GameScoreTable
Configurations related to ratings, somehow, as well as the max allowed score
<H4>Structure</H4>

| Name                        | Type             | Example Value | Notes                                                |
|-----------------------------|------------------|---------------|------------------------------------------------------|
| NotesScoreRate              | *FloatProperty*  | `1`           |                                                      |
| CrearBonusScoreRate         | *FloatProperty*  | `0`           | Name is not a typo                                   |
| AchievementBonusScoreRate   | *FloatProperty*  | `0`           |                                                      |
| JudgeScoreRateMarvelous     | *FloatProperty*  | `1`           |                                                      |
| JudgeScoreRateGreat         | *FloatProperty*  | `0.7`         |                                                      |
| JudgeScoreRateGood          | *FloatProperty*  | `0.5`         | (UAssetAPI seems to break this one?)                 |
| JudgeScoreRateMiss          | *FloatProperty*  | `0`           |                                                      |
| CrearBonusRateHalfCombo     | *FloatProperty*  | `0`           | Name is not a typo, not sure what this does          |
| CrearBonusRateFullCombo     | *FloatProperty*  | `0`           | ...                                                  |
| CrearBonusRateMaster        | *FloatProperty*  | `0`           | ...                                                  |
| CrearBonusRateSSS           | *FloatProperty*  | `0`           | ...                                                  |
| CrearBonusRateSS            | *FloatProperty*  | `0`           | ...                                                  |
| CrearBonusRateS             | *FloatProperty*  | `0`           | ...                                                  |
| TargetAchievementRateMaster | *FloatProperty*  | `1`           | I assume this is used for song folder completion     |
| TargetAchievementRateSSS    | *FloatProperty*  | `0.97`        | ...                                                  |
| TargetAchievementRateSS     | *FloatProperty*  | `0.93`        | ...                                                  |
| TargetAchievementRateS      | *FloatProperty*  | `0.9`         | ...                                                  |
| MaxScore                    | *UInt32Property* | `1000000`     | Not sure if changing this has any impact on gameplay |

### GateSkipSettingTable
Setting, Gate Skip (ON/OFF)

### GiveupSettingTable
Setting, Give Up Border (0-5), autofail when selected condition is no longer reachable

### GradePartsTable
A list of every Title Part, used to construct custom Titles.
Lists part ID, part type(?), part string, part explanation (unused), start/end times, and if it's an initial item
<H4>Structure</H4>

| Name                  | Type                             | Example Value        | Notes                                                  |
|-----------------------|----------------------------------|----------------------|--------------------------------------------------------|
| GradePartsId          | *IntProperty*                    | `107049`             |                                                        |
| GradePartsType        | *IntProperty*                    | `0`                  | Types defined by *Enum&lt;EGradePartsType&gt;*         |
| NameTag               | *StrProperty*                    | `うそはうそであると見抜ける人でないと` | The actual string of the title part                    |
| ExplanationTextTag    | *StrProperty*                    | `null`               | Unused, always `null`                                  |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date) | `0`                  | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property*<br/>(WACCA Date) | `0`                  | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*                   | `False`              | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*                    | `0`                  | How much additional WP to gain when getting this item? |

### GradeTable
A list of every Title.
Lists title ID, IDs of up to 3 title parts (0 is used for unused parts), title rarity, title string, explanation tag, start/end times, if it's an initial item, and how many WP you gain for earning the title
<H4>Structure</H4>

| Name                  | Type                             | Example Value                | Notes                                                  |
|-----------------------|----------------------------------|------------------------------|--------------------------------------------------------|
| GradeId               | *IntProperty*                    | `104048`                     |                                                        |
| GradePartsId01        | *IntProperty*                    | `107048`                     | 1st title part, `0` if unused                          |
| GradePartsId02        | *IntProperty*                    | `0`                          | 2nd title part, `0` if unused                          |
| GradePartsId03        | *IntProperty*                    | `107228`                     | 3rd title part, `0` if unused                          |
| GradeRarity           | *Int8Property*                   | `2`                          | The rarity of the title, in stars                      |
| NameTag               | *StrProperty*                    | `ＭＮＫ  メンバー`                  | The actual string of the title                         |
| ExplanationTextTag    | *StrProperty*                    | `GRADE_ACQUISITION_WAY_0028` | The message explaining how to unlock this title        |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date) | `0`                          | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property*<br/>(WACCA Date) | `0`                          | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*                   | `False`                      | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*                    | `500`                        | How much additional WP to gain when getting this item? |

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
<H4>Structure</H4>

| Name                  | Type                             | Example Value               | Notes                                                  |
|-----------------------|----------------------------------|-----------------------------|--------------------------------------------------------|
| IconId                | *IntProperty*                    | `302009`                    |                                                        |
| IconTextureName       | *StrProperty*                    | `S03/uT_UICN_S03_02_8`      | Path to texture, relative to `UI/Textures/USERICON/`   |
| IconRarity            | *Int8Property*                   | `2`                         | The rarity of the icon, in stars                       |
| NameTag               | *StrProperty*                    | `ICON_NAME_0250`            | The message tag for the name of the icon               |
| ExplanationTextTag    | *StrProperty*                    | `ICON_ACQUISITION_WAY_0250` | The message explaining how to unlock this icon         |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date) | `2021081007`                | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property*<br/>(WACCA Date) | `0`                         | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*                   | `False`                     | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*                    | `500`                       | How much additional WP to gain when getting this item? |

### JudgeInfoDetailPositionTable
Setting, show FAST/LATE indicator  (ON/OFF)

### JudgeInfoPositionTable
Setting, Judgement Info Position (0-3), 3 is OFF

### JudgeLineSettingTable
Setting, Offset (0-200), -10 to +10 in increments of .1, default 100

### JudgeParameterTable
Judgement timing table for each note type, unsure of how the values are used.
Contains fast/late timings for each judgement type and adjustments for front/rear
<H4>Structure</H4>

| Name                 | Type          | Example Value | Notes |
|----------------------|---------------|---------------|-------|
| MarvelousTimingFront | *IntProperty* | `3`           |       |
| MarvelousTimingRear  | *IntProperty* | `3`           |       |
| GreatTimingFront     | *IntProperty* | `5`           |       |
| GreatTimingRear      | *IntProperty* | `5`           |       |
| GoodTimingFront      | *IntProperty* | `6`           |       |
| GoodTimingRear       | *IntProperty* | `6`           |       |
| AdjustRateFront      | *IntProperty* | `100`         |       |
| AdjustRateRear       | *IntProperty* | `100`         |       |

#### Judgement Information
Listed here for quick reference, format is **Front** / **Rear**.

|             | Marvelous               | Great                    | Good                      | Adjust                      |
|-------------|-------------------------|--------------------------|---------------------------|-----------------------------|
| Touch       | **3**&nbsp;/&nbsp;**3** | **5**&nbsp;/&nbsp;**5**  | **6**&nbsp;/&nbsp;**6**   | **100**&nbsp;/&nbsp;**100** |
| Chain       | **4**&nbsp;/&nbsp;**4** | **4**&nbsp;/&nbsp;**4**  | **4**&nbsp;/&nbsp;**4**   | **20**&nbsp;/&nbsp;**100**  |
| Hold        | **3**&nbsp;/&nbsp;**3** | **5**&nbsp;/&nbsp;**5**  | **6**&nbsp;/&nbsp;**6**   | **100**&nbsp;/&nbsp;**100** |
| Hold End    | **7**&nbsp;/&nbsp;**7** | **7**&nbsp;/&nbsp;**7**  | **7**&nbsp;/&nbsp;**7**   | **100**&nbsp;/&nbsp;**100** |
| Snap Up     | **5**&nbsp;/&nbsp;**7** | **8**&nbsp;/&nbsp;**10** | **10**&nbsp;/&nbsp;**10** | **100**&nbsp;/&nbsp;**100** |
| Snap Down   | **7**&nbsp;/&nbsp;**5** | **10**&nbsp;/&nbsp;**8** | **10**&nbsp;/&nbsp;**10** | **100**&nbsp;/&nbsp;**100** |
| Slide Left  | **5**&nbsp;/&nbsp;**7** | **8**&nbsp;/&nbsp;**10** | **10**&nbsp;/&nbsp;**10** | **100**&nbsp;/&nbsp;**100** |
| Slide Right | **5**&nbsp;/&nbsp;**7** | **8**&nbsp;/&nbsp;**10** | **10**&nbsp;/&nbsp;**10** | **100**&nbsp;/&nbsp;**100** |

### KeyBeamEffectTable
Setting, Key Beam Effect (ON/OFF)

### LaunchDateTable
List of the launch dates of every major version of the game, not sure what it's used for, if at all.
<H4>Structure</H4>

| Name       | Type                             | Example Value | Notes |
|------------|----------------------------------|---------------|-------|
| LaunchDate | *Int64Property*<br/>(WACCA Date) | `2021081007`  |       |

### LevelUpTable
List of experience requirements for levels.
Lists starting level and required EXP for a level up. Only levels where it changes are defined.
<H4>Structure</H4>

| Name        | Type          | Example Value | Notes |
|-------------|---------------|---------------|-------|
| Level       | *IntProperty* | `50`          |       |
| RequiredExp | *IntProperty* | `800`         |       |

### LevelUpWaccaPointTable
Lists the WP reward for finishing each level. Seems to be the level the reward ends at, instead of where it starts at.
<H4>Structure</H4>

| Name       | Type          | Example Value | Notes |
|------------|---------------|---------------|-------|
| Level      | *IntProperty* | `9`           |       |
| WaccaPoint | *IntProperty* | `250`         |       |

### LimitationTimeTable
A list of all the UI timers used in the game, and how long their time limits are. Time limits bug out over 999.
<H4>Structure</H4>

| Name           | Type            | Example Value | Notes |
|----------------|-----------------|---------------|-------|
| LimitationTime | *FloatProperty* | `99`          |       |

### LoginRandomMessageTable
A list of randomized login messages.
<H4>Structure</H4>

| Name                       | Type            | Example Value         | Notes                                                      |
|----------------------------|-----------------|-----------------------|------------------------------------------------------------|
| MessageTag                 | *StrProperty*   | `WELCOME_NOR_MES_011` |                                                            |
| RandomMessageConditionType | *IntProperty*   | `2`                   | Types defined by *Enum&lt;ERandomMessageConditionType&gt;* |
| Value00                    | *Int64Property* | `50`                  |                                                            |
| Value01                    | *Int64Property* | `0`                   |                                                            |
| Priority                   | *IntProperty*   | `0`                   | Types defined by *Enum&lt;ERandomMessagePriorityType&gt;*  |

### MessageTagTable
Appears to be a list of message tag string replacements. Unused since Lily R, may however still be active. Lists a tag, a replacement string, and start/end times.
<H4>Structure</H4>

| Name           | Type                                  | Example Value    | Notes |
|----------------|---------------------------------------|------------------|-------|
| MessageTag     | *StrProperty*                         | `TITLE`          |       |
| ReplaceString  | *StrProperty*                         | `WACCA Lily R`   |       |
| AdaptStartTime | *Int64Property*<br/>(WACCA Date+Time) | `20210311070000` |       |
| AdaptEndTime   | *Int64Property*<br/>(WACCA Date+Time) | `20210810065959` |       |

### MirrorSettingTable
Setting, Mirror Notes (ON/OFF), mirrors notes across Y axis.

### MultiPlayPointTable
Appears to be a list of WP bonus multipliers for multiplayer games. Has 4 ranks? Not sure how this works.
<H4>Structure</H4>

| Name                             | Type            | Example Value | Notes |
|----------------------------------|-----------------|---------------|-------|
| MultiPlayVsPointBonusRateLevel01 | *FloatProperty* | `0.15`        |       |
| MultiPlayVsPointBonusRateLevel02 | *FloatProperty* | `0.15`        |       |
| MultiPlayVsPointBonusRateLevel03 | *FloatProperty* | `0.17`        |       |
| MultiPlayVsPointBonusRateLevel04 | *FloatProperty* | `0.17`        |       |
| MultiPlayVsPointBonusRateLevel05 | *FloatProperty* | `0.17`        |       |
| MultiPlayVsPointBonusRateLevel06 | *FloatProperty* | `0.2`         |       |
| MultiPlayVsPointBonusRateLevel07 | *FloatProperty* | `0.2`         |       |
| MultiPlayVsPointBonusRateLevel08 | *FloatProperty* | `0.2`         |       |
| MultiPlayVsPointBonusRateLevel09 | *FloatProperty* | `0.25`        |       |
| MultiPlayVsPointBonusRateLevel10 | *FloatProperty* | `0.25`        |       |
| MultiPlayVsPointBonusRateLevel11 | *FloatProperty* | `0.25`        |       |
| MultiPlayVsPointBonusRateLevel12 | *FloatProperty* | `0.3`         |       |
| MultiPlayVsPointBonusRateLevel13 | *FloatProperty* | `0.3`         |       |
| MultiPlayVsPointBonusRateLevel14 | *FloatProperty* | `0.35`        |       |
| MultiPlayVsPointBonusRateLevel15 | *FloatProperty* | `0.35`        |       |
| MultiPlayCoopPointBonusRate      | *FloatProperty* | `0.3`         |       |

### MultiRankInfoTable
Setting, Multiplayer Rank display (ON/OFF), controls the display of current multiplayer placement in-game.

### MusicParameterTable
List of all music selectable in the game. This is where you can add songwheel definitions.
This is a very dense table, will do a separate write-up about details later.
<H4>Structure</H4>

| Name                                  | Type             | Example Value                                           | Notes                                                                                                                |
|---------------------------------------|------------------|---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| UniqueID                              | *UInt32Property* | `1001`                                                  | Song ID                                                                                                              |
| MusicMessage                          | *StrProperty*    | `Bad Apple!! feat. nomico`                              | Song Name                                                                                                            |
| ArtistMessage                         | *StrProperty*    | `Masayoshi Minoshima`                                   | Artist Name                                                                                                          |
| CopyrightMessage                      | *StrProperty*    | `-`                                                     | Copyright message, unused in modern versions                                                                         |
| VersionNo                             | *UInt32Property* | `1`                                                     | Version the song came from, counting appends, so Reverse is 5. `0` if not shown in version select.                   |
| AssetDirectory                        | *StrProperty*    | `S01-001`                                               | Directory for the chart files, relative to `MusicData/`                                                              |
| MovieAssetName                        | *StrProperty*    | `mv_S01_001`                                            | Background Video for the chart, relative to `Movie/`, `-` for none                                                   |
| MovieAssetNameHard                    | *StrProperty*    | `null`                                                  | Background Video override for Hard, relative to `Movie/`, `null` if unused                                           |
| MovieAssetNameExpert                  | *StrProperty*    | `null`                                                  | Background Video override for Expert, relative to `Movie/`, `null` if unused                                         |
| MovieAssetNameInferno                 | *StrProperty*    | `null`                                                  | Background Video override for Inferno, relative to `Movie/`, `null` if unused                                        |
| JacketAssetName                       | *StrProperty*    | `S01/uT_J_S01_001`                                      | Jacket texture path                                                                                                  |
| Rubi                                  | *StrProperty*    | `ＢＡＤＡＰＰＬＥＦＥＡＴＮＯＭＩＣＯ`                                    | Used for title sort, should be fullwidth characters, ideally with no spaces                                          |
| bValidCulture_ja_JP                   | *BoolProperty*   | `True`                                                  | Is song available in JPN region?                                                                                     |
| bValidCulture_en_US                   | *BoolProperty*   | `True`                                                  | Is song available in USA region?                                                                                     |
| bValidCulture_zh_Hant_TW              | *BoolProperty*   | `True`                                                  | Is song available in TWN region?                                                                                     |
| bValidCulture_en_HK                   | *BoolProperty*   | `True`                                                  | Is song available in HKG region?                                                                                     |
| bValidCulture_en_SG                   | *BoolProperty*   | `True`                                                  | Is song available in SGP region?                                                                                     |
| bValidCulture_ko_KR                   | *BoolProperty*   | `True`                                                  | Is song available in KOR region?                                                                                     |
| bValidCulture_h_Hans_CN_Guest         | *BoolProperty*   | `False`                                                 | Unused in SDFE, is song available in CHN region for guests?                                                          |
| bValidCulture_h_Hans_CN_GeneralMember | *BoolProperty*   | `False`                                                 | Unused in SDFE, is song available in CHN region for members?                                                         |
| bValidCulture_h_Hans_CN_VipMember     | *BoolProperty*   | `False`                                                 | Unused in SDFE, is song available in CHN region for VIP members?                                                     |
| bValidCulture_Offline                 | *BoolProperty*   | `True`                                                  | Is song available offline?                                                                                           |
| bValidCulture_NoneActive              | *BoolProperty*   | `False`                                                 | Is song available when there's no region set? (This is typically not possible)                                       |
| bRecommend                            | *BoolProperty*   | `True`                                                  | If the song should be listed in the "Beginner Recommended" category                                                  |
| WaccaPointCost                        | *IntProperty*    | `1000`                                                  | Cost of unlocking the song, in WP, seems to be unused. Cost of song is set in [UnlockMusicTable](#unlockmusictable). |
| bCollaboration                        | *ByteProperty*   | `0`                                                     | ???                                                                                                                  |
| bWaccaOriginal                        | *ByteProperty*   | `0`                                                     | Might be used for conditions?                                                                                        |
| TrainingLevel                         | *ByteProperty*   | `3`                                                     | Unsure, seen values of 0-3                                                                                           |
| Reserved                              | *ByteProperty*   | `0`                                                     | Always `0`                                                                                                           |
| Bpm                                   | *StrProperty*    | `138`                                                   | The BPM string shown at song select, not validated                                                                   |
| HashTag                               | *StrProperty*    | `1001_WAC`                                              | Unused legacy feature from 1.x, most newer charts use `Nim_WAC`                                                      |
| NotesDesignerNormal                   | *StrProperty*    | `レッドアリス`                                                | Note Designer for Normal chart                                                                                       |
| NotesDesignerHard                     | *StrProperty*    | `レッドアリス`                                                | Note Designer for Hard chart                                                                                         |
| NotesDesignerExpert                   | *StrProperty*    | `レッドアリス`                                                | Note Designer for Expert chart                                                                                       |
| NotesDesignerInferno                  | *StrProperty*    | `-`                                                     | Note Designer for Inferno chart                                                                                      |
| DifficultyNormalLv                    | *FloatProperty*  | `1`                                                     | Difficulty of Normal chart                                                                                           |
| DifficultyHardLv                      | *FloatProperty*  | `5.5`                                                   | Difficulty of Hard chart                                                                                             |
| DifficultyExtremeLv                   | *FloatProperty*  | `9.3`                                                   | Difficulty of Expert chart, uses old name for Expert                                                                 |
| DifficultyInfernoLv                   | *FloatProperty*  | `0`                                                     | Difficulty of Inferno chart, `0` if no inferno difficulty                                                            |
| ClearNormaRateNormal                  | *FloatProperty*  | `0.45`                                                  | Percentage of clear gauge completion to clear the Normal chart, default `0.45`                                       |
| ClearNormaRateHard                    | *FloatProperty*  | `0.55`                                                  | Percentage of clear gauge completion to clear the Hard chart, default `0.55`                                         |
| ClearNormaRateExtreme                 | *FloatProperty*  | `0.8`                                                   | Percentage of clear gauge completion to clear the Expert chart, Uses old name for Expert, default `0.8`              |
| ClearNormaRateInferno                 | *FloatProperty*  | `0.8`                                                   | Percentage of clear gauge completion to clear the Inferno chart, default `0.8`                                       |
| PreviewBeginTime                      | *FloatProperty*  | `29.2`                                                  | Where to start the song preview, in seconds                                                                          |
| PreviewSeconds                        | *FloatProperty*  | `10`                                                    | How long to play the song preview for, in seconds                                                                    |
| ScoreGenre                            | *IntProperty*    | `8`                                                     | Types defined by *Enum&lt;EScoreGenre&gt;*                                                                           |
| MusicTagForUnlock0                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock1                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock2                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock3                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock4                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock5                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock6                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock7                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock8                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| MusicTagForUnlock9                    | *IntProperty*    | `0`                                                     | Music tag for conditions, types defined by *Enum&lt;EMusicTagForUnlock&gt;*                                          |
| WorkBuffer                            | *UInt64Property* | `0`                                                     | Unsure?                                                                                                              |
| AssetFullPath                         | *StrProperty*    | `D:/project/Mercury/Mercury/Content//MusicData/S01-001` | Not sure if this is used, but it seems like an internal path to the chart files, maybe for the official editor?      |

### MusicSelectOptionBeginner
Setting, List of option presets displayed for beginners.

### MusicSelectOptionDesignSetting
Setting, List that defines design options.

### MusicSelectOptionDisplayInfoSetting
Setting, List that defines display options.

### MusicSelectOptionGameSetting
Setting, List that defines game options.

### MusicSelectOptionNoteColorTable
Setting, List of note color options. Maps parameter to [NotesColorTable](#notescolortable) (note color ID).

### MusicSelectOptionSoundSetting
Setting, List of sound options.

### MusicSelectOptionTop
Setting, List of option menus.

### MyRoomTopMenu
Setting, List of My Room options.

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
<H4>Structure</H4>

| Name                            | Type                             | Example Value                 | Notes                                                                |
|---------------------------------|----------------------------------|-------------------------------|----------------------------------------------------------------------|
| NavigateCharacterID             | *IntProperty*                    | `210001`                      |                                                                      |
| bValidCulture_ja_JP             | *BoolProperty*                   | `True`                        | Is navigator available in JPN region?                                |
| bValidCulture_en_US             | *BoolProperty*                   | `True`                        | Is navigator available in USA region?                                |
| bValidCulture_zh_Hant_TW        | *BoolProperty*                   | `True`                        | Is navigator available in TWN region?                                |
| bValidCulture_en_HK             | *BoolProperty*                   | `True`                        | Is navigator available in HKG region?                                |
| bValidCulture_en_SG             | *BoolProperty*                   | `True`                        | Is navigator available in SGP region?                                |
| bValidCulture_ko_KR             | *BoolProperty*                   | `True`                        | Is navigator available in KOR region?                                |
| bValidCulture_h_Hans_CN         | *BoolProperty*                   | `True`                        | Unused in SDFE, is navigator available in CHN region?                |
| bValidCulture_Offline           | *BoolProperty*                   | `True`                        | Is navigator available offline?                                      |
| CharaType                       | *Int8Property*                   | `0`                           | Types defined in *Enum&lt;ECharacterType&rt;*                        |
| isOriginalCharacter             | *BoolProperty*                   | `True`                        | If this character is a WACCA original character                      |
| DefaultTextureName              | *StrProperty*                    | `BP_Chara000_00`              | Default texture, relative to `UI/Character`                          |
| StageupTextureName              | *StrProperty*                    | `BP_Chara000_01`              | Stage up texture, relative to `UI/Character`                         |
| MonitorTextureName              | *StrProperty*                    | `chara000/uT_Chara000_MR`     | Monitor texture prefix, relative to `UI/Textures/CHARACTER`          |
| SeeYouNormalTextureName         | *StrProperty*                    | `chara000/uT_Chara000_SY000`  | End card texture name, relative to `UI/Textures/CHARACTER`           |
| SeeYouRankInTextureName         | *StrProperty*                    | `chara000/uT_Chara000_SY001`  | "Rank In" end card texture name, relative to `UI/Textures/CHARACTER` |
| SeeYouStageupTextureName        | *StrProperty*                    | `chara000/uT_Chara000_SY002`  | Stage Up end card texture name, relative to `UI/Textures/CHARACTER`  |
| VIPJoinedTextureName            | *StrProperty*                    | `chara000/uT_Chara000_VIP000` | VIP joined texture, relative to `UI/Textures/CHARACTER`              |
| VIPJoinedBackGroundMaterialName | *StrProperty*                    | `uM_VIP000`                   | VIP joined background material, relative to `UI/Material/VIP`        |
| VIPJoinedLightMaterialName      | *StrProperty*                    | `uM_VIPfront000`              | VIP joined "light material", relative to `UI/Material/VIP`           |
| VIPJoinedFrontMaterialName      | *StrProperty*                    | `uM_VIPfront000`              | VIP joined "front material", relative to `UI/Material/VIP`           |
| VoiceActivateStartTime          | *Int64Property*<br/>(WACCA Date) | `0`                           | When to start using the voice lines for the navigator                |
| VoiceActivateEndTime            | *Int64Property*<br/>(WACCA Date) | `0`                           | When to stop using the voice lines for the navigator                 |
| NameTag                         | *StrProperty*                    | `NAVIGATE_CHARACTER_NAME_000` | Navigator name tag                                                   |
| ExplanationTextTag              | *StrProperty*                    | `NAVIGATE_CHARACTER_MES_000`  | Navigator description tag                                            |
| ItemActivateStartTime           | *Int64Property*<br/>(WACCA Date) | `0`                           | When to enable this item for use                                     |
| ItemActivateEndTime             | *Int64Property*<br/>(WACCA Date) | `0`                           | When to disable this item for use                                    |
| bIsInitItem                     | *BoolProperty*                   | `True`                        | If the item is part of a player's initial inventory                  |
| GainWaccaPoint                  | *IntProperty*                    | `0`                           | How much additional WP to gain when getting this item?               |

### NaviPanelTable
List of UI button visual appearances.
Lists button text tag A and B, help text tag (unused since WACCA S iirc), text sizes for each tag, button icon type, texture size, texture position, button widget type, and button widget color.
<H4>Structure</H4>

| Name              | Type           | Example Value          | Note |
|-------------------|----------------|------------------------|------|
| ButtonTextTagA    | *StrProperty*  | `NAVI_MES_CONFIRM_END` |      |
| TextFontSizeA     | *IntProperty*  | `20`                   |      |
| ButtonTextTagB    | *StrProperty*  | `-`                    |      |
| TextFontSizeB     | *IntProperty*  | `10`                   |      |
| HelpTextTag       | *StrProperty*  | `-`                    |      |
| ButtonIconType    | *IntProperty*  | `20`                   |      |
| TextureSize       | *IntProperty*  | `30`                   |      |
| TexturePosition   | *Int8Property* | `1`                    |      |
| ButtonWidgetType  | *IntProperty*  | `2`                    |      |
| ButtonWidgetColor | *IntProperty*  | `3`                    |      |

### NormaTable
List of gauge (health) points gained/lost for each judgement on each type of note. Referred to by the old terms SuperJust/Just/Good/Miss.
<H4>Structure</H4>

| Name                | Type          | Example Value | Note                                                         |
|---------------------|---------------|---------------|--------------------------------------------------------------|
| NormaGaugeSuperJust | *IntProperty* | `10`          | Health to add when hitting the note with Marvelous judgement |
| NormaGaugeJust      | *IntProperty* | `7`           | Health to add when hitting the note with Great judgement     |
| NormaGaugeGood      | *IntProperty* | `4`           | Health to add when hitting the note with Good judgement      |
| NormaGaugeMiss      | *IntProperty* | `-5`          | Health to add when hitting the note with Miss judgement      |

### NoteDesignTable
Setting, Mask (0-4), used to control the background dimming.

### NotesColorTable
List of note color definitions, used by [MusicSelectOptionNoteColorTable](#musicselectoptionnotecolortable).
Lists note color ID, note color type, color parameter name, color name tag, if the color is a support color, and the hold color ID
<H4>Structure</H4>

| Name               | Type           | Example Value              | Note                                             |
|--------------------|----------------|----------------------------|--------------------------------------------------|
| NotesColorId       | *IntProperty*  | `5`                        |                                                  |
| NotesColorType     | *IntProperty*  | `5`                        | Types defined by *Enum&lt;ENotesColorType&rt;*   |
| ColorParameterName | *StrProperty*  | `NormalNote_Color1`        |                                                  |
| ColorNameTag       | *StrProperty*  | `NOTE_COLOR_PARAM_NAME_00` | Color name tag                                   |
| bIsSupportColor    | *BoolProperty* | `False`                    | If the color is outside of the default color set |
| HoldColorNumber    | *IntProperty*  | `0`                        | Hold color ID is different than note color ID    |

### PlayerLevelInfoTable
Setting, Player Level Info (ON/OFF), toggles the display of the player's level.

### RateInfoTable
Setting, Rate Info (ON/OFF), toggles the display of the player's rate.

### RhythmGameAppearanceTable
Miscellaneous settings regarding in-game effects.
Lists "required combo for effect", song pass effect wait time, "change guide lane appearance combo border",
the brightness/gradation of the mask in songs with and without a video, hold note division length,
and hold note division lane width.
<H4>Structure</H4>

| Name                                    | Type             | Example Value | Note                                                   |
|-----------------------------------------|------------------|---------------|--------------------------------------------------------|
| RequiredComboNumForEffect               | *IntProperty*    | `200`         | What combo number to change the gameplay background at |
| NormaPassEffectWaitTime                 | *FloatProperty*  | `10.0`        | Delay for clear gauge pass effect                      |
| ChangeGuideLaneAppearanceComboBorder    | *UInt32Property* | `200`         |                                                        |
| GuideLaneBrightnessParamAlphaNormal     | *IntProperty*    | `600`         |                                                        |
| GuideLaneBrightnessParamAlphaMovie      | *IntProperty*    | `290`         | Alpha for mask when BG movie is played                 |
| GuideLaneBrightnessParamGradationNormal | *IntProperty*    | `3`           |                                                        |
| GuideLaneBrightnessParamGradationMovie  | *IntProperty*    | `6`           |                                                        |
| HoldNoteDivisionLength                  | *FloatProperty*  | `2.0`         |                                                        |
| HoldNoteDivisionLaneWidth               | *ByteProperty*   | `2`           |                                                        |

### RhythmGamePosTable
Defines the XYZ coordinates of where the notes appear, as well as effects.
<H4>Structure</H4>

| Name | Type            | Example Value | Notes |
|------|-----------------|---------------|-------|
| PosX | *FloatProperty* | `0.0`         |       |
| PosY | *FloatProperty* | `-600.0`      |       |
| PosZ | *FloatProperty* | `0.0`         |       |

### RhythmGameRuleTable
Defines "protect involve rock frame number", default note speed, amount of misses considered missless,
"basic experience", and "adapted start dash level".
<H4>Structure</H4>

| Name                       | Type             | Example Value | Notes               |
|----------------------------|------------------|---------------|---------------------|
| ProtectInvolveRockFrameNum | *IntProperty*    | `-1`          |                     |
| NoteSpeedRate              | *FloatProperty*  | `2.0`         | default note speed? |
| FlawlesslyMissCount        | *UInt32Property* | `5`           |                     |
| BasicExp                   | *IntProperty*    | `25`          |                     |
| AdaptedStartDashLevel      | *IntProperty*    | `4`           |                     |

### ScoreInfoTable
Setting, Score Info (ON/OFF)

### SeeYouRandomMessageTable
Same as [LoginRandomMessageTable](#loginrandommessagetable), except for endcards
<H4>Structure</H4>

| Name                       | Type            | Example Value         | Notes                                                      |
|----------------------------|-----------------|-----------------------|------------------------------------------------------------|
| MessageTag                 | *StrProperty*   | `SEE_YOU_NOR_MES_000` |                                                            |
| RandomMessageConditionType | *IntProperty*   | `0`                   | Types defined by *Enum&lt;ERandomMessageConditionType&gt;* |
| Value00                    | *Int64Property* | `0`                   |                                                            |
| Value01                    | *Int64Property* | `0`                   |                                                            |
| Priority                   | *IntProperty*   | `0`                   | Types defined by *Enum&lt;ERandomMessagePriorityType&gt;*  |

### SESetTable
List of every sound effect set. Theoretically possible to define custom ones if you can inject audio for them.
<H4>Structure</H4>

| Name                  | Type                             | Example Value            | Notes                                                  |
|-----------------------|----------------------------------|--------------------------|--------------------------------------------------------|
| SESetID               | *IntProperty*                    | `105001`                 |                                                        |
| MarvelousSEName       | *StrProperty*                    | `MER_SE_SYS_186`         | Cue name for Touch sound effect                        |
| GoodSEName            | *StrProperty*                    | `MER_SE_SYS_185`         | Cue name for Touch sound effect for Good judgements    |
| SlideMarvelousSEName  | *StrProperty*                    | `MER_SE_SYS_188`         | Cue name for Swipe sound effect                        |
| SlideGoodSEName       | *StrProperty*                    | `MER_SE_SYS_187`         | Cue name for Swipe sound effect for Good judgements    |
| SnapMarvelousSEName   | *StrProperty*                    | `MER_SE_SYS_194`         | Cue name for Snap sound effect                         |
| SnapGoodSEName        | *StrProperty*                    | `MER_SE_SYS_193`         | Cue name for Snap sound effect for Good judgements     |
| HoldMarvelousName     | *StrProperty*                    | `MER_SE_SYS_190`         | Cue name for Hold Start sound effect                   |
| HoldSEName            | *StrProperty*                    | `MER_SE_SYS_189`         | Cue name for looped Hold sound effect                  |
| ReHoldSEName          | *StrProperty*                    | `MER_SE_SYS_191`         | Cue name for looped Hold sound effect after dropping   |
| ChainSeName           | *StrProperty*                    | `MER_SE_SYS_192`         | Cue name for Chain sound effect                        |
| NameTag               | *StrProperty*                    | `ATTACK_SE_SET_NAME_001` | Sound effect set name tag                              |
| ExplanationTextTag    | *StrProperty*                    | `ATTACK_SE_SET_MES_001`  | Sound effect set description tag                       |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date) | `0`                      | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property*<br/>(WACCA Date) | `0`                      | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*                   | `True`                   | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*                    | `0`                      | How much additional WP to gain when getting this item? |

### SkillTable
list of skills, seems to be unused, translation keys no longer exist, and IDs only refer to 1.xx.xx
<H4>Structure</H4>

| Name                  | Type            | Example Value                | Notes                                                  |
|-----------------------|-----------------|------------------------------|--------------------------------------------------------|
| SkillID               | *IntProperty*   | `108001`                     |                                                        |
| SkillLevel            | *IntProperty*   | `1`                          |                                                        |
| SkillType             | *IntProperty*   | `0`                          |                                                        |
| NormaDownRate         | *FloatProperty* | `0.8999999761581421`         |                                                        |
| NormaUpRate           | *FloatProperty* | `-1.0`                       |                                                        |
| WaccaPointUpRate      | *FloatProperty* | `-1.0`                       |                                                        |
| TimeLimitUpRate       | *FloatProperty* | `-1.0`                       |                                                        |
| NameTag               | *StrProperty*   | `SKILL_NAME_0001`            | Skill name tag                                         |
| ExplanationTextTag    | *StrProperty*   | `SKILL_ACQUISITION_WAY_0001` | Skill description tag                                  |
| ItemActivateStartTime | *Int64Property* | `0`                          | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property* | `0`                          | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*  | `False`                      | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*   | `0`                          | How much additional WP to gain when getting this item? |

### SlideBonusTimingTable
A list of timing leniency windows(???) for swipes (slides) based on the BPM, measured in beats.
<H4>Structure</H4>

| Name       | Type            | Example Value | Notes                                    |
|------------|-----------------|---------------|------------------------------------------|
| BpmBorder  | *FloatProperty* | `75.0`        | Upper bounds of the BPM timing condition |
| BeatTiming | *IntProperty*   | `1`           |                                          |

#### Table Data
| BpmBorder | BeatTiming |
|-----------|------------|
| 75        | 1          |
| 100       | 1          |
| 125       | 2          |
| 150       | 2          |
| 175       | 2          |
| 200       | 4          |
| 225       | 4          |
| 250       | 4          |
| 275       | 4          |
| 9999      | 4          |

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
<H4>Structure</H4>

| Name                      | Type                        | Example Value                      | Notes                                                                              |
|---------------------------|-----------------------------|------------------------------------|------------------------------------------------------------------------------------|
| StageId                   | *IntProperty*               | `3010`                             |                                                                                    |
| StageClass                | *IntProperty*               | `10`                               | Stage class, reported to the server                                                |
| EventFlg                  | *IntProperty*               | `0`                                | Set if the stage is for an event, not a base stage                                 |
| TitleNameTag              | *StrProperty*               | `STAGE_UP_TITLE_10`                | Stage name tag                                                                     |
| BackGroundMaterialPath    | *StrProperty*               | `RTrate00/uM_RTrateB000`           | Stage material, used by stage select screen for icon background                    |
| MusicUniqueIDArray        | *Array&lt;IntProperty&gt;*  | `[2248, 2211, 2220]`               | An array of the 3 song IDs that are in the stage                                   |
| DifficultyArray           | *Array&lt;StrProperty&gt;*  | `["EXPERT", "EXPERT", "EXPERT"]`   | The difficulty of the songs in the stage                                           |
| bSecretMusicFlgArray      | *Array&lt;BoolProperty&gt;* | `[False, False, True]`             | Sets if a song is hidden before playing it                                         |
| ConditionJudge            | *StrProperty*               | `GREAT`                            | The highest judgement that you start taking damage at                              |
| ConditionLife             | *IntProperty*               | `90`                               | The amount of life points you are given for the entire stage                       |
| ConditionRecoveryLife     | *IntProperty*               | `15`                               | How much life points to recover after clearing each song, up to start amount       |
| BgChangeRate              | *FloatProperty*             | `0.2`                              | The rate at which the background will change as you lose life                      |
| SilverClearLife           | *IntProperty*               | `45`                               | The minimum amount of life points required to clear the stage with a silver badge  |
| GoldClearLife             | *IntProperty*               | `72`                               | The minimum amount of life points required to clear the stage with a gold badge    |
| RewordWaccaPoint          | *IntProperty*               | `1000`                             | Not a typo, amount of WP reward to give for clearing the stage                     |
| RewardItemArray           | *Array&lt;IntProperty&gt;*  | `[301015, 301016, 304060, 102087]` | An array of items received when clearing the stage                                 |
| RewardInfernoMusicIdArray | *Array&lt;IntProperty&gt;*  | `[1057]`                           | An array of song IDs to unlock infernos for                                        |
| WaccaPointCost            | *IntProperty*               | `5500`                             | Cost for playing the stage??? idk bro                                              |
| StageType                 | *IntProperty*               | `10`                               | The stage icon to use for the list and the clear screen, event stages should use 0 |
| ClearAnimationType        | *IntProperty*               | `1`                                | Types defined by *Enum&lt;EStageClearAnimationType&gt;*                            |

### StoreMenu
List of items available to buy from the Shop.
<H4>Structure</H4>

| Name                   | Type                             | Example Value                        | Notes                                                                      |
|------------------------|----------------------------------|--------------------------------------|----------------------------------------------------------------------------|
| GoodsId                | *IntProperty*                    | `2001`                               |                                                                            |
| ItemCategory           | *IntProperty*                    | `13`                                 | Network item type                                                          |
| ItemId                 | *IntProperty*                    | `109001`                             | Item ID                                                                    |
| ItemNum                | *IntProperty*                    | `1`                                  | Quantity of item to give                                                   |
| BonusItemCategory      | *IntProperty*                    | `0`                                  | [see above]                                                                |
| BonusItemId            | *IntProperty*                    | `0`                                  | [see above]                                                                |
| BonusItemNum           | *IntProperty*                    | `0`                                  | [see above]                                                                |
| PayableType            | *Int8Property*                   | `0`                                  | 0 = credits, 1 = WP                                                        |
| Price                  | *IntProperty*                    | `2`                                  | Price of the store item                                                    |
| StoreMenu              | *StrProperty*                    | `STORE_MENU_BOOST_BADGE_S`           | Store entry title tag                                                      |
| StoreMenuDescription   | *StrProperty*                    | `STORE_MENU_BOOST_BADGE_S_DES`       | Store entry description tag                                                |
| StoreMenuCharaMessage  | *StrProperty*                    | `STORE_MENU_BOOST_BADGE_S_CHARA_DES` | Store entry character description tag(??)                                  |
| ItemTexture            | *StrProperty*                    | `uT_CH_SHicn_01`                     | Texture name to use for store entry icon, relative to `UI/Textures/CHANGE` |
| SaleStartDate          | *Int64Property*<br/>(WACCA Date) | `0`                                  |                                                                            |
| SaleEndDate            | *Int64Property*<br/>(WACCA Date) | `0`                                  |                                                                            |
| ExclusionTargetGoodsId | *Int64Property*                  | `0`                                  | Not sure what this does, requires more research                            |

### SugorokuStageParameterTable
Gate page definitions, every page for every gate is defined here.
<H4>Structure</H4>

| Name            | Type                             | Example Value             | Notes                                                                                       |
|-----------------|----------------------------------|---------------------------|---------------------------------------------------------------------------------------------|
| SugorokuID      | *Int16Property*                  | `7`                       | Gate ID, must match the ID in [SugorokuUniqueParameterTable](#sugorokuuniqueparametertable) |
| PageNumber      | *Int16Property*                  | `11`                      | Gate page number                                                                            |
| TargetPoint     | *Array&lt;IntProperty&gt;*       | `[2100, 2900]`            | How many gate points to get to the next reward                                              |
| GetItemVariety  | *Array&lt;StrProperty&gt;*       | `["WP", "MUSIC"]`         | The item type of the reward                                                                 |
| GetItemValue    | *Array&lt;IntProperty&gt;*       | `[1500, 2017]`            | The item value of the reward (item ID, amount, etc)                                         |
| TaskMusic01     | *Array&lt;IntProperty&gt;*       | `[1009, 1013, 1086, ...]` | An array of song IDs that will grant a Lv.1 gate boost when played                          |
| TaskGenre01     | *IntProperty*                    | `-1`                      | The song genre that will grant a Lv.1 gate boost(???)                                       |
| TaskMusic02     | *Array&lt;IntProperty&gt;*       | `[]`                      | An array of song IDs that will grant a Lv.2 gate boost when played                          |
| TaskGenre02     | *IntProperty*                    | `-1`                      | The song genre that will grant a Lv.2 gate boost(???)                                       |
| TaskMusic03     | *Array&lt;IntProperty&gt;*       | `[0]`                     | An array of song IDs that will grant a Lv.3 gate boost when played                          |
| TaskGenre03     | *IntProperty*                    | `-1`                      | The song genre that will grant a Lv.3 gate boost(???)                                       |
| MissionMusicID  | *IntProperty*                    | `2017`                    | The mission song at the end of the gate page, 0 for no mission song                         |
| Condition       | *IntProperty*                    | `1`                       |                                                                                             |
| Difficulty      | *IntProperty*                    | `1`                       | Minimum difficulty to clear the mission                                                     |
| ClearRate       | *IntProperty*                    | `0`                       | Minimum letter grade to clear the mission(??)                                               |
| RewardGatePoint | *IntProperty*                    | `350`                     | Points to apply to the next gate page when completing the mission(??)                       |
| EasingDay       | *Int64Property*<br/>(WACCA Date) | `2020121707`              | A date for something to happen?                                                             |

### SugorokuUniqueParameterTable
List of Gates. 
<H4>Structure</H4>

| Name                      | Type            | Example Value            | Notes                                                                    |
|---------------------------|-----------------|--------------------------|--------------------------------------------------------------------------|
| SugorokuID                | *Int16Property* | `7`                      | Gate ID                                                                  |
| SugorokuStageName         | *StrProperty*   | `Sugoroku_Name_006`      | Gate name tag                                                            |
| SugorokuSelectCenterImage | *StrProperty*   | `Material/Gate/uM_SR003` | Material name for the center image on the gate select screen             |
| SugorokuCenterImage       | *StrProperty*   | `Material/Gate/uM_SR003` | Material name for the center image                                       |
| HasLoopPage               | *BoolProperty*  | `True`                   | Sets if this is an endless gate, will loop the last defined page forever |
| EndContentsStartUserLevel | *IntProperty*   | `1`                      | Not sure, seen this set to 1 and 5                                       |
| FirstPlayBonus            | *Int8Property*  | `100`                    | Gate point bonus for first play of the day(??)                           |
| BaseScoreNormal           | *FloatProperty* | `1.0`                    | Gate point multiplier for normal user                                    |
| BaseScoreVip              | *FloatProperty* | `1.0`                    | Gate point multiplier for VIP user                                       |
| MisslessBonus             | *Int16Property* | `10`                     | Gate point bonus for missless judgement on a song                        |
| FullComboBonus            | *Int16Property* | `10`                     | Gate point bonus for full combo judgement on a song                      |
| MultiBonus                | *FloatProperty* | `0.2`                    | Gate point bonus multiplier for multiplayer                              |
| TaskMusicBonus01          | *FloatProperty* | `0.1`                    | Gate point bonus mulitplier for Lv.1 gate boost                          |
| TaskMusicBonus02          | *FloatProperty* | `0.5`                    | Gate point bonus mulitplier for Lv.2 gate boost                          |
| TaskMusicBonus03          | *FloatProperty* | `1.0`                    | Gate point bonus mulitplier for Lv.3 gate boost                          |
| Priority                  | *IntProperty*   | `6`                      | The priority of showing a gate in the list of gates to choose            |

### TapBonusTimingTable
A list of timing leniency windows(???) for touch notes based on the BPM, measured in beats.
<H4>Structure</H4>

| Name       | Type            | Example Value | Notes |
|------------|-----------------|---------------|-------|
| BpmBorder  | *FloatProperty* | `75.0`        |       |
| BeatTiming | *IntProperty*   | `1`           |       |

#### Table Data
| BpmBorder | BeatTiming |
|-----------|------------|
| 75        | 1          |
| 100       | 1          |
| 125       | 1          |
| 150       | 1          |
| 175       | 1          |
| 200       | 2          |
| 225       | 2          |
| 250       | 2          |
| 275       | 2          |
| 9999      | 2          |

### TicketItemTable
A list of ticket items available in the game.
<H4>Structure</H4>

| Name                  | Type                             | Example Value             | Notes                                                  |
|-----------------------|----------------------------------|---------------------------|--------------------------------------------------------|
| TicketId              | *IntProperty*                    | `206002`                  |                                                        |
| TicketType            | *UInt32Property*                 | `0`                       | Seems unused, all tickets in the game use 0            |
| IconTexturePath       | *StrProperty*                    | `CHANGE/uT_CH_CMicn_ex22` | Texture name of icon for ticket?                       |
| MenuIconTexturePath   | *StrProperty*                    | `CHANGE/uT_CH_SHicn_07`   | Texture name of icon used in item use menu             |
| MaxPossessionNum      | *IntProperty*                    | `-1`                      | Maximum amount of tickets that can be owned            |
| isExpertOpen          | *BoolProperty*                   | `False`                   | Set if ticket causes all experts to be playable        |
| AddPlayMusicNum       | *IntProperty*                    | `1`                       | Number of additional song plays this ticket grant      |
| ItemUseSceneFlag      | *BoolProperty*                   | `True`                    | Set if ticket is usable from the item use menu         |
| NameTag               | *StrProperty*                    | `TICKET_ITEM_NAME_001`    | Ticket name tag                                        |
| ExplanationTextTag    | *StrProperty*                    | `TICKET_ITEM_MES_001`     | Ticket description tag                                 |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date) | `0`                       | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property*<br/>(WACCA Date) | `0`                       | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*                   | `False`                   | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*                    | `0`                       | How much additional WP to gain when getting this item? |


### TotalResultItemJudgementTable
List of items that can be granted based on conditions defined in [ConditionTable](#conditiontable) after playing a song.
<H4>Structure</H4>

| Name                      | Type                             | Example Value   | Notes                                            |
|---------------------------|----------------------------------|-----------------|--------------------------------------------------|
| ItemId                    | *IntProperty*                    | `104004`        | The item ID to grant when the conditions are met |
| ConditionGetableStartTime | *Int64Property*<br/>(WACCA Date) | `0`             |                                                  |
| ConditionGetableEndTime   | *Int64Property*<br/>(WACCA Date) | `0`             |                                                  |
| ConditionKeys             | *Array&lt;StrProperty&gt;*       | `['040230101']` | An array of condition IDs listed as strings      |

### TotalResultRandomItemTable
List of random drop conditions after playing a song?
<H4>Structure</H4>

| Name                 | Type          | Example Value | Notes                |
|----------------------|---------------|---------------|----------------------|
| ItemId               | *IntProperty* | `102115`      | The item ID to grant |
| HitRate              | *IntProperty* | `2135`        |                      |
| SubstituteWaccaPoint | *IntProperty* | `3000`        |                      |

### TouchEffectShootTable
Setting, Touch Effect Shoot (ON/OFF)

### TouchEffectTable
List of touch effects.
<H4>Structure</H4>

| Name                        | Type                             | Example Value                       | Notes                                                  |
|-----------------------------|----------------------------------|-------------------------------------|--------------------------------------------------------|
| TouchEffectId               | *IntProperty*                    | `312002`                            |                                                        |
| MarvelousPopEffectName      | *StrProperty*                    | `tap_1/vo_tap001_03`                | Particle to use for Marvelous judgement                |
| GreatPopEffectName          | *StrProperty*                    | `tap_1/vo_tap001_05`                | Particle to use for Great judgement                    |
| GoodEffectName              | *StrProperty*                    | `tap_0/vo_tap000_00`                | Particle to use for Good judgement                     |
| MissEffectName              | *StrProperty*                    | `tap_0/vo_miss000_00`               | Particle to use for Miss judgement                     |
| BonusMarvelousPopEffectName | *StrProperty*                    | `tap_0/vo_btap000_03`               | Particle to use for Marvelous judgement on bonus notes |
| BonusGreatPopEffectName     | *StrProperty*                    | `tap_0/vo_btap000_05`               | Particle to use for Great judgement on bonus notes     |
| MarvelousShootEffectName    | *StrProperty*                    | `tap_0/vo_tap000_04`                | Shoot particle effect for Marvelous judgement          |
| GreatShootEffectName        | *StrProperty*                    | `tap_0/vo_tap000_06`                | Shoot particle effect for Great judgement              |
| HoldEffectName              | *StrProperty*                    | `tap_0/vo_hold000_00_lp`            | Particle to use for hold notes                         |
| ReHoldEffectName            | *StrProperty*                    | `tap_0/vo_hold000_01_lp`            | Particle to use for hold notes that were dropped       |
| HoldInputEffectName         | *StrProperty*                    | `tap_0/vo_hold000_02_lp`            | Particle to use for hold starts(???)                   |
| OptionSettingTexture        | *StrProperty*                    | `uT_KZ_86`                          | Texture name of icon to show in settings               |
| NameTag                     | *StrProperty*                    | `TOUCH_EFFECT_NAME_0002`            | Touch effect name tag                                  |
| ExplanationTextTag          | *StrProperty*                    | `TOUCH_EFFECT_ACQUISITION_WAY_0002` | Touch effect description tag                           |
| ItemActivateStartTime       | *Int64Property*<br/>(WACCA Date) | `0`                                 | When to enable this item for use                       |
| ItemActivateEndTime         | *Int64Property*<br/>(WACCA Date) | `0`                                 | When to disable this item for use                      |
| bIsInitItem                 | *BoolProperty*                   | `True`                              | If the item is part of a player's initial inventory    |
| GainWaccaPoint              | *IntProperty*                    | `0`                                 | How much additional WP to gain when getting this item? |

### TouchNoteVolumeTable
Setting, Touch Note volume, same values as [BGMVolumeTable](#bgmvolumetable)

### TouchPanelSymbolColorTable
List of console colors. It is possible to define custom console colors, however it is somewhat involved.
<H4>Structure</H4>

| Name                  | Type                              | Example Value                       | Notes                                                      |
|-----------------------|-----------------------------------|-------------------------------------|------------------------------------------------------------|
| SymbolColorId         | *IntProperty*                     | `103001`                            |                                                            |
| SymbolColorFileName   | *StrProperty*                     | `SymbolColor00/S01/uMPC_SC_S01_000` | The definition of the colors to use for this console color |
| NameTag               | *StrProperty*                     | `SYMBOL_COLOR_NAME_001`             | Console color name tag                                     |
| ExplanationTextTag    | *StrProperty*                     | `SYMBOL_COLOR_ACQUISITION_WAY_0001` | Console color description tag                              |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date)  | `0`                                 | When to enable this item for use                           |
| ItemActivateEndTime   |  *Int64Property*<br/>(WACCA Date) | `0`                                 | When to disable this item for use                          |
| bIsInitItem           | *BoolProperty*                    | `True`                              | If the item is part of a player's initial inventory        |
| GainWaccaPoint        | *IntProperty*                     | `0`                                 | How much additional WP to gain when getting this item?     |

#### SymbolColor Value Names
| Name              | Description                                        |
|-------------------|----------------------------------------------------|
| Color1_Background | UI Background color, shown where there is no mask  |
| Color2_Guide      | UI Guide color, shown where there is mask          |
| Color3_Judge      | UI Judge color, shown where notes have been hit    |
| Console1_B        | LED Background color, shown where there is no mask |
| Console2_G        | LED Guide color, shown where there is mask         |
| Console3_J        | LED Judge color, shown where notes have been hit   |

### TrophyTable
List of trophies.
<H4>Structure</H4>

| Name                  | Type                             | Example Value | Notes                                                  |
|-----------------------|----------------------------------|---------------|--------------------------------------------------------|
| TrophyId              | *IntProperty*                    | `101001`      |                                                        |
| TrophyRarity          | *IntProperty*                    | `3`           | Rarity level in stars                                  |
| TrophyCategory        | *IntProperty*                    | `1`           | Types defined in *Enum&lt;ETrophyCategoryType&gt;*     |
| ImplementationSeason  | *Int8Property*                   | `1`           | The season this trophy is from                         |
| NameTag               | *StrProperty*                    | `初心者脱出！`      | Trophy name                                            |
| ExplanationTextTag    | *StrProperty*                    | `TEXT("")`    | Trophy description (unused)                            |
| ItemActivateStartTime | *Int64Property*<br/>(WACCA Date) | `0`           | When to enable this item for use                       |
| ItemActivateEndTime   | *Int64Property*<br/>(WACCA Date) | `0`           | When to disable this item for use                      |
| bIsInitItem           | *BoolProperty*                   | `False`       | If the item is part of a player's initial inventory    |
| GainWaccaPoint        | *IntProperty*                    | `0`           | How much additional WP to gain when getting this item? |

### UnlockInfernoTable
List of unlock requirements for INFERNO charts. Can have multiple entries for different unlock conditions over time.
<H4>Structure</H4>

| Name                          | Type                             | Example Value | Notes                                                  |
|-------------------------------|----------------------------------|---------------|--------------------------------------------------------|
| MusicId                       | *IntProperty*                    | `1056`        | Song ID that this inferno belongs to                   |
| bRequirePurchase              | *BoolProperty*                   | `True`        | Set if purchase with WP is required                    |
| RequiredInfernoOpenWaccaPoint | *IntProperty*                    | `1000`        | How many WP it costs to unlock the inferno             |
| bVipPreOpen                   | *BoolProperty*                   | `False`       | Set if VIP users unlock the inferno 1 day early        |
| NameTag                       | *StrProperty*                    | `Quon`        | Song name (unused?)                                    |
| ExplanationTextTag            | *StrProperty*                    | `TEXT("")`    | Song description (unused)                              |
| ItemActivateStartTime         | *Int64Property*<br/>(WACCA Date) | `2020091707`  | When to enable this item for use                       |
| ItemActivateEndTime           | *Int64Property*<br/>(WACCA Date) | `0`           | When to disable this item for use                      |
| bIsInitItem                   | *BoolProperty*                   | `True`        | If the item is part of a player's initial inventory    |
| GainWaccaPoint                | *IntProperty*                    | `0`           | How much additional WP to gain when getting this item? |

### UnlockMusicTable
List of unlock requirements for every song. Can have multiple entries for different unlock conditions over time.
<H4>Structure</H4>

| Name                        | Type                             | Example Value | Notes                                                  |
|-----------------------------|----------------------------------|---------------|--------------------------------------------------------|
| MusicId                     | *IntProperty*                    | `3`           |                                                        |
| AdaptStartTime              | *Int64Property*<br/>(WACCA Date) | `0`           | When this unlock condition starts                      |
| AdaptEndTime                | *Int64Property*<br/>(WACCA Date) | `0`           | When this unlock condition ends                        |
| bRequirePurchase            | *BoolProperty*                   | `False`       | Is purchase required                                   |
| RequiredMusicOpenWaccaPoint | *IntProperty*                    | `0`           | How many WP it costs to unlock this song               |
| bVipPreOpen                 | *BoolProperty*                   | `True`        | Set if VIP users unlock the song 1 day early           |
| NameTag                     | *StrProperty*                    | `name`        | Song name (unused)                                     |
| ExplanationTextTag          | *StrProperty*                    | `jouken`      | Song description (unused)                              |
| ItemActivateStartTime       | *Int64Property*<br/>(WACCA Date) | `0`           | When to enable this item for use                       |
| ItemActivateEndTime         | *Int64Property*<br/>(WACCA Date) | `0`           | When to disable this item for use                      |
| bIsInitItem                 | *BoolProperty*                   | `True`        | If the item is part of a player's initial inventory    |
| GainWaccaPoint              | *IntProperty*                    | `0`           | How much additional WP to gain when getting this item? |

### UserPlateBackgroundTable
List of all user plates.
<H4>Structure</H4>

| Name                          | Type                             | Example Value            | Notes                                                  |
|-------------------------------|----------------------------------|--------------------------|--------------------------------------------------------|
| UserPlateBackgroundId         | *IntProperty*                    | `211001`                 |                                                        |
| UserPlateBacgroundTextureName | *StrProperty*                    | `uT_US_1`                | Plate texture name                                     |
| UserPlateBacgroundRarity      | *Int8Property*                   | `1`                      | Rarity level in stars                                  |
| NameTag                       | *StrProperty*                    | `USER_PLATE_BG_NAME_001` | Plate name tag                                         |
| ExplanationTextTag            | *StrProperty*                    | `USER_PLATE_BG_MES_001`  | Plate description tag                                  |
| ItemActivateStartTime         | *Int64Property*<br/>(WACCA Date) | `0`                      | When to enable this item for use                       |
| ItemActivateEndTime           | *Int64Property*<br/>(WACCA Date) | `0`                      | When to disable this item for use                      |
| bIsInitItem                   | *BoolProperty*                   | `True`                   | If the item is part of a player's initial inventory    |
| GainWaccaPoint                | *IntProperty*                    | `0`                      | How much additional WP to gain when getting this item? |

### UserRateCoefficientTable
Lists correlations between minimum scores and rate coefficients.
<H4>Structure</H4>

| Name                | Type            | Example Value | Notes |
|---------------------|-----------------|---------------|-------|
| RequiredScore       | *IntProperty*   | `990000`      |       |
| CalcRateCoefficient | *FloatProperty* | `4.0`         |       |

### UserRateStepTable
Lists every rate level achievable in the game. Evaluated in reverse order, if you want to add higher ones,
add them to the top of the list.
<H4>Structure</H4>

| Name         | Type          | Example Value                    | Notes                                       |
|--------------|---------------|----------------------------------|---------------------------------------------|
| RequiredRate | *IntProperty* | `2500`                           | Minimum rate required for this rate level   |
| MaterialName | *StrProperty* | `Rating/uM_rate_000.uM_rate_000` | Material to use for the rate number display |

### UserRateTargetTable
Defines where the new/old song cutoff is for rate, how many songs apply, and the coefficient of the type of song.
<H4>Structure</H4>

| Name                | Type            | Example Value | Notes                                               |
|---------------------|-----------------|---------------|-----------------------------------------------------|
| RequiredDate        | *Int64Property* | `2021081007`  | The date required to count as this rate target      |
| CountMusicNum       | *IntProperty*   | `15`          | How many songs are used as part of this rate target |
| CalcRateCoefficient | *FloatProperty* | `1.0`         | Rate weighting multiplier                           |

### VolumeStepListTable
A list of the volume steps in increments of 10 as full-width strings. Assumed to be used by the settings menus.

### WaccaPointTable
List of how many WP you earn for each letter grade depending on the level of the song.
<H4>Structure</H4>

| Name    | Type          | Example Value | Notes                                            |
|---------|---------------|---------------|--------------------------------------------------|
| Level01 | *IntProperty* | `340`         | WP earned for this letter grade on a Lv. 1 song  |
| Level02 | *IntProperty* | `340`         | WP earned for this letter grade on a Lv. 2 song  |
| Level03 | *IntProperty* | `340`         | WP earned for this letter grade on a Lv. 3 song  |
| Level04 | *IntProperty* | `340`         | WP earned for this letter grade on a Lv. 4 song  |
| Level05 | *IntProperty* | `340`         | WP earned for this letter grade on a Lv. 5 song  |
| Level06 | *IntProperty* | `360`         | WP earned for this letter grade on a Lv. 6 song  |
| Level07 | *IntProperty* | `360`         | WP earned for this letter grade on a Lv. 7 song  |
| Level08 | *IntProperty* | `360`         | WP earned for this letter grade on a Lv. 8 song  |
| Level09 | *IntProperty* | `400`         | WP earned for this letter grade on a Lv. 9 song  |
| Level10 | *IntProperty* | `400`         | WP earned for this letter grade on a Lv. 10 song |
| Level11 | *IntProperty* | `400`         | WP earned for this letter grade on a Lv. 11 song |
| Level12 | *IntProperty* | `450`         | WP earned for this letter grade on a Lv. 12 song |
| Level13 | *IntProperty* | `450`         | WP earned for this letter grade on a Lv. 13 song |
| Level14 | *IntProperty* | `480`         | WP earned for this letter grade on a Lv. 14 song |
| Level15 | *IntProperty* | `500`         | WP earned for this letter grade on a Lv. 15 song |


#### WP Table
|       | Master | SSS+ | SSS | SS+ | SS  | S+  | S   | AAA | AA  | A  | B  | C  | D  |
|:-----:|--------|------|-----|-----|-----|-----|-----|-----|-----|----|----|----|----|
| Lv. 1 | 400    | 340  | 340 | 320 | 320 | 300 | 300 | 250 | 220 | 80 | 70 | 50 | 30 |
| Lv. 2 | 400    | 340  | 340 | 320 | 320 | 300 | 300 | 250 | 220 | 80 | 70 | 50 | 30 |
| Lv. 3 | 400    | 340  | 340 | 320 | 320 | 300 | 300 | 250 | 220 | 80 | 70 | 50 | 30 |
| Lv. 4 | 400    | 340  | 340 | 320 | 320 | 300 | 300 | 250 | 220 | 80 | 70 | 50 | 30 |
| Lv. 5 | 400    | 340  | 340 | 320 | 320 | 300 | 300 | 250 | 220 | 80 | 70 | 50 | 30 |
| Lv. 6 | 400    | 360  | 360 | 340 | 340 | 320 | 320 | 260 | 240 | 80 | 70 | 50 | 30 |
| Lv. 7 | 400    | 360  | 360 | 340 | 340 | 320 | 320 | 260 | 240 | 80 | 70 | 50 | 30 |
| Lv. 8 | 400    | 360  | 360 | 340 | 340 | 320 | 320 | 260 | 240 | 80 | 70 | 50 | 30 |
| Lv. 9 | 450    | 400  | 400 | 360 | 360 | 340 | 340 | 280 | 260 | 80 | 70 | 50 | 30 |
| Lv.10 | 450    | 400  | 400 | 360 | 360 | 340 | 340 | 280 | 260 | 80 | 70 | 50 | 30 |
| Lv.11 | 450    | 400  | 400 | 360 | 360 | 340 | 340 | 280 | 260 | 80 | 70 | 50 | 30 |
| Lv.12 | 500    | 450  | 450 | 380 | 380 | 360 | 360 | 280 | 260 | 80 | 70 | 50 | 30 |
| Lv.13 | 500    | 450  | 450 | 380 | 380 | 360 | 360 | 300 | 280 | 80 | 70 | 50 | 30 |
| Lv.14 | 600    | 480  | 480 | 400 | 400 | 380 | 380 | 320 | 300 | 80 | 70 | 50 | 30 |
| Lv.15 | 700    | 500  | 500 | 420 | 420 | 400 | 400 | 370 | 350 | 80 | 70 | 50 | 30 |

### WidgetTranslucencyTable
Setting, Widget Translucency (0-5). Impacts life bar, judgement, etc. visibility.