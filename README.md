# QuickSnip AI Free 🆓

**100% Free AI-powered Direct vision API and instant answer detection**

Chrome extension using OpenRouter's free vision models for screen capture, text extraction, and answer generation. Zero API costs, community-powered AI with stealth UI.

> 💡 **Looking for faster respose and stability?** Check out [QuickSnip AI]([https://github.com/CheffCorleOne/QuickSnip-AI) with GPT-4 Vision

---

## ✨ Key Features

- **🆓 Completely Free**: Uses OpenRouter's free AI models - no costs ever
- **🔇 Stealth Mode**: Ultra-minimal UI with barely visible answer popup
- **🤖 Multi-Model Fallback**: Tries 6 different free models until one works
- **⚡ Fast Processing**: Direct vision API - no OCR preprocessing needed
- **⌨️ Hotkey Support**: `Ctrl+Shift+X` (Windows/Linux) or `Cmd+Shift+X` (Mac)
- **👻 Nearly Invisible**: Transparent selection, subtle answer display
- **🔄 Auto-Retry**: Switches models if one fails or is rate-limited

---

## 🤖 Free Models Used

The extension tries these models in order (can be changed thorugh hardcode):

1. **BERT Nebulon Alpha** (OpenRouter experimental)
2. **Google Gemini 2.0 Flash** (fastest)
3. **Google Gemini Flash 1.5 8B** (balanced)
4. **Qwen 2 VL 7B** (Chinese/English)
5. **Meta Llama 3.2 11B Vision** (multilingual)
6. **OpenAI GPT-4o Mini** (fallback)

All models are **100% free** on OpenRouter!

---

## 🛠️ Installation

### 1. Get OpenRouter API Key (Free!)

1. Visit [OpenRouter](https://openrouter.ai/)
2. Sign up with GitHub or Google
3. Go to [Keys](https://openrouter.ai/keys)
4. Click "Create Key" (no credit card required!)
5. Copy your API key (starts with `sk-or-v1-...`)

### 2. Configure Extension

Open `background.js` and find **line 162**:

```javascript
const apiKey = "sk-or-v1-YOUR_KEY_HERE";
```

Replace with your actual OpenRouter API key:

```javascript
const apiKey = "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";
```

### 3. Load Extension in Chrome

1. Open Chrome and go to `chrome://extensions/`
2. Enable **Developer mode** (top right toggle)
3. Click **Load unpacked**
4. Select the extension folder
5. Done! Extension icon appears in toolbar

---

## 📖 How to Use

### Activation

**Method 1**: Press `Ctrl+Shift+X` (or `Cmd+Shift+X` on Mac)  
**Method 2**: Click the extension icon

### Capture & Answer

1. **Select area**: Click and drag to select question area
2. **Wait 3-5 seconds**: Processing happens silently (model tries may take time)
3. **View answer**: Small gray text appears in bottom-right corner
4. **Close**: Click the answer popup or wait 4 seconds

### Finding the Answer

The answer appears as a **barely visible popup**:
- **Position**: Bottom-right corner
- **Style**: Light gray text (60% opacity)
- **Hover**: Becomes more visible on mouse hover
- **Auto-dismiss**: Removes after 4 seconds

---

## 🎨 Stealth Design

QuickSnip AI Free is designed to be **nearly undetectable**:

### Visual Stealth
- Selection overlay: `rgba(0, 0, 0, 0.001)` - invisible
- Selection border: `rgba(200, 200, 200, 0.15)` - ultra-subtle
- Answer popup: 60% opacity, light gray text
- No loading spinners or progress indicators
- Minimal corner popup, auto-dismisses

### Operational Stealth
- No browser notifications
- Silent model switching
- Instant cleanup after capture
- No visible error messages

---

## 🔧 Technical Details

### Architecture

**Single-Step Vision Analysis:**

Unlike the GPT-4 version, OpenRouter models can do both OCR and reasoning in one call:
- Receives screenshot image
- Extracts question text internally
- Identifies correct answer
- Returns minimal response

### Model Fallback System

```javascript
const modelsToTry = [
  "openrouter/bert-nebulon-alpha",           // Newest, experimental
  "google/gemini-2.0-flash-exp:free",        // Fast, reliable
  "google/gemini-flash-1.5-8b:free",         // Balanced
  "qwen/qwen-2-vl-7b-instruct:free",         // Multilingual
  "meta-llama/llama-3.2-11b-vision-instruct:free", // Strong reasoning
  "openai/gpt-4o-mini:free"                  // Fallback
];
```

If one model fails (rate limit, error), automatically tries the next.

### Files Structure

```
QuickSnip-AI-Free/
├── manifest.json       # Extension configuration
├── background.js       # Core logic: OpenRouter API, model fallback
├── snipper.js         # UI: selection overlay, capture, answer display
└── README.md          # This file
```

### API Configuration

Hardcoded in `background.js` line 162:

```javascript
const apiKey = "sk-or-v1-YOUR_KEY_HERE";  // ← EDIT THIS
```

---

## 🆚 Free vs OPEN-AI personal API versions Comparison

| Feature | Free (OpenRouter) | GPT-4 (OpenAI) |
|---------|-------------------|------------------|
| **Cost** | $0.00 forever | ~$0.0003/question |
| **API Key** | Free signup | Requires payment |
| **Accuracy** | 85-95% | 95-99% |
| **Speed** | 3-7 seconds | 2-4 seconds |
| **Models** | 6 free options | GPT-4 Vision |
| **Reliability** | Good (fallback) | Excellent |
| **Rate Limits** | Shared pool | Personal limits |

---

## 🔐 Privacy & Security

- **No data storage**: Nothing saved locally or remotely
- **Direct API calls**: Your data goes only to OpenRouter
- **No tracking**: Zero analytics or telemetry
- **Community models**: Some models are hosted by volunteers

⚠️ **Important**: 
- Keep your OpenRouter API key private
- OpenRouter tracks usage for free tier limits
- Some models may have community moderators

---

## 💰 Cost & Limits

### 100% Free Forever

OpenRouter provides free access through:
- **Community credits**: Shared pool replenished daily
- **Free tier models**: Permanently free models
- **Rate limits**: ~20-50 requests per day per model

### If Rate Limited

The extension automatically switches to another free model. You have **6 models** available, so even if one is rate-limited, others likely work.

### No Hidden Costs

- No credit card required
- No trial period
- No premium upsells
- Truly free forever

---

## 🚨 Limitations

- **Slower than GPT-4 version**: 3-7 seconds vs 2-4 seconds
- **Rate limits**: May hit limits during heavy use
- **Model availability**: Free models can be temporarily unavailable
- **Accuracy variation**: Different models have different strengths
- **Complex questions**: May struggle with advanced math/reasoning

---

## 🛡️ Troubleshooting

### "All models failed" error

**Causes:**
- All free models are rate-limited (rare)
- Network connectivity issues
- Invalid API key
