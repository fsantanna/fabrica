# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with
code in this repository.

## Build & Run

```bash
# Run the game (compiles and executes)
atmos main.atm
```

Tests are embedded in source files (`test { ... }` blocks) and execute during
compilation. Do not run tests - let the user do this step by hand.

## Project Overview

Fábrica is a turn-based multiplayer tile placement game written in Atmos
(compiles to Lua 5.4) using pico-lua for SDL-based graphics.

Players take turns placing tiles (machines, pipes, IO) on an 8x8 grid. Each
turn allows placing 2 machines with connected pipe networks.

## Architecture

**Global State:**
- `MAP` - 8x8 grid of placed tiles
- `JOGS` - Players array; `JOGS.i` is active player index
- `HAND` - Task pool for the floating tile being placed (max 1)

**Modules:**
- `main.atm` - Game loop, MAP grid, player management, event handling
- `art.atm` - Tile graphics (6x6 pixel buffers), `paint()` colorization
- `panel.atm` - Bottom UI panel with selectable tiles
- `start.atm` - Player turn logic, validates 2 machines per turn
- `float.atm` - Floating tile placement, validation rules, cycle detection

**Tile Types:** machine, pipe.line, pipe.curve, io.inp, io.out

## Atmos Language Reference

See linked documentation in main.atm:
- `/x/claude/atmos.md` - Language fundamentals
- `/x/claude/pico-atmos.md` - Framework idioms
- `/x/claude/pico-lua.md` - Graphics API

Key patterns:
- `spawn { ... }` for tasks, `tasks` for pools
- `every :event { ... }` for event loops
- `watching :event { ... }` for cancellation scopes
- `await(:event)` for blocking on events
- `match val { :tag => ... }` for pattern matching

## Code Style

- 80-column lines
- 4-space indentation
- Comments only before blocks/functions, never inline
- If a line requires comments, create an explicit block and comment on top
- Always use else in if statements (unless empty), even if the true case
  returns

## Workflow

- After each instruction, and before editing files, you are allowed to make
  one-line suggestions.
- Update `CLAUDE.md` when necessary.
