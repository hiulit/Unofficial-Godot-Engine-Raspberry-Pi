# Compiling

- [Compile on the Raspberry Pi](#compile-on-the-raspberry-pi)
- [Cross-compile from Linux x86_64](#cross-compile-from-linux-x86_64)

**NOTES**:

- Up until `3.2.4 beta 4` there was an [audio issue](https://github.com/godotengine/godot/pull/43928) with Godot on a Raspberry Pi. To compile prior versions with the audio issue fixed, all references to `uint8_t` must be changed to `int16_t` in `drivers/alsa/audio_driver_alsa.cpp`.

## Requirements

- [Godot source files](https://github.com/godotengine/godot).
- [Godot dependecies to compile for Linux](https://docs.godotengine.org/en/stable/development/compiling/compiling_for_x11.html).

## Compile on the Raspberry Pi

### Raspberry Pi 0 and 1

#### Editor

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```

#### Export templates

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```

#### Headless

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```

#### Server

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```


### Raspberry Pi 2

#### Editor

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a7 -mtune=cortex-a7 -mfpu=neon-vfpv4 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Export templates

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a7 -mtune=cortex-a7 -mfpu=neon-vfpv4 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Headless

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a7 -mtune=cortex-a7 -mfpu=neon-vfpv4 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Server

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a7 -mtune=cortex-a7 -mfpu=neon-vfpv4 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

### Raspberry Pi 3

#### Editor

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Export templates

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Headless

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Server

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

### Raspberry Pi 4

#### Editor

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Export templates

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Headless

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

#### Server

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

## Cross-compile from Linux x86_64

You can use [cross-compile-godot-raspberry-pi](https://github.com/hiulit/cross-compile-godot-raspberry-pi), a script to easily cross-compile Godot binaries for the Raspberry Pi from Linux x86_64.