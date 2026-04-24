# TVC Prompt Engineering Knowledge Base

> **Scope**: Reference for Phase 3 art style confirmation + Phase 4/5 prompt writing. Covers syntax structure, art style selection, scene templates, and composition paradigms for Nano Banana Pro image prompts.
> **Not covered here**: Creative strategy (see treatment.md), asset planning and generation order (see pre-production.md), video prompts and multi-panel grids (see storyboard.md), output format and iteration (see delivery.md).

---

## Part 1: Prompt Structure

---

## 1. Core Prompt Structure

The optimal prompt structure for Nano Banana Pro consists of six layers, arranged left to right:

```
[Image quality anchor] + [Subject description] + [Environment/space] + [Lighting] + [Composition/camera] + [Art style anchor]
```

### Layer-by-Layer Breakdown

#### Layer 1: Image Quality Anchor (Highest front-weighted priority)

Image quality anchor words determine the overall generation quality and are placed at the very beginning of the prompt. The choice depends on the confirmed art style direction.

| Image quality anchor | Applicable art style direction | Applicable scenes |
|---------------------|-------------------------------|-------------------|
| Live-action photography | A. Live-action photography | Live-action characters/scenes |
| Cinematic photography | A. Live-action photography | Live-action film visuals |
| Live-action film still quality | B. Live-action film still | Marvel/Game of Thrones film-grade |
| Hyperrealistic cinematic quality | B/C. Film still or CG | Hyperrealistic CG scenes (⚠️ alone skews toward CG) |
| Ultra-photorealistic cinematic quality | C. AAA game CG | High-realism CG scenes |
| 8K ultra-high resolution | Universal | All scenes requiring fine texture |
| Cinematic lens | Universal | Cinematic imagery |
| Master-level CG rendering | C/D. CG or engine-grade | AAA games, animated CG |
| Unreal Engine 5 rendering | D. High-fidelity CG engine-grade | Top-tier CG approaching photorealism |
| Hyperrealistic CG | D. High-fidelity CG engine-grade | Hollywood VFX-grade CG |
| Cinematic CG visual effects | D. High-fidelity CG engine-grade | Ready Player One / Avatar-grade VFX |

**Combination examples by art style direction**:
- **Live-action photography**: `Live-action photography, cinematic photography, realistic skin pore texture, natural lighting`
- **Live-action film still**: `Live-action film still quality, 8K ultra-high resolution, cinematic color grading`
- **AAA game CG**: `Hyperrealistic cinematic quality, 8K ultra-high resolution, cinematic color grading`
- **High-fidelity CG engine-grade**: `Unreal Engine 5 rendering, 8K ultra-high resolution, SSS skin, global illumination` or `Hyperrealistic CG, cinematic CG visual effects, 8K ultra-high resolution, cinematic color grading`
- **Photography-leaning**: `8K ultra-high resolution, cinematic lens`

#### Layer 2: Subject Description

**Character description layers**:
```
[Identity/name] + [Physique/build] + [Facial features] + [Clothing/equipment] + [Pose/action] + [Expression/emotion]
```

**Object/prop description layers**:
```
[Type] + [Material] + [Size] + [Special effects] + [State]
```

#### Layer 3: Environment/Space

```
[Space type] + [Space scale] + [Materials/surfaces] + [Atmospheric effects] + [Environmental details]
```

#### Layer 4: Lighting

```
[Overall brightness/contrast] + [Key light position and type] + [Lighting effects] + [Color temperature/color]
```

#### Layer 5: Composition/Camera

Specify composition intent and camera parameters using natural language within the prompt.

#### Layer 6: Art Style Anchor (Closing safety net)

Art style anchor words are placed at the end as an overall style safeguard. **Must align with the confirmed art style direction.**

| Art style anchor | Applicable art style direction |
|-----------------|-------------------------------|
| Live-action photography, cinematic photography, realistic skin pore texture, natural lighting | A. Live-action photography |
| Live-action film still quality, realistic skin texture and hair detail | B. Live-action film still |
| Cinematic film color, grain | A/B. Live-action directions |
| AAA 3D game style | C. AAA game CG |
| Cinematic color grading | Universal |
| Unreal Engine 5 rendering, SSS skin, PBR materials | D. High-fidelity CG engine-grade |
| Hyperrealistic CG, cinematic CG visual effects, cinematic color grading | D. High-fidelity CG engine-grade |
| Impressionistic lighting | E. Specific aesthetic style |
| Minimal composition | Universal |

---

## 2. Image Quality × Art Style Quick Reference

| Visual goal | Art style direction | Image quality anchor (front) | Art style anchor (end) |
|-------------|--------------------|-----------------------------|------------------------|
| Live-action photography | A | Live-action photography, cinematic photography, 8K ultra-high resolution | Realistic skin pore texture, natural lighting |
| Live-action film still | B | Live-action film still quality, 8K ultra-high resolution | Realistic skin texture and hair detail, cinematic color grading |
| Hyperrealistic cinematic (CG-leaning) | B/C | Hyperrealistic cinematic quality, 8K ultra-high resolution, cinematic color grading | — |
| AAA game CG | C | Master-level CG rendering, 8K ultra-high resolution | AAA 3D game style |
| High-fidelity CG engine-grade (character-focused) | D | Unreal Engine 5 rendering, 8K ultra-high resolution | SSS skin, realistic skin texture, PBR materials, global illumination |
| High-fidelity CG engine-grade (environment-focused) | D | Hyperrealistic CG, cinematic CG visual effects, 8K ultra-high resolution | PBR materials, global illumination, cinematic color grading |
| Dark realism | A/B/C | Ultra-photorealistic cinematic quality, 8K material texture | Low-key photography (Low-key Lighting), high contrast, grain |
| Grand epic scene | Follow global direction | Hyperrealistic cinematic quality, 8K ultra-high resolution | Wide-angle lens, extremely low angle to emphasize spatial scale |
| Eastern classical style | E | Cinematic quality, 8K | Chinese ink wash aesthetics, impressionistic lighting |
| Healing/warm style | E | 8K ultra-high resolution | Golden Hour warm light, dreamy Bokeh |

---

## 3. Multi-Reference Image Description Format

```
Composition core (Composition):
Foreground: [Character/object] (Image 1) [pose/position description]. [Appearance details].
Midground/background: [Character/object] (Image 2) [pose/position description]. [Appearance details].
Lighting:
[Light source 1 description].
[Light source 2 description].
Key details: [Material reflections/shadows/special effects].
Camera language: [Lens type], [angle], [depth of field].
```

---

## 4. Prompt Length Control

| Scene complexity | Recommended length | Notes |
|-----------------|-------------------|-------|
| Simple (single subject + simple background) | 30–80 words | e.g., character turnaround sheet, product close-up |
| Medium (subject + environment + lighting) | 80–150 words | e.g., environment concept art, single-person scene |
| Complex (multi-layer composition + narrative) | 150–300 words | e.g., confrontation shot, multi-person scene |

**Principle**: Descriptive precision > descriptive length.

---

## Part 2: Art Style Anchor Word Library

---

## 1. Art Style Options

| Option | Description | Visual effect |
|--------|-------------|---------------|
| **A. Live-action photography / photographic** | Looks like real photography | Similar to film stills, fashion photography |
| **B. Live-action film still** | Between live-action and CG | Similar to Marvel film characters, Game of Thrones |
| **C. AAA game CG** | High-quality game CG rendering | Similar to Final Fantasy CG, Genshin Impact cutscenes |
| **D. High-fidelity CG engine-grade** | All CG but pursuing "near-photorealistic" top-tier quality | Similar to Ready Player One, Unreal Engine 5 MetaHuman |
| **E. Specific aesthetic style** | Ink wash, cyberpunk, anime, etc. | Varies by specific style |

---

## 2. Anchor Words and Combinations by Style

### A. Live-Action Photography / Photographic

| Anchor word | Applicable scenes | Pairing suggestions |
|-------------|------------------|---------------------|
| Live-action photography | Directly anchors live-action photo direction | + Cinematic photography + Natural lighting |
| Cinematic photography | Emphasizes photographic feel over rendered feel | + Live-action photography |
| Realistic skin pore texture | Forces live-action skin micro-details | For character reference sheets / close-ups |
| RAW photo quality | Unprocessed raw photography feel | + Natural lighting |
| Cinematic film color | Film-grade color toning | + Grain |

**Combination examples**:
- `Live-action photography, cinematic photography, realistic skin pore texture, natural lighting` — Pure live-action photo-grade
- `Live-action photography, 8K ultra-high resolution, cinematic film color` — High-definition live-action film grain

### B. Live-Action Film Still

**Combination examples**:
- `Live-action film still quality, 8K ultra-high resolution, realistic skin texture and hair detail, cinematic color grading` — Broadcast/film-grade
- `Hyperrealistic cinematic quality, live-action film still quality, cinematic color grading` — Hyperrealistic leaning live-action

### C. AAA Game / CG

Key anchor words: `AAA 3D game style`, `Master-level CG rendering`, `Hyperrealistic cinematic quality`, `8K ultra-high resolution`, `Cinematic color grading`

### D. High-Fidelity CG Engine-Grade

**Core positioning**: Entirely CG rendering, but in terms of materials, lighting, and skin, infinitely approaching photorealism. Difference from direction C: C retains a clear "game CG aesthetic", D pursues "indistinguishable from real CG".

| Anchor word | Applicable scenes | Pairing suggestions |
|-------------|------------------|---------------------|
| Unreal Engine 5 rendering | Extreme ray-traced quality | + Global illumination + PBR materials |
| SSS skin | Subsurface light translucency in skin | + Unreal Engine 5 rendering + Realistic skin texture |
| PBR materials | Physically correct material rendering | + Global illumination |
| Hyperrealistic CG | Directly anchors "CG pursuing realism" | + Cinematic color grading |
| Cinematic CG visual effects | Hollywood VFX blockbuster-grade | + 8K + Cinematic color grading |

**Combination examples**:
- `Unreal Engine 5 rendering, SSS skin, realistic skin texture, PBR materials, global illumination` — Top-tier engine-grade CG (character-focused)
- `Hyperrealistic CG, cinematic CG visual effects, 8K ultra-high resolution, cinematic color grading` — Hollywood VFX-grade CG (environment-focused)
- `Ray-traced rendering, PBR materials, global illumination, cinematic color grading` — Engine-grade CG environment

### E. Specific Aesthetic Style

| Anchor word | Applicable scenes |
|-------------|------------------|
| Chinese ink wash aesthetics | Classical / wuxia / Eastern themes |
| Cyberpunk aesthetics | Sci-fi / futuristic urban |
| Japanese anime style | 2D animation / anime quality |
| Studio Ghibli style | Healing / Miyazaki quality |
| Low-key photography (Low-key Lighting) | Dark / mystery / horror |
| Golden Hour warm light | Healing / nostalgic / emotional |

---

## 3. C vs D Comparison

| Dimension | C. AAA game CG | D. High-fidelity CG engine-grade |
|-----------|----------------|----------------------------------|
| Skin | Refined but smooth, idealized beauty | Pores, fine lines, uneven skin tone — close to real |
| Lighting | Game-level lighting, artistic stylization acceptable | Global illumination + ray tracing, physically correct |
| Materials | Refined but stylization allowed | PBR physically correct, every surface has real reflectance/roughness |
| Overall feel | "A refined game character" | "Is this CG or real?" |

---

## Part 3: TVC Scene Types

> Scene type classifications and prompt templates specific to TVC advertising. Designed around three core objectives: product showcase, brand narrative, and visual transitions.

---

## Scene Types Overview

| Category | Scene type | Core function |
|----------|-----------|---------------|
| Product World shots | Product Hero Shot | Setting the key visual tone |
| Product World shots | Cinematic product breakdown frame | Visualizing technical capability |
| Product World shots | Feature visualization frame | UI / data / sensor presentation |
| Product World shots | Material macro frame | Amplifying craftsmanship details |
| Product World shots | Pack Shot | Packaging display |
| Product World shots | End Frame | Closing freeze frame |
| Brand World shots | Extreme sports scene | Extreme environment credibility |
| Brand World shots | Lifestyle scene | Daily use resonance |
| Brand World shots | Emotional scene | Emotional connection between person and product |
| Brand World shots | Atmospheric establishing shot | Building brand worldview |
| Crosscut transition frames | Match cut transition frame | Visual bridge between Product World and Brand World |
| Crosscut transition frames | Product Reveal transition | Reveal transition from usage scene to product close-up |

---

## Category 1: Product World Shots

---

### 1. Product Hero Shot

#### Prompt Template
```
[Image quality anchor], [product description] resting at the center of [background]. [Lighting design — side light / rim light / top light]. [Material details — metal / glass / matte]. [Composition — product proportion / negative space]. [Art style anchor].
```

#### Key Points
- **Restrained background**: Solid color or minimal studio quality
- **At least two light sources**: Key light (side light for form definition) + fill light (rim light to separate from background)
- **Material must be described in detail**: Brushed metal, AG matte glass, ceramic gloss, etc.
- **Product proportion**: 40%–60% is optimal

#### Example
```
8K ultra-high resolution, cinematic product photography. A deep space gray titanium metal smartwatch resting at the center of a pure black background, the dial tilted slightly 15 degrees to the right. Soft side light from the left traces the brushed texture of the titanium case and the subtle chamfer highlights. Rim light from the right separates the product from the pure black background, forming an ultra-thin white light edge along the case rim. The dial shows a deep blue surface, with scales and hands reflecting cold white micro-light. The strap is black fluoroelastomer material with visible fine diamond-pattern embossing on the surface. The product occupies 50% of the center of the frame, with 30% negative space above. Very shallow depth of field, focal point on the dial. Product photography quality, cinematic color grading.
```

---

### 2. Cinematic Product Breakdown Frame

#### Prompt Template
```
[Image quality anchor], [product name]'s [component description] in floating exploded state. [Spatial positional relationships between components]. [Core sensor / chip glow effect]. [Studio side light]. [Art style anchor].
```

#### Key Points
- **Float spacing**: Describe specific spatial layer relationships between components
- **Glowing elements**: Add subtle self-illumination effects to chips, sensors, etc.
- **Control component count**: 3–5 component layers is optimal

#### Example
```
8K ultra-high resolution, cinematic CG visual effects. A smartwatch in a cinematic exploded view, components floating apart along the vertical axis. Top layer: sapphire crystal glass, edges refracting rainbow-colored halos. Second layer: AMOLED display panel, screen emitting a faint blue self-illumination. Third layer: titanium mid-frame, with visible precision CNC machining marks. Fourth layer: mainboard and sensor module, the core chip emitting a light green micro-glow, circuit traces as fine as hair. Bottom layer: ceramic back cover, optical heart rate sensor emitting red pulse light. Equal spacing between all layers, overall at a slight overhead 3/4 angle. Pure black gradient background, studio side light from the left illuminating component edges. Hyperrealistic CG, cinematic color grading.
```

---

### 3. Feature Visualization Frame

#### Prompt Template
```
[Image quality anchor], [product]'s screen / interface display. [Detailed screen content description — UI elements / data / charts]. [Effect of screen glow on surrounding environment]. [Product body position and state in the frame]. [Lighting — screen self-illumination as key light]. [Art style anchor].
```

#### Key Points
- **Screen content must be specific**: Describe UI layout using geometric shapes; avoid requesting precise text
- **Screen light spill effect**: Screen light illuminates surrounding surfaces
- **Dark environment amplifies effect**: Let the screen serve as the primary light source in the frame

#### Example
```
8K ultra-high resolution, cinematic product photography. In a low-light environment, a smartwatch is worn on a wrist with the dial facing the camera. The screen displays a fitness monitoring interface: a large green heart rate number in the center, surrounded by three colored ring progress bars (red / green / blue), and at the bottom a real-time heart rate waveform curve with faint green pulse light at the peaks. The screen's cold blue glow spills onto the wrist skin, forming a soft blue halo on the skin surface. The background is completely black; only the screen light serves as the sole light source. Close-up, slight overhead angle, very shallow depth of field, focal point on the screen, wrist edges softly bokeh out of focus. Product photography quality, cinematic color grading.
```

---

### 4. Material Macro Frame

#### Prompt Template
```
[Image quality anchor], macro close-up of [product part]'s [material type] surface. [Microscopic physical details — texture / grain / reflectance]. [Macro lighting — side light to sculpt texture / backlight to penetrate material]. [Very shallow depth of field, focal point position]. [Art style anchor].
```

#### Key Points
- **Side light is the king of macro**: Low-angle side light maximally sculpts surface texture relief
- **Physical microscopic detail**: Metal machining tooling marks, glass micro-bubbles, fiber weave intersections
- **Scale hint**: Add microscopic reference objects such as dust particles to suggest the magnification level

#### Example
```
8K material texture, macro close-up. The side chamfer area of a titanium metal watch case. Ultra-low angle side light grazes from the left, illuminating every precise parallel groove in the brushed texture, the high points between grooves reflecting sharp white highlight lines, the low points sinking into shadow. At the junction of chamfer and flat surface, ultra-fine concentric CNC machining marks are visible. Two or three micro-dust particles are scattered on the surface, suggesting an extreme magnification scale. The right edge transitions to an AG matte glass area, the matte grain sparkling like dense starlight under the side light. Very shallow depth of field, focal point at the midpoint of the brushed texture, foreground and far end rapidly falling out of focus. Product photography quality, high contrast.
```

---

### 5. Pack Shot

#### Prompt Template
```
[Image quality anchor], [product packaging description — shape / color / material] facing the camera, [placement state]. [Product body beside the packaging]. [Lighting — soft studio light]. [Composition — positional relationship between packaging and product]. [Art style anchor].
```

#### Key Points
- **Packaging + product in the same frame**
- **Packaging angle**: A slight 15–30 degree turn gives more dimensionality than a straight-on view
- **Soft light as primary**

#### Example
```
8K ultra-high resolution, product photography quality. On a light gray gradient studio background, a matte black square packaging box is placed at a slight 20-degree angle on the left side of the frame, the box face bearing a hot-silver-stamped brand mark. To the right of the box, the smartwatch body is shown at a 3/4 angle with the dial facing the camera, the screen displaying the time interface. The box lid is slightly open, revealing the dark gray suede inner lining. Soft top light evenly illuminates the product and packaging, casting a soft elliptical shadow on the background. The product and packaging box together occupy 60% of the frame, with negative space left above and to the right. Product photography quality, natural lighting.
```

---

### 6. End Frame

#### Prompt Template
```
[Image quality anchor], [product description] resting at [angle / pose] in [background]. [Lighting — clean, premium]. [Composition — product offset, negative space for text overlay]. [Art style anchor].
```

#### Key Points
- **Leaving space for text is the core**: At least 30%–40% clean area for the Logo and Slogan
- **Product pose is stable**, with no suggestion of movement
- **Post-production space**: Logo / Slogan / legal information overlaid in post

#### Example
```
8K ultra-high resolution, cinematic product photography. Deep space gray gradient background. In the lower-left third of the frame, a smartwatch rests stably facing the camera, the dial showing a deep blue interface. Soft side light from the left illuminates the product, with a natural transitional shadow forming on the right. The upper-right portion of the frame leaves 40% clean space, the background gradient smooth and unobstructed. Overall tone: composed, premium, restrained. Product photography quality, cinematic color grading.
```

---

## Category 2: Brand World Shots

---

### 7. Extreme Sports Scene

#### Prompt Template
```
[Image quality anchor], [sports scene environment description]. [Athlete description — action / pose / equipment]. [Product position and state on the athlete]. [Physical effects from motion — splash / airflow / snow spray]. [Lighting — natural light]. [Composition — dynamic]. [Art style anchor].
```

#### Key Points
- **Freeze the most tension-filled moment**
- **Physical effects amplify sense of motion**: Water splash, snow mist surge, dust cloud
- **Product must be visible but not dominant**

#### Example
```
Live-action photography, cinematic photography, 8K ultra-high resolution. An alpine ski slope, intense midday sunlight. A skier in the frozen instant of a high-speed carving turn on a steep slope, body extremely compressed and leaning, outside hand nearly touching the snow surface. The snow spray kicked up by the carving turn forms an arcing white wave wall, snow particles sparkling like shattered diamonds in the backlight. The smartwatch clearly visible on the athlete's left wrist, the green glow of the GPS track interface on the dial contrasting against the white snow. Low-angle side-tracking angle, the athlete cuts diagonally from upper-left to lower-right, the snow spray behind occupying the upper third of the frame. Realistic skin pore texture, natural lighting, cinematic color grading.
```

---

### 8. Lifestyle Scene

#### Prompt Template
```
[Image quality anchor], [everyday scene environment description — time / location / atmosphere]. [Subject description — clothing / state / emotion]. [Subject's interaction with the product]. [Environmental details — props that enhance life authenticity]. [Lighting — natural light / window light / warm tones]. [Composition]. [Art style anchor].
```

#### Key Points
- **The "incidental" feel is key**: Product appears naturally within everyday life
- **Environmental props feel authentic**: Coffee cups show signs of use, surfaces have natural clutter
- **Natural light + warm color tones**

#### Example
```
Live-action photography, cinematic photography, 8K ultra-high resolution. 7 AM, beside the dining table of a Nordic-style apartment. Warm morning side light streams in from a large window on the left, casting window frame light patterns on the wooden dining table. A woman in her early 30s wearing a beige linen shirt lifts a white ceramic coffee cup to take a sip with her left hand; her right wrist shows a smartwatch displaying today's exercise goal completion. On the table are scattered an open magazine, a croissant, and a small dish of butter. The background is a softly bokeh-blurred green plant and kitchen island. Medium shot at eye level, subject positioned in the right third of the frame, the window light on the left forming a large warm-toned light area. Realistic skin pore texture, natural lighting, cinematic film color.
```

---

### 9. Emotional Scene

#### Prompt Template
```
[Image quality anchor], [emotional scene environment]. [Subject description — key emotional expression and body language]. [Product's role in the emotional interaction]. [Lighting — color temperature and brightness matching the emotion]. [Composition — close-up or medium close-up to emphasize expression]. [Art style anchor].
```

#### Key Points
- **Emotion conveyed through multiple channels**: Micro-expression + body language + lighting + color tone
- **Product as emotional carrier**: A "prop" that triggers or contains the emotion
- **Avoid excessive sentimentality**

#### Example
```
Live-action photography, cinematic photography, 8K ultra-high resolution. Evening living room. A young father sits on a sofa, his 3-year-old daughter asleep on his shoulder. His right hand gently strokes the back of the child, while the screen of the smartwatch on his left wrist lights up showing a message notification from his wife, the screen's soft blue-white glow falling on his face. He looks down at the watch, the corner of his mouth involuntarily curling upward slightly, eyes warm. A warm yellow table lamp from the left side of the frame wraps father and daughter in a warm-toned light pool, the background completely bokeh'd into warm Bokeh light orbs. Medium close-up, subjects positioned center-right of the frame, very shallow depth of field, focal point on the father's facial expression. Realistic skin texture and hair detail, cinematic color grading.
```

---

### 10. Atmospheric Establishing Shot

#### Prompt Template
```
[Image quality anchor], [space type and scale]. [Environmental physical details — materials / textures / objects]. [Atmospheric effects — mist / light / particles]. [Lighting design]. [Composition / camera — wide angle / overhead / leading lines]. [Art style anchor].
```

#### Key Points
- **No people**
- **Light and shadow is the emotion**: Entirely reliant on lighting and color tone to convey feeling
- **Can serve as a transition**: Color tones and composition must consider how the surrounding shots connect

#### Example
```
8K ultra-high resolution, cinematic photography. A highland lake at dawn, the lake surface still as a mirror, perfectly reflecting the distant mountain range and gradient sky. The horizon transitions from deep blue to rose gold, the sun about to crest the mountain ridge at its brightest point. A thin layer of morning mist floats on the lake, the fog flowing slowly about one meter above the water's surface. The foreground is composed of shoreline pebbles and a clump of yellowed alpine meadow grass, bokeh'd into a foreground color block by shallow depth of field. Wide-angle lens, rule-of-thirds composition: sky occupying the upper third, lake surface and reflection occupying the middle third, foreground shore occupying the lower third. Cinematic film color, grain.
```

---

## Category 3: Crosscut Transition Frames

---

### 11. Match Cut Transition Frame

Designing the "bridge frame" within a Match Cut: establishing perceivable visual continuity between the tail frame of A and the lead frame of B. The complete Match Cut technique library is in `storyboard.md` Part 4.

---

### 12. Product Reveal Transition

Smoothly transitioning from a Brand World usage scene to a close-up showcase in Product World.

Transition path: `Usage scene wide shot → Product partially visible → Product fills the frame → Product Hero Shot`

#### Prompt Template (Three-Phase)

**Phase A (Brand World → Product first appears)**:
```
[Image quality anchor], [usage scene medium shot]. [Subject action brings product naturally into view]. [Product is clear but not the focal point in the frame]. [Ambient lighting]. [Art style anchor].
```

**Phase B (Transition frame — Product enlarges)**:
```
[Image quality anchor], [close-up / macro], [product occupies frame as the primary subject]. [Environmental elements from the usage scene bokeh'd into the background]. [Lighting transitions from ambient to product photography light]. [Very shallow depth of field, focal point locked on product]. [Art style anchor].
```

**Phase C (Product World — Hero Shot)**: Use the "Product Hero Shot" template.

#### Example (Outdoor sports → Watch close-up Reveal)

**Phase A**:
```
Live-action photography, cinematic photography, 8K ultra-high resolution. A sunlit mountaintop. A trail runner bends over with hands on knees catching breath after finishing a sprint, lifting the left wrist to check exercise data. The smartwatch is visible in the frame but small; the screen's green glow remains clearly legible in the sunlight. The background is a vast valley and blue sky. Medium shot, subject centered, natural lighting. Realistic skin pore texture, cinematic color grading.
```

**Phase B (Transition frame)**:
```
Live-action photography, cinematic photography, 8K ultra-high resolution. Close-up of the athlete's left wrist smartwatch, dial facing the camera, screen displaying the stats interface for completing a 10-kilometer trail run. The watch occupies 60% of the frame; sunlight highlights on the titanium case surface and micro-beads of sweat are visible. The wrist skin and distant mountain scenery are completely bokeh'd into a warm-toned background Bokeh. Very shallow depth of field, focal point on the dial. Natural sunlight mixed with subtle rim light. Product photography quality, cinematic color grading.
```

---

## Part 4: TVC Composition Paradigms

TVC composition must serve not only "beauty" but also "communication."

### 4.1 Reveal Composition

**Classic reveal sequence**:

```
Step 1: Extreme macro — audience sees abstract texture / lines, unsure what it is
Step 2: Slowly pull back — partial outlines begin to emerge, audience starts guessing
Step 3: Continue pulling back — full product form is revealed, "so that's what it is" moment of recognition
Step 4: Complete product reveal — showing the full form in a perfect composition
```

**Variant techniques**: Occlusion reveal, light reveal, focus reveal, rotation reveal.

### 4.2 End Frame Composition Standard

| Element | Composition position | Size requirement |
|---------|---------------------|-----------------|
| **Product** | Center of frame, slightly left or centered | 20%–40% of frame |
| **Brand Logo** | Lower right or bottom center | Clearly legible but not overpowering the product |
| **Tagline / Slogan** | Above Logo or below product | Font size smaller than product name |
| **Background** | Brand color or brand signature visual | Simple, not distracting |

**End Frame Three Rules**:
1. **3-second readability**: All information must be readable by the audience within 3 seconds
2. **3 elements or fewer**: Product + Logo + Slogan — maximum three information tiers
3. **3 visual hierarchy levels**: Clear primary–secondary–supporting visual priority

### 4.3 Text/Logo Safe Zones

| Zone | Definition | Purpose |
|------|-----------|---------|
| **Frame safe area** | 5% inset from edges | All key visual elements |
| **Title safe area** | 10% inset from edges | All text information |
| **Upper 1/5** | Top 20% | Tagline, title |
| **Lower 1/5** | Bottom 20% | Product information, legal disclaimer |
| **Central 60%** | Center zone | Core visual content; avoid being obscured by text |

---

## Appendix: TVC Visual Design Checklist

- [ ] Is there a clear integration strategy for the brand color?
- [ ] Does the brand color blend naturally into the overall color arc of the film?
- [ ] Is the beauty of the product materials released through the correct lighting strategy?
- [ ] Have the product shots been given a "sculptural" treatment?
- [ ] Does the ratio of product to negative space serve the narrative intent?
- [ ] Has the composition reserved safe zones for text / Logo?
- [ ] Does the End Frame satisfy "3-second readability, 3 elements, 3 visual tiers"?
- [ ] Has the visual world the brand inhabits been defined and carried consistently throughout the film?
- [ ] Does the choice of visual world match the brand tone and target audience?
