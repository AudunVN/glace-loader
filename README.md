# glace-loader

## Converting with ffmpeg
Note that the examples below use Windows-formatted paths. Switching to forward slashes in file paths and using `*.png` instead of `%02d.png` should work on most Linux-based shells.

Create new animated png from frames:
```powershell
ffmpeg -r 60 -i "frames\60fps\512px\glc-%02d.png" -framerate 60 -plays 0 -f apng glc.png
```

Create new gif from frames:
```powershell
ffmpeg -i "frames\50fps\512px\glc-%02d.png" -vf palettegen=reserve_transparent=1 "frames\50fps\512px\palette.png"
ffmpeg -i "frames\50fps\512px\glc-%02d.png" -i "frames\50fps\512px\palette.png" -lavfi paletteuse=alpha_threshold=128 -gifflags -offsetting -framerate 50 glc.gif
```