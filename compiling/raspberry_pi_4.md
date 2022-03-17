# Raspberry Pi 4

## Editor

### 32 bit

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

### 64 bit

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-march=armv8-a+fp+simd" arch=arm64 -j4
```

## Export templates

### 32 bit

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

### 64 bit

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-march=armv8-a+fp+simd" arch=arm64 -j4
```

## Headless

### 32 bit

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

### 64 bit

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-march=armv8-a+fp+simd" arch=arm64 -j4
```

## Server

### 32 bit

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard -mlittle-endian -munaligned-access" -j4
```

### 64 bit

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-march=armv8-a+fp+simd" arch=arm64 -j4
```
