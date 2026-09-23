# pjseka-60fps-fix

Guide to force higher FPS for Project SEKAI or any other games via `adb`, although you can set anything above 90 or 120, myself with a nothing phone 4a pro can only go up to 90fps. So it may varies between devices

## 1) Find the package name

Use this to list installed user apps and grep for SEGA packages:

```bash
adb shell pm list packages -3 | grep sega # or any other wildcard you can think of based on your game of choice
```

If needed, change `sega` to another identifier.

## 2) Set 120 FPS game mode

```bash
adb shell cmd game set --fps 120 --mode 2 com.sega.ColorfulStage.en # global version
adb shell cmd game set --fps 120 --mode 2 com.sega.pjsekai # jp version
adb shell cmd game set --fps 120 --mode 2 {change to your game's identifier}
```

## 3) Manually lock refresh rate

```bash
adb shell settings put system min_refresh_rate 120.0 # change this value
adb shell settings put system peak_refresh_rate 120.0 # this also
```

## 4) Optional: fixed performance mode

```bash
adb shell cmd power set-fixed-performance-mode-enabled true
```
