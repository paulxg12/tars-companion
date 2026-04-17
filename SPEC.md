# EVA — Pocket AI Companion

## Concept & Vision

EVA is a web-based AI companion that lives on your screen — an expressive, emotive face made of two big binocular-like eyes inspired by WALL-E's EVA. She listens, responds, and reacts. Not a chatbot. A presence.

The soul of EVA is her eyes — big, round, reflective, alive. They blink, widen with surprise, soften when calm, dart around nervously, and follow you. She's warm, slightly cheeky, and genuinely helpful.

## Design Language

### Aesthetic Direction
Industrial-cute meets space probe. EVA's face is a minimalist oval with two massive circular eyes. Clean, soft, inviting. The rest of the body is abstract — just enough to give her weight.

### Color Palette
- **Background:** `#1a1a2e` (deep space navy)
- **EVA Face:** `#e8e8e8` (soft white/cream)
- **Eye Color:** `#f4a261` (warm amber/orange — like EVA from WALL-E)
- **Eye Highlight:** `#ffffff` (pure white reflection)
- **Eye Pupil:** `#2d2d2d` (near black)
- **Accent Glow:** `#f4a261` with blur (subtle ambient glow)
- **Text/UI:** `#e0e0e0` (soft white)
- **Listening Indicator:** `#e76f51` (coral red pulse)

### Typography
- **Font:** "Space Grotesk" (Google Fonts) — techy but friendly
- **Fallback:** system-ui, sans-serif

### Motion Philosophy
- Eyes are never static — constant subtle movement (breathing, micro-darts)
- Blink every 3-6 seconds randomly
- Emotional states: calm, excited, thinking, surprised, sleepy
- Smooth easing on all movements (ease-out, 200-400ms)

## Layout & Structure

```
┌─────────────────────────────────┐
│         [Status Text]           │
│                                 │
│       ┌─────┐  ┌─────┐         │
│       │  O  │  │  O  │  ← EVA  │
│       │     │  │     │    Eyes │
│       └─────┘  └─────┘         │
│                                 │
│     [ Tap to Talk indicator ]  │
│                                 │
│  ─────────────────────────────  │
│  [ Transcript / History ]       │
└─────────────────────────────────┘
```

- Full viewport, centered face
- Status text above (listening, thinking, speaking)
- Eyes dominate the screen
- Tap anywhere to activate
- Transcript below (optional, off by default)

## Features & Interactions

### Core Loop
1. User taps screen → EVA "wakes up" (eyes open wider)
2. Eyes glow to indicate listening
3. User speaks → audio captured
4. EVA "thinks" (eyes look up, slight wobble)
5. EVA responds (eyes look at you, mouth animation if any)
6. Audio plays back
7. Eyes settle back to calm state

### Eye States
| State | Behavior |
|-------|----------|
| **Idle** | Soft blink every 3-6s, gentle sway, eyes centered |
| **Listening** | Eyes widen slightly, amber glow pulses, pupils dilate |
| **Thinking** | Eyes look up-left, slight oscillation, occasional blink |
| **Speaking** | Eyes forward, slight bounce with speech rhythm |
| **Surprised** | Eyes go wide, pupils contract, blink pause |
| **Happy** | Eyes curve slightly (happy shape), warm glow |
| **Sleepy** | Eyes half-closed, slower movement |

### Voice Interaction
- Web Speech API (built into browser, no API key)
- Mic permission requested on first tap
- Visual feedback during recording (red ring pulse)
- Works with Groq AI or Gemini for brain

### AI Integration
- **Primary:** Groq (free tier) with Llama 3.3
- **Fallback:** Google Gemini (free tier)
- System prompt sets EVA's personality
- Conversation history maintained in session

### Personality
- Warm, helpful, slightly cheeky
- British-ish casual tone
- Calls you "mate" occasionally
- Admits when she doesn't know something
- Makes small observations about the world

## Component Inventory

### EVA Face
- Oval container with soft shadow
- Two circular eyes (CSS or SVG)
- Each eye has: outer ring, inner iris, pupil, highlight
- States: idle, listening, thinking, speaking, surprised, happy, sleepy

### Eye Component
- Outer circle: amber fill, subtle gradient
- Inner circle: darker amber
- Pupil: moves within iris (CSS transform)
- Highlight: fixed position, white circle
- Glow: box-shadow blur on active states

### Status Indicator
- Text above eyes
- Fades in/out on state change
- Subtle typewriter effect on response

### Mic Button
- Circular, appears on tap
- Pulses red while recording
- Disappears when done

### Transcript Panel
- Collapsible, bottom of screen
- Shows last few exchanges
- Semi-transparent background

## Technical Approach

### Frontend
- Single HTML file (portable)
- Vanilla JS (no framework needed)
- CSS animations for eyes
- Web Speech API for voice
- Web Audio API for recording

### Backend (or edge function)
- Groq API for LLM
- Or Gemini API
- Simple fetch calls from frontend

### API Design
```
POST /chat
Body: { "message": "text", "history": [...] }
Response: { "response": "text", "emotion": "happy" }
```

### Data Model
- Session memory (in-memory for MVP)
- History array: [{role, content}, ...]
- Max ~10 turns before summary/trim

## File Structure
```
/eva
  index.html    ← Everything in one file
  SPEC.md       ← This spec
```
