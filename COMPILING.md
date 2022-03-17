# Compiling

- [Requirements](#requirements)
- [Compile on the Raspberry Pi](#compile-on-the-raspberry-pi)
- [Cross-compile from Linux x86_64](#cross-compile-from-linux-x86_64)

**NOTES**:

- Up until `3.2.4 beta 4` there was an [audio issue](https://github.com/godotengine/godot/pull/43928) with Godot on a Raspberry Pi. To compile prior versions with the audio issue fixed, all references to `uint8_t` must be changed to `int16_t` in `drivers/alsa/audio_driver_alsa.cpp`.

## Requirements

- [Godot source files](https://github.com/godotengine/godot).
- [Godot dependecies to compile for Linux](https://docs.godotengine.org/en/stable/development/compiling/compiling_for_x11.html).

## Compile on the Raspberry Pi

- [Raspberry Pi 0 and 1](/compiling/raspberry_pi_0_1.md)
- [Raspberry Pi 2](/compiling/raspberry_pi_2.md)
- [Raspberry Pi 3](/compiling/raspberry_pi_3.md)
- [Raspberry Pi 4](/compiling/raspberry_pi_4.md)

## Cross-compile from Linux x86_64

You can use [cross-compile-godot-raspberry-pi](https://github.com/hiulit/cross-compile-godot-raspberry-pi), a script to easily cross-compile Godot binaries for the Raspberry Pi from Linux x86_64.