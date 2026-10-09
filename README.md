# Trim & Meter for REAPER

**Trim & Meter** is a high-performance, lean JSFX utility designed specifically for the REAPER Mixer Control Panel (MCP). It provides real-time, precision telemetry (switching between authentic $2^{\text{nd}}$-order mechanical VU ballistics and instantaneous peak detection) combined with direct drag-to-trim gain staging in a sleek, low-profile two-line layout.

---

## Features

* **Dual Metering Engines:** Toggle instantly between **VU (RMS)** mode with mechanical ballistics and **Peak** mode for sample-accurate transient tracking.
* **Configurable Base Level:** Set your target operating reference level (e.g., $-18\text{ dBFS}$, $-12\text{ dBFS}$, $0\text{ dBFS}$) dynamically.
* **Relative Level Readout & Threshold Alert:** The digital display tracks levels relative to your Base Level ($0.0$ target), automatically shifting to a bright red warning color when overshooting the threshold.
* **Intelligent Visual Feedback:** Features a dual-zone horizontal bar (Green up to target, Red on overshoot) paired with a 1.2-second peak-hold decay.
* **Direct Mixer Gestures:** Fine vertical drag-to-trim volume adjustment directly inside the MCP slot, with a Shift-modifier for ultra-fine sub-decibel precision and a double-click reset.

---

## Technical Background

### 1. VU Meter Ballistics ($2^{\text{nd}}$-Order ANSI C16.5 Emulation)
Unlike basic $1^{\text{st}}$-order smoothing filters that under-read musical transients, Trim & Meter implements a true mass-spring-damper differential equation matching the **ANSI C16.5 specification** (similar to premium emulations like ZenoMOD and Blenheim):
* **Integration Window:** $300\text{ ms}$ time constant.
* **Inertial Overshoot:** Models mechanical needle physics, accurately reflecting human loudness perception while capturing the natural $1.0\text{ dB}$ to $1.5\text{ dB}$ transient overshoot characteristic of hardware meters.
* **Calibration:** Standardized $+3.0103\text{ dB}$ sine offset correction to ensure alignment with standard reference meters.

### 2. Peak Meter Mode
* Bypasses RMS integration to monitor instantaneous absolute sample peaks ($|\text{sample}|$) for strict ceiling and inter-sample peak awareness.

---

## Installation

1. Open REAPER.
2. Go to **Options > Show REAPER resource path in explorer/finder**.
3. Navigate to the `Effects` folder.
4. Download and place the provided script into this directory.
5. In REAPER, open the FX browser, click **Actions > Rescan all plugins**, and the plugin will be ready to load.

---

## Usage Guide
In the Reaper Mixer (MCP), right-click the plugin in the slot list and check **Show embedded UI in MCP**

### Mixer Layout
The plugins render in a compact 21(mono) / 48(stereo) px-height slot within the Mixer Control Panel (MCP):
* One or two narrow horizontal meter bars representing your signal relative to the Base Level threshold (Green up to $0.0$, Red above).
* above the bars
  * **Left Readout:** Measured signal level relative to target (e.g., `-1.5` or `2.1`). Turns red when exceeding $0.0$.
  * **Center Readout:** Peak signal level relative to target.
  * **Right Readout:** Current Gain Trim volume adjustment.

### Mouse Gestures & Controls
* **Adjust Gain Trim:** Click and drag **vertically** anywhere on the plugin display in the mixer. Drag **up** to boost volume, drag **down** to cut volume.
* **Ultra-Fine Adjustment:** Hold the **Shift** key while dragging for high-precision sub-decibel changes ($100\text{ pixels} = 1.0\text{ dB}$).
* **Plugin Configuration Window:** Open the full plugin window to adjust sliders for **Gain Trim (dB)**, **Base Level (dBFS)**, and the **Meter Mode** toggle switch (`VU (RMS)` vs `Peak`).

---

## Fair Warning
This plugin was vibe-coded by Gemini Pro / Extended. It was thoroughly tested in multiple rounds and in every aspect works as expected. It was run alongside ZenoMOD and Blenheim VU Meter plugins and visually provided the same measurement in VU mode, but I am not a mathematician, so the calculations in the script are not manually verified.
