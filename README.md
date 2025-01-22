## android-glibc-samsung-exynos
Termux native glibc environment for samsung xclipse GPU

# Installation Steps

## 1. Install Dependencies
- **Install Termux**:  
  Download and install the [Termux](https://f-droid.org/en/packages/com.termux/) app.

- **Install Termux-X11**:  
  Install Termux-X11 to enable graphical environment support.

---

## 2. Disable PHANTOM Processor Killer in Android
Run the following commands via **ADB** (Android Debug Bridge) on your computer:

```bash
adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
adb shell settings put global settings_enable_monitor_phantom_procs false
```

---

## 3. Transfer Backup File
Copy the backup file from your computer to your Android device using **ADB**:

```bash
adb push S:\user\tong.liu\proot-debian\backup-native.tar.xz /sdcard/Download/
```

---

## 4. Restore the Environment in Termux
Open Termux on your device and run the following commands:

```bash
termux-reset
termux-setup-storage
termux-restore /storage/download/backup-native.tar.xz
cp -r $PREFIX/restore/* ~
```

---

## 5. Launch the XFCE Desktop
To start the graphical environment in Termux:

```bash
chmod +x startxface4_termux.sh
./startxface4_termux.sh
```

---

# Vulkan Driver & Dependencies

## Vulkan Driver JSON Path
The Vulkan driver JSON can be found in:

```bash
$PREFIX/glibc/share/vulkan/icd.d/
```

## Library Paths
Path for `libdrm` and `SUMD`:

```bash
$PREFIX/glibc/lib
```

---

# Running Vulkan Tests
To test Vulkan functionality:

1. Navigate to the Vulkan test binaries directory:
   ```bash
   cd ~/workspace/Vulkan/build/bin
   ```

2. Use `glibc-runner` to run Vulkan executables:
   ```bash
   glibc-runner ./executable
   glibc-runner vkcube
   ```

---

# Running DX11 Tests
To test DirectX 11 functionality:

1. Navigate to the DX11 test binaries directory:
   ```bash
   cd ~/workspace/rubic/release-dx9
   ```

2. Run `cube.exe` using **Wine**, **Box64**, and **DXVK**:
   ```bash
   ./cube.exe
   ```

