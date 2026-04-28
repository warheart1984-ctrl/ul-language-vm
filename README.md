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
