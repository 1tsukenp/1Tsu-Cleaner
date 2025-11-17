# 1Tsu Cleaner

A lightweight, portable Windows cleaner that clears common junk in a single click: temp files, browser caches, Windows Update cache, and Recycle Bin.

> **Author:** KenpSoft  \
> **Platform:** Windows 10/11 (64‑bit)  \
> **Type:** Portable, single‑file EXE (no installer)

---

## ✨ Features

- **One‑click clean** – press _Clean Now_ and 1Tsu Cleaner does the rest.
- **Portable** – a single `.exe`, no installation required.
- **Runs as Administrator** – requests elevation via UAC so system locations can be cleaned safely.
- **Safe by design**
  - Skips files that are in use or access‑denied, instead of crashing.
  - Does **not** touch your personal files (`Documents`, `Pictures`, `Desktop`, etc.).

### System cleanup

- `%TEMP%` – current user temporary files
- `C:\Windows\Temp` – system temporary files
- `C:\Windows\Prefetch` – prefetch data (application launch cache)
- `C:\Windows\SoftwareDistribution` – Windows Update cache (SoftwareDistribution)
- **Recycle Bin** – attempts to empty Recycle Bin for all drives

### Browser cache cleanup (current user)

Chromium‑based browsers:

- **Google Chrome** – `Cache`, `Code Cache`, `GPUCache`
- **Microsoft Edge** – `Cache`, `Code Cache`, `GPUCache`
- **Brave** – `Cache`, `Code Cache`, `GPUCache`
- **Opera (Stable)** – `Cache`, `Code Cache`, `GPUCache`
- **Opera GX** – `Cache`, `Code Cache`, `GPUCache`
- **Vivaldi** – `Cache`, `Code Cache`, `GPUCache`

Firefox‑based:

- **Mozilla Firefox** – `cache2` in all detected Firefox profiles

If a location or browser is not found on the machine, 1Tsu Cleaner logs it as `[SKIP]` and moves on.

---

## 📥 Download

1. Go to the **Releases** page of this repository.  
2. Download the latest `1Tsu Cleaner.exe` file.  
3. Place it anywhere you like (Desktop, tools folder, USB drive, etc.).

> The shipped EXE is **self‑contained** – it includes the .NET runtime, so you don’t need to install .NET separately.

---

## 🚀 Usage

1. **Close browsers & apps**
   - Close Chrome, Edge, Brave, Opera, Opera GX, Vivaldi, Firefox.
   - Close VPN/overlay tools that may keep temp files locked (e.g. Cloudflare WARP).

2. **Run as Administrator**
   - Double‑click `1Tsu Cleaner.exe`.
   - Approve the **UAC prompt** ("Do you want to allow this app to make changes…?").

3. **Clean**
   - In the main window, click **Clean Now**.
   - A log window opens and shows progress, for example:

     ```text
     [CLEAN] %TEMP%: C:\Users\<User>\AppData\Local\Temp
     [CLEAN] Chrome Cache: C:\Users\<User>\AppData\Local\Google\Chrome\User Data\Default\Cache
     [SKIP] Firefox profiles not found.
     [WARN] Some recycle bin items could not be removed. Error code: 0x8000FFFF
     ```

4. **Finish**
   - When the log shows `Done.`, cleaning is complete.
   - Close the log window and main window.

---

## ⚠️ Safety notes

- 1Tsu Cleaner **never deletes user documents** (no changes to `Documents`, `Pictures`, `Desktop`, etc.).
- Files that are **in use** or **system‑protected** are skipped silently.
- Clearing these locations can have side effects:
  - `Prefetch` – first launches after cleaning may be slightly slower while Windows rebuilds prefetch data.
  - `SoftwareDistribution` – Windows Update may re‑download update packages after cleaning.
- Recycle Bin cleaning may report a warning if Windows does not allow emptying some items. This does not stop the rest of the cleanup.

Use this tool at your own risk, as with any system cleaner.

---

## 🛠 Build from source

1Tsu Cleaner is written in **C#** using **.NET (Windows)** and **Windows Forms**.

### Prerequisites

- Windows 10/11
- [.NET SDK](https://dotnet.microsoft.com/download) that supports `net10.0-windows` (or adjust the target framework in the project file)
- Optional: **Visual Studio** with ".NET desktop development" workload

### Build with Visual Studio

1. Clone this repository.
2. Open `OneTsuCleanerGUI.sln` or the project in Visual Studio.
3. Set configuration to **Release**.
4. Build the solution.
5. For a single self‑contained EXE:
   - Right‑click the project → **Publish…**
   - Target: **Folder**
   - Runtime: `win-x64`
   - Enable **Produce single file** and **Self‑contained**
   - Publish and use the generated EXE from the `publish` folder.

### Build with `dotnet` CLI

```bash
# From the OneTsuCleanerGUI project folder
 dotnet publish -c Release -r win-x64 -p:PublishSingleFile=true --self-contained true
```

The portable EXE will be under:

```text
bin/Release/net10.0-windows/win-x64/publish/OneTsuCleanerGUI.exe
```

You can rename it to `1Tsu Cleaner.exe` for distribution.

---

## 📋 Roadmap / Ideas

- [ ] Optional checkboxes for which areas to clean (browsers, Windows Update, Prefetch, etc.).
- [ ] Progress bar for long clean operations.
- [ ] Dark theme / additional UI skins.
- [ ] Multi‑language support.

Feel free to open issues or pull requests with suggestions.

---

## 📄 License

_Choose a license you prefer (e.g. MIT, Apache 2.0, GPL) and update this section and add a `LICENSE` file._

Example if you decide to use MIT:

```text
Copyright (c) KenpSoft

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## 🙌 Credits

Created and maintained by **KenpSoft**.

If you use 1Tsu Cleaner and like it, consider starring the repository on GitHub to support the project.