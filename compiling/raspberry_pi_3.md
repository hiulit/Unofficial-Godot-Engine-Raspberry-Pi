# Raspberry Pi 3

## Editor

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

## Export templates

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

## Headless

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

## Server

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a53 -mtune=cortex-a53 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```
