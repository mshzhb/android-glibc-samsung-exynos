# Mobox for Samsung Exynos (Xclipse GPU)  
**Native glibc Environment with DRI3 Support**

🚀 A lightweight Linux container (Mobox) running on **Samsung Exynos** with **Xclipse GPU**, featuring native `glibc` and full **DRI3** support for accelerated graphics.

🎥 **Demo Video**:  
[![Mobox on Xclipse GPU](https://img.youtube.com/vi/SHAmlbQAxXM/0.jpg)](https://www.youtube.com/watch?v=SHAmlbQAxXM)

🔗 [Watch on YouTube](https://www.youtube.com/watch?v=SHAmlbQAxXM)

## Installation Steps
### 1. Install Dependencies
- **Install Termux**:  
  Download and install the [Termux](https://f-droid.org/en/packages/com.termux/) app.
- **Install Termux-X11**:  
  Install [Termux-X11](https://github.com/termux/termux-x11/releases/tag/nightly) to enable graphical environment support. (20250121+)

### 2. Disable PHANTOM Processor Killer in Android
Run the following commands via **ADB** (Android Debug Bridge) on your computer:
```bash
adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
adb shell settings put global settings_enable_monitor_phantom_procs false
```

### 3. Transfer Backup File

📦 **Download Backup File:**  
[`backup-native.tar.xz`](https://mega.nz/file/edZFjKhZ#zi-7xDyzLUiFa4DbU0AIo7qOmQcMTwMXVFF0yt0pcjE)

📲 **Push to Device via ADB:**
```bash
adb push backup-native.tar.xz /sdcard/Download/


### 4. Restore the Environment in Termux
Open Termux on your device and run the following commands:
```bash
termux-reset #optional
termux-setup-storage
termux-restore ~/storage/download/backup-native.tar.xz
cp -r $PREFIX/restore/* ~
```

### 6. Launch Mobox
To start the graphical environment in Termux:
```bash
//detailed instruction: https://github.com/olegos2/mobox
mobox
```

## Optional. Launch the XFCE Desktop
To start the graphical environment in Termux:
```bash
chmod +x startxface4_termux.sh
./startxface4_termux.sh
```

## Running Vulkan Tests
To test Vulkan functionality:
Navigate to the Vulkan test binaries directory:
 ```bash
 cd ~/workspace/Vulkan/build/bin
 grun ./executable
 ```

## Running DX11 Tests
To test DirectX 11 functionality:
 ```bash
 cd ~/workspace/rubic/release-dx11
 run cube.exe
 ```



