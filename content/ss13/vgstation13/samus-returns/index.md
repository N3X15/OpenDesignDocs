Title: Return of Metroids

This is a project for /vg/station to return Metroids, which were removed during a rebase to Bay+TG code.  Metroids became slimes at that time, but there's some nostalgia for them.

**This document is open to pull requests and issue reports.**

[[_TOC_]]

# Mirrors

This page is mirrored at:

* [GitLab](https://gitlab.com/N3X15/open-design-docs/-/blob/main/content/ss13/vgstation13/samus-returns/index.md) (Best Rendering)
* [GitHub](https://github.com/N3X15/OpenDesignDocs/blob/main/content/ss13/vgstation13/samus-returns/index.md)

PRs, reviews, and issues are welcome from any mirror.

# Legal Information

Metroid-related materials are legally linked to Nintendo in a large number of ways, so we **MUST** find another name and likeness.  **Metroids** are a **working title** while we try to find alternatives.

While we don't find it likely that Nintendo would find us a threat due to the small community, we should still look for alternatives in case Nintendo breaks out the lawyers, as they have a history of such.

## USPTO Entries
* [Trademark #79323625](https://tmsearch.uspto.gov/bin/showfield?f=doc&state=4807:qhtjn7.2.1) - Nintendo of America, Inc.
* [Trademark #77749727](https://tmsearch.uspto.gov/bin/showfield?f=doc&state=4807:qhtjn7.2.7) (registered #3923764) - Nintendo of America, Inc.
## News
* [Youtube Channel Closes After 4,000 DMCA Takedowns](https://www.videogameschronicle.com/news/nintendo-music-youtuber-who-received-4000-copyright-strikes-is-closing-their-channel/)
* [Metroid II Remake Shut Down](https://www.animenewsnetwork.com/interest/2016-08-10/metroid-ii-remake-shut-down-after-dmca-copyright-claim/.105219)
* [Fan-Made 2D Metroid Prime Game Shut Down](https://www.nintendolife.com/news/2021/08/talking_point_as_the_fan-made_2d_metroid_prime_game_is_shut_down_where_do_you_stand_on_nintendos_takedowns)

## Alternatives

### Criteria

In order for us to have an acceptable alternative, the following criteria must be met:

* Must not exist in the game already.
* Must not be a legal issue if used.
* Must operate mechanically similar as the Metroid concept outlined below.

### Rejected
* ~~**Roros**~~ - They were the first stab at this eons ago, but they were overwhelmingly awful in a number of ways, and their sprites looked like bald furbies.
* ~~**Slimes**~~ - Already exist, but are mechanically different in a number of ways, making them trivial to wrangle.
* ~~**Brain Slugs/Yeerks**~~ - While the idea is similar mechanically, we already have them in the form of cortical borers.
* ~~**Headcrabs**~~ - Property of Valve Software.
* ~~**Giant Spiders**~~ - Already exist as Bay's crappy answer to Xenomorphs.

### Possibilities

Feel free to make suggestions
* Space Lice - Lays eggs in the brain, feeds on blood.
* Polyps (Space Jellyfish) - When a carbon is stung, it implants a Polyp into their skull and starts slowly feeding from their brain (increasing brain damage) until it gets X amount and spawns a new jelly, resetting the counter. After Y seconds, the host is paralyzed and the polyp appears as a barnacle-like hat. Death of the host kills the polyp.

**In the event of legal action, we will have to move very quickly and will likely have to choose one of these before much discussion.**

# What are Metroids?

Metroids are a small, flying carbon mob that hungers for flesh.  Metroid cores are used by Xenobiologists to make materials, chemicals, weapons and foods that can be immensely helpful or detrimental to the station at large.

They come in a variety of colors and shapes that signal genetic changes that can yield useful materials and information. Much of a Xenobio's time is spent carefully selectively breeding them to get the bloodlines they're interested in.

# Justification
*AKA: Why are Metroids a Thing Again?*

Pomf asked for them.

# Differences from Slimes

* Slimes are ground animals and can (theoretically) be blocked by various kinds of furniture and barriers.
* Metroids are flying mobs.
* Metroids are faster than slimes.
* Metroids are more aggressive than slimes.
* Metroids can produce more than one core per metroid, depending on bloodline and age.
* Metroids can take on some characteristics of their food (new).

# Gameplay Loop

Metroids can be encountered in laboratory vaults on the asteroid.

Once captured, they can be brought back to the station and farmed in a similar manner to slimes:
* Throw food animals into pen with Metroid.
* Metroid turns into adult, becomes faster
* Metroid splits/lays eggs after enough nutriment
* Metroid spawn have a chance of mutating into one of a few possible bloodlines from consuming that animal
* Xenobio uses extinguisher or temp gun to stun/kill metroids in the pen so they can retrieve desired animals
* Xenobio establishes new breeding pen
* Excess metroids are bonesawn to retrieve their cores.
* Cores can be liquified (grinder), eaten directly, cooked, or reacted with reagents to retrieve goodies.

# AI Loop

AI loop is similar to the slimes (since slimes were a direct derivative of them), but needs redone due to age.

* ECS-driven?

## Initial State
* Look for carbon mobs in vision
    * Move towards
    * If on same turf, attach and begin feeding
* Otherwise, move in random direction
* Tick down nutriment.

## Feeding
* Continue feeding unless removed
* Each tick produces X genetic damage and Y brute to victim and Z nutriment to the metroid.
* If removed, move back to initial state.
* If child and nutriment over threshold, release and begin evolution timer.
* If adult and released (by victim death or forcibly removed), release and begin spawning eggs.

## Evolution

* After X+rand() ticks, turn into adult and reset nutriment.
* Do not find or attack targets.
* Move slowly.

## Spawning
* Do not find or attack targets.
* Move slowly.
* Every X ticks, drop an egg and decrement X nutriment.
* At 0 nutriment, die.

# Cores

A Metroid's body contains 1 core during the juvenile stage and 3 cores during the adult stage.

## Core Removal

* Use bone saw on metroid corpse.
* Surgery failure destroys a core.

# Mutations

Metroids are capable of genetic mutations heralded by changes in the metroid's appearance, generally color and shape.

## Mechanics

* Metroids steal various kinds of behaviours from their prey.
* Metroids can mutate to adapt to adverse conditions.

## Bananium

Results from armored metroid exposure to bananium floor tiles.

Metroid is clown themed, with face paint, a party hat, and a bike horn. Instead of screeching, it honks. Has a small chance of slipping someone it's attached to.

### Core Behaviour
* **Used:** Bike horn noise.
* **Thrown:** 
  * Impacts turf: Fart noise, turns into a pool of space lube.
  * Impacts mob: Cream pie reaction, confetti
* **Ground:** Pick of:
    * Clown Mask
    * 3 Bananas
    * Bike Horn
    * 3 bananium sheets.  Yes, this lets you make lots of bananium.

## Phazon

Phazon-exposed metroid eggs turn into Phazon Metroids.

* Metroid has a different sprite to look like a Phazon Metroid from the games.
* Can stun and drag people around
* Infants can teleport to seen tiles
    * Will teleport away from projectiles
* Inflicts significantly more damage
* Instead of splitting, turns into a Hatcher, which is like a very dangerous jellyfish on crack.
### Core Behaviour
* **Used:** Nothing
* **Thrown:** 
  * Explodes, gives tox damage
* **Ground:** Gives Phazon Sheet.