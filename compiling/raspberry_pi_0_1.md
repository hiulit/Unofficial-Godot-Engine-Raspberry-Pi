# Raspberry Pi 0 and 1

## Editor

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```

## Export templates

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```

## Headless

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```

## Server

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=arm1176jzf-s -mtune=arm1176jzf-s -mfpu=vfp -mfloat-abi=hard -mlittle-endian -munaligned-access" -j1
```
