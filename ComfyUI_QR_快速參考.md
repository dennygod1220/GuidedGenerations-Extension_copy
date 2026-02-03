# ComfyUI QR 按鈕快速參考

## 🎯 三個按鈕一覽

| 按鈕 | 適用場景 | 功能重點 |
|------|---------|---------|
| 👤 **真實人物** | 真人照片角色卡 | 保持人物外觀一致 |
| 🎭 **卡通動漫** | 動漫/卡通角色卡 | 保持藝術風格一致 |
| 🌆 **場景風格** | 場景/風格參考圖 | 參照環境氛圍 |

## 📋 快速使用

### 1. 導入 QR
```
/qr-import file=scripts/extensions/third-party/GuidedGenerations-Extension_copy/qr/comfyui_image_gen.json
```

### 2. 確認設定
- ✅ Enable writing Custom Auto Guide to ST variable
- ✅ 變數名稱: `custom_auto_guide`
- ✅ 設定 Custom Auto Guide Prompt

### 3. 開始使用
- 對話中需要生圖 → 點擊對應風格按鈕
- 系統自動檢查變數 → 如果為空則自動生成
- 組合提示詞前綴 + Custom Auto Guide → 呼叫 ComfyUI

## 🔧 自訂提示詞位置

| 風格 | 文件路徑 |
|------|---------|
| 真實人物 | `scripts/qr/comfyui_realistic.stscript` |
| 卡通動漫 | `scripts/qr/comfyui_anime.stscript` |
| 場景風格 | `scripts/qr/comfyui_scene.stscript` |

編輯 `/let prefix [你的提示詞] |` 這一行即可

## 🐛 常見問題

| 問題 | 解決方法 |
|------|---------|
| 按鈕沒反應 | 檢查文件路徑和擴展名稱 |
| 無法生成 Guide | 檢查 LLM 連接和設定 |
| ComfyUI 沒生圖 | 確認 `/sd` 命令可用 |
| 變數內容過時 | `/setvar key=custom_auto_guide \|` 清空 |

## 💡 進階技巧

### 強制重新生成變數
```
/run-persistent-guide customAuto | /delay 1000
```

### 查看當前變數內容
```
/getvar key=custom_auto_guide
```

### 手動設定變數
```
/setvar key=custom_auto_guide 你的自訂內容 |
```

## 📁 文件結構

```
GuidedGenerations-Extension_copy/
├── qr/
│   └── comfyui_image_gen.json          # QR 配置
├── scripts/qr/
│   ├── comfyui_realistic.stscript      # 真實人物腳本
│   ├── comfyui_anime.stscript          # 卡通動漫腳本
│   └── comfyui_scene.stscript          # 場景風格腳本
├── ComfyUI_QR_使用說明.md               # 完整使用說明
├── 搭配的Image Prompt.md                # 提示詞範例
└── ComfyUI_QR_快速參考.md               # 本文件
```

## 🎨 提示詞結構

```
[提示詞前綴]
    ↓
定義風格、要求、限制
    ↓
[Custom Auto Guide]
    ↓
場景、服裝、姿勢描述
    ↓
[完整 Prompt]
    ↓
ComfyUI 生成
```

## 📚 相關文件

- [ComfyUI_QR_使用說明.md](./ComfyUI_QR_使用說明.md) - 詳細使用指南
- [搭配的Image Prompt.md](./搭配的Image%20Prompt.md) - 提示詞範例
- [Custom_Auto_Guide_Prompt_Log.md](./Custom_Auto_Guide_Prompt_Log.md) - Custom Auto Guide 模板
