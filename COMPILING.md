# Compiling

All the binaries are compiled and tested on a non-overcloked Raspberry Pi 4 4GB running [Raspberry Pi OS](https://www.raspberrypi.org/software/operating-systems/) (32 bits), following the [official documentation for compiling Godot in Linux](https://docs.godotengine.org/en/latest/development/compiling/compiling_for_linuxbsd.html).

**NOTES**:

- Up until `3.2.4 beta 4` there was an [audio issue](https://github.com/godotengine/godot/pull/43928) with Godot on a Raspberry Pi. To compile prior versions with the audio issue fixed, all references to `uint8_t` must be changed to `int16_t` in `drivers/alsa/audio_driver_alsa.cpp`.

The SCons parameters and flags used to compile the binaries are a mix between [FRT](https://github.com/efornara/frt) by [@efornara](https://github.com/efornara/) and this [blog post](https://bits.p1x.in/raspberry-pi-4-as-perfect-indie-console/) by [@w84death](https://github.com/w84death/).

### Editor (IDE)

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mtune=cortex-a72 -mcpu=cortex-a72 -mfloat-abi=hard -mlittle-endian -munaligned-access -mfpu=neon-fp-armv8" -j4
```

### Export templates

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mtune=cortex-a72 -mcpu=cortex-a72 -mfloat-abi=hard -mlittle-endian -munaligned-access -mfpu=neon-fp-armv8" -j4
```

### Headless

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mtune=cortex-a72 -mcpu=cortex-a72 -mfloat-abi=hard -mlittle-endian -munaligned-access -mfpu=neon-fp-armv8" -j4
```

### Server

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mtune=cortex-a72 -mcpu=cortex-a72 -mfloat-abi=hard -mlittle-endian -munaligned-access -mfpu=neon-fp-armv8" -j4
```