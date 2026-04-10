# 🎮 Reloaded II (Persona 5 Royal) Linux Guide

**(CachyOS Native Steam + Linux Mint Compatible)**

---

## 📌 Overview

This guide combines:

* Official Reloaded II Linux setup
* Community fixes (Reddit)
* Real-world issues (crashes, black screen, inconsistent launch)

### Fixes:

* ❌ Game closes after 2 seconds
* ❌ Black screen on launch
* ❌ Mods not loading
* ❌ Reloaded II inconsistency

---

## ⚠️ Core Principles (MOST IMPORTANT)

* ✅ Use **Reloaded II `.zip`**, NOT installer
* ✅ Run Reloaded II **inside the game’s prefix**
* ❌ Do NOT launch P5R through Reloaded II
* ✅ Launch ONLY via Steam
* ✅ Reloaded II = **mod manager only**

---

## 🧰 Requirements

* Steam (native install)
* Persona 5 Royal
* Proton (GE recommended but optional)
* Protontricks / Wine tools (native, NOT Flatpak)

---

## 🚀 Main Setup (Universal)

### 1. Download Reloaded II

* Download the **`.zip` version** from official releases

---

### 2. Locate P5R Prefix

```bash
~/.steam/steam/steamapps/compatdata/<APPID>/
```

---

### 3. Extract Reloaded II

Extract the `.zip` directly inside the folder above.

You should see:

```
Reloaded-II.exe
```

---

### 4. Run Reloaded II in Correct Prefix

```bash
protontricks
```

* Select **Persona 5 Royal**
* Run `Reloaded-II.exe`

---

### 5. Configure Reloaded II

Inside the app:

* Select **P5R**
* Go to **Settings**
* Click **Deploy ASI Loader**

---

### 6. Steam Launch Option (CRITICAL)

```bash
WINEDLLOVERRIDES="winmm.dll=n,b" %command%
```

---

### 7. Install Mods

* Launch Reloaded II via Protontricks ONLY
* Enable your mods

---

### 8. Launch Game (Correct Way)

* Launch via **Steam only**
* Mods will load automatically

---

## 🧊 CachyOS (Native Steam, No Flatpak)

### ✅ Use Native Tools Only

Do NOT use:

* Flatpak Protontricks ❌
* Flatpak Steam ❌

👉 Flatpak Protontricks can break prefix communication and cause crashes.

---

### Install Required Tools

```bash
sudo pacman -S protontricks wine winetricks
```

---

### ⚠️ Bottles Note

* Bottles uses a **different Wine environment**
* Do NOT install Reloaded II inside Bottles for this setup

👉 Always use:

* Steam prefix (`compatdata`)
* Protontricks

---

### 🧠 Wayland Fix (KDE Plasma)

If issues occur:

```bash
env GDK_BACKEND=x11 protontricks
```

---

## 🍃 Linux Mint Notes

Install Protontricks:

```bash
sudo apt install protontricks
```

---

## 🧨 Real-World Issues & Fixes

### ❌ Game closes after 2 seconds

✔ Use `.zip` version + native Protontricks

---

### ❌ Black screen

✔ Click the game window immediately after launch

👉 If unfocused → game may freeze

---

### ❌ Mods not loading

✔ Ensure:

* ASI Loader deployed
* Launch option set

---

### ❌ Works once then breaks

✔ Always run Reloaded II via Protontricks
✔ Do not mix environments (Bottles vs Steam)

---

## ❌ Common Mistakes

* Using installer `.exe` ❌
* Launching via Reloaded II ❌
* Using Flatpak Protontricks ❌
* Wrong compatdata path ❌
* Mixing Bottles + Steam ❌

---

## ✅ Expected Result

* Game launches normally
* Mods load automatically
* Stable performance

---

## ⚡ Automation Script

### `rii-manager.sh`

```bash
#!/bin/bash

APPID=1687950
STEAM_COMPAT="$HOME/.steam/steam/steamapps/compatdata/$APPID"

cd "$STEAM_COMPAT" || exit

echo "[INFO] Launching Reloaded II inside P5R prefix..."

protontricks -c "wine Reloaded-II.exe" $APPID
```

---

### Make executable:

```bash
chmod +x rii-manager.sh
```

---

### Run:

```bash
./rii-manager.sh
```

---

## 🔮 Future Improvements

* Auto-detect APPID
* GUI launcher (Zenity / KDialog)
* Mod backup system
* One-click setup script

---

## 💬 Credits

* Reloaded II official Linux guide
* r/linux_gaming community
* Community troubleshooting

---
