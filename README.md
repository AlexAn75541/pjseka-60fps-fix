# pjseka-60fps-fix

Guide to force higher FPS for Project SEKAI or any other games via `adb`, although you can set anything above 90 or 120, myself with a nothing phone 4a pro can only go up to 90fps. So it may varies between devices
This is **NOT** a permanent fix, just a temporary workaround. I still got hopes for Nothing OS and Sega or any other game publisher would work together and address this issue, but other than that then we - as users - has to stepped in and work our way through.

Any changes were made to that specific game would be reset if developer options being turned off or the package version got changed(e.g: game update) iirc.

## 1) Find the package name

Use this to list installed user apps and grep for SEGA packages:

```bash
adb shell pm list packages -3 | grep sega # or any other wildcard you can think of based on your game of choice
```

If needed, change `sega` to another identifier.

## 2) Set to high FPS mode

```bash
adb shell cmd game set --fps 120 --mode 2 com.sega.ColorfulStage.en # global version
adb shell cmd game set --fps 120 --mode 2 com.sega.pjsekai # jp version
adb shell cmd game set --fps 120 --mode 2 game.qualiarts.hololive.dreams.com
```
or
```bash
adb shell cmd game set --fps 120 --mode 2 {change to your game package identifier}
```

## 3) Optional: manually lock refresh rate

```bash
adb shell settings put system min_refresh_rate 120.0 # change this value
adb shell settings put system peak_refresh_rate 120.0 # this also
```

To revert it back, please change the `min` and `max` value accordingly to your specific device. For example:

```bash
adb shell settings put system min_refresh_rate 60.0
```

## 4) Optional: fixed performance mode

```bash
adb shell cmd power set-fixed-performance-mode-enabled true
```

And you can set it to `false` afterward if any issues regarding performance are observed.
