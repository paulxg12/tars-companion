# 3D Generation Prompts for AI Companion

Use these prompts with Google VEO, Runway, or any 3D model generator to create 3D assets for your EVE/TARS companion.

---

## Prompt 1: EVE-style Blue Oval Eyes (for 3D model)
```
Photorealistic 3D render of two large oval eyes from the robot EVE from WALL-E. 
Each eye is a smooth white hemisphere with a glowing blue-white oval display screen inside. 
The screen shows a red circular light in the center with realistic glass reflection. 
The eyes have a slight tilt inward (puppy-like curiosity). 
Soft studio lighting, 4K, highly detailed, Pixar quality, floating in black void.
```

---

## Prompt 2: EVE Head (full 3D model reference)
```
3D render of a sleek white robot head inspired by EVE from WALL-E. 
Smooth aerodynamic white shell, two large glowing blue oval eyes in the front, 
no mouth, no nose, minimal design. The eyes have inner red glowing cores. 
Clean futuristic aesthetic, studio lighting, Pixar style, 4K render.
```

---

## Prompt 3: TARS-style Laser Eyes
```
Photorealistic 3D render of two glowing red laser modules from the robot TARS 
from Interstellar. Each module is a square panel with a circular red glowing 
laser emitter in the center, surrounded by metallic black housing with green 
status LEDs. Sci-fi military robot aesthetic. Dramatic lighting, 4K.
```

---

## Prompt 4: TARS Body (3D reference)
```
3D render of a boxy military robot body inspired by TARS from Interstellar. 
Matte black and grey panels, hinged legs at bottom, red glowing laser eyes, 
green status lights, industrial sci-fi design. The robot stands in alert pose. 
Cinematic lighting, 4K render, highly detailed metal textures.
```

---

## For Google Antigravity / 3D Generation Tools:

### EVE Eyes 3D Asset Prompt:
```
Create a 3D model of EVE's eyes: two smooth white dome shapes with blue oval 
screens inside. Each screen has a glowing red center that can move/track. 
The eyes should look curious and alive. Pixar quality, UV mapped, PBR materials.
```

### Animation Loop Prompt:
```
Animate EVE's eyes following a cursor around the screen. The blue oval displays 
have inner red lights that move toward where you're looking. Blink occasionally. 
Smooth easing, 60fps, loopable.
```

### 3D Scene Prompt (for Three.js/WebGL):
```
Build a 3D scene of EVE's face floating in space. Two large white oval eyes 
with blue glowing displays. The red inner lights track the mouse cursor. 
The eyes occasionally blink and shift between curious and scanning states. 
Dark space background with subtle stars. WebGL ready, Three.js compatible.
```

---

## Three.js Ready Code Snippet (for the tracking):

```javascript
// If building in Three.js, use this for eye tracking:
const maxRotation = 0.5; // radians
const eyeLeft = leftEyeGroup;
const eyeRight = rightEyeGroup;

function onMouseMove(event) {
    const x = (event.clientX / window.innerWidth) * 2 - 1;
    const y = -(event.clientY / window.innerHeight) * 2 + 1;
    
    eyeLeft.rotation.y = x * maxRotation;
    eyeLeft.rotation.x = y * maxRotation;
    eyeRight.rotation.y = x * maxRotation;
    eyeRight.rotation.x = y * maxRotation;
}
```
