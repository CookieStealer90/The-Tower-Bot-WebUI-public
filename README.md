<div align="center">
<img width="422" height="95" alt="image" src="https://github.com/user-attachments/assets/7b986cb9-a470-4c9f-a26d-56d1b1127587" />
  
#  "The Tower" Automation-Bot (Python + ADB, MEmu/MuMu)


![Python](https://img.shields.io/badge/Python-3.8%E2%80%933.13-3776AB?logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)
![WebUI](https://img.shields.io/badge/WebUI-Flask-000000?logo=flask&logoColor=white)
![Socket.IO](https://img.shields.io/badge/Realtime-Socket.IO-010101?logo=socketdotio&logoColor=white)
![OpenCV](https://img.shields.io/badge/Vision-OpenCV-5C3EE8?logo=opencv&logoColor=white)
![ADB](https://img.shields.io/badge/ADB-Required-3DDC84?logo=android&logoColor=white)
![Layout](https://img.shields.io/badge/Layout-1600x900%20Landscape-2ea44f)
![Emulator](https://img.shields.io/badge/Emulator-MEmu%20%2F%20MuMu-00A3E0)
![Config](https://img.shields.io/badge/Config-WebUI%20%2B%20user__overrides-6f42c1)
<br>**A "The Tower" automation bot (gem clicking + upgrade workflows) with a modern Web UI — built for MEmu/MuMu via ADB.**.

</div>
<br>


# ⚠️ Project Status
THIS PROJECT IS NOT RELEASED.
It is a showcase of my development work only.

Maybe it will be released in the future — maybe not.



## Table of contents
- [Features](#features)
- [Screenshots](#screenshots)
- [WebUI overview](#webui-overview)
- [Project structure](#project-structure)
- [Requirements](#requirements)
- [Getting started](#getting-started)
- [Configuration overview](#configuration-overview)
- [WebUI: Settings tab (custom settings)](#webui-settings-tab-custom-settings)
- [WebUI: Perk-Pilot](#webui-perk-pilot)
- [WebUI: Wave-Pilot](#webui-wave-pilot)
- [WebUI: Workflow editor](#webui-workflow-editor)
- [User overrides: where everything is stored](#user-overrides-where-everything-is-stored)
- [Reload vs Restart](#reload-vs-restart)
- [ADB auto-connect & multi-instance](#adb-auto-connect--multi-instance)
- [Anti-detection features](#anti-detection-features)
- [How it works (under the hood)](#how-it-works-under-the-hood)
- [Troubleshooting](#troubleshooting)
- [Disclaimer](#disclaimer)

<br>

## Features
- Reliable **gem clicker** + **floating-gem clicker**
- **Auto restart the game on game-over or app-crash**
- **Web Dashboard** (Flask + Socket.IO): control the bot from your PC browser **or your phone/tablet on the same Wi‑Fi**
- **Live log stream** in the WebUI + `bot.log` on disk
- **Last screenshot** viewer in the WebUI
- **Stats capture** (optional): periodic screenshots of the in-game stats screen + manual capture button in WebUI
- **Perk-Pilot**: priority-based perk selection with WebUI reorder + blacklist
- **Wave-Pilot**: automatic card preset switching + WF toggling based on detected tier/wave
- **Workflows (WF1,2,3,5,6)**: upgrade & restart workflows + full WebUI workflow editor
- **AFK-Break-Mode** (random long pauses) with **wave gating** per tier (Wave-Pilot rules)
- **Random-Tap**: periodic random taps to look “human” (toggle in WebUI)
- Pure **ADB input + screenshots** driven (no root, no overlays)
- Template matching via **OpenCV** (ROI-based for speed & stability), no OCR
- **ADB auto-connect** with port scanning and multi-instance fallback
- **Log rotation** (configurable) + crash/restart counters
- many features to prevent bot-detection

<br>

## Screenshots
### Web GUI and Configuration

<p align="center">
  <a href="https://github.com/user-attachments/assets/78fe8aa9-c7d7-42b6-a4b4-3d6e39d67453">
    <img src="https://github.com/user-attachments/assets/78fe8aa9-c7d7-42b6-a4b4-3d6e39d67453" width="100%" />
  </a>
</p>

<p align="center">
  <a href="https://github.com/user-attachments/assets/b93b5163-c314-42d1-98fe-301453d73989">
    <img src="https://github.com/user-attachments/assets/b93b5163-c314-42d1-98fe-301453d73989" width="49%" />
  </a>
  <a href="https://github.com/user-attachments/assets/ebe256d4-d138-4bcd-bcab-8b2ce2cb7847">
    <img src="https://github.com/user-attachments/assets/ebe256d4-d138-4bcd-bcab-8b2ce2cb7847" width="49%" />
  </a>
  <a href="https://github.com/user-attachments/assets/bca4476c-947c-4a03-8bba-13f0c3ca343b">
    <img src="https://github.com/user-attachments/assets/bca4476c-947c-4a03-8bba-13f0c3ca343b" width="49%" />
  </a>
  <a href="https://github.com/user-attachments/assets/6ea699ae-1834-4d06-b6ac-d0f7c65ca8d6">
    <img src="https://github.com/user-attachments/assets/6ea699ae-1834-4d06-b6ac-d0f7c65ca8d6" width="49%" />
  </a>
</p>

### bot.log
<details>
  <summary><b>(click to expand)</b></summary>
  <img width="1462" height="992" alt="bot.log screenshot 1" src="https://github.com/user-attachments/assets/94f5fa0f-6bf4-410f-8b29-17d0bf1e81dd" />
  <br>
  <img width="1350" height="417" alt="bot.log screenshot 2" src="https://github.com/user-attachments/assets/93c9afe6-d78e-4c88-90c3-da7db889e078" />

</details>

### Debug Screenshots<br>
<table>
  <tr>
    <td align="center" valign="top">
      <img width="360" alt="Floating Clicker" src="https://github.com/user-attachments/assets/15de2f00-49dd-4af5-9980-64392ea61a3c" />
    </td>
    <td align="center" valign="top">
      <img width="430" height="385" alt="Perk Chooser" src="https://github.com/user-attachments/assets/4aa3ad4a-cafb-4b4c-ae22-684e6257ac77" /><br><br>
      <img width="440" height="230" alt="wf_star_enemy_attack_skip_step3_click_template_annot_20260208_214600_776" src="https://github.com/user-attachments/assets/d7848301-545e-47c6-9800-7b0169c6b70d" />
  </tr>
  <tr>
    <td align="center"><b>Floating Clicker</b></td>
    <td align="center"><b>Perk Chooser & Worklow</b></td>
  </tr>
</table>

</table>



## Project structure

```
The-Tower-Clicker-Bot-WebUI/
├── main.py                       # Entry point (starts WebUI + bot thread)
├── tray_runner.py                # Windows tray icon launcher (recommended)
├── Start TowerBot WebUI.bat       # Starts tray_runner via pythonw
├── Start TowerBot WebUI.vbs       # Same, fully silent (good for Startup folder)
├── INSTALL-ENVIRONMENT.bat        # Quick dependency install
├── TEST-ENVIRONMENT.bat           # Environment check (Python/OpenCV/ADB/device)
├── requirements.txt               # Pinned dependency versions
│
├── config/
│   ├── settings.py                # Defaults (WebUI overrides are applied on import)
│   ├── config_workflows.py        # Default workflows (WF1–WF6)
│   ├── config_wavepilot.py        # Default Wave-Pilot rules
│   ├── app_state.py               # Mutable runtime state (shared)
│   ├── runtime_flags.py           # SUPPRESS_EXCEPTIONS flag
│   ├── user_overrides.py          # Loads + validates user override JSON
│   ├── user_settings.json         # (generated) WebUI "Settings" tab overrides
│   ├── user_wavepilot.json        # (generated) WebUI Wave-Pilot rules
│   ├── user_workflows.json        # (generated) WebUI workflow editor
│   └── user_perks.json            # (generated) WebUI perk priorities/blacklist
│
├── web/
│   ├── app.py                     # Flask + Socket.IO server + command bridge
│   ├── config_api.py              # /api/config/* endpoints
│   ├── security.py                # LAN-only + same-origin protection
│   ├── state_builder.py           # Builds the state dict pushed every second
│   ├── templates/index.html       # Dashboard UI 
│   └── static/                    # CSS + JS (settings, editors, log, etc.)
│
├── automation/
│   ├── wavepilot.py               # Tier/Wave detection + preset switching engine
│   ├── workflows.py               # Workflow execution engine
│   └── scheduler.py               # Auto-scheduling for WF1–WF6
│
├── features/
│   ├── gem_clicker.py              # Normal + floating gem clicker (+ 2-factor "running detection") engine
│   ├── perk_chooser.py             # Perk-pilot engine
│   ├── anti_detection.py           # AFK-Break + Random-Tap engine
│   └── stats_collector.py          # Stats capture engine
│   └── gem_statistics.py           # gem stats
│
├── core/
│   ├── adb_helper.py               # ADB connect/reconnect + port scan
│   ├── screenshot.py               # Screenshot capture/cache via ADB
│   └── file_logger.py              # File logging + log rotation
│
├── ui/
│   ├── ui_console.py               # Console UI rendering (optional)
│   ├── ui_helpers.py               # Reload/apply config at runtime
│   └── hotkeys.py                  # WebUI command queue handler
│
└── images/
    ├── *_tpl.png                   # Templates used by workflows and some other stuff
    ├── Perk/                       # Perk-Pilot templates (Pxx_Name.png)
    └── Card_TPL_SWITCH/            # Tier/Wave digit templates for Wave-Pilot
```

<br>

## WebUI overview

When you start the bot via TowerBot WebUI.vbs or *.bat, it prints a list of URLs like:

- `http://localhost:5000`
- `http://<your-lan-ip>:5000`
<img width="690" height="216" alt="image" src="https://github.com/user-attachments/assets/5774dbd3-bb1a-4273-957a-e4cb2373a34b" />

Open it in your browser. Welcome to the WebUI! It gives you:

### Controls (top bar)
- **Gems**: pause/resume gem clicking
- **Perk-Pilot**: enable/disable perk chooser
- **Auto WF**: master toggle for scheduled workflows
- **WF1–WF6**: per-workflow auto toggle + manual “▶” trigger
- **Wave-Pilot**: enable/disable tier/wave detection + preset automation
- **AFK-Mode**: enable/disable random pause system
- **Random-Tap**: enable/disable random taps
- **Stats**: enable/disable stats collector + manual capture button
- **Debug**: show live template match scores (slash/perk/floating/active_validator/max_perk, plus tier/wave)

### Panels (main area)
- **Status**: running/paused, gem counters, cooldowns, restarts/crashes
- **Workflows**: next scheduled execution + whether the toggle came from “manual” or “pilot”
- **Wave-Pilot card**: current tier/wave/preset + the next scheduled rules (preview)
- **Stats images**: latest captured stats screenshots (two tabs)
- **Screenshot tab**: auto-refresh last screenshot from the bot
- **Log stream**: live bot log output

### Security note (important)
The dashboard API is **LAN-only by default** and checks same-origin requests (see `web/security.py`).  
If you *really* want public access, set environment variable:

- `TOWERBOT_ALLOW_PUBLIC=1`

…but don’t do that unless you know what you’re doing (firewall / reverse proxy / authentication) - all not tested and implemented at current state!.

<br>


## Requirements

### LABS
For a correct working perk-pilot you need **Lab: 4 perk options**.

### Emulator layout (required)

This bot is built and tuned for a **fixed emulator layout**:

- **MEmu Android 9** or **MuMu Android 12**  
- **Tablet**
- **Landscape**
- **1600×900** (the bot assumes this layout)! not 900x1600! (1600x900 is needed for crash recovery in WF4)
- ADB enabled (standard MEmu/MuMu ADB setup is fine)

Renderer (recommended):
- **DirectX** recommended in MEmu
- In MuMu I recommend **Vulkan**
- Vulkan can also work in MEmu, but can cause screenshot issues depending on GPU/driver/emulator

> [!IMPORTANT]
> Set the game language to **English** inside your game, otherwise template name-matching will fail.  
> Other languages are **not supported**.

> [!NOTE]
> Other emulators / real devices can work via ADB, but this repo is **not tuned for them** out of the box.  
> You must adapt **ROIs / templates / coordinates** yourself.

### Python
Use **Python 3.13 or below** (3.10–3.13 recommended).  
Newer versions (3.14+) can break OpenCV/NumPy wheels on Windows.

<br>

## Getting started

### 1) Install location (ADB convenience)
The bot tries to find `adb.exe` in the **parent directory** first (then falls back to known emulator paths).
So a simple setup is:

- Put the bot in a folder directly below your emulator’s `adb.exe`

If you don’t want that: it still works, but you may need to configure **ADB → DEVICE** (see below).

### 2) Environment test (recommended)
Run:

`TEST-ENVIRONMENT.bat`

It checks:
- Python version + `import cv2`
- Flask / SocketIO / tray deps
- ADB installations found
- `adb devices` output and whether your device is reachable

### 3) Install dependencies
Option A (recommended):

`py -m pip install -r requirements.txt`

Option B (quick):

`INSTALL-ENVIRONMENT.bat`

Option C (on py 3.13 and higher i guess):

`pip install --force-reinstall flask==3.1.0 flask-socketio==5.5.1 python-socketio==5.12.1 python-engineio==4.11.2 werkzeug==3.1.3`

### 4) Run (WebUI)
Recommended (silent + tray icon):

- Double-click `Start TowerBot WebUI.vbs`

Alternative (still tray, but via .bat):

- `Start TowerBot WebUI.bat`

Debug / console mode (prints the URLs + logs to console):

- `py main.py`
- Optional port: `py main.py 8080`

Then open:
- `http://localhost:5000`

To open from your phone:
- `http://<your-pc-lan-ip>:5000`  
(PC + phone must be on the same LAN/Wi‑Fi - check the tray-context-menu for your local pc ip  (Windows Firewall must allow the port))

<br>

## Configuration overview

### The new rule: **configure in WebUI**
Most users only touch:
- **Settings tab** (timings/thresholds/ROIs)
- **Perk-Pilot** (priorities/blacklist)
- **Wave-Pilot** (tier/wave rules)
- **Workflow editor** (WF5/WF6 especially)

### The old rule (my old ASNI client version - never published): `.py` files are defaults
You *can* still edit `config/settings.py`, `config/config_wavepilot.py`, `config/config_workflows.py` and every other *.py directly — but it’s not recommended unless you want to change the shipped defaults.

<br>

## WebUI: Settings tab (custom settings)

The Settings tab is a structured editor for what used to be “edit settings.py”.

It writes to `config/user_settings.json` and includes these sections:

### `adb`
- `DEVICE` (e.g. `127.0.0.1:16384`)
- `ADB_AUTO_CONNECT`
- `ADB_CONNECT_TIMEOUT`
- `ADB_MAX_RETRIES`
- `ADB_SCAN_PORTS` (list)

> [!IMPORTANT]
> ADB changes usually require a **Restart** (not just Reload), because `adb_helper.py` imports ADB constants at startup.

### `gem`
- `check_interval` / `cooldown` / `diamonds_per_claim`
- thresholds: `claim_threshold`, `slash_threshold`, `perk_threshold`, `active_validator_threshold`

### `floating_gem`
- enable/disable floating gem clicker
- threshold / cooldown / diamonds
- rotation count
- check interval
- ring ROI (center + inner/outer radius)

### `perk`
- thresholds: new perk detection, perk match, no_more_perks
- perk cooldown base + variance
- penalty cooldown
- selection delay min/max (human reaction time)

### `anti_detection`
- click jitter min/max (pixel randomness)
- random pause interval min/max
- random pause duration min/max
- random tap interval min/max

### `timers`
- `MAIN_LOOP_TICK`
- `SUPPRESS_EXCEPTIONS` (debugging)
- `DEBUG_REFRESH_SECONDS`

### `workflow_intervals`
- `wf1_interval ... wf6_interval`
- global `wf_interval_variance`

### `wavepilot`
- check interval / wave drop threshold
- tier thresholds: `PRESET_THRESHOLD_TIER` and strict minimum `PRESET_THRESHOLD_TIER_MIN`
- `ROI_MENU_CLOSED_Y_OFFSET` (helps tier/wave detection depending on menu state)

### `stats`
- enable/disable stats capture
- capture interval + variance
- ROIs for the “open stats menu” template and the screenshots
- click coords (close button, tab clicks)

<br>

## WebUI: Perk-Pilot

The Perk-Pilot tab controls **perk priorities** without renaming files in the .images dir (but you can do if you want):

manually:
- Perk templates live in `images/Perk/` as `Pxx_<Name>.png`
- `P0_...` means **blacklist**
- For `P1..Pn`: lower number = higher priority (**unique** priorities required)

But in the WebUI you can comfortably:
- **Drag & drop** perks to reorder priorities
- Toggle **blacklist** per perk
- Save → writes `config/user_perks.json`
- Apply → use **Reload Config** (no restart required)

> [!TIP]
> If you add new perk templates, you only need to drop the `.png` into `images/Perk/` and reload. 

<br>

## WebUI: Wave-Pilot

Wave-Pilot is the “tier/wave autopilot”:

- Detects **Tier** + **Wave** from the screen
- Switches to a configured **card preset** (P1..P5)
- Optionally toggles **WF1..WF6** on/off when a rule triggers
- Can optionally allow/disallow **AFK-Break** in specific wave windows (wave gating)

The Wave-Pilot editor:
- Groups rules by **Tier** (numeric tiers 1–30 + tournament tiers like `gold`, `platinum`, …)
- Each rule has:
  - `wave_min` (trigger wave, inclusive)
  - `preset` (0 = don’t switch preset, 1–5 = switch)
  - `wf1..wf6` (ON/OFF/—)
- Each tier can also define (only once per tier):
  - `afk_break_min`
  - `afk_break_max`

Saving writes `config/user_wavepilot.json`.  
Apply changes with **Reload Config**.

> [!NOTE]
> In the dashboard status area you’ll also see a **preview of the next scheduled rules** for your current tier/wave.

<br>

## WebUI: Workflow editor

The workflow editor lets you edit WF steps in the browser and save them as an override.

What you can do:
- Edit **WF1, 2,3,5,6** names and descriptions
- Add / delete / reorder steps
- Disable steps without deleting them
- Pick templates from a dropdown (auto-populated from `images/*_tpl.png`)
- Edit step parameters (ROI, threshold, offsets, sleeps, click jitter, etc.)
- Nested `repeat` steps are supported (edit the child step)

Note:
- **WF4 is intentionally locked** in the editor (crash recovery / safety logic).

Saving writes `config/user_workflows.json`.  
Apply changes with **Reload Config**.

<br>

## User overrides: where everything is stored

All WebUI changes are stored as JSON in `config/`:

- `config/user_settings.json` → Settings tab
- `config/user_wavepilot.json` → Wave-Pilot rules
- `config/user_workflows.json` → Workflow editor
- `config/user_perks.json` → Perk-Pilot priorities

Reset to defaults (if u mess something up):
- Delete those files manually **or**
- Use the tray menu: **Reset User Config (JSON)**

<br>

## Reload vs Restart

- **Reload Config**: reloads workflows + wavepilot + settings + perk priorities and applies most changes live.
- **Restart Bot**: fully restarts the process (recommended after ADB changes, or if you’re unsure).


<br>

## ADB auto-connect & multi-instance

Out of the box the bot does:
1) Try to connect to configured `DEVICE`  
2) If unreachable, scan known ports (MuMu, MEmu, Nox, …)  
3) If it finds a working device, it uses that device automatically

If you run multiple emulator instances:
- Turn off `ADB_AUTO_CONNECT`
- Set the exact `DEVICE` you want (Settings tab → `adb`)

<br>

## Anti-detection features

**AFK-Break-Mode**
- Random long pauses to mimic “went AFK”
- Can be wave-gated via Wave-Pilot tier rules (`afk_break_min/max`)

**Random-Tap**
- Random taps in a configurable ROI at random intervals

**Jitter**
- Click jitter (pixel offsets) used in perk selection + some workflow clicks

**"intelligent workflows**
- Upgrade taps are only executed if not maxed out.
  
Everything is toggleable in WebUI, and the timing parameters are in Settings.

<br>

## How it works (under the hood)

- The bot captures screenshots via ADB (`adb exec-out screencap` / pull, depending on function)
- It uses **OpenCV template matching** on ROIs to keep it fast and uses NO (!) OCR


<br>

## Troubleshooting

### WebUI not reachable from phone
- Make sure your phone is on the same Wi‑Fi/LAN
- Use the URL printed by the bot: `http://<your-pc-ip>:5000`
- Allow Python in **Windows Firewall** (or open port 5000)

### “forbidden (ip)” / “forbidden (origin)”
- This is the dashboard LAN/same-origin protection.
- Don’t open the UI via some random hostname/proxy unless you know what you’re doing.
- For public access you *can* set `TOWERBOT_ALLOW_PUBLIC=1` (not recommended).

### Tier/Wave detection unstable
- Check your emulator resolution (must be 1600×900)
- In Settings → wavepilot:
  - tune `PRESET_THRESHOLD_TIER` and strict min `PRESET_THRESHOLD_TIER_MIN`
  - try adjusting `ROI_MENU_CLOSED_Y_OFFSET`
- Enable **Debug** to see live scores
- Check `_debug_wavepilot/` for debug images (when debug mode is active)

### Perk chooser misses perks
- Game language must be English
- Lab must be set to 4 perk options
- Verify your perk templates in `images/Perk/` are sharp and correct
- In some cases, a new screenshot must be taken, cropped, and used to replace the old perk in `images/Perk/`.
- Use WebUI to reorder priorities / blacklist bad templates

### Hyper‑V (black screenshots / emulation issues)
Hyper‑V often causes issues with some emulators (black screens, broken rendering).
If you run into problems: disable Hyper‑V on the host and reboot.

How to disable:
1. Windows Features → uncheck **Hyper‑V**
2. Also consider disabling:
   - Virtual Machine Platform
   - Windows Hypervisor Platform  
3. Reboot

> [!NOTE]
> Disabling Hyper‑V may temporarily break **WSA** (Windows Subsystem for Android).

<br>

## Disclaimer

This project is for educational purposes and personal automation experiments. This is my first Python project, and I created it mainly for fun and learning.

- I’m not affiliated with the game developers.
- Use at your own risk (account bans, emulator instability, etc.).
- Don’t use this in competitive contexts.

