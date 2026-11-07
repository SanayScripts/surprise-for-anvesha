# Death Station Run: testing guide

Build under test: `index.html` (single file, Three.js, works offline except for the Three.js script from cdnjs).

## 1. Setup

- Use desktop Chrome or Firefox at roughly 1280×720 or larger. Phones are not supported for play.
- Open `index.html` from the GitHub Pages link, or double-click it locally.
- Audio starts only after a key press (browser rule). Press Enter on the title screen first.
- Keep the page focused. Clicking elsewhere on the page can drop keyboard focus.

## 2. Controls

| Action | Key |
|---|---|
| Steer | Arrows or WASD |
| Barrel roll (deflects turret bolts) | Shift (left or right) |
| Skip the crawl or approach (after 4 s) | Enter or Space |
| Advance a dialogue line | Enter |
| Fire torpedo in the final run-up | Space |
| Lock and fire in the boss fight | Hold Space 3 s to lock, tap to fire a missile |
| Pause menu | Esc |
| Pause menu buttons | Click, or C / R / M / T |
| Start, retry, replay | Enter, or click the button |
| Test stage jump (in test box) | Digit 1–8 while paused |

Mouse steering is removed on purpose. Menus are clickable.

## 3. Test mode: jump straight to any stage

Add these to the URL (replace `index.html` with the page's URL):

| Stage | URL suffix |
|---|---|
| Approach (warp in) | `?test=1&jump=approach` |
| Surface (MainTheme starts) | `?test=1&jump=surface` |
| Trench 1 | `?test=1&jump=P1` |
| Trench 2 | `?test=1&jump=P2` |
| Trench 3 | `?test=1&jump=P3` |
| Final run-up (torpedo) | `?test=1&jump=FINAL` |
| Boss fight | `?test=1&jump=boss` |
| Game over screen | `?test=1&jump=gameover` |

You can also press Esc during play, then press T for test mode and Digit 1–8 to jump. Esc does not open the pause menu on the title screen, so start a stage first.

## 4. Checklist by stage

Mark each item pass / fail. Note the time in seconds if something is off.

### Title and crawl
- [ ] Title card shows, then the crawl starts. Title music (anvesha theme) plays.
- [ ] Enter and Space both skip the crawl once it is past 4 s.
- [ ] After a skip or normal end, the title music stops. Nothing plays during the approach.

### Approach (hyperspace warp in)
- [ ] Wingmen drop out of hyperspace one after another. Dialogue plays over it.
- [ ] Space skips the approach even while a dialogue line is open. No lines carry over to the surface.
- [ ] Enter advances one line at a time.
- [ ] Ship cannot be hit during the approach.

### Surface
- [ ] MainTheme starts as the surface begins.
- [ ] Turret bolts fire from towers and are dodged or deflected with a roll.
- [ ] A bolt only hits when it reaches the ship, not while it is still well away. Hit box is smaller now.
- [ ] Hitting a tower costs a heart.

### Trench 1 and 2
- [ ] Beams and gaps line up with the ship's position.
- [ ] Turrets fire only within their own subsection. No shots through slits.
- [ ] Roll cooldown is about 0.75 s. Roll again after that and confirm it fires.
- [ ] **Side wall:** flying into the wall bounces you back and costs no heart. Hearts stay the same.

### Trench 3
- [ ] Difficulty feels right. Note any section that feels unfair.

### Final run-up
- [ ] The reticle fills while the vent is in view.
- [ ] Space fires the torpedo. The bomb guide sits 18 m ahead
- [ ] Two turrets fire along the final run-up, each about once a second, staggered. Their bolts aim where you are; dodge sideways or roll (Shift) to deflect. Shots loop with the run. on the floor; fire while it is over the vent hole. A full lock hits the vent and wins the run.
- [ ] A miss sends you back for a second pass with the short run-up.

### Boss fight
- [ ] Boss arena is open space. Death Star is visible in the distance and slowly bursts.
- [ ] Laser nets arrive every 1.7 s. The gaps are big enough to fly through.
- [ ] Holding Space 3 s locks on. Lock pauses when a net blocks your view and resets after each shot.
- [ ] Tapping Space fires a missile. Missiles evade and home in like missiles.
- [ ] Two guns on the sides of the arena fire once a second each, staggered. Their glow shows a shot coming. Dodge or roll (Shift) to deflect.
- [ ] Three hits on the boss end the fight. Her hyperspace battery fills over 60 s.
- [ ] If the battery fills, she jumps and the Wasted screen shows.
- [ ] MainTheme plays through the boss fight.

### Hearts, shields and calm mode
- [ ] You start with 5 hearts. Each hit costs one heart.
- [ ] A power orb refills hearts and gives a 3 s shield, where hits do nothing.
- [ ] Calm mode (C in the pause menu) makes hits cost nothing.

### Game over and win
- [ ] Losing all hearts shows the GAME OVER screen with the game over theme.
- [ ] Retry (Enter or click) starts the stage again.
- [ ] Winning shows the win screen with the exact message: "Anvesha, thank you for winning my heart back! And, thank you for making the past few months of my life beautiful <3" Replay (Enter or click) works.

### Pause menu
- [ ] Esc pauses. Resume (Esc or click) continues.
- [ ] Calm, Restart, Mute and Test buttons all work with the mouse and keys.
- [ ] Muting stops the music and silences effects.

## 5. Specific checks for this round

1. **Side wall:** hit the wall at speed. Expected: a small bounce and spark, no heart lost, no game over.
2. **Roll cooldown:** roll, then time until the next roll is possible. Expected: about 0.75 s.
3. **Hitbox and far hits:** let bolts come from the far end of a tower's line and dodge them. Expected: no hit until the bolt is visually at the ship.
4. **Approach skip:** start the approach, wait for a dialogue line, press Space. Expected: skips to the surface immediately.
5. **Menus clickable:** click Start, Resume, Calm, Restart, Mute, Test, the stage buttons, Retry and Replay with the mouse.
6. **Music:** title theme stops after the crawl. Surface and boss use MainTheme. Loss plays the game over theme.

## 6. Known things to watch (not bugs yet)

- The approach length follows the dialogue, so it changes with the script.
- Nets and missiles may be too hard or too easy. Record how many attempts each boss phase takes.
- The 60 s hyperspace timer may feel too short or too long.
- "STAR WARS" is a Lucasfilm trademark. Do not share the public link widely until that is settled.

## 7. Reporting a bug

Send:
1. The URL or stage (for example `?jump=P2`)
2. The time into the stage, in seconds
3. What you did, step by step
4. What you expected and what happened
5. A screenshot or short screen recording, if possible
6. Your browser and OS
