🔥 UL Language VM

A minimal custom language runtime built from scratch — tokenizer, parser, bytecode compiler, and stack-based virtual machine.

Designed for deterministic execution and as the foundational engine of the AAIS architecture.

🧠 What is UL?

UL is a custom programming language with its own runtime — built entirely from scratch in Python.

It is not a toy interpreter.

It is a deterministic execution substrate:

Source code → tokens → AST → bytecode → execution
Every step is explicit, inspectable, and controlled
The same input always produces the same output

This repository contains the core engine.

Everything else — the playground, evolution arena, and challenge system — builds on top of it.

⚙️ What this is / is not
✅ What this is
A working custom language runtime
A deterministic execution engine
A foundation for governed systems (AAIS)
🚫 What this is not
Not a general-purpose Python framework
Not a toy scripting demo
Not production-hardened (yet)
🚀 Features
Feature	Status
Tokenizer	✅
Recursive descent parser	✅
AST builder	✅
Bytecode compiler	✅
Stack-based VM	✅
Variable assignment	✅
Arithmetic operations	✅
Functions (params + return)	✅
Conditionals (if / else)	✅
Loops (while, repeat)	✅
Lists and dictionaries	✅
Built-ins (print, len, etc.)	✅
⚡ Quick Start
git clone https://github.com/warheart1984-ctrl/ul-language-vm.git
cd ul-language-vm
python ul_core_1.py
💡 Example
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

Output:

8
loop
loop
loop
🧩 Architecture
UL Source Code
      ↓
  Tokenizer        → breaks source into tokens
      ↓
   Parser          → recursive descent, builds AST
      ↓
     AST           → abstract syntax tree
      ↓
  Bytecode         → compiled instructions
 Compiler
      ↓
Stack-based VM     → deterministic execution
🧪 Dev Playground

The interactive UL sandbox is included as a packaged build:

dev playground.zip contains the UL sandbox environment
Kept separate to maintain a clean, minimal core runtime
Usage
Extract dev playground.zip
Open the extracted folder
Run the playground app (instructions inside)

👉 This represents Phase 2 (UL Sandbox) of the roadmap.

🗺️ Roadmap — UL Dev Playground

This VM is Phase 1 of a larger system.

🎮 Play Mode — UL Sandbox
Live UL editor
AST viewer
Bytecode viewer
VM stepper (step / run / rewind)
Stack + heap visualizer
Execution timeline
🔥 Chaos Mode — Evolution Arena
Mutation engine
Fitness graph
Evolution tree
Export best version
🧩 Puzzle Mode — VM Challenge Pack
Fix broken instructions
Implement CALL / RET
Optimize bytecode
Add built-ins
📦 Build Order
Phase	Milestone	Description
✅ 1	Core Engine	Full runtime pipeline
🔜 2	UL Sandbox	Interactive visualizer
🔜 3	Evolution Arena	Mutation + fitness
🔜 4	VM Challenges	Community puzzles
🔜 5	Extensions	Packages · stdlib · WASM
🧠 Part of the AAIS Architecture

UL is the execution substrate for AAIS.

It enables:

deterministic execution
full traceability
inspectable computation

Every token, AST node, and instruction is intentional.

This makes UL suitable for governed runtime systems, not just general scripting.

🤝 Contributing

Want to help?

Add built-ins
Extend VM instructions
Build UI for sandbox
Create challenge puzzles

Open an issue or PR — contributions welcome.

📜 License

Apache 2.0 — use it, fork it, build on it.

Built by @warheart1984-ctrl
