# ScreenRuler

A Windows desktop tool for screen measurements, layout inspection, and alignment. Edge rulers, guidelines, markers, continuous measurements, and window snapping support independent multi-monitor configurations.

[简体中文](README.zh-CN.md) | **English**

![.NET](https://img.shields.io/badge/.NET-5.0-blue)
![Platform](https://img.shields.io/badge/Platform-Windows_x64-lightgrey)
![Version](https://img.shields.io/badge/Version-1.2.1-blue)

[Downloads](../../releases) · [Default keys](#default-keys) · [Build and verify](#build-and-verify)

![ScreenRuler desktop rulers and guidelines](https://github.com/user-attachments/assets/381d4a2e-7e22-4922-a895-11511a10b842)

## Features

| Feature | Purpose |
| --- | --- |
| Screen rulers | Top and left rulers with pixels, centimeters, inches, pointer indicators, and numeric tooltips |
| Guidelines | Create by dragging or double-clicking, inspect positions while moving, customize line styles, and save positions |
| Quick and continuous measurements | Inspect boundary spans and gaps, or click successive points to draw paths and closed outlines |
| Screen markers | Mark positions with circles, squares, diamonds, crosses, or custom images |
| Snapping | Align guides with anchors, windows, controls, and image edges; fit external windows into guide-defined regions |
| Named anchors | Store named positions in fixed units or percentages, separately for each screen |
| Physical calibration and precision | Calibrate horizontal and vertical dimensions per screen; configure tick intervals and decimal places per unit |
| Multi-monitor visibility | Toggle one screen from its corner button or all screens from the tray |
| Appearance and controls | Customize colors, styles, thickness, opacity, and keys; Chinese/English UI and optional startup with Windows |
| User manual | Searchable chapters, diagrams, terminology, and the currently configured keys |

## Download and start

Intended for Windows 10/11 x64. Currently, only the framework-dependent package is available from [Releases](../../releases); it does not include the runtime:

| Package | Requirements |
| --- | --- |
| Framework-dependent | Requires [.NET Desktop Runtime 5.0 x64](https://dotnet.microsoft.com/en-us/download/dotnet/5.0); the plain .NET Runtime does not include WPF desktop components |

1. Download a program ZIP attachment. GitHub's automatic `Source code` archives contain source files.
2. Extract it to a folder you can write to, then run `ScreenRuler.exe`.
3. Right-click the corner button or tray icon to open settings or help.

This version targets .NET 5, which has reached end of support. See the [Microsoft download page](https://dotnet.microsoft.com/en-us/download/dotnet/5.0).

## Getting started

### Guidelines and markers

- Drag down from the top ruler to create a **horizontal guideline**, or right from the left ruler to create a **vertical guideline**. Direct dragging is the default; key-assisted mode requires the guide key first.
- Double-click the top ruler to create a vertical guideline, or the left ruler to create a horizontal guideline.
- Hold `Left Shift` to move an existing guide. Also hold `Left Ctrl` to snap; when creating a guide, `Left Ctrl` alone enables snapping.
- Hold `Left Shift` and double-click a guide to delete it, or drag it back to its corresponding ruler. Dashed gaps and the area immediately beside the line remain selectable.
- Drag from the corner button to create a **marker**. Hold `Left Shift` to move or double-click to delete it; dragging back to the top-left corner also deletes it.

### Quick measurements

Hold `Left Alt` alone for **500 ms**. Once measurements appear, move the pointer to inspect distances. Releasing the key without clicking ends the measurement and saves nothing.

After activation, hold `Left Shift` for vertical distances only or `Left Ctrl` for horizontal distances only. Settings let you choose spans between nearest boundaries, gaps to nearest guides or screen edges, and distances to all four screen edges. Measurement units can follow the ruler or use a separate unit.

Another key, mouse click, or wheel input during the hold delay cancels activation, allowing shortcuts such as `Alt+Z`. Once active, measurements capture subsequent keyboard, mouse-button, and wheel input until the measurement key is released.

### Continuous measurements

1. Hold `Left Alt` alone and wait for measurements to appear.
2. Left-click the starting point, move to preview the next segment, and click to confirm its endpoint. Repeat as needed.
3. **Release the measurement key** to keep confirmed segments and discard the preview. A single point is discarded.
4. **Double-click the endpoint or press `Enter`** to confirm the endpoint and connect back to the start. Closing requires at least three distinct points; two points remain a single segment.
5. Release the key after finishing, then hold it again to start another measurement. No `Esc` action is needed.

Drawing stays on the starting screen. After activation, hold the snap key to align nodes with anchors, guides, or screen edges. Hold `Left Shift`, hover over a completed path, and double-click to delete the whole result. Paths last only for the current session.

### Anchors, calibration, and precision

An **anchor** is a named position saved on a ruler. Right-click a ruler to add a name and a value in `px`, `cm`, `in`, or percent. Hover to see its name and position. Manage, disable, delete, or restore center anchors per screen in settings. The former center marks are represented by two removable `50%` anchors.

**Physical calibration** aligns centimeters and inches with a physical ruler. Select a screen in the calibration settings, measure both displayed sample lines, enter their actual lengths in centimeters, and apply. Each screen stores its own calibration, with conversion adjusted for resolution and rotation changes.

**Precision** controls presentation. Configure minor and major tick intervals, automatic labels, and 0–4 decimal places for each unit. Display rounding does not reduce internal position precision.

### Snapping and window layouts

| Object | Snap targets |
| --- | --- |
| New or existing guideline | Anchors, screen edges, window borders, controls, and detectable image edges |
| Continuous measurement node | Anchors, guidelines, and screen edges |
| External window | Guidelines and screen edges; anchors are not direct window snap targets |

Enable the corresponding snapping option and hold the snap key, `Left Ctrl` by default. Dragging an external window previews the target region; release the mouse to apply it. By default, both position and size change, with a position-only option available.

Guide pixel-edge detection runs in the background and discards stale results. Release the snap key while dragging to return immediately to free movement.

### Visibility and clearing

| Entry point | Scope and behavior |
| --- | --- |
| Corner-button click | Toggles only the current screen and always keeps the button available |
| Tray visibility toggle | Toggles all screens; the optional corner-button visibility setting also hides/restores corner buttons with tray actions |
| Corner-menu clear actions | Clear the selected content on the current screen |
| Tray-menu clear actions | Clear the selected content on all screens |

Choose **Hide all** or **Hide rulers only** for the corner button. Hide all includes guides, markers, and measurements; Hide rulers only keeps these overlays visible. Following tray visibility is off by default and requires the tray icon to be enabled. Corner-button options are grouped in the ruler settings.

**Clear all** removes guides, markers, and measurements. Anchors are managed separately. **Clear confirmation is off by default**; enable it in system settings to review scope and counts before clearing.

## Default keys

These defaults use the left-side keys and can be changed in key settings. Feature switches and drag mode still apply.

| Action | Default input |
| --- | --- |
| Move a guide or marker | `Left Shift` + left-button drag |
| Delete a guide, marker, or complete measurement path | `Left Shift` + double-click |
| Snap | Hold `Left Ctrl` during the operation |
| Start measuring | Hold `Left Alt` alone for 500 ms |
| Vertical / horizontal quick measurements only | After activation, hold `Left Shift` / `Left Ctrl` |
| Finish and close a measurement path | Double-click the endpoint or press `Enter` |
| Interact with a window beneath a ruler | Hold `Left Ctrl` while interacting over the ruler |

Desktop tools remain available while settings or help windows are open. Measuring does not start over a foreground tool dialog; move the pointer outside it to measure.

## Settings and saved data

Settings cover rulers, guides, markers, measurements, snapping, keys, anchors, calibration, precision, and system options. **Apply** saves changes immediately without closing the dialog. Ruler, guide, and measurement opacity can all be set to `0%`.

| Data | Storage |
| --- | --- |
| Settings, anchors, calibration, and precision | `settings.json` |
| Guide positions | `guidelines.json`; saving is enabled by default |
| Marker positions and images | `markers.json` and `marker-assets`; saving is enabled by default |
| Continuous measurement paths | Current session only |

- **Portable mode:** `portable.txt` beside the executable stores configuration in the application folder. Publishing scripts create this marker by default.
- **Normal mode:** without `portable.txt`, configuration is stored in `%APPDATA%\ScreenRuler`.
- **Upgrading:** exit the app, back up the configuration folder, then replace program files. Preserve configuration, images, and the existing `portable.txt` state.
- **Changing modes:** exit the app before adding/removing `portable.txt`, and move configuration manually if needed. Data is not migrated automatically.

## Build and verify

On Windows, install a .NET SDK supporting `net5.0-windows` (the project currently uses .NET 5 / WPF). Download the source and run these commands from the repository root:

```powershell
dotnet restore ScreenRuler.sln
dotnet build ScreenRuler.sln -c Release
dotnet test ScreenRuler.Tests/ScreenRuler.Tests.csproj -c Release
dotnet run --project ScreenRuler/ScreenRuler.csproj -c Release
```

Desktop dragging, multiple screens, input capture, and snapping also require the [manual verification checklist (Chinese)](docs/MANUAL_VERIFICATION.md).

Generate portable package contents with the existing script:

```powershell
# Requires .NET Desktop Runtime 5.0 x64
.\publish.ps1 -OutputDir .\publish\framework-dependent
```

The script clears its output directory before publishing; use a dedicated build folder. See the [1.2.1 release guide (Chinese)](docs/RELEASE_1.2.1.md) for packaging and GitHub publication, and the [release notes](docs/RELEASE_NOTES_1.2.1.md) for the announcement.

## Author and license

Created by [windmo](https://windmo.com). MIT License.
