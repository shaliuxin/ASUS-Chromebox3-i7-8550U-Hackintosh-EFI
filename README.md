# Asus Chromebox 3 (i7-8550U) macOS Sequoia 15.4 EFI (OpenCore 1.0.3)

[English Version](#english-version) | [中文版](#中文版)

## English Version

This repository contains the EFI files for running macOS Sequoia 15.4 on the Asus Chromebox 3 with an Intel i7-8550U CPU using OpenCore 1.0.3.

### Specifications

- **Model:** Asus Chromebox 3
- **CPU:** Intel Core i7-8550U
- **GPU:** Intel UHD 620
- **RAM:** 32GB DDR4 (user-upgraded)
- **Storage:** 2T NVMe SSD (user-upgraded)
- **Audio:** Realtek ALC5650
- **Wi-Fi:** Broadcom BCM943602CS
- **Bootloader:** OpenCore 1.0.3
- **macOS Version:** Sequoia 15.4
- **Drivers:** All of kexts up to date (6/4/2025)

### What's Working

- [x] Intel UHD 620 Graphics (with hardware acceleration)
- [x] Audio (internal speakers, microphone, headphone jack)
- [x] Wi-Fi & Bluetooth (with BCM943602CS from Apple)
- [x] USB Ports (Type-A and Type-C)
- [x] HDMI output
- [x] Sleep/Wake
- [x] Brightness Control
- [x] Ethernet
- [x] macOS Power Management (including CPU power states)
- [x] AirDrop, Handoff, and Sidecar

### Not Working / Issues

- [ ] SD Card Reader (if present, typically unsupported in macOS)
- [ ] Thunderbolt 3 (if present, hot-plug may not work)
- [ ] Occasional wake from sleep issues (depends on ACPI patch configuration)

### Coreboot Configuration

To run macOS smoothly on the Asus Chromebox 3, it is recommended to replace the stock firmware with Coreboot. Here's a brief overview of the process:

1. **Install and Configure MrChromebox Coreboot**:
    - Follow the instructions on [MrChromebox.tech](https://mrchromebox.tech) to flash Coreboot firmware.
    - Ensure the firmware is configured to allow UEFI boot mode.

2. **Bootloader Setup**:
    - Use OpenCore as the bootloader. The EFI folder provided in this repository is already configured for optimal compatibility with macOS Sequoia.

3. **Disable Write Protection**:
    - Before flashing, you may need to disable write protection by removing the WP screw on the motherboard.

4. **Update Firmware**:
    - Use the MrChromebox script to install the UEFI firmware. This will replace the factory BIOS with Coreboot.

### Installation

1. **Prepare macOS USB Installer**: Create a macOS Sequoia 15.4 installer using [macOS Recovery](https://support.apple.com/en-us/HT201372) or from a working macOS environment.

2. **Copy EFI Folder**: After creating the USB installer, replace the EFI folder on the USB drive with the one from this repository.

3. **Boot the Installer**: Boot from the USB installer and follow the standard macOS installation steps.

4. **Post-Installation**:
    - Copy the EFI folder from the USB to your system's EFI partition after installing macOS.
    - Generate your own SMBIOS using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) and replace the `SerialNumber`, `BoardSerialNumber`, and `SmUUID` in `config.plist`.

### Known Issues & Troubleshooting

- **Wake from Sleep Issues**: If the system does not wake from sleep properly, try adjusting the `Darkwake` settings in `config.plist`.

### Credits

- [SomeTech](https://github.com/SoMeTech/) for base of OpenCore and kexts
- [MrChromebox.tech](https://mrchromebox.tech) for Coreboot/UEFI firmware
- [laoWu Hackintosh Studio](https://hpglw.com/) for update
- [jingkunchen](https://github.com/jingkunchen) for base of readme

---

## 中文版

本仓库包含用于在 Asus Chromebox 3 (搭载 Intel i7-8550U CPU) 上运行 macOS Sequoia 15.4 的 EFI 文件，使用 OpenCore 1.0.3 引导。

### 规格

- **型号：** Asus Chromebox 3
- **处理器：** Intel Core i7-8550U
- **显卡：** Intel UHD 620
- **内存：** 32GB DDR4 (用户自行升级)
- **存储：** 2T NVMe SSD (用户自行升级)
- **音频：** Realtek ALC5650
- **无线网络：** Broadcom BCM943602CS
- **引导器：** OpenCore 1.0.3
- **macOS 版本：** Sequoia 15.4
- **驱动：** 所有kexts升级到当前最新版本（2025/4/6）

### 已实现功能

- [x] Intel UHD 620 显卡 (支持硬件加速)
- [x] 音频 (内置扬声器、麦克风、耳机接口)
- [x] Wi-Fi 和蓝牙 (使用Apple拆机BCM943602CS)
- [x] USB 接口 (Type-A 和 Type-C)
- [x] HDMI 输出
- [x] 睡眠/唤醒
- [x] 亮度控制
- [x] 以太网
- [x] macOS 电源管理 (包括 CPU 电源状态)
- [x] AirDrop, Handoff, and Sidecar

### 不工作/存在问题

- [ ] SD 卡读卡器 (如果存在，macOS 通常不支持)
- [ ] Thunderbolt 3 (如存在，热插拔可能无法正常工作)
- [ ] 偶尔的睡眠唤醒问题 (取决于 ACPI 补丁配置)

### Coreboot (兔子 BIOS) 配置

要在 Asus Chromebox 3 上顺畅运行 macOS，建议将原厂固件替换为 Coreboot (通常称为 “兔子 BIOS”)。以下是简要步骤：

1. **安装和配置 MrChromebox Coreboot**：
    - 按照 [MrChromebox.tech](https://mrchromebox.tech) 上的说明刷写 Coreboot 固件。
    - 确保固件已配置为允许 UEFI 启动模式。

2. **引导器设置**：
    - 使用 OpenCore 作为引导器。本仓库提供的 EFI 文件夹已经为 macOS Sequoia 做了最佳兼容性配置。

3. **禁用写保护**：
    - 在刷写之前，可能需要通过移除主板上的 WP 螺丝来禁用写保护。

4. **更新固件**：
    - 使用 MrChromebox 的脚本安装 UEFI 固件，这将用 Coreboot 替换工厂 BIOS。

### 安装步骤

1. **准备 macOS USB 安装盘**：使用 [macOS 恢复](https://support.apple.com/zh-cn/HT201372) 或一个正常工作的 macOS 环境创建 macOS Sequoia 15.4 安装盘。

2. **复制 EFI 文件夹**：创建 USB 安装盘后，将该仓库中的 EFI 文件夹替换到 USB 安装盘的 EFI 分区。

3. **启动安装程序**：从 USB 启动安装程序，按照标准的 macOS 安装步骤进行操作。

4. **安装后处理**：
    - 在安装 macOS 后，将 USB 中的 EFI 文件夹复制到系统的 EFI 分区。
    - 使用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成你自己的 SMBIOS，并在 `config.plist` 中替换 `SerialNumber`、`BoardSerialNumber` 和 `SmUUID`。

### 已知问题和故障排除

- **睡眠唤醒问题**：如果系统无法正常从睡眠中唤醒，可以尝试调整 `config.plist` 中的 Darkwake 设置。

### 鸣谢

- [SomeTech](https://github.com/SoMeTech/) 本套件是在其基础上制作的
- [MrChromebox.tech](https://mrchromebox.tech) 提供的 Coreboot/UEFI 固件
- [laoWu Hackintosh Studio](https://hpglw.com/) 提供了OpenCore的更新
- [jingkunchen](https://github.com/jingkunchen) 本readme在其基础上修改而来

---

