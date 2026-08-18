# vscode-kindle-loc

A VS Code extension that shows the Kindle **location** (the "Loc" number Kindle uses instead of page numbers) for your cursor position in a plain text file, and lets you jump straight to any location.

If you sideload `.txt` files onto a Kindle, the device splits the file into "locations" based on byte offsets rather than pages. This extension mirrors that calculation inside VS Code, so you can align edits, bookmarks, or reading notes with the exact spot a Kindle would show.

This project started as a fork of [vscode-position](https://github.com/joerohde/vscode-position), adapted specifically for Kindle's location scheme.

## Features

- **Live location in the status bar** — shows the current Kindle location (`kloc`) for the cursor position in the active text file.

  ![animation](assets/kindle-loc.gif)

- **Jump to a location** — click the status bar item (or run the `kindle-loc.kloc` command) to type in a target location number and jump the cursor there.

## Usage

1. Open a plain text file in VS Code.
2. Look at the bottom-right status bar — it shows `kloc <number>` for your current cursor position.
3. Click the status bar item to open a prompt, type a location number, and press Enter to jump there.

## Installation

Search for **kindle-loc** in the VS Code Extensions view, or install it from the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=katalog.kindle-loc).

To build and run it from source instead:

```bash
git clone https://github.com/katalog/vscode-kindle-loc.git
cd vscode-kindle-loc
npm install
npm run compile
```

Then open the folder in VS Code and press `F5` to launch an Extension Development Host with `kindle-loc` active, or package it yourself with [`vsce`](https://github.com/microsoft/vscode-vsce) and install the resulting `.vsix` via **Extensions: Install from VSIX...**.

## Requirements

None — works on any plain text file with no extra setup.

## Extension Settings

This extension doesn't contribute settings to the Settings UI, but it does read one value if you add it to your `settings.json` manually:

| Setting | Description | Default |
|---|---|---|
| `kindle-loc.positionName` | Label shown before the location number in the status bar | `kloc` |

## Known Issues

Location math is based on a fixed bytes-per-location constant, so very large files or non-ASCII-heavy text may cause the displayed number to drift slightly from what the actual Kindle device shows.

## Release Notes

### 0.9.2

Rewrote the README for the Marketplace listing.

### 0.9.1

Ongoing refinements after the initial release.

### 1.0.0

Initial release.

## License

See [LICENSE](LICENSE).
