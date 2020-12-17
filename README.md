# Unnoficial Raspberry Pi Godot Engine

Unnoficial [Godot Engine](https://godotengine.org/) editor and export templates binaries for the Raspberry Pi.

All the binaries are compiled and tested on a non-overcloked **Raspberry Pi 4 4GB** running [Raspberry Pi OS](https://www.raspberrypi.org/software/operating-systems/), following the [official documentation for compiling Godot in Linux](https://docs.godotengine.org/en/latest/development/compiling/compiling_for_linuxbsd.html).

The scons parameters and flags used to compile both the editor and the export templates are a mix between [FRT](https://github.com/efornara/frt) by [@efornara](https://github.com/efornara/) and this [blog post](https://bits.p1x.in/raspberry-pi-4-as-perfect-indie-console/) by [@w84death](https://github.com/w84death/).

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mtune=cortex-a72 -mcpu=cortex-a72 -mfloat-abi=hard -mlittle-endian -munaligned-access -mfpu=neon-fp-armv8" -j4
```

*The scons parameters above are used to compile the editor. To compile the export templates, `target=release` and `tools=no` must be used*.

**NOTE**:

Currently only the Raspberry Pi 4 is supported.

## Editor

### Support and downloads

|  | 2.1.6 | 3.0.6 | 3.1.0 | 3.1.1 | 3.1.2 | 3.2.0 | 3.2.1 | 3.2.2 | 3.2.3 | 3.2.4 beta 4 |
|-|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| Status | &#x2713; | &#x2717; | * | * | * | * | * | * | * | &#x2713; |
| Download | URL | &#x2717; | URL | URL | URL | URL | URL | URL | URL | URL |

- ✓: Works perfectly.
- ✗: Doesn't work.
- \*: It works, but it's laggy/unresponsive at fullscreen (1920x1200). Making the editor 1/2 or 1/3 of that size makes it run better.

### How to launch the editor

To open the editor, run:

```
./godot_x.x.x_rpi4_editor.bin
```

*(where `x.x.x` is the version of Godot)*.

You might need to give executable permissions to the binary. If that's the case, run:

```
sudo chmod +x godot_x.x.x_rpi4_editor.bin
```

## Export templates

### Support and downloads

|  | 2.1.6 | 3.0.6 | 3.1.0 | 3.1.1 | 3.1.2 | 3.2.0 | 3.2.1 | 3.2.2 | 3.2.3 | 3.2.4 beta 4 |
|-|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| Status | &#x2713; | &#x2717; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; | &#x2713; |
| Download | URL | &#x2717; | URL | URL | URL | URL | URL | URL | URL | URL |

- ✓: Works perfectly.
- ✗: Doesn't work.

### How to use the export templates

**NOTE**:

You don't have to use a Raspberry Pi to export a game for it. You can use any computer running any OS supported by Godot.

#### Godot 2.x

- In the editor, go to `Export`.
- Select the `Linux/X11` template.
- In `Debug`, uncheck `Debugging Enabled`.
- In `Custom Binary -> Release`, select the version of the export template that matches the version of your project.
- In `Binary`, uncheck `64 bits`.
- Click `Export`.
- You can use the `.rpi4` extension when naming the exported game.

#### Godot 3.x

- In the editor, go to `Project -> Export`.
- Select the `Linux/X11` template.
- In `Binary Format`, uncheck `64 bits`.
- In `Custom template -> Release`, select the version of the export template that matches the version of your project.
- Click `Export Project`.
- Uncheck `Export With Debug`.
- Optionally, after the game is packed, you can rename the extension of the game's executable binary from `.x86` to `.rpi4` to avoid confusion.

## Exporting an independant PCK file

You can just export a `.pck` file and run it with the export templates from this repository.

### Godot 2.x

- In the editor, go to `Project -> Export`.
- Select the `Linux/X11` template.
- In `Binary Format`, uncheck `64 bits`.
- Click `Export PCK/Zip`.
- Enter the name of your game with the `.pck` extension.
- Click `OK`.

### Godot 3.x

- In the editor, go to `Project -> Export`.
- Select the `Linux/X11` template.
- In `Binary Format`, uncheck `64 bits`.
- Click `Export PCK/Zip`.
- Uncheck `Export With Debug`.
- Enter the name of your game with the `.pck` extension.
- Click `Save`.

## How to run a game

### Case 1

- The `.pck` file is embedded/compiled in the executable binary.
- The `.pck` file has the same name as the executable binary and they are both in the same directory.

You can just run the executable binary, like this:

```
./name_of_your_godot_game.ext
```

### Case 2

- The `.pck` file has a different name than the executable binary.
- The `.pck` file is in a different directory than the executable binary.
- You are using an independant `.pck` file.

You'll have to pass the `.pck` file's path using the `--main-pack` option, like this:

```
# Using your own exported binary.
./name_of_your_godot_game.ext --main-pack "/path/to/the/pck/file.pck"

# Using the export template binaries from this repository.
./godot_x.x.x_rpi4_export-template.bin --main-pack "/path/to/the/pck/file.pck"
```

## Troubleshooting

### A game doesn't launch or crashes

If the game you are trying to play doesn't work, it will most likely be because it was made with another version of Godot.

It could also be because it uses GDNative or C++ with the Raspberry Pi binaries doesn't support.

## Force Godot to use the GLES2 video render

If you get this error when trying to play a game:

> Your video card driver does not support any of the supported OpenGL versions. Please update your drivers or if you have a very old or integrated GPU upgrade it.

It means that the game you are trying to run uses the GLES3 video driver, which the Raspberri Pi doesn't support. 

You'll have to force Godot to use the GLES3 video driver by passing the `--video-driver GLES2` parameter, like this:

```
# Using your own exported binary.
## Embedded/compiled PCK.
./name_of_your_godot_game.ext --video-driver GLES2
## Independant PCK.
./name_of_your_godot_game.ext --main-pack "/path/to/the/pck/file.pck" --video-driver GLES2

# Using the export template binaries from this repository.
./godot_x.x.x_rpi4_export-template.bin --main-pack "/path/to/the/pck/file.pck" --video-driver GLES2
```

## Changelog

See [CHANGELOG](/CHANGELOG.md).

## Author

Me 😛 [@hiulit](https://github.com/hiulit).

## Credits

Thanks to:

- Juan Linietsky ([@reduz](https://github.com/reduz)), Ariel Manzur ([@punto-](https://github.com/punto-)), Rémi Verschelde ([@akien-mga](https://github.com/akien-mga)) and all the Godot contributors - For creating and maintaining the [Godot Engine](https://github.com/godotengine/godot).
- Emanuele Fornara ([@efornara](https://github.com/efornara)) - For creating [FRT - A Godot "platform" targeting single board computers](https://github.com/efornara/frt).
- Krzysztof Jankowski [@w84death](https://github.com/w84death/) - For the [Raspberry Pi 4 as Perfect Indie Console](https://bits.p1x.in/raspberry-pi-4-as-perfect-indie-console/) blog post.

## LICENSE

- Source code: [MIT License](/LICENSE).
- Godot - Game Engine: [MIT License](/LICENSE_GODOT.txt).
