# Raspberry Pi 4

## Editor

### 32-bit

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72" arch=arm64 -j$(nproc)
```

## Export Templates

### 32-bit

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72" arch=arm64 -j$(nproc)
```

## Headless

### 32-bit

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a72" arch=arm64 -j$(nproc)
```

## Server

### 32-bit

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72 -mtune=cortex-a72 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a72" arch=arm64 -j$(nproc)
```
