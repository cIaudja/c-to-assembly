# C to Assembly

Assignment for the Computer Architecture course at the University of Verona (2022–23). The program is a car settings menu that runs in the terminal (date, time, automatic door lock, turn signals, tyre pressure reset…). It was first written in C and then reimplemented in 32-bit x86 Assembly (AT&T syntax, GNU `as`). Both versions behave the same way.

## Structure

- `src/` – `elaborato.s` (Assembly version) and `elaborato.c` (reference C version)
- `obj/` – object files created by the build
- `bin/` – the compiled executable
- `Makefile`
- `Relazione.pdf` – project report (in Italian)

## How to run it

The Makefile builds a 32-bit Linux executable with `as` and `ld`, so it does **not** run directly on macOS. Use either a Linux machine/VM or Docker.

### Option A: Linux (or a Linux VM)

1. Install the tools (Ubuntu/Debian):

   ```bash
   sudo apt install build-essential
   ```

2. Get the project and go into its folder:

   ```bash
   git clone https://github.com/cIaudja/c-to-assembly.git
   cd c-to-assembly
   ```

3. Build:

   ```bash
   make
   ```

4. Run:

   ```bash
   ./bin/elaborato
   ```

### Option B: Docker on macOS

1. Start Docker Desktop.
2. Open Terminal and go into the project folder:

   ```bash
   cd path/to/c-to-assembly
   ```

3. Start a 32-bit Linux container with the project folder mounted inside it:

   ```bash
   docker run --rm -it --platform linux/386 -v "$PWD":/work -w /work i386/debian:bookworm bash
   ```

4. Inside the container, install the tools (you need to do this every time you start a new container):

   ```bash
   apt-get update && apt-get install -y binutils make
   ```

5. Build and run as in Option A:

   ```bash
   make
   ./bin/elaborato
   ```

6. Type `exit` to leave the container.

### Using the program

- Press **↑** or **↓** and then **Enter** to move through the menu.
- Press **→** and then **Enter** to open the selected item (door lock, back-home, turn signals, tyre pressure).
- Press **Enter** on its own to go back to the main menu.
- Press **Ctrl+C** to quit.

To start in **supervisor mode**, which adds the turn signals and tyre pressure items, pass the code `2244`:

```bash
./bin/elaborato 2244
```

### Running the C version

```bash
gcc src/elaborato.c -o elaborato_c
./elaborato_c
```

The C version also runs on macOS.

### Cleaning up

```bash
make clean
```

removes the object files and the executable.
