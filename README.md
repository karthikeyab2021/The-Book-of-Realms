# The Book of Realms: Stickman Combat

A fast, keyboard-driven stickman fighting game that runs entirely in your browser. Fight an AI rival or a friend on the same keyboard across two magical domains from the universe of *The Book of Realms*: the bright **Celestial Dominion** and the molten **Ashen Throne**.

Built with plain HTML5 Canvas, CSS and vanilla JavaScript. No frameworks, no build step, no external assets, no server.

## Features

- **Two modes:** Player vs AI (Easy, Normal, Hard) and local two-player on one keyboard.
- **Two domains** with their own arenas, colors and effects:
  - **Celestial Dominion (Light):** a bright heaven with a white palace, rainbow and drifting clouds. Stickmen wear golden halos. Shots are light bullets, and a K.O. ends in a beam of light.
  - **Ashen Throne (Fire):** a lava cave with glowing lava, rising embers and cracked rock. Stickmen wear horns. Shots are fireballs. A K.O. drops a fireball on the loser, who burns away under a red, flaming "K.O."
- **Responsive combat:** light and heavy attacks with startup, active and recovery frames, hit stun, knockback, hit-stop, screen shake, and attacks that hit only once per swing.
- **Three skills** with cooldowns: ranged shots, a dash, and a dodge shield that cuts damage.
- **Procedurally animated stickmen** drawn with Canvas (running, jumping, punches, a slanted high kick, hit reactions, knockouts). No image files.
- **Round-based matches:** single round, best of 3 or best of 5, with a 60-second round timer.
- **Polished interface:** animated title screen with domain cards and sliding selectors, glass HUD, skill circles with key labels and cooldown sweeps, pause menu, and victory/defeat screens.

## Play

1. Download or clone the repository.
2. Open `index.html` in a modern browser (Chrome, Edge, Firefox or Safari).

That's it. There is nothing to install.

To host it on GitHub Pages: push the files to a repository, then go to **Settings → Pages**, choose the main branch and the root folder, and open the URL GitHub gives you.

## Controls

| Action | Player 1 | Player 2 |
|---|---|---|
| Move | A / D | Left / Right arrows |
| Jump | W | Up arrow |
| Light attack | J | Numpad 1 |
| Heavy attack | K | Numpad 2 |
| Shoot (bullets / fireball) | U | Numpad 4 |
| Dash | Shift | Numpad 0 |
| Dodge (shield) | L | Numpad 3 |

Other keys: **Esc** or **P** pauses, **H** shows hitboxes. In Player vs AI you use the Player 1 keys.

Notes:
- Player 2 needs a keyboard with a numpad and Num Lock on.
- Some keyboards cannot register many keys at once ("ghosting"), which can affect two-player play. On Windows, holding Shift while pressing numpad keys can cancel the Shift key, so Player 1's dash may drop while Player 2 uses the numpad.
- The game pauses automatically when the browser window loses focus.

## How combat works

| Move | Details |
|---|---|
| Light attack | 6 damage, fast, short reach |
| Heavy attack | 14 damage, slower, longer reach, launches the target, slanted high kick |
| Shoot | 4 damage per shot, 0.4s cooldown, travels across the arena, disappears on hit or at the edge |
| Dash | Quick burst in the direction you hold (forward if none), 0.8s cooldown, no invulnerability |
| Dodge (shield) | Lasts 1s, you take 40% of the damage (not zero), little knockback, no stun, slow movement, cannot attack while it is up, 3.5s cooldown |

Both domains play identically (same physics, damage and cooldowns). They differ only in look and effects. When the timer runs out, the fighter with more health wins the round.

The AI uses the same rules as a player: it approaches, attacks, retreats, jumps, dashes, shoots from range and shields. Higher difficulties think and react faster.

## Project structure

```
index.html   Page structure, title screen, HUD, menus
style.css    Styling, animations, domain themes
game.js      Input, fighters, combat, AI, rendering, game flow
README.md    This file
```

Inside `game.js` the code is split into sections: config, input, fighter, combat, AI, rendering, game flow and the main loop. Physics runs on a fixed 60 Hz timestep, independent of the display frame rate, and rendering is separate from updating. Each domain is an entry in the `REALMS` table (names, colors, effects) plus a background painter, which is where a new domain would be added.

## Current status

Implemented: both game modes, both domains, the combat system above, the skills, the AI, rounds, pause, rematch, and the full interface.

Not implemented yet:
- Hold-to-block, combo chains with damage scaling, and an energy meter
- The full realm ability system (Radiant Bolt, Divine Dash, Heaven's Wrath and the Ashen Throne equivalents)
- Saved progression, unlockable abilities and settings (`localStorage`)
- Remappable controls
- Sound and music

Testing so far has been automated logic runs (full AI and two-player matches in both domains with the drawing code exercised) plus syntax checks. It has not had a full manual test pass on every browser, so please report anything odd as an issue.

## Roadmap

1. Combos, blocking and balance tuning
2. The complete Celestial Dominion ability set with energy and cooldowns
3. Saved progression, unlocks, settings and remappable controls
4. More domains and sound

## Contributing

Issues and pull requests are welcome. The game is plain JavaScript, so you can edit the files and refresh the browser to see changes.


## Credits

Created for the universe of *The Book of Realms*.
