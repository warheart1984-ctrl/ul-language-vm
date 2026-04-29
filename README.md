# ul-language-vm
A minimal custom language runtime featuring a tokenizer, parser, bytecode compiler, and virtual machine. Designed for deterministic execution and as a foundational component of the AAIS architecture.
# AAIS UL Runtime

A minimal custom language runtime built from scratch, including:

- Tokenizer
- Recursive descent parser
- Bytecode compiler
- Stack-based virtual machine

Designed for deterministic execution and structured system behavior as part of the AAIS architecture.

---

## Features

- Variable assignment (`set x to 5`)
- Arithmetic operations
- Functions with parameters and return values
- Conditionals (`if / else`)
- Loops (`while`, `repeat`)
- Lists and dictionaries
- Built-in functions (`print`, `len`, etc.)

---

## Example

```plaintext
set x to 5
set y to 3

function add a b
    return a + b
end

set z to add(x, y)
print z

repeat 3 times
    print "loop"
end
8
loop
loop
loop




bash python ul_core.py









🔥 UL Dev Playground
Complete System Design
A transparent, deterministic language playground with three modes

A single product. Three modes. One deterministic substrate.
•🎮  Play Mode → UL Sandbox — write UL, see AST, bytecode, and VM state live
•🔥  Chaos Mode → Evolution Arena — watch your functions evolve under a real evolving engine
•🧩  Puzzle Mode → VM Challenge Pack — fix and extend the UL VM through curated puzzles

🔥 1. Core Engine — Shared by All Modes
The heart of the system — the part you already built. Everything else sits on this substrate.

Modules
core/
    tokenizer.py
    parser.py
    ast.py
    compiler.py
    bytecode.py
    vm.py
    evolving_engine.py
    runtime_state.py

Capabilities
•Deterministic tokenizer
•Full parser + AST builder
•Expression engine + bytecode compiler
•Stack-based VM with CALL / RET / JUMP
•Local scopes + stack frames
•Lists, objects, indexing, and properties
•Built-ins
•Evolving engine — mutation, fitness scoring, lineage tracking

🔥 2. UL Sandbox — Play Mode
Instant fun. Instant visibility. Instant "wow."
It's like opening the hood of a language engine and watching it run.

Core Features
•Live UL editor
•AST viewer
•Bytecode viewer
•VM stepper (step, run, rewind)
•Stack + heap visualizer
•Jump arrows (CALL, RET, JUMP)
•Execution timeline
•Performance meter
•"Mutate this code" button (optional)

UI Layout
UL Editor
AST Tree
Bytecode
VM Stack / Frames / Heap

Controls: [Run]  [Step]  [Reset]  [Show Mutations]   Exec time: 0.42 ms

🔥 3. Evolution Arena — Chaos Mode
Let devs watch code mutate, compete, and evolve. It's addictive. It's visual. It's alive.

Core Features
•Write a UL function
•Choose a goal:
◦Speed
◦Size
◦Correctness
◦Weirdness
◦Creativity
•Watch generations evolve in real time
•Mutation diff viewer
•Fitness graph
•Branching evolution tree
•Export best version

UI Layout
Original Function
Best Current Generation
Mutation Diff
Fitness Graph

Controls: [Start Evolution]  [Pause]  [Reset]   Target: Speed ▼   Gen: 42   Best: 0.987

How it Works
•Dev pastes or writes a UL function and picks a target
•Backend uses evolving_engine.py to mutate the AST, compile to bytecode, run in VM, and score fitness
•UI updates live: best generation, mutation diff, and fitness graph
•Optional: "Export best" copies the winning code to clipboard

🔥 4. VM Challenge Pack — Puzzle Mode
A set of VM puzzles devs can solve. Like Advent of Code, but for language nerds.

Challenge Types
•Fix a broken instruction
•Add JUMP_IF_FALSE
•Implement CALL / RET
•Make recursion work
•Optimize bytecode
•Add a built-in
•Make a UL program run correctly

Each Challenge Includes
•UL program
•Expected AST
•Expected bytecode
•Expected VM trace
•Failing behavior description
•Hints
•Solution validator

🔥 5. Unified Architecture
All three modes share the same engine. One codebase, three experiences.

UL Source
   ↓
Tokenizer
   ↓
Parser
   ↓
AST
   ↓
Bytecode Compiler
   ↓
VM
   ↓
Evolving Engine  (Arena only)

🔥 6. Unified Repo Structure
UL-Playground/
    core/
        tokenizer.py
        parser.py
        ast.py
        compiler.py
        bytecode.py
        vm.py
        evolving_engine.py
    sandbox/
        sandbox_app.py
        ui/
            editor.js
            ast_viewer.js
            bytecode_viewer.js
            vm_visualizer.js
    arena/
        arena_app.py
        ui/
            mutation_diff.js
            fitness_graph.js
            evolution_tree.js
    challenges/
        challenge_engine.py
        challenge_sets/
            01_basics/
            02_vm/
            03_advanced/
    shared_ui/
        components/
        themes/
    docs/
        README.md
        API.md
        CONTRIBUTING.md

FastAPI Entry Point
from fastapi import FastAPI
from ul_playground.sandbox.api    import router as sandbox_router
from ul_playground.arena.api      import router as arena_router
from ul_playground.challenges.api import router as challenges_router

app = FastAPI(title='UL Playground')
app.include_router(sandbox_router,    prefix='/api/sandbox')
app.include_router(arena_router,      prefix='/api/arena')
app.include_router(challenges_router, prefix='/api/challenges')

pyproject.toml
[project]
name = "ul-playground"
version = "0.1.0"
requires-python = ">=3.10"
dependencies = ["fastapi", "uvicorn[standard]"]

[project.scripts]
ul-playground = "ul_playground.app:run"

🔥 7. Roadmap — Build Order

Phase
Description
Phase 1 — Core Engine
You already built 90% of this. The deterministic substrate everything else runs on.
Phase 2 — UL Sandbox
Fastest to ship. Instantly fun. Perfect teaser — devs see their code come alive.
Phase 3 — Evolution Arena
Showcases the evolving engine. Huge viral potential — watching code evolve is addictive.
Phase 4 — VM Challenge Pack
Community engagement. Weekly challenges. Devs start contributing.
Phase 5 — Extensions
UL package manager · UL standard library · UL → WASM compiler · UL desktop app · UL web playground

🔥 8. Branding Options
Pick the vibe that fits your project:

🎈 Playful
🔧 Technical
⚡ Epic
UL Playground
UL Lab
UL Funhouse
UL DevKit
UL Engine Suite
UL Runtime Studio
UL Forge
UL Arena
UL Nexus

🏛 A Note on Naming: Mnemosyne
If your project name draws from Greek mythology, the repo name practically writes itself:

Mnemosyne Dev Playground
Mnemosyne = memory in Greek mythology. It fits what you're actually building: a deterministic, replayable, traceable substrate that remembers everything — every AST node, every bytecode instruction, every VM step.

Top-level folder:
Mnemosyne Dev Playground/

How to Run
pip install -e .
ul-playground

# Routes:
#   http://127.0.0.1:8000/            → Landing page
#   http://127.0.0.1:8000/sandbox     → UL Sandbox
#   http://127.0.0.1:8000/arena       → Evolution Arena
#   http://127.0.0.1:8000/challenges  → VM Challenge Pack

