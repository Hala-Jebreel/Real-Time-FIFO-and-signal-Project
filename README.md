# Real-Time-FIFO-and-signal-Project
# 🧠 Real-Time Rope Pulling Game Simulation

## 📌 Overview
This project is a real-time, multi-process simulation of a **tug-of-war game** using **Linux signals, pipes, FIFOs**, and **OpenGL graphics**. Players are divided into two teams and compete by pulling a rope. The system simulates energy dynamics, player coordination, and team effort while visualizing the match in real time.

🛠 Developed as part of the **ENCS4330: Real-Time Applications & Embedded Systems** course at **Birzeit University**, Spring 2024/2025.

---

## 🎮 Game Features

- 👥 **2 Teams**, 4 players each.
- ⚡ Each player has dynamic energy (randomly initialized).
- ⏱️ Energy decays during the round and regenerates between rounds.
- 💤 Players may **fall** (energy = 0) and **recover** after a random time.
- 🧠 **Referee process**:
  - Controls round start/stop via signals.
  - Collects effort (energy × position factor) via FIFOs.
  - Determines team scores and round winners.
- 🖼️ Real-time **OpenGL GUI**:
  - Displays players, energy levels, positions, and rope movement.
- 🧾 All parameters are configurable through a simple text file: `arguments.txt`.

---

## 📂 File Structure
├── Makefile # Build instructions
├── arguments.txt # User-defined game parameters
├── functions.c # Config reader & FIFO helpers
├── header.h # Shared constants, structs, and globals
├── player.c # Player logic
├── player.h # Player header
├── tug_of_war.c # OpenGL GUI
├── project1_signal_pipe_fifo_202502.pdf # Project instructions
└── README.md # This file

## ⚙️ Configuration

You can easily customize game settings by editing the `arguments.txt` file:

```txt
NUMBER_OF_ROUNDS=5
THRESHOLD=400
ROUND_TIME=10
INITIAL_ENERGY_MIN=20
INITIAL_ENERGY_MAX=80
ENERGY_DECAY_MIN=1
ENERGY_DECAY_MAX=5
FALL_TIME_MIN=2
FALL_TIME_MAX=6
ENERGY_INCREASE_MIN=1
ENERGY_INCREASE_MAX=10

🚀 How to Run
✅ Requirements
Linux OS

GCC Compiler

OpenGL and GLUT installed (sudo apt install freeglut3-dev)

🔨 Compile the Project
make
🏁 Start the Simulation

./main arguments.txt
This runs the referee logic and spawns player processes.

🖼️ Start the GUI
./tug_of_war
Run the GUI in a separate terminal window. It visualizes game progress in real time.

🧪 Concepts Used
Multiprocessing: fork()

Inter-process communication (IPC):

Named pipes (FIFOs)

Signals (SIGUSR1, SIGUSR2, SIGTERM, SIGALRM)

Synchronization between parent and children

OpenGL 2D rendering with GLUT

Runtime parameter loading from text file






