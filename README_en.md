# TVC Director

[中文版](README.md)

From product brief to cinematic TVC keyframes — your AI advertising creative director.

A skill that turns your AI agent into a **TVC Advertising Creative Director**, handling the complete creative pipeline for television commercials and brand advertising: from a product brief to production-ready single-frame storyboard image prompts and video prompts.

## How It Works

The workflow mirrors real TVC advertising production stages:

```
"Make a 30-second TVC for an outdoor camera"
        ↓
  Phase 1: Creative Brief        ← Client Brief
  Phase 2: Creative Proposal     ← Creative Director Pitch
  Phase 3: Look Development      ← Art Style Lock
  Phase 4: Pre-production        ← Casting & Wardrobe + Product Photography + Location Scouting
  Phase 5: Storyboard & Shoot    ← Storyboard + On-set Shooting
  Phase 6: Review & Iteration    ← Director's Review + Revisions
  Phase 7: Delivery              ← Final Delivery
        ↓
  Copy-paste-ready single-frame storyboard image prompts,
  video prompts & creative docs
```

## Key Features

- **Mirrors real TVC production** — Casting & wardrobe, product photography, location scouting, storyboarding, shooting — each stage has a corresponding AI prompt deliverable
- **End-to-end creative pipeline** — From a one-line brief to deliverable storyboard prompts and video scripts, fully AI-driven
- **8 TVC narrative models** — Problem-solution, cinematic product breakdown, brand world crosscut, and more
- **Cinematic visual system** — 5 art style presets (A-E), 12 scene types, per-second camera choreography
- **Product + brand world dual narrative** — Not just product close-ups, but crosscut storytelling in real-world scenes
- **Copy-paste ready** — Output prompts work directly in Nano Banana Pro / Seedance with no rework needed

## Demo

### Car TVC — Cinematic Product Breakdown

https://github.com/user-attachments/assets/541055ed-d716-4087-86e2-a27d375282ed

### Perfume TVC — Brand World Crosscut

https://github.com/user-attachments/assets/df2d51af-acc2-4f34-a228-8b35ea754345

## Quick Start: Making a Car TVC

A real end-to-end example — from a reference photo to a 15-second commercial.

### Step 1 — Provide a reference image + one-line brief

> "Make a 15-second TVC for this silver sedan"

<img src="https://github.com/user-attachments/assets/0d774888-0dbb-4fb7-a861-ca3116b812b7" width="400" alt="Reference: silver sedan" />

The AI enters the full creative pipeline: brief analysis → creative concept → art style → asset generation → storyboard + video script.

### Step 2 — AI generates 4 product image prompts → Nano Banana Pro renders each separately

The AI outputs 4 independent product image prompts (A1-1 front 45° / A1-2 pure side / A1-3 rear / A1-4 grille macro). Copy each into Nano Banana Pro (edit mode, pass in the reference image) to get 4 standardized product shots from different angles:

<img src="https://github.com/user-attachments/assets/9d97df38-79f1-4a6a-a6bb-0fdbd731faca" width="600" alt="Product multi-angle images" />

### Step 3 — AI generates 8 single-frame storyboard prompts → Nano Banana Pro renders each separately

The AI first plans the full narrative timeline (0–15s across 8 shots), then outputs prompts one frame at a time. For each frame, upload the matching A1 angle image in edit mode (front-facing shots use A1-1, side shots use A1-2, and so on) to get 8 coherent, individual storyboard frames:

<img src="https://github.com/user-attachments/assets/1ca54c8a-e1c2-4a13-8e67-461ea327f2ab" width="600" alt="Single-frame storyboards" />

### Step 4 — AI generates video prompts → Seedance renders video

The AI outputs a Seedance Multi-Phase video script (8 Phases / 15s). Use Frame 1 (first frame reference) + A1-X (product anchor) as dual-image input to Seedance to generate the final video.

### Output Summary

| Deliverable | Count | Tool | Purpose |
|-------------|-------|------|---------|
| Product images (A1-1 ~ A1-4) | 4 images | Nano Banana Pro (edit) | Product appearance anchor, referenced by angle |
| Single-frame storyboards (Frame 1 ~ 8) | 8 images | Nano Banana Pro (edit) | Full narrative timeline; Frame 1 passed into Seedance |
| Multi-Phase video script | 1 | Seedance | Generate 15s final video |
| Creative brief document | 1 | — | Full creative brief for archival |

## Design Philosophy

Traditional AI-generated ads tend to be an endless loop of "product + black background + rotation." TVC Director is different — it organizes prompt generation around the real TVC production SOP, so every prompt maps to a specific production stage:

- **Narrative-driven** — Determine the narrative model and creative direction first, then generate visuals; no mindless template filling
- **Dual-world crosscutting** — Product close-ups interweave with brand world scenes, telling stories like a real TVC
- **Per-second camera design** — Every storyboard panel has explicit shot size, angle, lighting, and transition logic
- **Progressive human-AI collaboration** — Intervene and adjust at every phase; not a black-box one-click generator

## Three Core Capabilities

### 1. Cinematic Product Breakdown

Product as sole protagonist, pure studio, multi-phase product micro-films:

- Component disassembly/assembly animations (floating parts, exploded views, snap-back)
- Material macro shots (brushed metal, glass refraction, carbon fiber weave)
- Precise per-second camera choreography (ultra-slow reveal → explosive rotation → macro dive)
- Cinematic studio lighting (low-key, side light silhouettes, light flowing with rotation)

### 2. Brand World Crosscut

Brand world and product world take turns, connected via match cuts:

- Action cameras → skydiving, diving, skiing, climbing
- Off-road vehicles → mountain roads, desert, snow
- Each Phase stays in one world; world switches happen between Phases

### 3. Lifestyle Film

Product stays in the brand world throughout — no studio cutaways:

- Running shoes on feet, watches on wrists, glasses on faces
- Highlighted through cinematography (low-angle tracking, slow motion, depth-of-field shifts)
- Hero Shot concentrated at the end

## Installation

### Cursor

```bash
git clone https://github.com/Ethanxwang/tvc-director.git ~/.cursor/skills/tvc-director
```

### Claude Code

```bash
git clone https://github.com/Ethanxwang/tvc-director.git ~/.claude/skills/tvc-director
```

## Entry Modes

| Mode | Trigger | Description |
|------|---------|-------------|
| **A: Full TVC Pipeline** | "帮我做一条xx产品广告" | Brief → Concept → Style → Assets → Keyframes → Package |
| **B: Quick Asset/Prompt** | "帮我做一个产品 Hero Shot" | Skip creative phase, go to asset or keyframe generation |
| **C: Storyboard** | Provide a TVC script/storyboard | Style → Assets → Convert storyboard to keyframes |
| **D: Iteration** | "这张产品图xx不对" | Fix and regenerate specific assets or keyframes |

## TVC Narrative Models

| Model | Name | Core Logic |
|-------|------|-----------|
| A | Problem-Solution | Pain point → product saves the day |
| B | Cinematic Product Breakdown | Multi-phase micro-film revealing USPs |
| C | Brand World Crosscut | Scene ↔ product close-up crosscutting |
| D | Lifestyle Film | Product stays in scene, highlighted by cinematography |
| E | Emotional Anchor | Emotional story, product as carrier |
| F | Montage Reveal | Visual spectacle → product reveal |
| G | Before/After | Before/after strong contrast |
| H | Brand Anthem | Values-driven, product closes |

## Deliverables

```
my-tvc-project/
├── concept.md                      # TVC creative brief
├── storyboard.md                   # Storyboard (if applicable)
│
├── assets/                         # Product image prompts (Nano Banana Pro)
│   └── prompts/
│       ├── A1-1-front-45.md        # Front 45° top-down full body
│       ├── A1-2-side.md            # Pure side full body
│       ├── A1-3-rear.md            # Rear full body
│       └── A1-4-grille-detail.md   # Grille + headlight macro
│
├── keyframes/                      # Single-frame storyboard prompts (Nano Banana Pro)
│   └── prompts/
│       ├── frame-01-hook.md        # 0–2s Opening hook
│       ├── frame-02.md
│       ├── ...
│       ├── frame-07-hero.md        # 11–13s Hero Shot
│       └── frame-08-endframe.md    # 13–15s End Frame
│
└── video-scripts/                  # Multi-Phase video prompts (Seedance)
    └── segment-01-15s.md
```

## How to Use Deliverables

1. **Product images (A1-1 ~ A1-4)** — Copy each prompt into Nano Banana Pro, edit mode, pass in the reference image to generate 4 product shots from different angles
2. **Single-frame storyboards (frame-01 ~ frame-08)** — Copy each prompt into Nano Banana Pro, edit mode, pass in the matching A1 angle image (front shots → A1-1, side shots → A1-2, rear shots → A1-3, detail shots → A1-4)
3. **Video scripts** — Use the Multi-Phase script with Frame 1 (first frame reference) + A1-X (product anchor) as dual-image input to Seedance to generate the final video

## Knowledge Base Architecture

Knowledge base is organized by crew roles in real ad production, loaded on demand:

| Crew Role | File | Real Production Equivalent | Loading |
|-----------|------|---------------------------|---------|
| Line Producer | `SKILL.md` | Production workflow control, phase transitions | Always loaded |
| Creative Director | `treatment.md` | Creative pitches, narrative models, category strategy, casting decisions | Creative Proposal |
| Director of Photography | `shot-language.md` | Shot language, art style system, scene types, composition paradigms | Look Dev / Storyboard |
| Production Team | `pre-production.md` | Casting & wardrobe, product photography, location scouting, asset consistency | Pre-production |
| Director | `storyboard.md` | Storyboard, video scripts, product breakdown, brand world shots | Storyboard & Shoot |
| Post-production | `delivery.md` | Output formats, iteration guide (11 failure modes) | Review / Delivery |

## License

MIT
