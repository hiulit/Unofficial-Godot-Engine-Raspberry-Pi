# Unofficial Godot Engine for the Raspberry Pi

Unofficial [Godot Engine](https://godotengine.org/) binaries for the [Raspberry Pi](https://www.raspberrypi.org/).

![Unofficial Godot Engine for the Raspberry Pi](unofficial-godot-raspberry-pi.jpg)

## Limitations

- The Raspberry Pi only supports GLES2.
- The Raspberry Pi doesn't support GPU particles, only CPU particles.
- We don't have `3.0.6` binaries because it doesn't have GLES2 support, only GLES3.
- If the export templates from this repository don't work, you can try the ones from [FRT: a Godot "platform" targeting single board computers](https://github.com/efornara/frt), which offers support for multiple Raspberry Pi revisions and other single-board computers and are well tested.
- We don't offer any kind of support. The binaries are distributed as-is 🙃.

If you would like official Godot support for the Raspberry Pi, there is a [proposal](https://github.com/godotengine/godot-proposals/issues/988) about it. Go there and give us a thumbs up so we can get it 👍 😉 !

## Table of contents

- [Compiling](#compiling)
- [Status](#status)
- [Downloads](#-downloads)
- [How to launch the Editor](#-how-to-launch-the-editor)
- [How to export a game using the Export Templates](#-how-to-export-a-game-using-the-export-templates)
- [How to export an independent PCK file](#%EF%B8%8F-how-to-export-an-independent-pck-file)
- [How to run a game](#-how-to-run-a-game)
- [Troubleshooting](#ℹ%EF%B8%8F-troubleshooting)

## Compiling

See [COMPILING](/COMPILING.md).

## Status

This table refers to the Raspberry Pi 4 only. Prior version are untested.

|  | 2.1.6 | 3.1.2 | 3.3 |
|-|:-:|:-:|:-:|
| Editor | &#x2713; | \*| &#x2713; |
| Export template | &#x2713; | &#x2713; | &#x2713;
| Headless | - | \*\* | \*\* | \*\* |
| Server | - | \*\* | \*\* | \*\* |

- &#x2713;: Works perfectly.
- \*: It works, but it's laggy/unresponsive at fullscreen (1920x1200). Making the editor 1/2 or 1/3 of that size makes it run better.
- \*\*: Untested, but should work fine.

## 📥 Downloads

### 2.1.6

- Raspberry Pi 4
  - [Editor](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/releases/download/v1.2.0/godot_2.1.6_rpi4_editor.zip)
  - [Export template](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/releases/download/v1.2.0/godot_2.1.6_rpi4_export-template.zip)

### 3.1.2

Each ZIP file contains: Editor, Export template, Headless and Server.

- [Raspberry Pi 3](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/releases/download/v1.3.0/godot_3.1.2-stable_rpi3.zip)
- [Raspberry Pi 4](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/releases/download/v1.3.0/godot_3.1.2-stable_rpi4.zip)

### 3.3.2

Each ZIP file contains: Editor, Export template, Headless and Server.

- [Raspberry Pi 3](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/releases/download/v1.4.0/godot_3.3.2-stable_rpi3.zip)
- [Raspberry Pi 4](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/releases/download/v1.4.0/godot_3.3.2-stable_rpi4.zip)

## 🚀 How to launch the Editor

To open the editor, run:

```
./godot_x.x.x_rpi4_editor.bin
```

*(where `x.x.x` is the version of Godot)*.

You might need to give executable permissions to the binary. If that's the case, run:

```
sudo chmod +x godot_x.x.x_rpi4_editor.bin
```

## 🤖 How to export a game using the Export Templates

> You don't have to use a Raspberry Pi to export a game for it. You can use any computer running any OS supported by Godot.

### Godot 2.x

- In the editor, go to `Export`.
- Select the `Linux/X11` template.
- In `Debug`, uncheck `Debugging Enabled`.
- In `Custom Binary -> Release`, select the version of the export template that matches the version of your project.
- In `Binary`, uncheck `64 bits`.
- Click `Export`.
- You can use the `.rpi4` extension when naming the exported game.

### Godot 3.x

- In the editor, go to `Project -> Export`.
- Select the `Linux/X11` template.
- In `Binary Format`, uncheck `64 bits`.
- In `Custom template -> Release`, select the version of the export template that matches the version of your project.
- Click `Export Project`.
- Uncheck `Export With Debug`.
- Optionally, after the game is packed, you can rename the extension of the game's executable binary from `.x86` to `.rpi4` to avoid confusion.

## 🗃️ How to export an independent PCK file

You can export a `.pck` file and run it with the export templates from this repository.

### Godot 2.x

- In the editor, go to `Export`.
- Select the `Linux/X11` template.
- In `Binary`, uncheck `64 bits`.
- Click `Export PCK/ZIP`.
- Enter the name of your game with the `.pck` extension.
- Click `OK`.

### Godot 3.x

- In the editor, go to `Project -> Export`.
- Select the `Linux/X11` template.
- In `Binary Format`, uncheck `64 bits`.
- Click `Export PCK/ZIP`.
- Uncheck `Export With Debug`.
- Enter the name of your game with the `.pck` extension.
- Click `Save`.

## 🎮 How to run a game

### Case 1

- The is no `.pck` file (meaning that it's embedded/compiled in the executable binary).
- The `.pck` file has the same name as the executable binary and they are both in the same directory.

You can just run the executable binary, like this:

```
./name_of_your_godot_game.ext
```

### Case 2

- The `.pck` file has a different name than the executable binary.
- The `.pck` file is in a different directory than the executable binary.
- You are using an independent `.pck` file (without an executable binary).

You'll have to pass the `.pck` file's path using the `--main-pack` option, like this:

```
./godot_x.x.x_rpi4_export-template.bin --main-pack "/path/to/the/pck/file.pck"
```

## ℹ️ Troubleshooting

### A game doesn't launch or crashes

If the game you are trying to play doesn't work, it will most likely be because it was made with another version of Godot.

It could also be because it uses GDNative or C#, which the Raspberry Pi binaries doesn't support.

### Force Godot to use the GLES2 video render

If you get this error when trying to play a game:

> Your video card driver does not support any of the supported OpenGL versions. Please update your drivers or if you have a very old or integrated GPU upgrade it.

It means that the game you are trying to run uses the GLES3 video driver, which the Raspberri Pi doesn't support. 

You'll have to force Godot to use the GLES2 video driver by passing the `--video-driver GLES2` parameter, like this:

```
./godot_x.x.x_rpi4_export-template.bin --main-pack "/path/to/the/pck/file.pck" --video-driver GLES2
```

## 🗒️ Changelog

See [CHANGELOG](/CHANGELOG.md).

## 👤 Author

**hiulit**

- Twitter: [@hiulit](https://twitter.com/hiulit)
- GitHub: [@hiulit](https://github.com/hiulit)

## 🤝 Contributing

Feel free to:

- [Open an issue](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/issues) if you find a bug.
- [Create a pull request](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/pulls) if you have a new cool feature to add to the project.
- [Start a new discussion](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/discussions) about a feature request.

## 🙌 Supporting this project

If you love this project or find it helpful, please consider supporting it through any size donations to help make it better ❤️.

[![Become a patron](https://img.shields.io/badge/Become_a_patron-ff424d?logo=Patreon&style=for-the-badge&logoColor=white)](https://www.patreon.com/hiulit)

[![Suppor me on Ko-Fi](https://img.shields.io/badge/Support_me_on_Ko--fi-F16061?logo=Ko-fi&style=for-the-badge&logoColor=white)](https://ko-fi.com/F2F7136ND)

[![Buy me a coffee](https://img.shields.io/badge/Buy_me_a_coffee-FFDD00?logo=buy-me-a-coffee&style=for-the-badge&logoColor=black)](https://www.buymeacoffee.com/hiulit)

[![Donate Paypal](https://img.shields.io/badge/PayPal-00457C?logo=PayPal&style=for-the-badge&label=Donate)](https://www.paypal.com/paypalme/hiulit)

If you can't, consider sharing it with the world...

[![](https://img.shields.io/badge/Share_on_Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/intent/tweet?url=https%3A%2F%2Fgithub.com%2Fhiulit%2FUnofficial-Godot-Engine-Raspberry-Pi&text=Cross-compile+Godot+binaries+for+the+Raspberry+Pi%3A%0D%0AA+script+to+easily+cross-compile+Godot+binaries+for+the+Raspberry+Pi+from+Linux+x86_64+by+%40hiulit)

... or giving it a [star ⭐️](https://github.com/hiulit/Unofficial-Godot-Engine-Raspberry-Pi/stargazers).

Thank you very much!

## 👏 Credits

Thanks to:

- Juan Linietsky ([@reduz](https://github.com/reduz)), Ariel Manzur ([@punto-](https://github.com/punto-)), Rémi Verschelde ([@akien-mga](https://github.com/akien-mga)) and all the Godot contributors - For creating and maintaining the [Godot Engine](https://github.com/godotengine/godot).
- Emanuele Fornara ([@efornara](https://github.com/efornara)) - For creating [FRT - A Godot "platform" targeting single board computers](https://github.com/efornara/frt).
- Krzysztof Jankowski [@w84death](https://github.com/w84death/) - For the [Raspberry Pi 4 as Perfect Indie Console](https://bits.p1x.in/raspberry-pi-4-as-perfect-indie-console/) blog post.

## 📝 Licenses

- Source code: [MIT License](/LICENSE).
- Godot - Game Engine: [MIT License](/LICENSE_GODOT.txt).
