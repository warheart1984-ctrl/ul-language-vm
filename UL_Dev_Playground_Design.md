# 🔥 UL Dev Playground — System Design

> A transparent, deterministic language playground with three modes.

**A single product. Three modes. One deterministic substrate.**

- 🎮 **Play Mode → UL Sandbox** — write UL, see AST, bytecode, and VM state live
- 🔥 **Chaos Mode → Evolution Arena** — watch your functions evolve under a real evolving engine
- 🧩 **Puzzle Mode → VM Challenge Pack** — fix and extend the UL VM through curated puzzles

---

## 🔥 1. Core Engine — Shared by All Modes

The heart of the system. Everything else sits on this substrate.

### Module Structure

```
core/
    tokenizer.py
    parser.py
    ast.py
    compiler.py
    bytecode.py
    vm.py
    evolving_engine.py
    runtime_state.py
```

### Capabilities

- Deterministic tokenizer
- Full parser + AST builder
- Expression engine + bytecode compiler
- Stack-based VM with `CALL` / `RET` / `JUMP`
- Local scopes + stack frames
- Lists, objects, indexing, and properties
- Built-ins
- Evolving engine — mutation, fitness scoring, lineage tracking

---

## 🎮 2. UL Sandbox — Play Mode

Instant fun. Instant visibility. Instant "wow."

*It's like opening the hood of a language engine and watching it run.*

### Core Features

- Live UL editor
- AST viewer
- Bytecode viewer
- VM stepper (step, run, rewind)
- Stack + heap visualizer
- Jump arrows (`CALL`, `RET`, `JUMP`)
- Execution timeline
- Performance meter
- "Mutate this code" button (optional)

### UI Layout

```
┌─────────────────────┬─────────────────────┐
│      UL Editor      │      AST Tree        │
├─────────────────────┼─────────────────────┤
│      Bytecode       │  VM Stack/Frames/Heap│
└─────────────────────┴─────────────────────┘
Controls: [Run]  [Step]  [Reset]  [Show Mutations]   Exec time: 0.42 ms
```

---

## 🔥 3. Evolution Arena — Chaos Mode

Let devs watch code mutate, compete, and evolve. It's addictive. It's visual. It's alive.

### Core Features

- Write a UL function
- Choose a goal:
  - Speed
  - Size
  - Correctness
  - Weirdness
  - Creativity
- Watch generations evolve in real time
- Mutation diff viewer
- Fitness graph
- Branching evolution tree
- Export best version

### UI Layout

```
┌─────────────────────┬─────────────────────┐
│  Original Function  │ Best Current Gen     │
├─────────────────────┼─────────────────────┤
│    Mutation Diff    │    Fitness Graph     │
└─────────────────────┴─────────────────────┘
Controls: [Start Evolution]  [Pause]  [Reset]   Target: Speed ▼   Gen: 42   Best: 0.987
```

### How it Works

- Dev pastes or writes a UL function and picks a target
- Backend uses `evolving_engine.py` to mutate the AST, compile to bytecode, run in VM, and score fitness
- UI updates live: best generation, mutation diff, and fitness graph
- Optional: "Export best" copies the winning code to clipboard

---

## 🧩 4. VM Challenge Pack — Puzzle Mode

A set of VM puzzles devs can solve. Like Advent of Code, but for language nerds.

### Challenge Types

- Fix a broken instruction
- Add `JUMP_IF_FALSE`
- Implement `CALL` / `RET`
- Make recursion work
- Optimize bytecode
- Add a built-in
- Make a UL program run correctly

### Each Challenge Includes

- UL program
- Expected AST
- Expected bytecode
- Expected VM trace
- Failing behavior description
- Hints
- Solution validator

---

## 🔥 5. Unified Architecture

All three modes share the same engine. One codebase, three experiences.

```
UL Source Code
      ↓
  Tokenizer          →  breaks source into tokens
      ↓
   Parser            →  recursive descent, builds AST
      ↓
     AST             →  abstract syntax tree
      ↓
Bytecode Compiler    →  compiles AST to instructions
      ↓
  Stack-based VM     →  executes bytecode deterministically
      ↓
 Evolving Engine     →  (Arena only) mutation + fitness scoring
```

---

## 🔥 6. Unified Repo Structure

```
UL-Playground/
├── core/
│   ├── tokenizer.py
│   ├── parser.py
│   ├── ast.py
│   ├── compiler.py
│   ├── bytecode.py
│   ├── vm.py
│   └── evolving_engine.py
├── sandbox/
│   ├── sandbox_app.py
│   └── ui/
│       ├── editor.js
│       ├── ast_viewer.js
│       ├── bytecode_viewer.js
│       └── vm_visualizer.js
├── arena/
│   ├── arena_app.py
│   └── ui/
│       ├── mutation_diff.js
│       ├── fitness_graph.js
│       └── evolution_tree.js
├── challenges/
│   ├── challenge_engine.py
│   └── challenge_sets/
│       ├── 01_basics/
│       ├── 02_vm/
│       └── 03_advanced/
├── shared_ui/
│   ├── components/
│   └── themes/
└── docs/
    ├── README.md
    ├── API.md
    └── CONTRIBUTING.md
```

### FastAPI Entry Point

```python
from fastapi import FastAPI
from ul_playground.sandbox.api    import router as sandbox_router
from ul_playground.arena.api      import router as arena_router
from ul_playground.challenges.api import router as challenges_router

app = FastAPI(title='UL Playground')
app.include_router(sandbox_router,    prefix='/api/sandbox')
app.include_router(arena_router,      prefix='/api/arena')
app.include_router(challenges_router, prefix='/api/challenges')
```

### pyproject.toml

```toml
[project]
name = "ul-playground"
version = "0.1.0"
requires-python = ">=3.10"
dependencies = ["fastapi", "uvicorn[standard]"]

[project.scripts]
ul-playground = "ul_playground.app:run"
```

### How to Run

```bash
pip install -e .
ul-playground
```

Routes once running:

```
http://127.0.0.1:8000/            →  Landing page
http://127.0.0.1:8000/sandbox     →  UL Sandbox
http://127.0.0.1:8000/arena       →  Evolution Arena
http://127.0.0.1:8000/challenges  →  VM Challenge Pack
```

---

## 🔥 7. Roadmap — Build Order

| Phase | Description |
|---|---|
| ✅ **Phase 1 — Core Engine** | The deterministic substrate everything else runs on. Already 90% built. |
| 🔜 **Phase 2 — UL Sandbox** | Fastest to ship. Instantly fun. Devs see their code come alive. |
| 🔜 **Phase 3 — Evolution Arena** | Showcases the evolving engine. Huge viral potential. |
| 🔜 **Phase 4 — VM Challenge Pack** | Community engagement. Weekly challenges. Devs start contributing. |
| 🔜 **Phase 5 — Extensions** | UL package manager · standard library · WASM compiler · desktop app · web playground |

---

## 🔥 8. Branding Options

| 🎈 Playful | 🔧 Technical | ⚡ Epic |
|---|---|---|
| UL Playground | UL DevKit | UL Forge |
| UL Lab | UL Engine Suite | UL Arena |
| UL Funhouse | UL Runtime Studio | UL Nexus |

---

## 🏛 A Note on Naming: Mnemosyne

If your project draws from Greek mythology, the name practically writes itself:

**Mnemosyne Dev Playground**

Mnemosyne = memory in Greek mythology. It fits exactly what this is: a deterministic, replayable, traceable substrate that remembers everything — every AST node, every bytecode instruction, every VM step.

```
Mnemosyne Dev Playground/
```

---

*Built by [@warheart1984-ctrl](https://github.com/warheart1984-ctrl)*
