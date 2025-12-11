# PostureFlow - AI Posture Checker App

A beautiful, accessible multi-screen web application that helps users maintain good posture using real-time AI-powered camera feedback via Teachable Machine.

## Features

### 🏠 Home Screen
- Clean landing page with app introduction
- Clear value proposition: "Better Posture, Better Health"
- Two prominent call-to-action buttons (Learn Tips & Check Posture)
- Responsive design optimized for mobile and desktop

### 📚 Learn Screen
- 5 evidence-based posture tips with helpful icons
- Visual hierarchy with color-coded sections
- "Wall Test" quick reference guide
- Helpful info boxes with rounded corners and clear typography
- Scroll support for all content

### 🎯 Tools Screen (Posture Checker)
- Real-time camera integration with Teachable Machine model
- Live posture detection and confidence scoring
- Visual feedback with:
  - Prediction cards with class labels and percentages
  - Animated progress bars showing confidence levels
  - Status indicators (Good/Warning/Poor) with emoji
- Error handling for model loading issues
- Camera lifecycle management (start/stop)

### ℹ️ Credits Screen
- Technology stack credits
- Health information sources
- Support resources and hotline information
- Proper citations for all external resources

### 🧭 Navigation
- Footer navigation bar with 4 buttons (Home, Learn, Check, Info)
- Active state indicators (color highlighting)
- Smooth screen transitions with fade-in animations
- Persistent navigation across all screens

## Design Highlights

### Color Palette
- **Primary**: Indigo (#6366f1) - Modern, professional, accessible
- **Success**: Green (#10b981) - Positive feedback
- **Warning**: Amber (#f59e0b) - Cautionary feedback
- **Danger**: Red (#ef4444) - Critical feedback
- **Neutral**: Gray scale for text and backgrounds

### Accessibility Features
- **High Contrast**: WCAG AA compliant text-to-background ratios
- **Touch-Friendly**: All buttons ≥ 44px minimum height
- **ARIA Labels**: Semantic HTML with role attributes
- **Focus States**: Clear 2px outline for keyboard navigation
- **Responsive**: Mobile-first design that scales to all devices
- **Alt Text**: Image alternatives for screen readers
- **Clear Typography**: System fonts with strong hierarchy

### UI/UX Principles Applied
1. **Visual Hierarchy**: Large headings, scannable content, prominent CTAs
2. **Consistency**: Unified button styles, spacing, and color usage
3. **Feedback**: Real-time model predictions, loading states, status messages
4. **Simplicity**: Minimal design, focused on core functionality
5. **Affordance**: Interactive elements clearly indicate their purpose

## Setup Instructions

### 1. Create Your Posture Model
1. Visit [Teachable Machine](https://teachablemachine.withgoogle.com/)
2. Click "Get Started" → "Image Project"
3. Create classes for different posture states:
   - Good Posture
   - Bad Posture/Slouching
   - Neutral/Fair Posture
4. Upload training images or use webcam to capture examples
5. Train your model
6. Export as "Teachable Machine" format (TensorFlow.js)

### 2. Set Up Model Files
```bash
# In your project root, create the model directory
mkdir my_model

# Download your model from Teachable Machine export
# Extract the contents to my_model/
# You should have:
# - model.json
# - metadata.json
# - weights.bin (or similar)
```

### 3. Deploy or Run Locally
**Option A: Local Development (with CORS considerations)**
```bash
# Install a simple HTTP server
npm install -g http-server

# Run from project directory
http-server

# Visit http://localhost:8080
```

**Option B: GitHub Pages**
1. Push this repository to GitHub
2. Enable GitHub Pages in Settings
3. Deploy from the `main` branch

**Option C: Deploy to Web Host**
- Upload `index.html` and `my_model/` folder to your web hosting
- Ensure `my_model/` files are in the same directory as `index.html`

## File Structure
```
AI-Project/
├── index.html          # Complete single-file application
├── my_model/           # Your Teachable Machine model
│   ├── model.json
│   ├── metadata.json
│   └── weights.bin (or similar)
└── README.md           # This file
```

## Testing Checklist

- [ ] **Navigation**: All buttons switch screens correctly
- [ ] **Home Screen**: Logo, title, and buttons display properly
- [ ] **Learn Screen**: All 5 tips visible and readable
- [ ] **Credits Screen**: All sources properly cited
- [ ] **Posture Checker**: Camera starts/stops correctly
- [ ] **Model Loading**: Proper error message if model missing
- [ ] **Predictions**: Real-time feedback displays accurately
- [ ] **Mobile**: Responsive layout on small screens
- [ ] **Accessibility**: Keyboard navigation works, focus visible
- [ ] **Colors**: Sufficient contrast on all text

## Browser Compatibility
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers (iOS Safari, Chrome Mobile)

## Troubleshooting

### "Error loading model" message
**Solution**: Ensure your `my_model/` folder contains `model.json` and `metadata.json` files from Teachable Machine export.

### Camera won't start
**Solution**: 
- Check browser permissions for camera access
- Try a different browser
- Ensure HTTPS if not on localhost

### Model predictions inaccurate
**Solution**: 
- Retrain your model with more diverse training images
- Ensure good lighting and camera angle
- Include multiple posture variations per class

### Webcam canvas not displaying
**Solution**:
- Clear browser cache (Ctrl+Shift+Del)
- Check if webcam is already in use by another app
- Try a different browser

## Design Reflection

### Audience
PostureFlow is designed for students, office workers, and anyone concerned with maintaining healthy posture throughout their day—people aged 13-65 who use computers or spend extended time sitting.

### How It Helps
The app addresses the widespread problem of poor posture by:
- Providing **awareness** through real-time AI feedback
- Offering **education** via evidence-based tips
- Enabling **accountability** with visual posture status indicators
- Supporting **wellness** with accessible health resources

### Design Pride Point
**Smooth Multi-Screen Navigation with Footer Tabs**: The persistent footer navigation bar allows instant access to all features without the back-button pattern. The smooth fade-in transitions (0.3s) and active state highlighting create a professional, app-like experience that keeps users engaged and prevents screen switching friction.

### Accessibility Choice
**Touch-Friendly Targets (44px minimum)**: All interactive elements—buttons, nav buttons, and form controls—meet or exceed the 44px minimum touch target size recommended by accessibility standards. This ensures ease of use for users of all abilities and device types, particularly important for this health-focused app.

## Requirements Compliance

✅ **Theme**: Health & Wellness (posture improvement)
✅ **Screens**: 4 screens (Home, Learn, Tools, Credits)
✅ **Navigation**: Footer tabs with event-driven switching
✅ **Design Quality**: Modern UI with consistent colors, typography, spacing
✅ **Accessibility**: High contrast, alt text, 44px+ targets, ARIA labels
✅ **Content**: Accurate health info with proper citations
✅ **Interactive Tool**: Real-time posture detection with visual feedback
✅ **Resources**: Support hotline and healthcare provider recommendations

## Future Enhancements
- [ ] Historical posture tracking with charts
- [ ] Daily posture reminders/notifications
- [ ] Export posture reports
- [ ] Personalized exercise recommendations
- [ ] Dark mode support
- [ ] Multi-language support
- [ ] Integration with health apps

## License
Educational use - Open source

## Support
For issues or improvements, please ensure your Teachable Machine model is properly exported and placed in the `my_model/` directory.

---

**Version 1.0** | December 2025
