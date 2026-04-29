# Contributing to UL Language VM

Thanks for your interest in contributing. This doc explains how the engine works internally so you know exactly where to start.

---

## How the Engine Works

UL source code passes through five stages before anything executes. Each stage has one job.

```
UL Source Code
      ↓
  Tokenizer        →  ul_core.py  (Tokenizer class)
      ↓
   Parser          →  ul_core.py  (Parser class)
      ↓
  Compiler         →  ul_core.py  (Compiler class)
      ↓
     VM            →  ul_core.py  (VirtualMachine class)
```

---

## Stage 1 — Tokenizer

**What it does:** Reads raw source text character by character and outputs a flat list of tokens.

**A token looks like:**
```python
Token(type='NUMBER', value=5)
Token(type='IDENTIFIER', value='x')
Token(type='KEYWORD', value='set')
```

**Where to find it:** Look for the `Tokenizer` class in `ul_core.py`.

**Good first contributions:**
- Add a new keyword (e.g. `foreach`)
- Add support for a new literal type (e.g. floats, negative numbers)
- Improve error messages when an unknown character is encountered

---

## Stage 2 — Parser

**What it does:** Takes the flat token list and builds an Abstract Syntax Tree (AST) — a nested structure that represents the program's meaning, not just its text.

**A parsed assignment looks like:**
```python
AssignNode(
    name='x',
    value=NumberNode(value=5)
)
```

**Where to find it:** Look for the `Parser` class in `ul_core.py`. It uses recursive descent — each grammar rule is its own method.

**Good first contributions:**
- Add a new statement type (e.g. `for x in list`)
- Extend expression parsing (e.g. modulo `%`, power `**`)
- Improve parse error messages with line numbers

---

## Stage 3 — Compiler

**What it does:** Walks the AST and emits bytecode instructions — a flat list of operations the VM can execute.

**Example bytecode output:**
```
LOAD_CONST   5
STORE_VAR    x
LOAD_VAR     x
LOAD_VAR     y
ADD
STORE_VAR    z
```

**Where to find it:** Look for the `Compiler` class in `ul_core.py`.

**Good first contributions:**
- Add a new instruction (e.g. `JUMP_IF_FALSE` for short-circuit evaluation)
- Optimize redundant loads (e.g. `LOAD_VAR x` followed immediately by `STORE_VAR x`)
- Add a bytecode pretty-printer for debugging

---

## Stage 4 — Virtual Machine

**What it does:** Executes bytecode instructions one at a time using a stack and a frame system for local scopes.

**How the stack works:**
```
Instruction: ADD
Before:  stack = [3, 5]
After:   stack = [8]
```

**How frames work:** Each function call pushes a new frame onto the call stack. The frame holds local variables. When the function returns, the frame is popped.

**Where to find it:** Look for the `VirtualMachine` class in `ul_core.py`.

**Good first contributions:**
- Add a new built-in function (e.g. `range`, `type`, `input`)
- Add a `CALL_BUILTIN` instruction
- Implement tail call optimization
- Add a VM execution trace / debugger mode

---

## How to Run Locally

```bash
git clone https://github.com/warheart1984-ctrl/ul-language-vm.git
cd ul-language-vm
python ul_core.py
```

To test a UL program, edit the example at the bottom of `ul_core.py` or pass a file path as an argument.

---

## How to Add a New Built-in Function

1. Find the `builtins` dictionary in the `VirtualMachine` class
2. Add a new entry:

```python
'your_function': lambda args: # your logic here
```

3. Write a UL test program that calls it:

```
print your_function(x)
```

4. Run it and verify the output

---

## How to Add a New Keyword

1. Add the keyword string to the keywords list in the `Tokenizer`
2. Add a parse method in the `Parser` (e.g. `parse_foreach_statement`)
3. Add a new AST node class (e.g. `ForeachNode`)
4. Add a compile method in the `Compiler` that walks the new node
5. Add any new VM instructions needed to execute it

---

## VM Challenge Ideas

If you want to submit a VM puzzle for the upcoming Challenge Pack:

- Pick one broken or missing feature (e.g. recursion depth, missing instruction)
- Write a UL program that should work but doesn't
- Document the expected vs actual behavior
- Open an issue tagged `challenge`

---

## What's Coming Next

| Module | Description |
|---|---|
| `sandbox/` | Live web UI — edit UL, see AST + bytecode + VM state in real time |
| `arena/` | Evolution engine — mutate functions, score fitness, watch code evolve |
| `challenges/` | Curated VM puzzles with validators and hints |
| `evolving_engine.py` | AST mutation, lineage tracking, fitness scoring |

---

## Questions?

Open an issue. All questions welcome — no such thing as a dumb one when you're building a language from scratch.

---

*Built by [@warheart1984-ctrl](https://github.com/warheart1984-ctrl)*
