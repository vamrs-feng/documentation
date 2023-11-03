---
sidebar_label: "使用 rsetup 安装设备树覆盖文件（DTBO）或源码（DTS）"
sidebar_position: 10
---

# 使用 rsetup 安装设备树覆盖文件（DTBO）或源码（DTS）

:::info
rsetup 的 Install 3rd party overlay 功能既可安装设备树覆盖文件（DTBO）也可安装源码（DTS）。  
官方设备树覆盖文件仓库 radxa/overlays 的预编译文件可以[从此下载](https://github.com/radxa/overlays/actions)，  
解压后可跳转到[进入 rsetup，并加载设备树覆盖文件（DTBO）或源码（DTS）](/radxa-os/rsetup/install_overlays#进入-rsetup并加载设备树覆盖文件dtbo或源码dts)继续操作。
:::

## 获取 radxa/overlays 源码

```bash
git clone https://github.com/radxa/overlays.git
cd overlays
```

## 进入 rsetup，并加载设备树覆盖文件（DTBO）或源码（DTS）

```bash
rsetup
# 按照以下选项进入 Install 3rd party overlay 界面
# Overlays -> Install 3rd party overlay
```

![Overlays](/img/radxa-os/rsetup/install_overlays/Overlays.webp)

![Install_3rd_party_overlay](/img/radxa-os/rsetup/install_overlays/Install_3rd_party_overlay.webp)

:::info
以下为瑞芯微 SOC 设备树覆盖文件源码的路径。  
arch/arm64/boot/dts/rockchip/overlays/\*.dts  
如果 SOC 厂商为晶晨需要更换以上路径里的 rockchip 为 amlogic。
:::

### 进入后选择你所需要的设备树覆盖文件（DTBO）或源码（DTS），然后退出 rsetup。

## 重启

```bash
#可以使用 cat /boot/extlinux/extlinux.conf 检查参数
sudo reboot
```