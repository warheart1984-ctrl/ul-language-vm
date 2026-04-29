# 🔥 UL Language VM

> A minimal custom language runtime built from scratch — tokenizer, parser, bytecode compiler, and stack-based virtual machine. Designed for deterministic execution and as the foundational engine of the **AAIS architecture**.

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![License](https://img.shields.io/badge/License-Apache%202.0-green?style=flat-square)
![Version](https://img.shields.io/badge/Version-0.1.0-orange?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

---

## What is UL?

UL is a custom programming language with its own runtime — built entirely from scratch in Python. It's not a toy script. It's a real execution substrate: source code goes in, tokens come out, an AST gets built, bytecode gets compiled, and a stack-based VM runs it deterministically.

This repo is the core engine. Everything else — the playground, the evolution arena, the VM challenge pack — runs on top of this.

---

## Features

| Feature | Status |
|---|---|
| Tokenizer | ✅ |
| Recursive descent parser | ✅ |
| AST builder | ✅ |
| Bytecode compiler | ✅ |
| Stack-based VM | ✅ |
| Variable assignment | ✅ |
| Arithmetic operations | ✅ |
| Functions with parameters + return values | ✅ |
| Conditionals (`if` / `else`) | ✅ |
| Loops (`while`, `repeat`) | ✅ |
| Lists and dictionaries | ✅ |
| Built-ins (`print`, `len`, etc.) | ✅ |

---

## Quick Start

```bash
git clone https://github.com/warheart1984-ctrl/ul-language-vm.git
cd ul-language-vm
python ul_core_1.py
```

---

## Example

```
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
```

**Output:**
```
8
loop
loop
loop
```

---

## Architecture

Source code flows through the full pipeline:

```
UL Source Code
      ↓
  Tokenizer        →  breaks source into tokens
      ↓
   Parser          →  recursive descent, builds AST
      ↓
     AST           →  abstract syntax tree
      ↓
  Bytecode         →  compiles AST to instructions
 Compiler
      ↓
Stack-based VM     →  executes bytecode deterministically
```

---

## Roadmap — UL Dev Playground

This VM is Phase 1 of a larger project: the **UL Dev Playground** — a transparent, interactive environment for developers to explore how programming languages actually work.

### Three Modes

#### 🎮 Play Mode — UL Sandbox
Write UL code and watch the AST, bytecode, and VM state update live. Like opening the hood of a language engine while it's running.

- Live UL editor
- AST viewer
- Bytecode viewer
- VM stepper (step / run / rewind)
- Stack + heap visualizer
- Execution timeline
- Performance meter

#### 🔥 Chaos Mode — Evolution Arena
Write a UL function, pick a goal (speed, size, correctness, weirdness), and watch the engine mutate and evolve your code across generations.

- Mutation diff viewer
- Fitness graph
- Branching evolution tree
- Export best version

#### 🧩 Puzzle Mode — VM Challenge Pack
Curated VM puzzles. Fix broken instructions. Implement `CALL` / `RET`. Make recursion work. Like Advent of Code, but for language nerds.

- Fix a broken instruction
- Add `JUMP_IF_FALSE`
- Implement `CALL` / `RET`
- Optimize bytecode
- Add a built-in

### Build Order

| Phase | Milestone | Description |
|---|---|---|
| ✅ 1 | Core Engine | Tokenizer → Parser → Bytecode Compiler → VM |
| 🔜 2 | UL Sandbox | Live editor with AST + VM visualizer |
| 🔜 3 | Evolution Arena | Mutation engine + fitness graph |
| 🔜 4 | VM Challenge Pack | Weekly puzzles, community contributions |
| 🔜 5 | Extensions | Package manager · Standard library · WASM compiler |

---

## Project Structure (Planned)

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
├── arena/
│   ├── arena_app.py
│   └── ui/
├── challenges/
│   ├── challenge_engine.py
│   └── challenge_sets/
└── docs/
```

---

## Part of the AAIS Architecture

UL is the execution substrate for **AAIS** — a structured system designed around deterministic, auditable, and traceable behavior. Every token, every AST node, every bytecode instruction is intentional and inspectable.

---

## Contributing

This project is early and moving fast. If you want to:

- Add a new built-in function
- Extend the VM instruction set
- Build a UI for the sandbox
- Submit a VM challenge puzzle

Open an issue or a PR. All contributions welcome.

---

## License

[Apache 2.0](LICENSE) — use it, fork it, build on it.

---

*Built by [@warheart1984-ctrl](https://github.com/warheart1984-ctrl)*
