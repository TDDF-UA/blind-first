# Blind-First Teachable Machine Prototype

## Purpose

This prototype replaces the original interaction model in `test-delete-me` with a blind-first user experience.

The model remains unchanged. Any Teachable Machine image classifier can be swapped in, provided it exports:

- model.json
- metadata.json
- weights.bin

The interface is model-agnostic and works with 4 classes or 100+ classes.

---

## Files

### index.html

Main application page.

Responsibilities:

- Loads CSS and JavaScript
- Loads TensorFlow.js and Teachable Machine libraries
- Provides ARIA live region support
- Defines the blind-first interface layout

### style.css

Visual styling.

Design goals:

- High contrast
- Minimal screen clutter
- Large typography
- Developer-visible status information

### script.js

Application logic.

Responsibilities:

- Welcome message
- Camera permission flow
- Teachable Machine model loading
- Webcam initialization
- Prediction loop
- Speech synthesis
- State management

---

## Expected Folder Structure

```text
project/
├── index.html
├── style.css
├── script.js
└── model/
    ├── model.json
    ├── metadata.json
    └── weights.bin
```

---

## User Flow

```text
Page Loads
    ↓
Welcome Message
    ↓
User Activates Page
    ↓
Camera Permission
    ↓
Camera Connected
    ↓
Scanning
    ↓
Object Detected
    ↓
Result Spoken
```

---

## Naught Class Handling

The model contains a trained class called:

```text
Naught
```

This class is treated as background.

The user never hears:

```text
Naught
```

Instead:

| Model State | User Feedback |
|------------|---------------|
| Naught | Silence |
| Object Appears | Object detected. Hold steady. |
| High Confidence | Object announced |
| Object Removed | Object moved out of view. |

---

## Swapping Models

The UX does not depend on specific class names.

Examples:

- Cup / Bottle / Light
- Bakery Products
- Industrial Gears
- Archaeological Artifacts
- Laboratory Equipment

Only the exported Teachable Machine model changes.

---

## Testing

1. Open the site.
2. Activate the page.
3. Grant camera permissions.
4. Present a trained object.
5. Wait for stable classification.
6. Listen to spoken feedback.

---

## Future Improvements

- Haptic feedback
- Sound cues instead of speech for state changes
- Configurable confidence thresholds
- Screen-reader specific onboarding
- Multi-language support
