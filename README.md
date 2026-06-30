# HuneX-Tsukire
A tool for extracting and repacking the `script_text.mrg` file from **Tsukihime -A piece of blue glass moon-** (Nintendo Switch).

> **Easier alternative:** Use [TsukiRe-Translator](https://github.com/Jannabie/TsukiRe-translation) if you want to edit the text directly through a GUI without needing to convert it to a `.txt` file first.

---
## What Is This?
`script_text.mrg` is an MZP-format archive file (`mrgd00`) that stores all of the game's dialogue text in UTF-8 encoding. This tool extracts the archive's contents into an editable `.txt` file, then repacks it back into an MRG format compatible with the game.

The extracted output is organized by route for easier navigation: **Common Route**, **Arcueid Route**, **Ciel Route**, and **QA**. Each line of text in the extracted file is linked to its unique offset ID so that the repacking process can recalculate all pointers precisely without breaking the engine's internal structure.

---
## Important Notes
* **Game Dump:** The game must first be dumped independently to obtain the required files.
* **Game Version:** This tool only works on and is compatible with the **Japanese Version**.

---
## Patch Result Comparison
<table>
  <tr>
    <th align="center">Before — Original Japanese Text</th>
    <th align="center">After — English Patch</th>
  </tr>
  <tr>
    <td><img src="https://i.imgur.com/Fl6iTqW.png" width="350"></td>
    <td><img src="https://i.imgur.com/eEtdYFB.jpeg" width="350"></td>
  </tr>
</table>

---
## File Structure
| File | Role |
|---|---|
| `mrg_tool.py` | Main tool — extracts and repacks MRG via GUI or CLI |
| `mrg_editor.py` | Simple text editor for the extracted files |
| `scene_map.json` | Offset-to-scene-name map, required for per-route organization |

---
## How to Use

### GUI Mode
Run it directly to open the graphical interface:

```bash
python mrg_tool.py
```

Open `script_text.mrg` using the available button, choose an output folder, then click Extract. Once the `.txt` file is finished being edited, reopen the tool and use the Repack function to generate a new MRG.

### CLI Mode

```bash
# Extract MRG into a text folder
python mrg_tool.py extract script_text.mrg output/

# Repack the text folder back into MRG
python mrg_tool.py repack output/ script_text_patched.mrg
```

---
## Installing the Patch into the Game (LayeredFS)
Place the repacked `script_text.mrg` at the following path depending on the emulator, without modifying the original ROM file:

**Yuzu:** `%AppData%\Roaming\yuzu\load\010064101344A000\[Mod Name]\romfs\script\`

**Ryujinx:** `%AppData%\Roaming\Ryujinx\mods\contents\010064101344a000\[Mod Name]\romfs\script\`

---
## Requirements
Python 3.8 or newer. `tkinter` is required for GUI mode and is automatically installed alongside Python on Windows.

---
## Disclaimer
This tool is created for educational and personal localization purposes. Use it in accordance with the copyright rules and Terms of Service of the original game.
