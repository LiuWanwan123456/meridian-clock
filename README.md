# 真太阳时 · 子午流注

中医传统时辰钟 · GPS真太阳时 · 安卓PWA应用

---

## 文件清单

```
index.html      主页面（所有功能）
manifest.json   PWA配置（图标、名称、颜色）
sw.js           Service Worker（离线缓存）
icon.svg        阴阳太极图标（浅棕色）
icon-192.png    应用图标192×192（需自行从SVG导出）
icon-512.png    应用图标512×512（需自行从SVG导出）
```

---

## 部署到 GitHub Pages（步骤）

1. 在 GitHub 新建仓库，例如 `solar-clock`
2. 把以上所有文件上传到仓库根目录
3. 进入 **Settings → Pages → Branch: main → /(root)** → Save
4. 等1~2分钟，访问：`https://你的用户名.github.io/solar-clock/`

---

## 打包成 APK（免费，无需Android Studio）

### 方法一：PWABuilder（推荐）

1. 打开 https://www.pwabuilder.com
2. 输入你的 GitHub Pages 网址
3. 点击 **Package for stores**
4. 选择 **Android** → 下载 APK
5. 安装到手机（需开启「允许安装未知来源」）

### 方法二：Bubblewrap（命令行，需Node.js）

```bash
npm install -g @bubblewrap/cli
bubblewrap init --manifest https://你的域名/manifest.json
bubblewrap build
```

---

## 功能说明

| 功能 | 说明 |
|------|------|
| 真太阳时 | GPS定位 + 经差修正 + 时差方程（EoT）|
| 系统时间 | 手机标准时区时间 |
| 切换 | 点击顶部按钮切换两种时间 |
| 指针表盘 | 圆形模拟时钟，内圈显示十二时辰 |
| 数字显示 | 大字数字时间 + 日期星期 |
| 子午流注 | 完整12时辰表，自动高亮当前时辰与经络 |
| 离线支持 | Service Worker缓存，无网络可用 |

---

## 真太阳时算法

```
真太阳时 = 标准时间 + 经差修正 + 时差方程(EoT)

经差修正 = (当地经度 - 时区中央经线) × 4分钟/度
时差方程 = 9.87×sin(2B) - 7.53×cos(B) - 1.5×sin(B)  [分钟]
B = 360/365 × (一年中第N天 - 81)  [度]
```

---

*天人合一 · 顺时养生*
