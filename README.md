# Splashmem AI Game

**A multiplayer grid-based strategy and simulation game developed in C using SDL2.**

Splashmem is a university programming project developed at **Polytech Tours**. Autonomous players compete to control as many cells as possible on a 100 × 100 grid while managing a limited action budget.

The project was originally designed as a two-person assignment, but I completed the implementation individually.

## 🎮 Game Overview

- **4 to 8 autonomous players**
- **100 × 100 grid** with wraparound boundaries
- **9,000 initial action credits** per player
- Cell ownership and score tracking
- Different movement strategies and special abilities
- Real-time graphical visualization using SDL2
- Start, pause, and turbo simulation controls

The objective is to claim more cells than the other players before the match ends.

## ⚙️ Features

### Player Actions

Players can perform several types of actions:

| Category | Actions |
|---|---|
| Movement | Move up, down, left or right |
| Dash | Move eight cells in a direction |
| Teleport | Teleport eight cells in a direction |
| Bomb | Place a delayed area-effect bomb |
| Fork | Create a temporary clone that replays previous actions |
| Clean | Clear cells in a surrounding area |
| Mute | Temporarily prevent an opponent from claiming cells |
| Swap | Temporarily change which player receives an opponent's claimed cells |

### Autonomous Agents

Players can be loaded from:

- **Shared libraries (`.so`)**, using dynamically loaded `get_action()` functions.
- **Text scripts (`.txt`)**, containing sequences of actions.

Four example agents are included for testing the game mechanics.

## 🛠️ Technologies

- **Language:** C
- **Graphics:** SDL2, SDL2_ttf
- **Dynamic loading:** `dlopen`, `dlsym`
- **Build system:** GNU Make / GCC
- **Platforms:** Linux, with macOS build support in the Makefile

## 🏗️ Project Architecture

| File | Responsibility |
|---|---|
| `splash.c` | Application entry point, SDL2 rendering, UI and event handling |
| `splash_game.c` | Game simulation, player actions, scoring and special effects |
| `splash_game.h` | Shared data structures, constants and function declarations |
| `actions.h` | Action identifiers |
| `joueur1.c` – `joueur4.c` | Example autonomous player implementations |
| `Makefile` | Compilation and execution |

The separation between the graphical interface and game logic makes the simulation easier to understand and maintain.

## 🚀 Installation & Usage

### Dependencies

On Ubuntu/Debian:

```bash
sudo apt-get install -y build-essential libsdl2-dev libsdl2-ttf-dev
```

### Build

```bash
make
```

This generates the `splash` executable and four example player libraries (`p1.so` to `p4.so`).

### Run

Launch the game with the included agents:

```bash
make run
```

Or specify player libraries manually:

```bash
./splash ./p1.so ./p2.so ./p3.so ./p4.so
```

The application also accepts text-based player scripts and supports up to eight player arguments.

### Clean

```bash
make clean
```

## 📸 Screenshots

*Gameplay screenshots coming soon.*

## 🎓 Project Context

**Polytech Tours — C Programming Project (2026)**

Developed individually as part of an engineering coursework assignment originally intended for a team of two.

The project involved implementing the initial game specifications, integrating additional gameplay mechanics in a second development phase, and maintaining compatibility with external player implementations.

### Skills Demonstrated

- Modular C programming
- Dynamic library loading
- Event-driven graphical programming
- State management and simulation logic
- Compilation and build automation
- Independent project development

---

*Developed by Sara Oulmaki — Polytech Tours*
