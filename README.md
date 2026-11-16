# EMBERLINE — Foundry Yard

A round-based tactical shooter in the browser. Ember attacks the Furnace,
Wardens hold it, first to 8 rounds wins the match. Three lanes, one bombsite,
bots that actually play the objective.

I built this because I wanted a Counter-Strike-style round loop I could open
in a tab and play — buy phase, plant, defuse, economy — without installing
anything. The whole game is static files: three.js for rendering, plain
ES modules, no build step, no network. If you have played a round, you
already know the whole game; the depth is in the corners and the timing.

## How to play

Open `game/index.html` in desktop Chrome (or serve `game/` with any static
server). Click **CLICK TO PLAY**, and the game locks your mouse.

- **WASD** move, **Shift** walk, **Ctrl** crouch, mouse to aim
- **Click** fire, **R** reload, **B** buy menu between rounds
- **G** throw a FRAG-7, **E** plant the bomb / defuse it

## The game

- **Rounds**: buy phase, then a 100-second round. Win by eliminating the
  other team, planting and blowing the Furnace, or — as Wardens — running
  the clock out or defusing.
- **Economy**: $1,400 for a round win, $900 for a loss, $300 a kill, $300
  for a defuse. Spend it on four guns and grenades in the buy menu.
- **Gunplay**: hitscan with headshots worth 4x, spread and recoil that grow
  when you fire on the move, so stopping to aim pays. No friendly fire.
- **Bots**: Ember bots push lanes and plant; Warden bots hold posts, patrol,
  hear gunfire, and run to defuse once the bomb is down. They fire in
  bursts with a real reaction delay.
- **Map**: Foundry Yard — North, Mid and South lanes into the Furnace
  bombsite, dusk light, amber and teal. Crates and divider walls make the
  corners worth clearing.
- **Tech**: fixed-step 60 Hz simulation kept apart from rendering, one
  module per job (`state`, `map`, `player`, `weapons`, `bots`, `rounds`,
  `hud`, `audio`, `fx`), procedural WebAudio sounds, pooled tracers and
  particles so the hot loops allocate nothing.

## Run it

```sh
# serve the game folder and open http://localhost:8080
npx --yes serve game
```

## License

MIT — see LICENSE.
