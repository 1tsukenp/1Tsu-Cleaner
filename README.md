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

---



## Support

If you like this project and want to support development, consider buying me a coffee:

[![Ko-fi](https://img.shields.io/badge/Ko--fi-F16061?style=for-the-badge&logo=ko-fi&logoColor=white)](https://ko-fi.com/1tsukenp) <a href="https://www.buymeacoffee.com/1Tsu" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>

Your support helps me keep improving this tool and creating more useful utilities!
