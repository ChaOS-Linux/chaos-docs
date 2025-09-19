# Scope & Vision Document — ChaOS  

## 1. Vision  
Build a **custom Linux distribution** based on Arch with **Hyperland** as the core environment. Deliver a **“Fedora/Ubuntu-like” daily driver experience** that hides the rough edges of tiling WM life behind polished, custom-made GUI apps for settings, quick settings, customisation options, etc. (we’ll call these **“System Shell Apps”**) Allowing users of levels to access tiling WM's.

This distro is **not a respin** but an opinionated, curated OS with its own identity, apps, and theme engine.

---

Welcome to ChaOS

# Why the Name *ChaOS*?  

The name *ChaOS* is a deliberate play on words: it’s both **Chaos** and an **Operating System**.
It represents rebellion against the closed, restrictive ecosystems of companies Microsoft, Apple, and NVIDIA.
Where others see “chaos” as disorder, we embrace it as **freedom** — the freedom to shape your desktop exactly how you want, without compromise.

ChaOS is built on the belief that **tiling should be first-class**, not an afterthought, and that **customisation belongs to the user**, not the vendor. This is why Hyprland was chosen as the manager, for its bare bones, customise from the ground up approach.

If you’ve ever wanted a system that gets out of your way, respects your control, and celebrates your individuality — ChaOS is for you.

---

## 2. Guiding Principles for Design and Implimentation
- **Custom, not cobbled together** — no borrowed nm-applets, blueman, etc. Everything branded, cohesive, and consistent.
- **Hyperland-first** — features and apps are built around wlroots/Wayland; no fallback to X11.
- **Simplicity over complexity** — start with the simplest working option, refine later.
- **Customisation is first-class** — config files + GUI theming, so power users and casual users both feel at home.
- **Stable ISOs** — rolling Arch base underneath, but only the ISOs we ship are “certified/tested” combos.
- **Respect the Community**
- **Keep It Simple STUPID**

---

## 3. Hard Scope  

### 3.1 Base System  
- Arch Linux base.
- Hyperland compositor as sole DE/WM.
- greetd + customisable login manager.
- Waybar, hyprpaper, hypridle, hyprlock, etc preinstalled and preconfigured.
- Flatpak support out of the box.

### 3.2 Hardware Targets  
- **Supported:** AMD CPUs/GPUs, Intel CPUs/GPUs, Framework laptops/desktops.
- **Explicitly unsupported:** NVIDIA.

### 3.3 System Shell Apps (Custom GUI Apps)  
Monolithic **Control Center** (GNOME Settings–style) with modules:
- **Network:** Wi-Fi, Ethernet.
- **Bluetooth:** Pair/connect/manage devices.
- **Display:** Resolution, scaling, refresh rate, multi-monitor.
- **Audio:** Volumes, input/output switching, profiles.
- **Power:** Profiles, battery status.
- **Users:** Add/remove users, change password, avatar, biometric login.
- **About/System Info:** Distro version, hardware summary.

+ **System Tray “Applets”** for quick toggles:
- Wi-Fi, BT, Audio, Battery, Lock, Power menu.
- Notifications Centre.
- Consistent UI with the Control Center.

### 3.4 Snapshot Tool  
- 1-click export of:
  - Hyperland config (binds, gaps, monitors).
  - Waybar, wallpapers, themes.
  - Installed applications (manifest of pacman + Flatpak).
- Share/import feature.
- Can be used as reinstall bootstrap or shared with other users. Can be imported into the "Welcome" wizard for instant theming.

### 3.5 Theme System  
- All custom apps are **themeable**.
- GUI Theme Manager to install/switch/delete.
- User can **edit config files directly** (like Ghostty/Starship) — configs must be clean, documented, and not hidden in binary formats.
- Login screen theming fully supported.

### 3.6 Installer Experience  
- GUI Installer (Calamares).
- Category-based software selection at install:
  - **Browser:** Zen (default), Firefox, Brave, Chrome, etc.
  - **Terminal:** Multiple options (default TBD). User also selects shell (bash, zsh, etc.).
  - **Office Suite:** OnlyOffice (default), LibreOffice, etc.
  - **Files Manager:** TBD (must be themeable, feature-complete).
  - **Package Manager:** Flatpak + pacman wrapper (custom app if needed).
- Defaults preselected, but user can customise.
- User Selected packages auto mapped to keybinds in Hyprland.

### 3.7 First Boot Experience  
- Our Prefferd themes loaded visual cohesiveness
- GUI Welcome App, guides new users through first boot and first customisations (and allows for loading of snapshot for power users)

---

## 4. Out-of-Scope  
- NVIDIA drivers/support. (NVIDIA with their STUPID anti consumer practices can go and get FUCKED! I don't care if I have to choose the "Second Best" hardware, I'm not giving into their Shit! And if AMD/Intel try it they can get fucked too.)
- Multiple DE/WM support (Hyperland-only).
- Btrfs/snapshots at v1 (stick to ext4).
- Supporting every Arch update combo (only released ISOs are “certified”).

---

## 5. Stretch Goals (Later Versions)  
- GUI front end for pacman + flatpak supporting updates. (Find an already existing package or DIY if we have to)
- Update Custom System Shell Apps through pacman.
- Switch to btrfs + snapshot GUI.
- Built-in auto-update manager (timer + GUI).
- Secure Boot support via sbctl.
- Online snapshot sharing (push configs to GitHub/GitLab).
- Optional containerisation of system shell apps (Flatpak packaging).

### 5.1 Future Gaming Enhancements  

ChaOS should evolve to include a first-class **gaming experience**, similar to what Nobara and Bazzite provide, but tailored to Hyperland and the ChaOS vision. These enhancements will not be part of the initial release but are considered a strategic future goal.

#### 5.1.1 Gaming Metapackage  
- Provide a **ChaOS-Gaming** metapackage that installs and configures all essential gaming tools.
- Allow users to opt into this during installation or later via package manager.

#### 5.1.2 Core Gaming Tools
- **Steam + Proton** preinstalled (Flatpak by default).
- **Wine** and **Heroic** preconfigured.

#### 5.1.3 Kernel & System Tweaks
- Gaming-oriented kernel parameters (schedulers, hugepages, etc.).
- Latency optimisations (similar to zen kernel patches).
- PipeWire tuned for low-latency audio.

#### 5.1.4 Controller & Peripheral Support
- Preinstalled drivers for:
  - Xbox controllers (wired/wireless).
  - DualShock/DualSense controllers.
  - Switch Pro controller.

#### 5.1.5 GPU & Graphics Stack  
- AMD + Intel GPU support out of the box.
- Vulkan drivers (Mesa, AMDVLK, Intel ANV).

#### 5.1.6 UX Enhancements for Gamers  
- Preconfigured **Waybar module for performance stats** (CPU/GPU usage, V/RAM Usage, and FPS via MangoHud).
- “Game Mode” quick toggle in the system tray applets.

---

## 6. Success Criteria  
- ISO installs and boots on AMD/Intel/Framework hardware without extra config.
- First boot delivers a **working desktop** with:
  - Network manager, audio, display, power all configurable in GUI.
  - Wi-Fi connection + browser launch possible in <5 mins.
- Framework Laptop's Webcam, Microphone, Trackpad, and Fingerprint Sensor all work as expected.
- System Shell Apps feel modern and integrated (not rebranded third-party applets).
- Snapshot tool can **restore a setup on a fresh install** with one command/click.
- Theme manager works both GUI and config-file based.
- Login screen can be themed like any other part of the system.
