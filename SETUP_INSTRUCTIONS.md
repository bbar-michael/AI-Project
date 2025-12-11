# Quick Setup: How to Connect Your Teachable Machine Model

## 🚀 Two Easy Options

### **OPTION 1: Use a Hosted Model (Easiest!)**

If you already have a Teachable Machine model trained, just do this:

1. **Go to**: https://teachablemachine.withgoogle.com
2. **Open your project** (or create a new one)
3. **Click "Share"** button
4. **Copy the model URL** (looks like: `https://teachablemachine.withgoogle.com/models/MUKJ_LGTl/`)
5. **Open** `index.html` in a text editor
6. **Find this line** (around line 715):
   ```javascript
   const MODEL_URL = "./my_model/";
   ```
7. **Replace it with** (paste your URL):
   ```javascript
   const MODEL_URL = "https://teachablemachine.withgoogle.com/models/YOUR_MODEL_ID/";
   ```
8. **Save** and open in browser
9. **Click** "Check Posture" → "Start Camera"
10. ✅ Done!

---

### **OPTION 2: Use Local Model Files**

If you want to keep files locally (no internet needed after first load):

1. **Go to**: https://teachablemachine.withgoogle.com
2. **Open your project** and **Export**
3. **Select "TensorFlow.js"** → **Download**
4. **Extract the ZIP** file
5. **Create folder**: `my_model` in same folder as `index.html`
6. **Copy these files** into `my_model/`:
   - `model.json`
   - `metadata.json`
   - `weights.bin` (or `group1-shard1of1.bin`)

Your folder structure should look like:
```
AI-Project/
├── index.html
├── my_model/
│   ├── model.json
│   ├── metadata.json
│   └── weights.bin
└── (other files)
```

7. **In index.html**, keep this line (should already be set):
   ```javascript
   const MODEL_URL = "./my_model/";
   ```
8. **Save** and open in browser
9. **Click** "Check Posture" → "Start Camera"
10. ✅ Done!

---

## 🎯 Which Option Should I Choose?

| Option | Pros | Cons |
|--------|------|------|
| **Hosted (Option 1)** | No setup, works instantly, always latest model | Needs internet |
| **Local (Option 2)** | Works offline, faster after first load | Need to download files |

**I recommend**: Start with **Option 1** (hosted) because it's fastest!

---

## ✅ Test It

1. Open `index.html` in browser
2. You should see the home screen
3. Click "🎯 Check Posture"
4. Click "📷 Start Camera"
5. You should see:
   - Loading spinner
   - Your camera feed
   - Real-time predictions
   - A status indicator (Good/Warning/Poor)

---

## 🆘 If It's Not Working

### **"Error loading model" message?**

**If using Option 1 (Hosted):**
- ✅ Check URL is correct (copy-paste from Teachable Machine)
- ✅ Check URL ends with `/` (important!)
- ✅ Check internet connection

**If using Option 2 (Local):**
- ✅ Check `my_model/` folder exists
- ✅ Check all 3 files are there
- ✅ Check `index.html` is in same folder as `my_model/`
- ✅ Open with HTTP server (not `file://` protocol)
  ```bash
  python3 -m http.server 8000
  # Then visit: http://localhost:8000
  ```

### **Camera won't start?**
- Allow camera permission when browser asks
- Try a different browser
- Check camera isn't already in use

---

## 📝 Code Changed

Your app now has **improved error messages** that tell you:
- Which URL it's trying to load
- What went wrong
- How to fix it

The code automatically detects if you're using a hosted or local model and handles both!

---

## 🎉 You're All Set!

Once you add your model URL or files, your posture checker will work perfectly.

**Next**: Choose Option 1 or 2 above and follow the steps!
