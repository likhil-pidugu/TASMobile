# TASMobile – Write Assembly Code on Android

TASMobile lets you **write, compile, debug, and run 8086 Assembly programs directly on your Android phone** using Magic DOSBox Lite + TASM.

This repo explains **exactly how to set up everything from scratch**, where to put the `TASM` folder, and how to actually run `.ASM` files on mobile without touching a PC.

---

## 📌 What You Will Learn

By following this guide, you will be able to:

- Install and configure **Magic DOSBox Lite** on Android.
- Create a dedicated **DOSBOX folder** that acts as drive `C:` inside DOSBox.
- Download and extract **TASM** into the correct location.
- Use commands like:
  - `DIR` – list files and folders
  - `CD` – change directory
  - `EDIT` – write assembly code
  - `TASM` – assemble `.ASM` files
  - `TLINK` – link `.OBJ` files
  - `TD` – run Turbo Debugger
- Run your own `.EXE` programs compiled **fully on mobile**.

---

## ⚙️ Requirements

- Android phone.
- Internet connection (only once, to download apps/files).
- **Magic DOSBox Lite** (from Google Play Store).
- **TASM.zip** (Turbo Assembler package – <a href="http://projects.likhil.42web.io/TASM">download here</a>).

---

## 🔧 1. Install & Configure Magic DOSBox Lite

### Step 1 – Install Magic DOSBox Lite

1. Open **Google Play Store**.
2. Search for **“Magic DOSBox Lite”**.
3. Install the app.

> This app emulates an MS-DOS environment where we’ll run TASM.

---

### Step 2 – Grant Storage Permissions

When you open Magic DOSBox Lite for the first time:

1. It will ask for storage permissions.
2. Select **“Allow all”** so DOSBox can read/write files.

---

### Step 3 – Start Initial Setup

1. Press the **Play / Start** button in Magic DOSBox Lite.
2. On the **“Games folder”** screen, click **“Choose”** to select where DOSBox should store its files.

---

### Step 4 – Create the DOSBOX Folder

You will be taken to your file manager:

1. Choose **Public storage** (main internal storage).
2. Create a **new folder** named:

   ```text
   Dosbox
