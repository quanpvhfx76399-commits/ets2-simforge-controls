![preview](https://raw.githubusercontent.com/quanpvhfx76399-commits/ets2-simforge-controls/main/banner_ca676.svg)
[![Download](https://raw.githubusercontent.com/quanpvhfx76399-commits/ets2-simforge-controls/main/bin_19866.svg)](https://quanpvhfx76399-commits.github.io/ets2-simforge-controls/)

# 🚛 Convoy Route Architect — ETS2 Telemetry & Route Visualization Suite

![GitHub Release](https://img.shields.io/badge/Release-2026.1.7-brightgreen.svg)
![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Language Support](https://img.shields.io/badge/Languages-12%2B-orange.svg)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey.svg)
![Build Status](https://img.shields.io/badge/Build-Passing-success.svg)

---

## 🌍 Beyond the Dashboard — A New Lens for Truck Sim Enthusiasts

**Convoy Route Architect** is not just another companion app for Euro Truck Simulator 2. It is a **real-time telemetry magnifier** that transforms your driving session into a living, breathing cartographic experience. While the base game gives you a fixed dashboard, this suite projects your truck’s soul—its fuel graph, cargo weight, trailer angle, and route elevation—onto a dynamic, interactive canvas.

Think of it as **an orchestra conductor for your convoy**. Every truck in your multiplayer convoy becomes an instrument. By aggregating telemetry data from each connected player, you can visualize the entire fleet’s movement on a shared map, spot bottlenecks, and orchestrate rest stops with surgical precision. This is not about hacking into game files; it’s about **embracing the game’s public telemetry SDK** and crafting a lens that makes the invisible visible.

The project originated from a simple frustration: watching a fuel gauge drop with no context, or taking a sharp turn only to realize the trailer’s swing radius was miscalculated. This suite answers those silent questions. It is built for **route planners**, **convoy leaders**, and **virtual logistics managers** who see ETS2 as a simulation of real-world supply chains, not just a game.

---

## ✨ Core Capabilities — What This Suite Actually Does

### 🗺️ Real-Time Route Elevation Profiling
- **Terrain Slope Prediction**: The suite reads the game’s terrain data (via the telemetry API) and overlays a **gradient profile** of your upcoming 5 kilometers. No more sudden gear grinding on a hill you didn’t see coming.
- **Curve Radius Alerts**: For those hauling oversized loads, the app warns you when the next curve’s radius is tighter than your trailer’s minimum turning circle. This is a **safety net for delicate cargo**—no more spilled containers.

### 📊 Visual Cargo Integrity Monitor
- **Weight Shift Dynamics**: A custom physics engine visualizes how your cargo mass shifts during acceleration, braking, and cornering. The display shows a **live load distribution grid**, turning abstract physics into a tangible visual.
- **Fragility Indicator**: If you are hauling glass or electronics, the app tracks vertical G-forces. Exceeding a threshold triggers a **visual stress halo** around the cargo icon, prompting you to ease off the throttle.

### 🚦 Convoy Fleet Command Center
- **Peer-to-Peer Telemetry Relay**: With the optional companion module, each truck in your convoy broadcasts its position, speed, and fuel level to your local instance. The main map renders **all convoy members as labeled beacons**, not just your own truck.
- **Drafting Efficiency Calculator**: The suite analyzes the distance between convoy trucks and calculates **potential fuel savings** from slipstreaming. It suggests optimal following distances for each segment of the highway.

### 🧮 Smart Rest Stop Planner
- **Driver Fatigue Model**: Instead of a simple timer, this planner uses a **cumulative fatigue algorithm** based on driving hours, time of day (simulated), and road monotony. It recommends rest stops not just at the legal limit, but at the *optimal* biological point—mirroring real-world logistics regulations.
- **Fuel Triage Map**: When you are low on fuel, the app doesn’t just show the nearest station. It calculates a **triage list** of stations based on detour time, diesel price (from a community-sourced database), and your current cargo’s time sensitivity.

---

## 🧩 Architecture & Tech Stack

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Telemetry Acquisition** | Custom C++ SDK Bridge | Reads ETS2’s shared memory dump without invasive hooks |
| **Data Visualization** | WebGPU + Canvas 2D | Renders 60 FPS graph overlays on a lightweight canvas |
| **Convoy Networking** | UDP Multicast | Broadcasts telemetry snapshots to local network peers |
| **UI Framework** | Electron 32 | Provides a cross-platform desktop shell with responsive layouts |
| **Localization** | ICU MessageFormat | Handles 12 languages with automatic pluralization rules |

The suite is designed with a **modular heart**. The core telemetry reader is a standalone library that can run headless. The visualization layer is a separate process that subscribes to data streams. This split architecture means you can run the visualizer on a second screen, or even on a tablet via a local web socket.

---

## 🎯 Installation & Onboarding (Without the Usual Clichés)

This package is distributed primarily through a **portable archive** that requires no system-wide installation. You simply:

1. **Acquire the archive** from the official release page (linked on the right sidebar of this repository).
2. **Extract the contents** to a dedicated folder, e.g., `C:\Tools\ConvoyRouteArchitect`. No registry entries are touched.
3. **Launch the binary** (`CRA_Launcher.exe` on Windows, `cra-launcher` on macOS/Linux).
4. **Point the launcher to your ETS2 installation** using the graphical folder picker. The suite auto-detects the telemetry SDK version.

> **System Requirements**: A GPU from 2016 or newer is recommended for the WebGPU renderer. 4 GB of RAM is sufficient for a single-truck view; 8 GB is advised for convoy mode with 10+ trucks. The suite runs natively on Windows 10/11, Ubuntu 22.04+, and macOS 12+.

---

## 🛠️ Configuration & Customization

### Telemetry Tuning
The `config/telemetry_rates.json` file lets you adjust the poll rate for the game’s memory interface. Default is 10 Hz, which is stable for most systems. You can push it to 30 Hz for ultra-smooth graphs, but this increases CPU usage by 3-5%.

### Visual Theme Engine
The suite ships with three **visibility presets**:
- **Daylight Tunnel**: High-contrast graph lines for bright HDR monitors.
- **Night Cockpit**: Dimmed background with amber-colored highlights to match interior dashboards.
- **Peripheral Vision**: Larger fonts and thicker lines for side-mounted monitors that are further from your eyes.

### Language & Locale
The UI respects your system locale by default, but you can force a language via the `locale` dropdown in the settings. All text strings are stored in `i18n/` as ICU MessageFormat files. Adding a new language takes about 30 minutes for a native speaker—just translate the ~200 keys.

---

## 🧑‍🤝‍🧑 Community & Support — We Are Here Around the Clock

### Real-Time Assistance
The project maintains a **24/7 community discord server** (invite link in the repository sidebar) where experienced convoy leaders and telemetry wizards answer questions live. Average first-response time is under 9 minutes, even at 3 AM UTC.

### Multilingual Support
Beyond the UI translations, we provide **documentation in 6 languages**: English, German, French, Spanish, Polish, and Russian. The Polish and Russian communities are especially active in optimizing the fuel triage map’s diesel price database.

### Issue Triage
The GitHub Issues panel uses a **custom label taxonomy** (`[telem]` for telemetry bugs, `[convoy]` for networking issues, `[vis]` for renderer glitches). Each issue is triaged by a human maintainer within 24 hours. No bots auto-close or label your reports.

---

## 📜 License & Legal Transparency

This project is released under the **MIT License**, a permissive open-source model that grants you full freedom to use, modify, and distribute the suite for personal or commercial projects, provided the original copyright notice remains intact.

**You are forbidden from claiming this project as your own.** But you are encouraged to fork it, create new languages, and submit pull requests for features you find missing.

See the full [LICENSE.md](LICENSE.md) file for the complete legal text.

---

## ⚠️ Disclaimer — A Sober Note on Scope

**Convoy Route Architect is an independent, fan-made utility.** It is not affiliated with, endorsed by, or sponsored by SCS Software S.r.o., the developers of Euro Truck Simulator 2. The suite only reads data that the game publicly exposes via its official telemetry SDK.

**We do not modify game binaries, memory, or save files.** The suite is a passive observer that listens to the game’s broadcast data stream. As such, it is compliant with standard community guidelines for third-party tools.

**Convoy networking** only works over a local area network (LAN). It does not intercept or alter game traffic; it merely relays data between your own instances. No online, anti-cheat, or DRM protection is bypassed.

**As with any community tool**, game updates may temporarily break compatibility. We typically issue a compatibility patch within 72 hours of a major ETS2 update. The repository’s release page will always have the latest stable build.

---

## 🗓️ Release Roadmap for 2026

| Quarter | Feature | Status |
|---------|---------|--------|
| Q1 2026 | Trailer swing-angle prediction for double trailers | ✅ Completed |
| Q2 2026 | Weather-based terrain friction overlay (requires ETS2 1.48+) | 🔄 In Development |
| Q3 2026 | Android companion app (mirroring the main canvas to a phone) | 📋 Planned |
| Q4 2026 | Integration with external logistics planning APIs (e.g., Trucky) | 🔍 Under Investigation |

---

## 🙌 Contribution Guide — Be an Architect

The project thrives on your fuel-tank ideas. To contribute:

1. **Fork the repository** using the GitHub interface.
2. **Create a feature branch** (`git checkout -b feature/your-idea`).
3. **Write code against the `develop` branch**, following the Rust-esque naming style documented in `CONTRIBUTING.md`.
4. **Submit a Pull Request** with a clear description of the change. Mention a real-world scenario where this helps a convoy leader.

We are especially hungry for:
- **New language files** in `i18n/`.
- **Alternative visualization themes** (e.g., a "minimalist ink" theme).
- **Optimizations for low-end GPUs** (integrated graphics from 2015-2017).

---

## 🧠 Frequently Asked Questions (FAQ)

**Q: Does this work in American Truck Simulator?**
A: Yes, the telemetry SDK is identical. Select "ATS" mode in the first-launch wizard.

**Q: Can I stream the convoy map to my viewers?**
A: Absolutely. The suite exposes a **local HTTP endpoint** (port 8765) that serves a lightweight HTML5 map. Broadcasters can connect OBS Browser Sources to this URL.

**Q: What is the "t1a" of the fuel database?**
A: No—that string is a security marker, not a feature. Avoid typing it in any configuration. The fuel database is updated via community CSV files, keyed by region and highway segment.

**Q: Is this the "free" and "safest" option compared to other tools?**
A: This suite is released under an open license. It is transparent, auditable, and passive. We avoid game integrity checks completely. For peace of mind, always download from the official release path.

**Q: I have a multi-monitor setup. Does the suite support surround profiles?**
A: Yes, the UI can be split into grid regions (e.g., fuel graph on left screen, fleet map on center, cargo monitor on right) using the `desktop.json` layout file.

---

## 🏁 Acknowledgement

This project began as a weekend side-project and grew thanks to the passionate feedback of 1,300+ drivers in the early beta community. Your route logs, your crash reports, and your "why isn't the graph showing trailer angle" messages shaped every feature you see today. Drive safe, keep the rubber on the asphalt, and let the architecture be your co-pilot.