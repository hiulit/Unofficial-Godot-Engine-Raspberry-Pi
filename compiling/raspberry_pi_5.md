
# Raspberry Pi 5

## Editor

### 32-bit

```bash
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a76 -mtune=cortex-a76 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```bash
scons platform=x11 target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a76" arch=arm64 -j$(nproc)
```

## Export Templates

### 32-bit

```bash
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a76 -mtune=cortex-a76 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```bash
scons platform=x11 target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a76" arch=arm64 -j$(nproc)
```

## Headless

### 32-bit

```bash
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a76 -mtune=cortex-a76 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```bash
scons platform=server target=release_debug tools=yes use_llvm=yes CCFLAGS="-mcpu=cortex-a76" arch=arm64 -j$(nproc)
```

## Server

### 32-bit

```bash
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a76 -mtune=cortex-a76 -mfpu=neon-fp-armv8 -mfloat-abi=hard" -j$(nproc)
```

### 64-bit

```bash
scons platform=server target=release tools=no use_llvm=yes CCFLAGS="-mcpu=cortex-a76" arch=arm64 -j$(nproc)
```