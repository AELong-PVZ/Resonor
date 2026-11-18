# Resonor

在Resonor里，使用数字和符号就可以做出一首简单的纯音乐，适合想编曲但是又不想折腾专业软件的新手
基于网页（HTML / JavaScript）+ Capacitor 打包的安卓 App，使用 Android Studio 编译生成 APK。

## 环境要求

- Node.js（建议 18 以上）
- Android Studio（用于打开安卓工程、编译打包 APK）
- Android SDK（Android Studio 安装时一并配置）

## 快速开始

### 1. 安装依赖

```bash
npm install
```

### 2. 生成安卓工程（仅首次需要）

```bash
npx cap add android
```

### 3. 修改代码后，同步网页资源到安卓项目

每次改动 `www/` 目录下的内容后执行，把网页代码同步进安卓工程：

```bash
npx cap sync android
```

### 4. 用 Android Studio 打开安卓工程

```bash
npx cap open android
```

在弹出的 Android Studio 中等待 Gradle 同步完成，即可编译、打包 APK。

> 打包步骤：Android Studio → Build → Build Bundle(s) / APK(s) → Build APK(s)

## 音色库说明

`default.sf2` 是音乐合成所需的音色库文件，大小约 30MB，超出 GitHub 网页上传单文件 25MB 的限制，**不放在源码仓库里面**。

请到本仓库的 **Releases** 页面下载 `default.sf2`，下载完成后放到项目的 `www/` 文件夹内，与 `index.html` 同级，App 才能正常发声。

> 注意：音色库文件体积较大。如果代码中的读取路径为相对路径，请确保文件位置与代码引用一致，否则 App 内会加载不到音色。

## 项目结构

```
.
├── www/                     # 网页源码目录（Capacitor 的 webDir）
│   ├── index.html           # App 入口页面
│   ├── bundle.js            # 主要业务逻辑
│   ├── lame.min.js          # MP3 编码库
│   ├── spessasynth_core.js  # 合成器核心库
│   └── spessasynth_processor.min.js
├── assets/                  # App 图标、启动图
│   ├── logo.png
│   └── splash.png
├── capacitor.config.json    # Capacitor 配置（webDir 指向 www）
├── package.json
├── package-lock.json
└── .npmrc
```

## 常见问题

**1. 改了网页代码，App 里没变化？**

需要重新执行 `npx cap sync android`，再用 Android Studio 重新编译安装。

**2. App 打开后没有声音？**

检查 `www/default.sf2` 是否存在，以及 `index.html` 中的音色文件加载路径是否正确。

## 许可

本项目仅供学习与个人使用。
README.md 由 AI生成