# House Motion Design Web App (Planning Doc)

This repository now contains the implementation plan for a web app where you can:

- Load a 3D model of your house (from Blender, exported as `.glb`)
- Click or tap parts of the model
- Show related media (photos, short videos, text overlays)
- Run an automated camera/interaction sequence
- Record a 15-second screen/video output

## Recommended Stack

- **Frontend**: Next.js + React
- **3D Rendering**: React Three Fiber (`@react-three/fiber`) + Drei (`@react-three/drei`)
- **Animation/Sequence**: GSAP timeline or Theatre.js (camera moves + UI transitions)
- **Asset storage**: Cloudinary, Supabase Storage, or S3-compatible bucket
- **Video recording/export**:
  - MVP: browser recording via `MediaRecorder` (records canvas + overlays)
  - Higher quality: server-side render pipeline (Remotion / FFmpeg)

## Core User Flow

1. Upload/prepare house model (`house.glb`)
2. Define interactive hotspots on model elements (e.g., roof, door, pool)
3. Attach content per hotspot:
   - up to one 15-second video
   - photos
   - text/captions
4. Play scripted walkthrough (camera path + automatic hotspot activations)
5. Export/share final 15-second output

## Blender -> Web Pipeline

1. In Blender, clean hierarchy and names (e.g., `Roof_Main`, `Kitchen_Window_01`)
2. Export as **glTF Binary (`.glb`)**
3. Keep textures optimized (WebP/JPEG where possible)
4. In web app, map mesh names to hotspot metadata

## Data Model (MVP)

- **Project**
  - id
  - title
  - modelUrl
- **Hotspot**
  - id
  - projectId
  - meshName
  - position
  - media[]
- **MediaItem**
  - id
  - type (`image` | `video` | `text`)
  - url/content
  - duration

## Milestone Plan

### Milestone 1 (MVP)
- Load one `.glb`
- Clickable hotspots on named meshes
- Side panel/carousel showing photos/video/text
- Basic camera transitions
- 15-second recording with `MediaRecorder`

### Milestone 2
- Timeline editor for scripted sequence
- Better transitions and overlays
- Preset animation templates
- Cloud persistence

### Milestone 3
- Branded export styles
- Multi-project dashboard
- Collaboration/share links

## What to Provide Next

To start building fast, share:

1. Your `.blend` or exported `.glb`
2. A list of clickable zones (mesh names or screenshot markup)
3. Media assets:
   - 1x video (15s)
   - photos
   - text snippets
4. Preferred visual style (minimal, luxury real-estate, cinematic, etc.)
5. Target platform (desktop-only or desktop+mobile)

## Build Strategy With Codex

Best method:

1. We define the exact MVP in writing (done in this file)
2. We scaffold the app structure
3. We integrate your `.glb`
4. We wire interactions + media
5. We add recording/export
6. We iterate polish

If you want, next step is: **I scaffold the Next.js + React Three Fiber starter and add a sample hotspot workflow.**
