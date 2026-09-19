# chihiro-netboot

Convert MAME Sega Chihiro dumps into playable netboot images.

## What you need

From a standard MAME ROM set (which you must provide yourself):

1. **The game's `.zip`**, e.g. `hotd3.zip` (contains the decryption key)
2. **The game's disc**, either of:
   - a MAME `.chd`, e.g. `hotd3/gdx-0001.chd`
   - a Redump `.cue` with its `.bin` tracks beside it

**chdman** is only needed for `.chd` files. A Redump cue/bin set is read
directly, with nothing else to install. On Windows chdman is provided on
the Releases page next to the tool; on macOS/Linux install it with your
package manager:

| Platform | chdman |
|----------|--------|
| Windows | provided on the [Releases](../../releases) page |
| macOS | `brew install rom-tools` |
| Linux (apt) | `sudo apt install mame-tools` |
| Linux (pacman) | `sudo pacman -S mame-tools` |

## Windows

Download **`chihiro-netboot.exe`** and **`chdman.exe`** from the
[Releases](../../releases) page and put both in the folder with your
games. Nothing to install.

```
my-chihiro-games/
  chihiro-netboot.exe
  chdman.exe
  hotd3.zip
  hotd3/gdx-0001.chd
```

Double-click **`chihiro-netboot.exe`**. All games are found and converted
automatically into `output/`. You can also drag-and-drop a game folder
onto the exe.

Note: the first launch takes a few seconds (the single-file executable
unpacks itself). The executable is built by CI from the source in this
repository.

## macOS / Linux

Python 3 is already on your system. Download `chihiro-netboot.py` from
the [Releases](../../releases) page and run it from the folder with your
MAME files:

```
python3 chihiro-netboot.py
```

Or point it at a folder, or at one game explicitly:

```
python3 chihiro-netboot.py /path/to/games
python3 chihiro-netboot.py hotd3/gdx-0001.chd hotd3.zip
python3 chihiro-netboot.py "hotd3/Disc (Track 1).cue" hotd3.zip
```

## Output

Creates `output/<game>.bin` for each game, ready to netboot.

```
output/
  hotd3.bin      (357 MB)
  vcop3.bin      (461 MB)
```

## License

MIT. Based on [JayFoxRox's Chihiro-Tools](https://github.com/JayFoxRox/Chihiro-Tools).

chdman is part of [MAME](https://github.com/mamedev/mame) ((c) the MAME team,
GPL-2.0-or-later) and may be redistributed alongside releases under that
license.

This tool converts dumps you already own from one format to another. It
contains no keys, no game data, and no way to obtain either.
