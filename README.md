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
- **Magic DOSBox Lite** (from Google Play Store) or <a href="https://play.google.com/store/apps/details?id=bruenor.magicbox.free">click here</a>.
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

3. Select that **Dosbox** folder.
4. Confirm any permission popups (**Allow**).

This folder will act as the **root directory (C:)** for DOSBox.

---

### Step 5 – Use the Same Folder for Layouts/Settings

Magic DOSBox will then ask for a location to store:

* Game layouts
* Settings

You **don’t need a separate folder**.

Instead:

1. Click **“Choose”** again.
2. Select the **same `Dosbox` folder** you created earlier.
3. Confirm with **Allow** and click **Next** until setup finishes.

---

### Step 6 – Finish Setup Prompts

* Choose any theme you like (Standard/Fantasy).

* On the final **Help** / info screen, **uncheck**:

  ```text
  [ ] Show on start
  ```

* Click the **X** to close the help screen.

Now you’re at the **main Magic DOSBox interface**.

---

## 🖥️ 2. Create the TASM DOSBox Profile

We’ll create a “game” profile called **TASM** to quickly launch our assembly environment.

### Step 7 – Add a New Game/Profile

1. On the main Magic DOSBox screen, tap the **+ (plus)** icon.
2. Select **“New game”**.

### Step 8 – Name the Profile

In the configuration screen:

1. Set **Title** to:

   ```text
   TASM
   ```

2. Make sure **Enabled** is checked.

3. Click **OK** to save.

You should now see a tile/card named **TASM**.

---

### Step 9 – Launch the DOSBox Shell

1. Tap on the **TASM** tile.
2. A DOSBox shell window will open (`C:\>` style blue or text screen).
3. If a **congratulations/help** dialog appears again:

   * **Uncheck** `Show on start`.
   * Close it with **X**.

Now you are inside the **DOSBox shell**.

---

## ⌨️ 3. Enable the On-Screen Keyboard

To actually type commands:

1. Press your phone’s **Back** button (inside Magic DOSBox).
2. A side menu / controls panel will appear.
3. Tap **“Second keyboard”**.
4. The DOS-style keyboard will appear at the bottom.

You’re now ready to type commands in DOSBox.

---

## 📂 4. Verify the Mounted Folder

We must confirm that the DOSBox `C:` drive is exactly the same as the **`Dosbox` folder** you created in internal storage.

### Step 10 – Check from DOSBox

Inside DOSBox, type:

```dos
DIR
```

You will see the list of files/folders in `C:\`.

### Step 11 – Check from File Manager

1. Open your phone’s file manager.
2. Navigate to:

   ```text
   Internal Storage / Dosbox
   ```

You should see the **same folders and files** there as you saw after typing `DIR` in DOSBox.

> If both match, you’re correct: DOSBox `C:\` = `Dosbox` folder in internal storage.
> **This is exactly where we will place the `TASM` folder.**

---

## 📦 5. Download and Extract TASM

### Step 12 – Download `TASM.zip`

From your mobile browser, open:

```text
https://projects.likhil.42web.io/TASM
```

Then:

1. Tap **Download TASM.zip**.
2. The file will be saved in your **Downloads** folder.

*(Or else download that TASM.zip from this github itself.)*

---

### Step 13 – Extract TASM into DOSBOX Folder

1. Open your **Downloads** folder in the file manager.
2. Locate:

   ```text
   TASM.zip
   ```
3. Extract it.
4. When asked for extraction path, choose the **`Dosbox` folder** you created earlier.

After extraction, you should have:

```text
Internal Storage / Dosbox / TASM / ...
```

So inside DOSBox, this will be:

```dos
C:\TASM
```

---

## 💻 6. Enter TASM Folder in DOSBox

Open Magic DOSBox and launch the **TASM** profile.

Then type:

```dos
CD TASM
DIR
```

You should now see files like `TASM.EXE`, `TLINK.EXE`, `TD.EXE`, etc.

> From now on, **every time** you want to use TASM:
>
> 1. Open **Magic DOSBox Lite**
> 2. Tap the **TASM** profile
> 3. Run:
>
>    ```dos
>    CD TASM
>    ```

---

## 🧪 7. First Assembly Program (Copy-Paste Example)

Here’s a minimal **“Hello World”** style example (prints a message and exits to DOS):

> ⚠ On mobile, you’ll type this inside DOSBox’s `EDIT` editor.

### Step 1 – Open EDIT

Inside `C:\TASM`:

```dos
EDIT HELLO.ASM
```

### Step 2 – Type This Code

```asm
.MODEL SMALL
.STACK 100H

.DATA
msg DB 'Hello from TASMobile!$'

.CODE
MAIN PROC
    MOV AX, @DATA
    MOV DS, AX

    MOV DX, OFFSET msg
    MOV AH, 09H
    INT 21H

    MOV AH, 4CH
    INT 21H
MAIN ENDP
END MAIN
```

### Step 3 – Save & Exit

* In `EDIT`, open the menu, save the file as `HELLO.ASM`, and then exit.

### Step 4 – Assemble and Link

Back in DOSBox:

```dos
TASM HELLO.ASM
TLINK HELLO.OBJ
```

If there are **no errors**, it will create `HELLO.EXE`.

### Step 5 – Run the Program

```dos
HELLO
```

You should see:

```text
Hello from TASMobile!
```

Congrats, you just wrote and executed assembly **completely on Android**.

---

## 🐞 8. Using Turbo Debugger (TD)

If you want to debug your program:

```dos
TD HELLO.EXE
```

Turbo Debugger (`TD`) will open, allowing you to:

* Step through instructions.
* Inspect registers.
* Set breakpoints.

---

## 🔁 Quick Command Summary (Copy-Paste Friendly)

**Every session:**

```dos
CD TASM
```

**Create / Edit a file:**

```dos
EDIT FILENAME.ASM
```

**Assemble:**

```dos
TASM FILENAME.ASM
```

**Link:**

```dos
TLINK FILENAME.OBJ
```

**Run:**

```dos
FILENAME
```

**List files:**

```dos
DIR
```

---

## ❓ Troubleshooting

* **`Bad command or file name`**
  → You are not in the correct folder. Run:

  ```dos
  CD TASM
  DIR
  ```

* **`File not found` when assembling**
  → Check that your `.ASM` file is saved in `C:\TASM` and the spelling matches.

* **Keyboard not visible**
  → Press **Back** → tap **Second keyboard** inside Magic DOSBox.

* **TASM folder not visible in DOSBox**
  → Confirm:

  * `TASM` folder exists under `Internal Storage / Dosbox`.
  * You extracted `TASM.zip` into **Dosbox**, not somewhere else.
  * Run `DIR` inside DOSBox and check TASM is listed.

---

## 📚 Screenshots & Demo

The PDF/documentation and this repo may contain screenshots showing:

* DOSBox shell running on mobile.
* EDIT editor open with assembly source.
* Turbo Debugger and file listing.

These prove that TASM and your programs run **fully on mobile**.

---

## 🤝 Support / Contact

If you get stuck at any step:

* Open my project site: *(add your URL here)*
* Reach me on:

  * Instagram: *(your handle)*
  * LinkedIn: *(your profile)*
  * GitHub: [@likhil-pidugu](https://github.com/likhil-pidugu)

---

## 📝 License

Add your chosen license here (MIT, GPL, etc.).

---

## ✅ Status

* [x] Mobile DOSBox environment working
* [x] TASM integrated
* [x] Able to write, assemble, link, and run 8086 Assembly on Android
* [ ] More sample programs (coming soon)

Happy coding with Assembly on mobile 👾
