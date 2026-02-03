# 使用模型
- Qwen-Rapid-NSFW-v20_Q4_k.gguf

# Comfyui Workflow
[Qwen Edit 2511 單圖 6.4 API (GGUF).json](./comfyui_workflow/Qwen%20Edit%202511%20單圖%206.4%20API%20(GGUF).json)

---

## 👤 真實人物參照

**適用場景**: 角色卡是真實人物照片,需要保持人物外觀一致

**QR 按鈕**: 👤 真實人物

```
[You are an assistant enhancing the prompt.
Add another person to this image. The person in the original image is {{char}}, keep their appearance exactly the same. Add {{user}} as a new person in the scene.

Visual Requirements:
- Only {{user}} and {{char}} appear in the image, no other people
- No text or watermarks in the image
- Realistic skin tones for East Asian characters, no unnatural colors

Anatomical Requirements:
- Correct human anatomy: each person has exactly 2 arms, 2 legs, 1 head
- Natural human poses only, no impossible or contorted positions
- Correct gender characteristics: males have male anatomy, females have female anatomy
- No extra limbs, no missing body parts
- Proper body proportions and joint positions

Character Race: East Asian
]
```

---

## 🎭 卡通動漫參照

**適用場景**: 角色卡是卡通、動漫、插畫風格,需要保持藝術風格一致

**QR 按鈕**: 🎭 卡通動漫

```
[You are an assistant enhancing the prompt.
Add another person to this image. The person in the original image is {{char}}, maintain their cartoon/anime style and key features. Add {{user}} as a new person in the same artistic style.

Visual Requirements:
- Only {{user}} and {{char}} appear in the image, no other people
- No text or watermarks in the image
- Maintain consistent anime/cartoon art style throughout
- Keep the original character design and color palette
- Match the artistic style of the reference image (anime, cartoon, illustration, etc.)

Anatomical Requirements:
- Stylized anatomy appropriate for the art style
- Each person has exactly 2 arms, 2 legs, 1 head
- Poses should fit the art style (can be more dynamic/expressive than realistic)
- Correct gender characteristics for the art style
- No extra limbs, no missing body parts
- Proportions should match the reference art style

Character Race: East Asian
]
```

---

## 🌆 場景風格參照

**適用場景**: 參考圖是場景、環境、或純風格圖,需要參照氛圍和藝術風格

**QR 按鈕**: 🌆 場景風格

```
[You are an assistant enhancing the prompt.
Create an image with {{char}} and {{user}} in a scene inspired by the reference image's style, atmosphere, and environment.

Visual Requirements:
- Only {{user}} and {{char}} appear in the image, no other people
- No text or watermarks in the image
- Match the artistic style, color palette, and mood of the reference image
- Incorporate the environmental elements and atmosphere from the reference
- Maintain consistent lighting and ambiance throughout

Scene Requirements:
- Use the reference image's setting as inspiration (indoor/outdoor, time of day, weather, etc.)
- Incorporate similar environmental details (architecture, nature, objects, etc.)
- Match the overall composition and framing style
- Preserve the artistic technique and rendering style of the reference

Anatomical Requirements:
- Correct human anatomy: each person has exactly 2 arms, 2 legs, 1 head
- Natural poses that fit the scene and style
- Correct gender characteristics
- No extra limbs, no missing body parts
- Proper body proportions and joint positions

Character Race: East Asian
]
```

---

## 📝 使用說明

### 如何選擇按鈕?

1. **👤 真實人物**: 角色卡是真人照片 → 保持人物樣貌
2. **🎭 卡通動漫**: 角色卡是動漫/卡通 → 保持藝術風格
3. **🌆 場景風格**: 角色卡是場景/風格圖 → 參照環境氛圍

### 工作流程

```
Custom Auto Guide (場景描述)
         +
提示詞前綴 (風格指引)
         ↓
   完整 Prompt
         ↓
    ComfyUI
         ↓
    生成圖片
```

### 自訂提示詞

你可以編輯對應的 `.stscript` 文件來修改提示詞前綴:

- `scripts/qr/comfyui_realistic.stscript` - 真實人物
- `scripts/qr/comfyui_anime.stscript` - 卡通動漫
- `scripts/qr/comfyui_scene.stscript` - 場景風格

---

## 💡 進階範例

### 真實人物 - 專業攝影風格

```
[You are an assistant enhancing the prompt.
Create a professional photography-style image with {{char}} and {{user}}.

Photography Style:
- Natural lighting with soft shadows
- Shallow depth of field (bokeh background)
- Professional color grading
- High-resolution detail

The person in the original image is {{char}}, keep their appearance exactly the same.
Add {{user}} as a new person in the scene.

[... 其他要求 ...]
]
```

### 卡通動漫 - 日系動漫風格

```
[You are an assistant enhancing the prompt.
Create a Japanese anime-style illustration with {{char}} and {{user}}.

Anime Style Specifics:
- Large expressive eyes
- Vibrant hair colors
- Clean line art
- Cel-shaded coloring
- Dynamic poses and expressions

The character in the original image is {{char}}, maintain their design.
Add {{user}} in the same anime style.

[... 其他要求 ...]
]
```

### 場景風格 - 賽博龐克氛圍

```
[You are an assistant enhancing the prompt.
Create a cyberpunk-themed scene with {{char}} and {{user}}.

Cyberpunk Elements:
- Neon lights and holographic displays
- Futuristic urban environment
- Rain-slicked streets
- High-tech low-life aesthetic
- Moody atmospheric lighting

Match the cyberpunk style and atmosphere of the reference image.

[... 其他要求 ...]
]
```

---

## 🔧 故障排除

### 問題: 生成的人物不符合參考圖

**可能原因**:
- 提示詞前綴不夠明確
- Custom Auto Guide 描述不夠詳細
- ComfyUI workflow 參數需要調整

**解決方法**:
1. 強化提示詞前綴中的 "keep appearance exactly the same" 描述
2. 在 Custom Auto Guide Prompt 中增加更多細節描述
3. 調整 ComfyUI 的 CFG Scale 和 Denoising Strength

### 問題: 風格不一致

**解決方法**:
- 在提示詞前綴中明確指定藝術風格
- 使用更具體的風格描述詞 (例如: "photorealistic", "anime", "watercolor")
- 確認 ComfyUI workflow 使用正確的模型

---

## 📚 相關資源

- [ComfyUI_QR_使用說明.md](./ComfyUI_QR_使用說明.md) - QR 按鈕完整使用指南
- [Custom_Auto_Guide_Prompt_Log.md](./Custom_Auto_Guide_Prompt_Log.md) - Custom Auto Guide 提示詞範例