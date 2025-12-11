# Model Setup Guide - Getting Your Posture Model Ready

## Complete Step-by-Step Instructions

### Phase 1: Create Your Posture Model (15 minutes)

#### Step 1: Access Teachable Machine
1. Open [teachablemachine.withgoogle.com](https://teachablemachine.withgoogle.com) in your browser
2. Click **"Get Started"** button
3. Select **"Image Project"**
4. Choose **"Standard Image Model"**

#### Step 2: Create Posture Classes
You'll see a default "Class 1" - rename and create classes:

**Class 1: Good Posture**
- Keep shoulders back
- Straight spine
- Head level
- Chest forward

**Class 2: Bad Posture/Slouching**
- Rounded shoulders
- Curved spine
- Head forward
- Slouched position

**Class 3: Neutral/Fair Posture**
- In-between state
- Partial slouching
- Slight forward head

#### Step 3: Gather Training Data
For each class, you need 50-100+ images:

**Option A: Use Webcam (Recommended)**
1. Click **"Webcam"** for each class
2. Click **"Hold to Record"** (or take multiple snapshots)
3. Record 30 seconds of yourself in that posture
4. Move around slowly to capture different angles
5. Ensure good lighting
6. Get different distances from camera

**Option B: Upload Images**
1. Find your own posture images
2. Or use free images from:
   - [Unsplash](https://unsplash.com) (search "posture")
   - [Pexels](https://pexels.com) (search "sitting")
   - [Pixabay](https://pixabay.com)
3. Ensure variety (different people, angles, clothing, backgrounds)

**Example Data Collection**:
```
Good Posture (80 images)
├── 20 images: sitting at desk
├── 20 images: standing upright
├── 20 images: 45-degree angle
├── 20 images: different lighting
└── Include different body types, ages, clothing

Bad Posture (80 images)  
├── 20 images: slouching in chair
├── 20 images: forward head posture
├── 20 images: hunched shoulders
├── 20 images: extreme slouching
└── Include realistic "bad" positions

Neutral (60 images)
├── 15 images: partial slouching
├── 15 images: okay but not great
├── 15 images: medium slouch
└── 15 images: transitional positions
```

#### Step 4: Train Your Model
1. After uploading images, click **"Train Model"**
2. Wait for training to complete (usually 2-5 minutes)
3. Monitor accuracy in the right panel:
   - Green = Good (>85% accuracy)
   - Yellow = Okay (70-85%)
   - Red = Poor (<70%)

**If accuracy is poor**:
- Add more training images to weak classes
- Ensure good variety in your images
- Make sure images clearly show posture
- Remove blurry or poorly lit images
- Try again

#### Step 5: Test Your Model
1. Before exporting, test with webcam
2. Click **"File"** or **"Webcam"** to test
3. Try different poses to verify accuracy:
   - ✅ Good posture: Should predict "Good Posture" (>80%)
   - ✅ Slouching: Should predict "Bad Posture" (>80%)
   - ✅ In-between: Should predict "Neutral" (>70%)

**Troubleshooting**:
- If predictions are wrong, retrain with better images
- If accuracy < 70%, you need more/better training data
- Click the dataset tab and review images for quality

---

### Phase 2: Export Your Model (5 minutes)

#### Step 1: Prepare for Export
1. Ensure training is complete and accuracy is acceptable
2. Click **"Export Model"** button (top right)

#### Step 2: Choose Export Format
1. Select **"TensorFlow.js"** (should be default)
2. You'll see 3 options:
   - ☑️ **Uploaded Link** - Shows a direct link (good for testing)
   - ☑️ **Downloadable Link** - Creates a ZIP file (good for self-hosting)
3. Click **"Download my model"**

#### Step 3: Extract Files
1. Your download will be `converted_savedmodel.zip`
2. Extract the ZIP to your computer
3. Inside, you should see a folder with:
   ```
   model.json
   metadata.json
   group1-shard1of1.bin
   ```
   OR
   ```
   model.json
   metadata.json
   weights.bin
   ```

---

### Phase 3: Deploy Model to Project (5 minutes)

#### Step 1: Create Model Directory
```bash
# In your AI-Project folder, create:
mkdir my_model
```

#### Step 2: Copy Model Files
1. Copy the three files from your export:
   - `model.json`
   - `metadata.json`
   - `group1-shard1of1.bin` (or `weights.bin`)
2. Place them in your `my_model/` folder

Your project structure should look like:
```
AI-Project/
├── index.html
├── README.md
├── QUICKSTART.md
├── DESIGN_REFLECTION.md
└── my_model/
    ├── model.json
    ├── metadata.json
    └── group1-shard1of1.bin
```

#### Step 3: Test Locally
```bash
# Start a local server
python3 -m http.server 8000

# Visit: http://localhost:8000
# Click "Check Posture" → "Start Camera"
# You should see your model predictions!
```

---

## Verification Checklist

After setup, verify everything:

- [ ] `my_model/` folder exists in project root
- [ ] `model.json` is in `my_model/` folder
- [ ] `metadata.json` is in `my_model/` folder
- [ ] `group1-shard1of1.bin` OR `weights.bin` is in `my_model/`
- [ ] No errors when starting app locally
- [ ] Camera starts without errors
- [ ] Predictions appear in real-time
- [ ] Status indicator shows (Good/Warning/Poor)
- [ ] Stopping camera works properly

---

## Common Issues & Solutions

### ❌ "Error loading model"
**Cause**: Model files not found
**Solution**: 
```bash
# Verify files exist
ls my_model/
# Should show: model.json  metadata.json  group1-shard1of1.bin
```

### ❌ Camera won't start
**Cause**: Browser camera permission denied
**Solution**: 
- Click permission prompt and allow camera
- Or check browser camera settings
- Try a different browser (Chrome usually more reliable)

### ❌ Predictions always say "loading"
**Cause**: Model still loading or network issue
**Solution**:
- Wait longer (first load takes 10-20 seconds)
- Check browser console (F12) for errors
- Ensure model files are accessible
- Try refreshing page

### ❌ Model accuracy is poor
**Cause**: Insufficient or low-quality training data
**Solution**:
- Add more images (150+ per class minimum)
- Ensure good variety:
  - Different people
  - Different angles
  - Different lighting
  - Different distances
- Retrain the model
- Remove blurry/poor quality images

### ❌ Model file size too large
**Cause**: Normal - models are large files
**Solution**:
- This is expected (typically 5-50 MB)
- First load takes longer
- Subsequent loads are cached
- Consider web hosting vs local

---

## Best Practices for Better Posture Detection

### Training Data Quality
✅ **DO**:
- Use clear, well-lit images
- Include full upper body in frame
- Show multiple angles for each posture
- Include various body types
- Have clear differences between classes
- Use real people (not drawings)

❌ **DON'T**:
- Use blurry or dark images
- Have only head/shoulders in frame
- Mix postures (partially in each class)
- Use only one angle
- Use low-resolution images
- Forget about background variation

### Model Training
✅ **DO**:
- Aim for 100+ images per class
- Keep classes balanced (similar number per class)
- Test before deploying
- Retrain if accuracy < 75%
- Record training progress

❌ **DON'T**:
- Deploy untested models
- Use models with < 70% accuracy
- Have very imbalanced classes (200 vs 50 images)
- Expect perfect accuracy (80% is good)

### Real-World Usage
✅ **DO**:
- Test with various users
- Use good lighting
- Position 1-2 meters from camera
- Have full upper body visible
- Wear different clothing types
- Adjust camera height

❌ **DON'T**:
- Expect accuracy in poor lighting
- Stand too close or far away
- Hide upper body
- Use only on training people
- Assume it works in all conditions

---

## Example Training Sequence

### Day 1: Data Collection (30 minutes)
```
10:00 - Record Good Posture (100 clips)
10:10 - Record Bad Posture (100 clips)  
10:20 - Record Neutral Posture (80 clips)
10:30 - Gather external images (50 per class)
```

### Day 2: Model Training (20 minutes)
```
14:00 - Upload all images
14:05 - Train model
14:10 - Wait for completion
14:15 - Test model accuracy
14:20 - Download if >75% accuracy
```

### Day 3: Deployment (10 minutes)
```
16:00 - Extract model files
16:02 - Copy to my_model/ folder
16:05 - Test locally
16:08 - Deploy
16:10 - Verify on device
```

---

## Deployment Options After Model is Ready

### Option 1: GitHub Pages (Recommended)
```bash
git add .
git commit -m "Add PostureFlow app with trained model"
git push
# Enable Pages in Settings → Pages → main branch
```
**Pros**: Free, automatic deployment, good for sharing
**Cons**: Public repository

### Option 2: Netlify
```bash
npm install -g netlify-cli
netlify deploy --prod
```
**Pros**: Simple, free tier available
**Cons**: Need Node.js

### Option 3: Vercel  
```bash
npm install -g vercel
vercel
```
**Pros**: Optimized for web apps, very fast
**Cons**: Need Node.js

### Option 4: Self-Hosted
- Upload to your own web server
- Works with any hosting provider
- Just ensure `my_model/` files are accessible

---

## Support Resources

**Teachable Machine**:
- [Official Docs](https://teachablemachine.withgoogle.com/faq)
- [Google Colab Tutorials](https://colab.research.google.com)
- [Community Forum](https://groups.google.com/forum/#!forum/teachable-machine)

**TensorFlow.js**:
- [Documentation](https://js.tensorflow.org)
- [Examples](https://github.com/tensorflow/tfjs-examples)
- [Model Format](https://www.tensorflow.org/js/guide/conversion/import_savedmodel)

---

## Final Verification

Before sharing your app:

1. ✅ Model trained with >200 images per class
2. ✅ Accuracy >75% across all classes
3. ✅ Model files in `my_model/` folder
4. ✅ App works locally without errors
5. ✅ Camera starts and makes predictions
6. ✅ All 4 screens functional
7. ✅ Navigation buttons work
8. ✅ Responsive on mobile
9. ✅ Ready to deploy

**Your app is now ready to help people improve their posture! 💪**

---

**Last Updated**: December 2025  
**Version**: 1.0
