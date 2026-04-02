# Implementation Plan: Flappy Cat Game

> Generated: 2026-04-02
> Source: KAN-6 — Create a simple Flappy Bird clone game
> Branch: `feat/KAN-6-flappy-cat-game`
> Status: 🔵 In Progress

## Overview
Build a complete Flappy Bird clone as a single HTML file using HTML5 Canvas and vanilla JavaScript. The bird is replaced with a cute grey cat with wings. The game includes gravity physics, scrolling pipe obstacles, score tracking, and a polished visual style.

## Business Goal
Deliver a fun, playable browser game featuring a grey winged cat that can be opened directly as an HTML file with no server or build step.

## Tech Stack & Constraints
- Language/Framework: Vanilla HTML5 + JavaScript + CSS (single file)
- Key libraries: None (pure Canvas API)
- Constraints: Single file, no external dependencies, no build tools
- Typecheck command: N/A (vanilla JS)
- Test command: Open in browser and play

## Phases

### Phase 1: Game Foundation & Loop
**Goal**: Set up the HTML structure, canvas, and core game loop

- [ ] Task 1.1: Create `index.html` with HTML boilerplate, full-viewport canvas, and embedded CSS for centering/background
- [ ] Task 1.2: Implement the game loop using `requestAnimationFrame` with delta-time tracking
- [ ] Task 1.3: Add game state machine (MENU → PLAYING → GAME_OVER) with state transitions
- [ ] Task 1.4: Wire up click/tap/spacebar input handlers that respond based on current game state

### Phase 2: Cat Character & Physics
**Goal**: Draw and animate the grey winged cat with gravity and flap mechanics

- [ ] Task 2.1: Draw the grey cat body using Canvas paths (rounded body, ears, face with eyes/nose/whiskers)
- [ ] Task 2.2: Draw wings on the cat that animate (flap up/down) when the player taps
- [ ] Task 2.3: Implement gravity (downward velocity += gravity each frame) and flap (set upward velocity on input)
- [ ] Task 2.4: Add slight rotation based on velocity (nose up when flapping, nose down when falling)

### Phase 3: Obstacles & Scrolling
**Goal**: Create pipe obstacles that scroll from right to left with random gaps

- [ ] Task 3.1: Implement pipe pair generation with randomized vertical gap position
- [ ] Task 3.2: Scroll pipes from right to left at constant speed, remove off-screen pipes
- [ ] Task 3.3: Spawn new pipes at timed intervals to maintain consistent obstacle flow
- [ ] Task 3.4: Draw pipes with styled gradients (green with highlights, rounded caps)

### Phase 4: Collision & Scoring
**Goal**: Detect collisions and track score

- [ ] Task 4.1: Implement AABB collision detection between cat hitbox and pipe rects
- [ ] Task 4.2: Detect collision with ground and ceiling boundaries
- [ ] Task 4.3: Increment score when cat passes a pipe pair (track which pipes have been scored)
- [ ] Task 4.4: Display score on-screen during gameplay (large centered number with text shadow)

### Phase 5: UI Screens & Polish
**Goal**: Add menu, game over screen, and visual polish for a polished feel

- [ ] Task 5.1: Create start/menu screen with title "Flappy Cat", cat preview, and "Click to Play" prompt
- [ ] Task 5.2: Create game-over screen showing final score, best score (in-memory), and "Click to Restart"
- [ ] Task 5.3: Add scrolling ground/grass layer at the bottom for depth
- [ ] Task 5.4: Add parallax sky background with clouds
- [ ] Task 5.5: Add particle effects on flap (small feather/sparkle puffs) and screen flash on death
- [ ] Task 5.6: Final visual tuning — colors, speeds, gap sizes, gravity feel — to make gameplay smooth and fun

## Key Design Decisions
| Decision | Chosen Approach | Rationale |
|----------|----------------|----------|
| Rendering | HTML5 Canvas | Best for smooth 2D game animation |
| Cat art | Canvas path drawing | No external assets needed, single file |
| File structure | Single HTML file | Matches "simple" requirement, zero setup |
| State management | Simple state machine | Clean transitions, easy restart |
| Score persistence | In-memory only | No localStorage needed for simplicity |

## Files to Create
- `index.html` — The complete game (HTML + CSS + JS all inline)

## Files to Modify
- None (greenfield project)

## Testing Checklist
- [ ] Cat renders as a grey cat with visible wings
- [ ] Click/tap/space causes cat to flap upward
- [ ] Gravity pulls cat down naturally
- [ ] Pipes scroll smoothly from right to left
- [ ] Collision with pipes triggers game over
- [ ] Collision with ground/ceiling triggers game over
- [ ] Score increments correctly when passing pipes
- [ ] Game restarts cleanly from game-over screen
- [ ] Works in Chrome, Firefox, Safari

## Out of Scope
- Sound effects / music
- Mobile-specific touch optimization
- Leaderboard / high score persistence
- Difficulty progression

## Open Questions / Assumptions
| Question | Assumption |
|----------|------------|
| Art style detail level | Cute but simple canvas-drawn cat (not pixel art) |
| Game difficulty | Medium — tuned to be fun, not punishing |
| Canvas size | Responsive, max 480×640 centered on page |
