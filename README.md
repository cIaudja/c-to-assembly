# C to Assembly

Assignment for the Computer Architecture course at the University of Verona (2022–23). The program was first written in C and then reimplemented in 32-bit x86 Assembly (AT&T syntax, GNU `as`). Both versions behave the same way: the program is an interactive menu that runs in the terminal.

## Structure

- `src/` – `elaborato.s` (Assembly version) and `elaborato.c` (reference C version)
- `obj/` – object files created by the build
- `bin/` – the compiled executable
- `Makefile`
- `Relazione.pdf` – project report (in Italian)

## Build and run

The Makefile assembles and links a 32-bit ELF binary with `as` and `ld`, so you need Linux (a VM works fine).

```bash
make
./bin/elaborato
```

`make clean` removes the object files and the executable.
