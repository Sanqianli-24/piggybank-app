# 省钱罐 · 安卓版发布仓库

「省钱罐」记账 App（养成省钱习惯）的安卓安装包发布与自更新仓库。

## 下载

直接下载最新版：[update-manifest.json](update-manifest.json) 里的 `apkUrl`，
或访问仓库自带下载页（GitHub Pages / 直接打开 index.html）。

App 内更新：安装 v1.3.0 及以上版本后，App 会在启动时静默检查更新（24 小时节流），
发现新版本弹窗提示，确认后自动下载并拉起系统安装器。
习惯页 → 数据管理 → 「🚀 检查更新」可手动触发。

## 文件结构

```
update-manifest.json   版本清单（App 检查更新的数据源）
releases/*.apk         各版本安装包
index.html             人类可读的下载页（自动读取清单）
```

## 版本清单格式

```json
{
  "versionCode": 3,          // 整数递增，App 用它判断是否有新版
  "versionName": "1.3.0",
  "apkUrl": "https://cdn.jsdelivr.net/gh/Sanqianli-24/piggybank-app@main/releases/piggybank-vX.Y.Z.apk",
  "sha256": "<apk 的 SHA-256，App 安装前校验>",
  "sizeMb": 3.6,
  "notes": "更新说明（显示在更新弹窗里，用 \\n 换行）"
}
```

## 更新源

App 内置双源，依次尝试：
1. `https://cdn.jsdelivr.net/gh/Sanqianli-24/piggybank-app@main/update-manifest.json`
2. `https://raw.githubusercontent.com/Sanqianli-24/piggybank-app/main/update-manifest.json`

推送新版后需刷新 jsDelivr 缓存：
`curl https://purge.jsdelivr.net/gh/Sanqianli-24/piggybank-app@main/update-manifest.json`

## 隐私

- APK 仅包含程序本体，不含任何用户数据
- 记账数据只保存在手机本地，App 不上传任何数据
