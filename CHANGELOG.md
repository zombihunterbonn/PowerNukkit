# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html) 
with an added upstream's major version number in front of the major version so we have an better distinction from
Nukkit 1.X and 2.X.

## [Unreleased 1.3.0.0-PN] - Future ([Check the milestone](https://github.com/GameModsBR/PowerNukkit/milestone/11?closed=1))
Click the link above to see the future.

### Breaking change
The following breaking change will be pulled in `1.3.0.0-PN`
- [8a09f93](https://github.com/GameModsBR/PowerNukkit/commit/8a09f933f83c9a52531ff8a184a58c6d733c9174) Quick craft implementation. ([NukkitX#1473](https://github.com/NukkitX/Nukkit/pull/1473)) Jedrzej* 05/06/2020

### Planned:
- Add support to the new 1.16 blocks, items, biomes and entities (without AI)
- Inherit protocol support from NukkitX

## [1.2.1.0-PN] - 2020-06-07 ([Check the milestone](https://github.com/GameModsBR/PowerNukkit/milestone/9?closed=1))
Click the link above to see the future.

### Fixes
- [#224] Enchantment compatibility rules when merging enchanted items in an anvil
- [#113] Beehives not dropping in creative when it has bees
- [#270] Replacing sugarcane's water don't break the sugarcane immediately
- [#272] `EntityPortalEnterEvent` not being fired when entering end portals
- [#279] `BlockEndPortal` missing collision bounding box
- [#279] `Entity.checkBlockCollision()`'s over scaffolding logic outdated
- [#281] Levers and buttons don't replace the snow layers
- [#285] Chicken, cow, pig, rabbit and sheep not dropping cooked food when on fire
- [#285] Chorus plant and flower not dropping
- [#285] Item string placing tripwire hooks instead of tripwires
- [#285] Wrong block name and color for dark prismarine block and prismarine bricks
- [#285] Nether bricks fence were burnable and flammable
- [#285] Item on hands disappear (looses one from the stack) when interacting with chest minecarts and hopper minecarts

### Added
- [#227] PlayerJumpEvent called when jump packets are received.
- [#242] `Item.equalsIgnoringEnchantmentOrder` method for public usage.
- [#244] `Enchantment.getPowerNukkit().isItemAcceptable(Item)` to check if an enchantment can exist 
         in a given item stack by any non-hack means.
- [#256] `CapturingCommandSender` intended to capture output of commands which don't require players.
- [#259] `Hash.hashBlock(Vector3)` method for public usage.
- [#261] `Player.isCheckingMovement()` method for public usage.
- [#261] Protected field `EntityEndCrystal.detonated` to disable the `EndCrystal.explode()` method.
- [#275] New annotations to document when elements get added and when deprecated elements will be removed
- [#123] Adds and register the banner pattern items
- [#276] `Block.afterRemoval()` called automatically when the block is replaced using any `Level.setBlock()`
- [#277] `Block.mustSilkTouch()` and `Block.mustDrop()` to allow blocks to force the dropping behaviour when being broken
- [#279] `Entity.isInEndPortal()` for public usage
- [#285] `LoginChainData.getRawData()` for public usage

### Changed
- [#227] Sugar canes now fires BlockGrowEvent when growing naturally.
- [#261] Kicked players can now view the kick reason on kick.
- [#285] Limit the maximum size of BookEditPacket's text to 256, ignoring the packet if it exceeds the limit
- [#285] Ender pearls will now be unable to teleport players across different dimensions
- [#285] ShortTag.load(NBTInputStream) now reads a signed short. Used to read an unsigned short.

## [1.2.0.2-PN] - 2020-05-18 ([Check the milestone](https://github.com/GameModsBR/PowerNukkit/milestone/10?closed=1))
Contains several fixes, including issues which cause item losses and performance issues

### Fixes
- [#239] Anvil fails to merge some enchantments because the ordering mismatches
- [#240] Anvils were charging fewer levels to merge thorn books
- [#243] Anvils were charging more levels to merge punch books
- [#246] Anvil checking the enchantment table property instead of the enchantment id
- [#246] Compatibility rules for unbreaking, fortune, mending, riptide, loyalty and channeling enchantments
- [#248] Air blocks with metadata were being rendered as "UPDATE!" block (backward compatibility fix)
- [#212] The `/tp player 0 1 2` command doesn't work
- [#220] Stripping old full bark log results in a wrong block
- [#157] Wrong Packed and Blue Ice break time with the hands
- [#193] Wrong explosion behaviour with waterlogged block
- [#103] Fixes BlockLeaves's random update logic spamming packets and consuming CPU unnecessarily
- [#253] Fixes `LeavesDecayEvent` also being called when leaves wouldn't decay
- [#254] Fixes BlockLeaves not checking for log connectivity, was checking only if it had a log block nearby
- [#255] Fix /status information in /debugpaste not being collected
- [#260] Fix a stack overflow when setting off end crystals near to each other
- [#260] Fix drops of block entity inventory contents on explosion
- [#260] Check SUPPORTED_PROTOCOLS instead of CURRENT_PROTOCOL in `LoginPacket.decode()`
- [#79] Sugarcane can grow without water
- [#262] Removing the water don't break the sugarcane (using empty bucket or breaking water flow)
- [#263] Fixes disconnect messages not reaching the player sometimes
- [#116] Fishing hooks don't attach to entities and damages multiples entities
- [#95] The Level Up sound is not centered
- [#267] Fishing hooks without players, loaded from the level save. They are now removed on load
- [#266] Loosing connection with items in an open anvil makes you loose the items
- [#273] Loosing connection with items in an open grindstone, enchanting table, stone cutter  makes you loose the items
- [#273] Loosing connection with items in an open crafting table, 2x2 crafting grid makes you loose the items

### Changed
- [#247] Invalid BlockId:Meta combinations now log an error when found. It logs only once
- [#255] The report issues link has been changed to point to the PowerNukkit repository
- [#268] The `/xp` command now makes level up sound every 5 levels
- [#273] If an anvil, grindstone, enchanting, stonecutter, crafting GUI closes, the items will try to go to the player's inventory
- [#273] `FakeBlockUIComponent.close(Player)` now calls `onClose(Player)`
- [#274] `Player.checkInteractNearby()` is now called once every 10 ticks, it was called every tick

## [1.2.0.1-PN] - 2020-05-08 ([Check the milestone](https://github.com/GameModsBR/PowerNukkit/milestone/8?closed=1))
Fixes several anvil issues.

### Added
- [#224] Added option to disable watchdog with `-DdisableWatchdog=true`. 
  This should be used **only by developers** to debug the server without interruptions by the crash detection system.

### Fixes
- [#224] Anvil not merging enchanted items correctly and destroying the items.
- [#228] Invalid enchantment order on anvil's results causing the crafting transaction to fail.
- [#226] Anvil cost calculation not applying bedrock edition reductions
- [#222] Anvil changes the level twice and fails the transaction if the player doesn't have enough.
- [#235] Wrong flags in MoveEntityAbsolutePacket
- [#234] Failed anvil transactions caused all involved items to be destroyed
- [#234] Visual desync in the player's experience level when an anvil transaction fails or is cancelled. 

### Changed
- [#234] Anvil's result is no longer stored in the PlayerUIInventory at slot 50 as 
         it was vulnerable to heavy duplication exploits.
- [#234] `setResult` methods in `AnvilInventory` are now deprecated and marked for removal at 1.3.0.0-PN
         because it's not supported by the client and changing it will fail the transaction.

## [1.2.0.0-PN] - 2020-05-03 ([Check the milestone](https://github.com/GameModsBR/PowerNukkit/milestone/6?closed=1))
**Note:** Effort has been made to keep this list accurate but some bufixes and new features might be missing here, specially those made by the NukkitX team and contributors.

### Added
- This change log file
- [#108] EntityMoveByPistonEvent
- [#140] `isUndead()` method to the entities

### Fixes
- [#129] A typo in the BlockBambooSapling class name **(breaking change)**
- [#102] Leaves decay calculation
- [#87] Arrows in offhand are black in the first person view
- [#46] checked if ProjectileHitEvent is cancelled before the action execution
- [#108] Lever sounds
- [#108] Incorrect sponge particles
- [#12] Wrong redstone signal from levers
- [#129] You can now shift to climb down while you are in the edges of a scaffold
- [#129] Fixes a turtle_egg placement validation
- [#129] Campfire can no longer be placed over an other campfire directly
- [#129] The sound that campfire does when it extinguishes
- [#140] Instant damage and instant health are now inverted when applied to undead entities
- [#140] A collision detection issue on Area Effect Cloud which could make it wears off way quicker than it should
- [#152] Changes the blue_ice blast resistance from 2.5 to 14
- [#170] Trapdoors behaving incorrectly when they receive redstone signal
- [#219] Button and door sounds
- [#44] Different daytime from Android and Windows 10 Edition
- [#93] Nukkit sends a rain time that doesn't matches the server
- [#210] Issues with old blocks from old NukkitX worlds, specially fully barked logs (log:15 for example)

### Changed
- Make BlockLectern implements Faceable
- The versioning convention now follows this pattern:<br>`upstream.major.minor.patch-PN`<br>[Click here for details.](https://github.com/GameModsBR/PowerNukkit/blob/7912aa4be68e94a52762361c2d5189b7bbc58d2a/pom.xml#L8-L14)

## [1.1.1.0-PN] - 2020-01-21
### Fixes
- Piston heads not rendering
- Cauldron implementation, should be closer to vanilla now
- Implements hashCode in the NBT Tags, fixes usage with Set and HashMap
- Fixes BaseInventory ignoring it's own max stack size
- Fix cauldron's lightFilter value
- Fix the project throwing sound effect
- No particles when snow hits something
- Fixes projectile sounds
- Fixes egg particles and exp sounds
- The anvil block implementation
- Plants now requires light to grow
- Fix player does not get update for own skin
- Fix ~ operator in teleport command
- Fix ~ operator in /particle command
- Fall damage with slow falling effect
- Fishing Hook drag and gravity values
- [a8247360] Crops, grass, leaves, tallgrass growth and population
- Fixes fuzzy spawn radius calculation
- [#49] noDamageTicks should make the entity completely invulnerable while active
- [#54] Fixes movement issues on heavy server load
- [#57] Fixes block placement of Bone Block, End Portal Frame, Jukebox and Observer

### Changed
- Unregistered block states will be shown as 248:0 (minecraft:info_update) now
- Improves the UI inventories
- The codename to PowerNukkit to distinct from [NukkitX]'s implementation
- [#50] The kick message is now more descriptive
- [#80] Merged the "New RakNet Implementation" pull request which greatly improves the server performance and connections

### Added 
- Waterlogging support
- Support with blocks ID higher then 255 to the Anvil save format
- Support for blocks with 6 bits data value (used to support only 4 bits)
- [#51] Support for the offhand slot
- [#52] Merge the "More redstone components" pull request which fixes and implements many redstone related blocks
- [#53] Merge the "Vehicle event fix" pull request which add new events and fixes damage issues related to vehicles
- [#55] Minecart (chest and hopper) inventories
- [#56] ServerStopEvent
- Shield block animation (without damage calculation)
- New gamerules
- The /setblock command
- Dyeing leather support to cauldrons
- Color mixing support to cauldron
- Implementation for the entities (without AI):
    - Bees
    - Lingering Potions
    - Area Effect Clouds
- Implementation for the items:
    - Honey
    - Honey Bottle
    - Honeycomb
    - Suspicious Stew
    - Totem of Undying (without functionality)
    - Name Tags
    - Shulker Shell
- Implementation for the blocks:
    - [#58] Daylight Sensor
    - Lectern
    - Smoker
    - Blast Furnace
    - Light Block
    - Honeycomb Block
    - Wither Roses
    - Honey Block
    - Acacia, Birch, Dark Oak, Jungle, Spruce signs
    - Composter
    - Andesite, Polished Andesite, Diorite, Polished Diorite, End Brick, Granited, Polished Granite, Mossy Cobblestone stairs
    - Mossy Stone Brick, Prismarine Brick, Red Nether Brick stairs, Smooth Quartz, Red Sandstone, Smooth Sandstone stairs
    - Beehive and Bee Nests
    - Sticky Piston Head
    - Lava Cauldron
    - Wood (barks)
    - Jigsaw
    - Stripped Acacia, Birch, Dark Oak, Jungle, Oak and Spruce logs and barks
    - Blue Ice
    - Seagrass
    - Coral
    - Coral Fans
    - Coral Blocks
    - Dried Kelp Block
    - Kelp
    - Carved Pumpkin
    - Smooth Stone
    - Acacia, Birch, Dark Oak, Jungle, Spruce Button
    - Acacia, Birch, Dark Oak, Jungle, Spruce Pressure Plate
    - Acacia, Birch, Dark Oak, Jungle, Spruce Trapdoor
    - Bubble Column
    - Scaffolding
    - Sweet Berry Bush
    - Conduit
    - All stone type slabs
    - Lantern
    - Barrel
    - Campfire
    - Cartography Table
    - Fletching Table
    - Smithing Table
    - Bell
    - Turtle Eggs
    - Grindstone
    - Stonecutter
    - Loom
    - Bamboo

[updated changelog]:https://github.com/GameModsBR/PowerNukkit/blob/master/CHANGELOG.md

[Unreleased 1.3.0.0-PN]: https://github.com/GameModsBR/PowerNukkit/compare/v1.2.1.0-PN...master
[1.2.1.0-PN]: https://github.com/GameModsBR/PowerNukkit/compare/v1.2.0.2-PN...v1.2.1.0-PN
[1.2.0.2-PN]: https://github.com/GameModsBR/PowerNukkit/compare/v1.2.0.1-PN...v1.2.0.2-PN
[1.2.0.1-PN]: https://github.com/GameModsBR/PowerNukkit/compare/v1.2.0.0-PN...v1.2.0.1-PN
[1.2.0.0-PN]: https://github.com/GameModsBR/PowerNukkit/compare/v1.1.1.0-PN...v1.2.0.0-PN
[1.1.1.0-PN]: https://github.com/GameModsBR/PowerNukkit/compare/1ac6d50d36f07b6f1a02df299d9591d78c379db9...v1.1.1.0-PN#files_bucket

[a8247360]: https://github.com/GameModsBR/PowerNukkit/commit/a8247360

[NukkitX]: https://github.com/NukkitX/Nukkit

[#12]: https://github.com/GameModsBR/PowerNukkit/issues/12
[#44]: https://github.com/GameModsBR/PowerNukkit/issues/44
[#46]: https://github.com/GameModsBR/PowerNukkit/issues/46
[#49]: https://github.com/GameModsBR/PowerNukkit/pull/49
[#50]: https://github.com/GameModsBR/PowerNukkit/pull/50
[#51]: https://github.com/GameModsBR/PowerNukkit/pull/51
[#52]: https://github.com/GameModsBR/PowerNukkit/pull/52
[#53]: https://github.com/GameModsBR/PowerNukkit/pull/53
[#54]: https://github.com/GameModsBR/PowerNukkit/pull/54
[#55]: https://github.com/GameModsBR/PowerNukkit/pull/55
[#56]: https://github.com/GameModsBR/PowerNukkit/pull/56
[#57]: https://github.com/GameModsBR/PowerNukkit/pull/57
[#58]: https://github.com/GameModsBR/PowerNukkit/pull/58
[#79]: https://github.com/GameModsBR/PowerNukkit/issues/79
[#80]: https://github.com/GameModsBR/PowerNukkit/pull/80
[#87]: https://github.com/GameModsBR/PowerNukkit/issues/87
[#93]: https://github.com/GameModsBR/PowerNukkit/issues/93
[#95]: https://github.com/GameModsBR/PowerNukkit/issues/95
[#102]: https://github.com/GameModsBR/PowerNukkit/pull/102
[#103]: https://github.com/GameModsBR/PowerNukkit/issues/103
[#108]: https://github.com/GameModsBR/PowerNukkit/pull/108
[#113]: https://github.com/GameModsBR/PowerNukkit/issues/113
[#116]: https://github.com/GameModsBR/PowerNukkit/issues/116
[#123]: https://github.com/GameModsBR/PowerNukkit/issues/123
[#129]: https://github.com/GameModsBR/PowerNukkit/pull/129
[#140]: https://github.com/GameModsBR/PowerNukkit/pull/140
[#152]: https://github.com/GameModsBR/PowerNukkit/pull/152
[#157]: https://github.com/GameModsBR/PowerNukkit/issues/157
[#170]: https://github.com/GameModsBR/PowerNukkit/pull/170
[#193]: https://github.com/GameModsBR/PowerNukkit/issues/193
[#210]: https://github.com/GameModsBR/PowerNukkit/issues/210
[#212]: https://github.com/GameModsBR/PowerNukkit/issues/212
[#220]: https://github.com/GameModsBR/PowerNukkit/issues/220
[#219]: https://github.com/GameModsBR/PowerNukkit/pull/219
[#222]: https://github.com/GameModsBR/PowerNukkit/issues/223
[#224]: https://github.com/GameModsBR/PowerNukkit/pull/224
[#226]: https://github.com/GameModsBR/PowerNukkit/issues/226
[#227]: https://github.com/GameModsBR/PowerNukkit/pull/227
[#228]: https://github.com/GameModsBR/PowerNukkit/issues/228
[#234]: https://github.com/GameModsBR/PowerNukkit/issues/234
[#235]: https://github.com/GameModsBR/PowerNukkit/issues/235
[#239]: https://github.com/GameModsBR/PowerNukkit/issues/239
[#240]: https://github.com/GameModsBR/PowerNukkit/issues/240
[#242]: https://github.com/GameModsBR/PowerNukkit/pull/242
[#243]: https://github.com/GameModsBR/PowerNukkit/issues/243
[#244]: https://github.com/GameModsBR/PowerNukkit/pull/244
[#246]: https://github.com/GameModsBR/PowerNukkit/issues/246
[#247]: https://github.com/GameModsBR/PowerNukkit/pull/247
[#248]: https://github.com/GameModsBR/PowerNukkit/pull/248
[#253]: https://github.com/GameModsBR/PowerNukkit/pull/253
[#254]: https://github.com/GameModsBR/PowerNukkit/issues/254
[#255]: https://github.com/GameModsBR/PowerNukkit/pull/255
[#256]: https://github.com/GameModsBR/PowerNukkit/pull/256
[#259]: https://github.com/GameModsBR/PowerNukkit/pull/259
[#260]: https://github.com/GameModsBR/PowerNukkit/pull/260
[#261]: https://github.com/GameModsBR/PowerNukkit/pull/261
[#262]: https://github.com/GameModsBR/PowerNukkit/pull/262
[#263]: https://github.com/GameModsBR/PowerNukkit/pull/263
[#266]: https://github.com/GameModsBR/PowerNukkit/issues/266
[#267]: https://github.com/GameModsBR/PowerNukkit/issues/267
[#268]: https://github.com/GameModsBR/PowerNukkit/pull/268
[#270]: https://github.com/GameModsBR/PowerNukkit/issues/270
[#272]: https://github.com/GameModsBR/PowerNukkit/issues/272
[#273]: https://github.com/GameModsBR/PowerNukkit/pull/273
[#274]: https://github.com/GameModsBR/PowerNukkit/pull/274
[#275]: https://github.com/GameModsBR/PowerNukkit/pull/275
[#276]: https://github.com/GameModsBR/PowerNukkit/pull/276
[#277]: https://github.com/GameModsBR/PowerNukkit/pull/277
[#279]: https://github.com/GameModsBR/PowerNukkit/pull/279
[#281]: https://github.com/GameModsBR/PowerNukkit/pull/281
[#285]: https://github.com/GameModsBR/PowerNukkit/pull/285
