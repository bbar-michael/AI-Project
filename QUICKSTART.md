# Quick Start Guide - PostureFlow

## 5-Minute Setup

### Step 1: Export Your Model from Teachable Machine
1. Go to [teachablemachine.withgoogle.com](https://teachablemachine.withgoogle.com)
2. Create an Image Project with posture classes
3. Train and export as **TensorFlow.js**
4. Download the ZIP file

### Step 2: Add Model to Project
```bash
# Create model directory
mkdir my_model

# Extract downloaded files into my_model/
# Your folder should contain:
# ✓ model.json
# ✓ metadata.json  
# ✓ weights.bin (or group1-shard*)
```

### Step 3: Run Locally
```bash
# Option A: Using Python (built-in on most systems)
python3 -m http.server 8000

# Option B: Using Node.js
npx http-server

# Then visit: http://localhost:8000
```

### Step 4: Test All Features
- ✅ Click "Learn Tips" - view 5 posture tips
- ✅ Click "Check Posture" - start camera
- ✅ Click "Credits & Resources" - view citations
- ✅ Use footer tabs to navigate between screens

## Key Features to Test

### Home Screen
- Logo (💪) and app title visible
- Clear tagline and purpose statement
- Three working buttons

### Learn Screen  
- 5 tips with icons and descriptions
- "Wall Test" info section
- Smooth scrolling
- Back button works

### Posture Checker
- "Start Camera" button triggers model loading
- Camera feed appears (requires webcam)
- Real-time predictions with confidence %
- Status indicator shows feedback (Good/Warning/Poor)
- "Stop" button properly stops camera

### Credits Screen
- Technology stack listed
- Health sources cited
- Support resources visible

### Navigation
- Footer buttons always visible
- Active button highlights in purple
- Smooth transitions between screens
- Camera auto-stops when leaving Check screen

## Deployment Options

### GitHub Pages (Recommended for Sharing)
```bash
git init
git add .
git commit -m "Initial PostureFlow app"
git remote add origin https://github.com/YOUR_USERNAME/posture-app
git push -u origin main
```
Then enable Pages in repository settings.

### Netlify (Quick Deploy)
```bash
npm install -g netlify-cli
netlify deploy
```

### Vercel
```bash
npm install -g vercel
vercel
```

## Troubleshooting Quick Fixes

| Issue | Solution |
|-------|----------|
| "Error loading model" | Check `my_model/model.json` exists |
| Camera won't start | Allow camera permission in browser |
| Predictions not showing | Train more images in Teachable Machine |
| Layout looks wrong | Clear browser cache (Ctrl+Shift+Del) |
| Can't deploy | Make sure `my_model/` folder is committed |

## File Checklist

Before going live, verify:
- [ ] `index.html` - complete application file
- [ ] `my_model/model.json` - your trained model
- [ ] `my_model/metadata.json` - model metadata
- [ ] `my_model/weights.bin` - model weights (or group1-shard* files)
- [ ] `README.md` - documentation

## Design Features Implemented

✨ **Professional Look**
- Modern gradient background
- Consistent indigo color scheme
- Rounded corners and shadows
- Smooth animations (300ms transitions)

📱 **Mobile Responsive**
- Adapts to any screen size
- Touch-friendly buttons (44px minimum)
- Readable text on small screens
- Horizontal scrolling not needed

♿ **Accessible**
- High contrast text (WCAG AA)
- Keyboard navigation support
- Focus indicators on all buttons
- ARIA labels for screen readers

⚡ **Fast & Efficient**
- Single HTML file (no build needed)
- No external CSS frameworks
- TensorFlow.js loaded from CDN
- Works offline after initial load

## Next Steps

1. **Customize**: Edit colors, text, and icons in the HTML
2. **Brand**: Add your logo/organization name
3. **Improve Model**: Train with more posture variations
4. **Share**: Deploy and share your app link
5. **Gather Feedback**: Monitor user experience

## Support Resources

- **Teachable Machine Help**: [help.teachablemachine.withgoogle.com](https://help.teachablemachine.withgoogle.com)
- **TensorFlow.js Docs**: [js.tensorflow.org](https://js.tensorflow.org)
- **Web Accessibility**: [WCAG 2.1 Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)

---

**You're all set! Start improving posture 💪**
