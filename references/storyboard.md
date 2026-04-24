# TVC Storyboard & Video Production Knowledge Base

> **Responsibility**: The sole reference for storyboarding and shooting phases. Covers multi-grid storyboards, video prompt syntax, cinematic product breakdown, and Brand World shots. Multi-grid storyboards and video prompts are paired deliverables — each multi-grid corresponds to one video prompt.
> **Out of scope**: Creative strategy (see treatment.md), image prompt syntax (see shot-language.md), output formats and iteration (see delivery.md).

---

## Part 1: Multi-Grid Storyboard

---

## I. Four-layer structure of multi-grid prompts

A complete multi-grid prompt consists of four layers, arranged in the following order:

### Layer 1: Global style

Defines the visual tone and physical format of the entire image. Must include:

- **Grid declaration**: `Generate a composite image containing N panels, arranged in an RxC grid`
- **Art style anchor**: Consistent with the art direction confirmed in Phase 3 (see `art-style-library.md`)
- **Aspect ratio**: The ratio of the entire multi-grid image (usually 16:9 or 1:1)
- **Rendering/shooting system** (optional): e.g. `shot on an ARRI Alexa cinema camera` or `Unreal Engine 5 real-time rendering`, used to lock in the image quality

Example:
> Generate a composite image containing 9 panels, arranged in a 3x3 grid. 3D fantasy animation style, shot on an ARRI Alexa cinema camera, 16:9 landscape.

### Layer 2: Reference image mapping

When using `edit` mode to reference Phase 4 asset images, establish the mapping in this layer.

Format: `(Image 1)[asset type/name], (Image 2)[asset type/name]...`

If there are no reference images (pure text-to-image mode), skip this layer and describe the key visual characteristics of the character/environment in Layer 1.

### Layer 3: Narrative thread + per-panel description

This is the core of the multi-grid prompt. The approach varies with **story density** — see Section IV for details.

### Layer 4: Consistency anchor

After all per-panel descriptions, append global consistency requirements:

- **Style unity**: `Maintain consistent overall style` (required)
- **Visual motif**: Elements that recur across all panels (e.g. a lighting effect, a prop, a color, a compositional technique)
- **Color continuity**: Describes the color/lighting gradient trend across panels
- **Character consistency**: If a character appears across multiple panels, emphasize that their appearance must not change
- **Video narrative**: Briefly describe how the 9 panels function as a video flow — camera movement trajectory, product state changes, key transition points (e.g. `Video narrative: wide establishing shot (P1) → arc around the bottle (P2-P3) → macro dive in (P4) → ... → freeze frame (P9)`). This is not an instruction for the image generation model — it is a mental anchor for downstream video prompt writing

---

## II. Video narrative first

A multi-grid storyboard is not a collage of 9 beautiful images — it is 9 key frames frozen from a 15-second video. **Flow first, then frames.**

### Core principle

Before writing per-panel descriptions, sketch the **video narrative** of these 15 seconds in 1-2 sentences: how the camera language connects continuously, how the product state changes, how the shots transition. The video narrative is a causal chain on the timeline — what each panel inherits and what it transitions to — not just "9 panels that look good together."

The video narrative **does not mean a single continuous shot**. It can include hard cuts, Match Cuts, dissolves, jump cuts, and other transitions — the key is continuity of camera language, not physically continuous camera movement. A single continuous shot is one choice; multi-shot editing is another choice. But every panel must know its position on the timeline.

The multi-grid storyboard is the **frozen** form of the video narrative; the video prompt is the **unfolded** form of the video narrative. Both grow from the same narrative — there is no sequential relationship of "do the images first, then add video."

### Three densities, one principle

- **High-density** "narrative threads" are naturally video narratives — character actions flow across panels, and temporal causality is embedded in the story
- **Mid-density** "journey overviews" are close to video narratives — scene progression itself contains a time flow
- **Low-density has no story, but must have a video narrative** — the continuity of camera language, lighting changes, and product state transitions are the temporal causality of low-density. "No narrative arc" does not mean "no time flow"

### How to write a video narrative (low-density example)

Before the per-panel descriptions, add one line of video narrative:

> Video narrative: slow push into balcony wide shot → tabletop still life → low-angle side shot piercing through bottle caustics → silhouette of bottle against backlit curtain → cat looks up, amber echo between foreground bokeh bottle → overhead tabletop still life anchor → bottle cap macro → bottle on railing with distant view → she walks over, bottle in the distance on the table

In this narrative, P5's cat has a clear temporal position: it inherits the backlit atmosphere of P4, provides product presence through the foreground bokeh bottle, and transitions to the overhead overview of P6. Every panel knows where it comes from and where it goes.

### The video narrative is not part of the prompt

The video narrative is a **mental step** before writing, not text to be output to the image generation model. It can be written in the "Video narrative" note of Layer 4's consistency anchor (for downstream video prompt reference), but it will not appear in the body of Layers 1 through 3.

### Division of labor for dynamic effects

When the creative plan includes dynamic visual effects (material transformation, particle convergence, energy flow, etc.): **the multi-grid storyboard only freezes the final state of the effect; the video prompt describes the complete process of the effect.** The multi-grid storyboard consists of static key frames and cannot express "change" — forcing the process into it will only make the image chaotic.

| Dynamic concept | Multi-grid storyboard (frozen final state) | Video prompt (describes the complete process) |
|---------|-------------------|----------------------|
| Liquid metal solidifies into product | Product is fully formed | Liquid metal flows → slows → solidifies → surface texture gradually changes → takes shape |
| Product floating disassembly | Exploded View with components separated | Animation of components slowly separating, floating, connected by energy lines |
| Screen Activation | Screen is on, showing the interface | Pixels light up from center → ripple spreads outward → interface elements emerge |
| Particles converge into shape | Product is fully presented | Particles converge from all directions → outline appears → surface solidifies |
| Water droplets rolling on shoe surface | Water droplet resting somewhere on the shoe | Water droplet slides along the fabric → demonstrates waterproofing |
| Liquid spilled (coffee/red wine) | Liquid suspended in mid-air, forming a frozen arc | Cup is knocked over → liquid flies out → freezes in mid-air → is caught/righted |
| Person "frozen" | Person remains still in walking/action pose, coat hem suspended | Everyone suddenly stops moving → ambient sound disappears → only protagonist moves freely |
| Paper/fragment storm | Papers suspended at various angles in the air | Wind rises → papers fly → suddenly freeze → removed one by one |

---

## III. Grid format selection

| Format | Panels | Duration coverage | Use case |
|------|------|---------|---------|
| **3x3** | 9 panels | ≈15 seconds | Standard narrative segments, full product promotional flow, most common |
| **2x2** | 4 panels | ≈5-8 seconds | Short transition sequences, compact segments, openers/closers |
| **2x3** | 6 panels | ≈10 seconds | Mid-density narrative, vertical video |
| **3x2** | 6 panels | ≈10 seconds | Horizontal mid-density |

Selection principle: default **3x3**; use **2x2** or **2x3** when content is under 6 frames; prefer **2x3** for vertical, **3x2** or **3x3** for horizontal.

---

## IV. Story density spectrum: how to write per-panel descriptions

The core difference in multi-grid storyboards lies in **story density** — how much weight goes to character action/story progression vs. cinematography direction/visual design.

**TVC density declaration**: TVC advertising uses only **low-density** and **mid-density** modes, with low-density as the default. High-density mode (where AI decides the shot size) does not apply to TVC — every frame of an ad requires precise aesthetic control; compositional decisions cannot be delegated to AI.

### 4.1 Mid-density: Scene progression

**Characteristics**: Has narrative progression (journey/process), but each panel is also a relatively independent scene. Action and cinematography directions are mixed.

**Approach**: Write one sentence summarizing the narrative thread of the journey, then describe panel by panel. Shot size may or may not be specified.

**Complete example** (Mountain ranch at dawn · Walking into the ranch):

```
Generate a composite image containing 9 panels, arranged in a 3x3 grid.
Live-action, cinematic photography, natural light, 16:9 landscape.

Narrative thread: A pre-dawn mountain ranch. The rancher rises alone, steps outside, and walks through the mist toward the herd — a complete dawn.
Color tone shifts from the cold blue-gray of panel 1 to the warm golden-green of panel 9, simulating morning light illuminating the ranch.

1. Rolling hills shrouded in blue-gray mist, sky shifting from deep blue to faint gold. At the very bottom of the frame, the orange glow from a cabin window is the only warm color.
2. The rancher's roughened hands twist an old brass faucet in dim warm light. Clear water flows through the fingers, droplets rolling along calloused skin.
3. A wooden fence disappears into the mist in the distance. Water droplets have condensed on the fence rails; an old leather glove hangs on a crossbar — he just passed this way.
4. Low-angle shot following old brown leather boots stepping through wet grass, each step bending the blades and sending dewdrops flying. Light grows gradually warmer.
5. The rancher pushes open the heavy wooden barn door. Golden morning light floods in through the gap, forming radiating shafts of light that illuminate dancing motes of dust.
6. Dewdrops on a spider's web are illuminated by the flowing morning light, the threads shimmering like silver strings. One droplet, disturbed by a faint vibration, slowly slides down.
7. Golden Tyndall light beams pierce the thick mist and illuminate the foreground grass. Fine dust particles float within the light shafts. In the depths of the mist, a silhouette in a work jacket walks further into the ranch.
8. Golden morning light filters through oak branches and leaves, the leaf edges translucent gold-green. A gleaming metal milk pail sits in the shade below the tree, its wall reflecting a streak of warm light.
9. Wide shot of the ranch. The mist has cleared; golden sunlight blankets the pasture. In the distance, the rancher's figure has reached the herd — person and cattle alike are outlined in golden light.

Maintain consistent overall style. Visual motif: the rancher's "hands" and "footprints" run through all panels.
Tyndall light beams and dewy grass tips recur as environmental cues. Cinematic color grading.
```

### 4.2 Low-density: Visually driven (TVC default)

**Characteristics**: No narrative arc, but a **video narrative** — each panel is a key frame extracted from a video with continuous camera language, not an independent visual design. Pure product/atmosphere showcase with precise cinematography directions.

**Approach**: Write one sentence of **video narrative** first (continuity of camera language + product state flow), then describe panel by panel. Each panel begins with `[Shot size·Angle]:`, precisely specifying camera language, lighting design, and product angle.

**Complete example** (Perfume ad · Multi-angle lighting showcase):

```
Generate a composite image containing 9 panels, arranged in a 3x3 grid.
Using the perfume product in Image 1 as the subject. Pure black background, warm gold side light + white smoke, luxurious quality.

Video narrative: wide establishing shot → rotating to reveal facets → push through smoke → distant smoke enveloping → macro nameplate → rising through smoke → swaying light patterns → alternating warm-cool sweep light → settling to freeze frame

1. Wide shot·overhead: A deep brown amber square perfume bottle rests centered on a pure black background. Warm gold side light sweeps the bottle body; white smoke slowly rises from the bottle's edges; the amber liquid sways faintly, conveying the rich warmth of oud and sandalwood.
2. Medium shot·side-low angle: The perfume bottle slowly rotates 30° clockwise. Facets reflect the black background and swirling smoke; the gold nameplate is illuminated by a spotlight; smoke wraps around the bottle walls as it turns.
3. Medium shot·eye level: The perfume bottle slowly pushes toward the lens. Smoke spreads and billows with the push speed; warm light gradually shifts to deep golden tones; light and shadow form layered warm halos between smoke and bottle.
4. Wide shot·diagonal side: The perfume bottle is half-enveloped in white smoke. The warm gold side light gradually shifts to a dusk deep-gold tone; the amber liquid sways gently in the light; smoke sways like ink patterns.
5. Close-up macro·overhead: A spotlight locks onto the gold nameplate text. Smoke flickers above the lettering; the background is pure black with smoke fully out of focus; highlights the heavy, premium quality of the oud.
6. Wide shot·low angle: The perfume bottle slowly rises through gaps in the smoke. The overhead warm light gradually shifts to soft gold; the bottle refracts warm luminosity; light and shadow shift from sharp to gentle.
7. Medium shot·side: The perfume bottle sways gently left and right. Smoke billows in waves with the movement; the bottle's facets rapidly alternate between light and shadow.
8. Medium shot·eye level: The perfume bottle is still, centered in the background. Warm gold and cold black light alternately sweep the bottle body — first the warm light highlights the warmth of the wood, then the cool light highlights the clarity of the glass.
9. Wide shot·diagonal overhead: The perfume bottle slowly settles back to the center of the frame. Soft warm gold light envelops the bottle body; smoke gradually dissipates; light and shadow settle into calm stillness.

Maintain consistent overall style. Lighting arc: warm gold → deep gold → cold black → warm gold cycle.
Smoke as the visual motif running through all panels.
Video narrative: wide establishing shot (P1) → rotating reveal (P2) → pushing through smoke (P3) → enveloped at distance (P4) → macro nameplate (P5) → rising breakthrough (P6) → swaying rhythm (P7) → alternating warm-cool (P8) → settling to freeze frame (P9).
```

### 4.3 Density comparison quick reference

| Dimension | Mid-density | Low-density (TVC default) |
|------|--------|--------|
| Narrative thread | Recommended (1 sentence journey overview) | **Video narrative** (1-2 sentences of camera language continuity / product state flow) |
| Shot size | Optional | Required, at the start of each panel |
| Panel driving force | Scene + action mix | Cinematography direction |
| Panel relationship | Thematic thread | **Visual rhythm driven by video narrative** |
| Per-panel length | 2-3 sentences | 2-4 sentences |

### 4.4 Mixed density within the same project

Different grids within a project can use different densities. TVC defaults to all low-density.

| Project type | G1 | G2 | G3 | G4 |
|---------|----|----|----|----|
| **TVC product ad** | **Low (product + scene establishing)** | **Low (product display/crosscut)** | **Low (details + climax)** | **Low (closing freeze frame)** |
| Brand narrative film | Mid (character opening) | Low/Mid (product journey) | Low (product display) | Low (closing freeze frame) |

---

## V. General writing guidelines (shared across all densities)

### 5.1 Narrative arc structure

Standard pacing for 9 panels:

| Position | Panels 1-3 | Panels 4-6 | Panels 7-8 | Panel 9 |
|------|-------|-------|-------|-----|
| Function | Establish | Develop | Climax | Coda/closing |

4-panel narrative: Establish → Develop → Climax → Close, one panel each.

### 5.2 Lighting arc

Lighting across panels should form a continuous atmospheric flow: progression of light and shadow, color temperature drift, the climax panel having the most intense contrast. In mid-density, lighting can be woven into the narrative description; in low-density, it must be explicitly specified in every panel.

### 5.3 Visual motif

Design 1-2 visual elements that recur throughout all panels. The motif can be: a lighting effect, a prop, a color, a compositional technique.

---

## VI. Integration with Phase 4 asset images

### Text-to-image mode (no asset references)

Write the character's/product's visual characteristics into Layer 1's Global style:

> Protagonist: a young female warrior in black armor, silver long hair, wielding a curved blade, a scar on her right cheek.

### Image-to-image mode (referencing asset images)

In Nano Banana Pro, use edit mode and upload asset images:
- Layer 1: write Global style as normal
- Layer 2: map asset images: `(Image 1) three-view character sheet of the female warrior, (Image 2) snow mountain environment concept`
- Layer 3: reference directly in per-panel descriptions: `The female warrior from Image 1 stands at the peak of the snow mountain in Image 2...`

---

## VII. Multi-grid planning strategy

Cut the video into 15-second segments, each corresponding to one 3x3 grid. **Each grid independently selects its story density.**

### Cross-grid consistency

- **Global style**: All grids use exactly the same Layer 1
- **Reference image mapping**: All grids reference the same set of asset images
- **Transition continuity**: The atmosphere of the 9th panel of the previous grid ≈ the atmosphere of the 1st panel of the next grid
- **Color continuity**: Color temperature changes across grids remain gradual, with no sudden shifts

---

## VIII. Single-frame extraction template

When the downstream video model does not support multi-grid input, extract panel by panel:

```
Generate only the storyboard image for [Row X, Column Y], maintaining exactly the same style and character appearance as the original image
```

In Nano Banana Pro, use edit mode and upload the original multi-grid image as the reference. Extract panel by panel in reading order.

---

## IX. TVC multi-grid specific approach

TVC advertising multi-grid storyboards, beyond the general approach, require additional handling of the **interweaving of Product World and Brand World**, the **closing End Frame panel**, and **cross-grid product consistency**.

---

### 9.1 Product World Grid approach

**Role**: Low-density (visually driven), each panel opens precisely with `[Shot size·Angle]:`.

**Key writing points**:
- Product angles are logically organized: from overall to detail, from exterior to interior, from static to functional state
- The lighting system is globally unified, with only minor variations in color temperature/intensity
- Background is extremely restrained: solid color gradient or pure black
- Material keywords remain consistent

**Complete example** (Action camera · Product World 9-panel grid):

```
Generate a composite image containing 9 panels, arranged in a 3x3 grid.
Using the action camera product in Image 1 as the subject. Pure black gradient background, Low-key studio lighting, cinematic product photography quality.

1. Wide shot·3/4 low-angle looking up: The action camera floats centered in the frame at a classic 3/4 angle. A softbox at 45° to the left illuminates the front of the body; rim light on the right traces the sharp light edge of the aluminum body; a cold white specular highlight reflects off the lens glass surface.
2. Medium shot·pure side, eye level: Pure side view of the action camera, showing body depth and the side button layout. The matte texture of the button surfaces is clearly visible under side light; a long, thin highlight band forms at the chamfer on the body's waistline.
3. Close-up macro·front, overhead: Extreme macro focused on the lens surface. The multi-layer coated glass displays purple-blue optical interference colors under side light; the metal ring around the lens edge reflects a ring-shaped highlight; depth of field is extremely shallow, at only millimeter level.
4. Medium shot·front, eye level: The camera screen is on, displaying a POV extreme sports interface — the viewfinder image is centered, the waterproof icon in the upper left emits a blue glow, and the recording duration digits are visible at the bottom. Screen light overflows and illuminates the front of the body.
5. Wide shot·3/4 overhead: The camera is in a floating disassembly state. The outer shell has separated upward, the lens module has rotated and unfolded forward, the waterproof seal ring floats at mid-level, and the mainboard and sensor at the bottom emit a faint green glow. Blue energy lines connect the components.
6. Medium shot·3/4 front, eye level: The product packaging box is placed at a slight 20° angle on the left of the frame. The matte black box face is printed with a silver brand logo; the camera body on the right is displayed at a Hero Shot angle; the box lid is slightly ajar, revealing the dark gray velvet interior lining.
7. Close-up·back, macro side light: Extreme macro of the heat dissipation grille on the camera's back. The cross-woven carbon fiber texture is clearly visible; each fiber bundle reflects light at a different angle; low-angle side light enhances the light-shadow relief of the texture.
8. Medium shot·front, eye level: The camera is in night mode. The indicator light on the front of the body glows with a dim red pulse. The screen displays the night vision interface at low brightness. The environment is extremely dark — only the product's own glow illuminates the surrounding area.
9. Wide shot·front, eye level: The camera rests in a stable pose at the lower-left third of the frame. Soft side light illuminates the product; the upper right leaves 40% of the frame as clean black space for post-production overlay of logo and slogan.

Maintain consistent overall style. Lighting system: Low-key dark studio lighting runs through all panels.
Visual motif: the specular highlight of the brushed aluminum texture recurs across different panels.
```

---

### 9.2 Brand World Grid approach

**Role**: Low-density (TVC default) or mid-density. Characters use the product in Brand World scenes.

**Product visibility hard rules** (non-negotiable):
- **The product must be visible in every panel** — Brand World does not mean "a scenic video without the product." In TVC, Brand World is "the world the product lives in"
- Product occupies 10%-25% of the frame, naturally integrated into the scene but must be identifiable
- The product's position in the frame must be explicitly described (`camera mounted on chest`, `camera on left wrist`, `perfume bottle on the table`)
- The glow color of the product screen/indicator lights must be written to enhance identifiability

**Key writing points**:
- In low-density: each panel opens precisely with `[Shot size·Angle]:`, precisely specifying scene, product state, and lighting
- In mid-density: each panel expands with three elements: **scene environment + character action + product state**

**Complete example** (Action camera · Brand World 9-panel grid):

```
Generate a composite image containing 9 panels, arranged in a 3x3 grid.
Live-action, cinematic photography, natural light, 16:9 landscape.

Narrative thread: An action camera follows an extreme sports athlete conquering nine extreme environments —
from sky to deep sea, from snow mountain to desert, capturing every impossible moment.

1. Ten thousand meters high altitude. The frozen moment of a skydiver leaping from the aircraft hatch, body spread wide. The action camera mounted on the chest is clearly visible, lens pointing down toward the earth, recording indicator light glowing red. Below are white clouds and a blue horizon.
2. Deep sea canyon. A diver descends vertically along a coral cliff face, bubbles kicked by the fins rising upward. The action camera screen on the left wrist glows green in the blue underwater light, displaying depth data. Sunlight refracts through the water surface into rippling light patches.
3. Alpine ski resort. A skier carves a high-speed turn, launching an arc of snow spray. Body extremely low and tilted. The action camera mounted on the helmet top captures the POV angle; snow particles sparkle in backlight like shattered diamonds.
4. A vertical rock face. Close-up of the moment a climber grips a hold with one hand, knuckles white. The action camera on the wrist is pressed close to the rock face; the lens has faint chalk dust and sweat drops; the background is an out-of-focus abyss.
5. Desert Gobi. A motocross bike leaps to the apex of a sand dune, the rider and bike completely airborne. Sand is blasted from the wheels, forming a golden dust trail. The action camera mounted on the handlebars is lit by the setting sun; the aluminum body reflects an orange-gold glow.
6. Whitewater canyon. A kayaker threads white-water rapids; water splashes violently in front of the lens. The action camera mounted on the bow is covered in water droplets; the droplets refract sunlight into micro-prism effects.
7. City nightscape. The moment a parkour athlete leaps from a rooftop edge. Below are neon-lit city skylines; the screen of the chest camera glows in harmony with the city lights.
8. Blizzard ridge. A mountaineer trudges through a whiteout snowstorm, ice crystals striking the face mask. The action camera held in a gloved hand is still recording; the indicator light blinks stubbornly red in the wind and snow.
9. Mountain summit at sunrise. An athlete stands at the peak looking back at the path traveled; golden morning light surges from behind. The action camera is raised toward the sunrise; the screen reflects the entire golden sky.

Maintain consistent overall style. Visual motif: the product's red recording indicator light persists in each extreme environment.
Color arc: gradually shifts from the cold blue of panel 1's high-altitude sky to the warm gold of panel 9's sunrise.
```

---

### 9.3 Crosscut Grid approach

**Role**: Within the same grid, mixes "Brand World" and "Product World" panels to simulate TVC crosscut editing rhythm.

**Key writing points**:
- Odd-numbered panels (1/3/5/7) are Brand World scenes — high/mid density, character uses product
- Even-numbered panels (2/4/6/8) are Product World close-ups — low density, precise cinematography directions
- Panel 9 is always the End Frame
- Design visual transitions between adjacent panels (shape match / color match / texture match)

**Complete example** (Action camera · Crosscut 9-panel grid):

```
Generate a composite image containing 9 panels, arranged in a 3x3 grid.
Cinematic photography, 16:9 landscape.
Brand World panels are live-action with natural light; Product World panels are Low-key studio light on pure black background.

(Image 1) Action camera product reference image.
Brand World and Product World alternated: odd panels are usage scenes, even panels are product close-ups, panel 9 is the closing freeze frame.

1. Backlit ski slope. Frozen moment of a skier carving a high-speed arc.
Snow spray curls like a white wave wall; the action camera on the helmet glints in the sunlight.
2. Medium shot·3/4 side: Pure black background. The body arc chamfer of the Image 1 action camera in close-up.
Side light traces a smooth curved surface similar to the arc of the snow wave; brushed aluminum texture reflects a cold white highlight.
3. Above the sea. Diver in a backward somersault entry, body curled.
A circular crown of water splashes surrounds; the action camera mounted on the waist is about to submerge.
4. Close-up·straight overhead: Pure black background. Action camera lens shot overhead.
Circular lens outline centered; multi-layer coating reflects blue-purple optical colors similar to the sea water; water droplets remain on the lens edge.
5. Desert dusk. Motocross silhouette leaping over a sand dune.
Behind is a blazing orange-gold sunset; the action camera mounted on the handlebars is gilded by the setting sun.
6. Medium shot·side, eye level: Pure black background. Warm gold side light sweeps from the left across the aluminum body.
Surface takes on the same amber gold tone as the desert sunset; the highlight band of material texture flows slowly.
7. Vertical rock face. Extreme close-up of the moment a climber grips rough rock with fingertips, knuckles white.
The action camera on the wrist is pressed to the rock face; background is an out-of-focus abyss.
8. Close-up·straight front macro: Pure black background. Extreme macro of the anti-slip rubber grip zone on the product's side.
The diamond tread pattern has a roughness similar to the rock surface;
low-angle side light delineates the highlight of each raised ridge and the shadow of each groove.
9. Wide shot·front, eye level: Pure black gradient background. The action camera rests at its best angle at the lower-left third of the frame.
Soft side light illuminates the product; upper right has generous whitespace for logo and slogan overlay.

Maintain consistent overall style. Odd panels maintain live-action natural light quality; even panels maintain Low-key studio product photography quality.
The two worlds are linked through visual transitions of shape/color/texture.
```

---

### 9.4 End Frame panel

**Overall principle**: Layout depends on brand guidelines — both **product centered** (Hero Pose) and **product offset with whitespace** are valid approaches.

**Core rules**:
1. The composition must leave space for post-production text (approximately 30%-40% clean area)
2. Product state must be the "final state": screen on, exterior intact, posture stable and calm
3. Lighting is clean and refined. Do not write logo/slogan text content — only describe the whitespace area

**End Frame panel prompt template**:

```
[Panel number]. [Shot size]·[Angle]: [Background description], [product name] rests [angle/pose] at [position in frame],
[product final state description]. [Clean lighting]. 
[Whitespace area position] leaves [percentage]% of the frame as clean space, background gradient is smooth with no clutter.
```

**Example**:

```
9. Wide shot·front, eye level: Deep space gray gradient background. The action camera rests at a 3/4 low angle at the lower-left third of the frame.
Screen displays the brand's primary blue interface; all indicator lights glow faintly. Soft left side light illuminates the product,
forming a natural shadow transition on the right. The upper-right of the product leaves 40% of the frame as clean space, background gradient smooth with no clutter.
```

---

### 9.5 TVC multi-grid planning example

The following example shows how a 30-second TVC (action camera) uses 2 grids to cover the complete content.

**Project information**:

| Dimension | Content |
|------|------|
| Product | Professional action camera |
| Duration | 30 seconds |
| Narrative model | Brand World traversal (Model C) |

**Grid planning overview**:

| Grid | Time segment | Type | Story density | Narrative function |
|------|------|------|---------|---------|
| G1 | 0-15s | Brand World Grid | Low-density | Extreme sports scene montage |
| G2 | 15-30s | Product World Grid + End Frame | Low-density | Multi-angle studio product display + closing |

**Cross-grid consistency checklist**:

- [ ] **Global style**: G1 and G2 use the same image quality anchor
- [ ] **Reference image**: Both grids reference the same product reference image (`Image 1`)
- [ ] **Transition continuity**: G1 panel 9 color tone → G2 panel 1 color tone, color temperature continuous
- [ ] **Product description**: Material keywords for the product are completely consistent across both grids
- [ ] **Product color**: Product color scheme descriptions are consistent across all panels

---

### 9.6 Product consistency maintenance

When a product appears across multiple grids in a TVC, its visual consistency must be maintained.

#### Rule 1: Lock the product description template

```
Standard product description template:
[Product name], [core material A] + [core material B] body,
[color/color scheme], [key design feature 1], [key design feature 2],
[size/proportion characteristics].
```

Example:
```
Standard product description:
XX Pro action camera, brushed aluminum body + carbon fiber rear shell,
deep space gray color scheme, front ultra-wide lens module (circular, multi-layer coated),
three red functional buttons on the side, body is square and sturdy, palm-sized.
```

#### Rule 2: Unified lighting keywords

Product World panels for the same product across different grids should use the same set of lighting vocabulary (primary light direction, rim light direction, material highlight description terms, and color temperature baseline all globally consistent).

#### Rule 3: Standardized angle descriptions

The same angle across grids must use exactly the same angle description text — you cannot write `slight overhead` in G1 and `30° from above` in G2.

#### Rule 4: Minimum product description requirements in Brand World

Even if the product occupies only 10% of the frame, four information points must still be included: product mounting position, material keywords, functional state hint, and product color scheme.

#### Rule 5: Global reference to product asset image

All grids must reference the same product asset image; different product reference images may not be used.

#### Rule 6: On-screen character wardrobe consistency

When a character appears on screen in Brand World panels (whether full body / lower body / from behind / silhouette), the character's wardrobe description must be completely consistent across all grids. The **standard character description** established during pre-production is the sole authority — it must be reused every time a character is involved; you cannot write "black shorts" in G1 and "black trousers" in G2. Style, color, and material — the three wardrobe elements — cannot change across panels; only pose and action may vary.

#### Rule 7: No figurative language

Multi-grid prompts **must not use metaphors, personification, analogies, or other figures of speech**. AI image models interpret text literally — "like a sculpture" will generate a plaster-textured human figure, "like a garden" will generate flowers and plants, "like silk" will change the material rendering.

| Incorrect | Problem | Correct |
|---------|------|---------|
| Passerby frozen **like a sculpture** | Model may generate a plaster/marble human figure | Passerby remains still in a walking pose, expression frozen, coat hem suspended in motion |
| Moving through the papers **like picking flowers** | Model may generate floral elements | Reaching up to pluck suspended papers from the air one by one |
| Droplet **like an amber bead** | Model may render the droplet as amber-colored solid | Droplet is semi-transparent and dark in light, surface reflecting highlights |

Principle: **Describe what you want, not what it resembles.**

#### Rule 8: Multi-grid only describes state, not process

Multi-grid storyboards are static key frames; each panel can only describe **the state of the image at one point in time** — it cannot describe a dynamic process. Verbs must be static (floating, still, resting, frozen) rather than process-oriented (flying out, surging out, splashing up, falling). Process-oriented actions are left to video prompts.

| Incorrect (process state) | Problem | Correct (result state) |
|----------------|------|----------------|
| Coffee cup **flies out of hand**, liquid **starts to overflow** from the rim | "flies out" and "overflow" are dynamic processes; a static frame cannot express them | Coffee cup is suspended in mid-air; liquid is frozen into an arc, cup facing downward |
| Red wine **starts to surge** from the rim, forming a curve **about to cascade** | "surge" and "cascade" are in-progress actions | Red wine column is suspended between the tilted wine glass and the table, liquid surface reflecting candlelight |
| Papers **flutter** in the air | "flutter" is dynamic | Dozens of papers are suspended in the air at various angles |

This rule complements "Division of labor for dynamic effects": the division of labor resolves "what to write," and this rule resolves "how to write it."

---

## Part 2: Video prompt syntax

---

## I. Video prompts vs static keyframe prompts

Core conversion idea: turn "what it is" into "how it changes."

| Dimension | Static keyframe | Video prompt |
|------|-----------|-----------|
| Time | None | Has time codes, precise to the second |
| Subject | Frozen state/pose | Process in motion (action + change) |
| Camera | Fixed shot size + angle | Camera movement trajectory (push/pull/arc/follow) |
| Shot transition | None | Transition direction (hard cut/dissolve/Match Cut) |
| Lighting | Fixed light source direction | Lighting changes over time (gradient/flicker/day-night) |

---

## II. Video prompt writing logic and format

Video prompts follow a three-part logic. **Output uses natural language** — do not use terms like "style envelope" or "continuity directive."

### Part 1: Style and constraint declaration

**Must cover**: Visual style, color tone, constraints, **"No background music" (required)**, **product@product multi-view image**.

> **Video model dual-image input**: The video model receives two images — the multi-grid storyboard image (first frame) + the product multi-view image (product anchor). At the end of the style declaration, reference the product multi-view with `product@product multi-view image advertisement` to let the model understand the product's appearance. The `(Image 1)(Image 2)` reference image mapping is syntax for multi-grid prompts (image generation phase) and is not used in video prompts.

> **Audio iron rule**: Video models generate BGM by default — if not specified, there will be BGM. When multiple segments are spliced together, the BGM from each segment breaks at the seam. BGM is laid as a separate audio track in post-production. Character dialogue in shot descriptions is marked in quotation marks.

> **Do not write post-production directives**: Video prompts only describe image content that the video model can generate. The following are post-production tasks and must not appear in video prompts: logo/brand identity overlay, slogan/text fade-in, color grading directives, sound design, subtitle layout. In a video prompt, the End Frame only needs to describe pure visual states such as "product centered, freeze frame, clean whitespace." Space reserved for logo and slogan is the responsibility of the multi-grid image prompt (End Frame panel).

**Output example**:
> Style: dark fairy tale farewell scene / high-contrast red-black forest tones / stop-motion animation quality / strong opposing light sources (white light inside door vs. red forest outside) / delicate close-up expressions / emotionally restrained farewell atmosphere / no subtitles / no background music product@product multi-view image advertisement

### Part 2: Shot script

Two formats — choose based on the target video model:

#### Format A: Compact shot list

```
Shot 1 [0-2s] [Medium shot] A massive tree door is set into a thick tree trunk, surrounded by a red forest. The little girl and the little mouse stand side by side before the door, the girl bowing her head slightly, the mouse looking up at her.
Shot 2 [2-4s] [Close-up] The little mouse raises a small paw and waves, "squeak squeak" — a soft farewell. The girl and mouse look at each other, her expression gentle but reluctant.
Shot 3 [4-7s] [Medium shot] The girl slowly turns and walks toward the tree door, extending a hand to push it. The gap in the door radiates an intense white light, casting her silhouette. She walks two steps and stops, looking back at the little mouse.
...
```

#### Format B: Detailed segmented description

```
[0-3s: Mountain origins, green grapes rolling]
Camera: Camera slowly pushes in from a wide shot, then cuts into a macro tracking shot.
Frame: The visual baseline is a black-and-white minimalist mountain wilderness. A line-drawing girl with a bamboo basket on her back walks into the frame holding a shovel.
      As she climbs onto a rock, the bamboo basket tilts behind her and several line-drawn fruits roll out.

[4-7s: Pink poured in, fruit fragrance awakens]
Camera: Camera shoots from a low angle looking up, then pans rapidly downward following the trajectory of the liquid.
Frame: A large realistic transparent cup stands on a mountain rock; the bottom is already filled with fresh green grapes.
      Suddenly, a stream of pink peach juice with real luminosity pours down from above like a waterfall...
```

### Part 3: Transitions and throughlines (naturally integrated)

Two treatment methods:

1. **Integrated into each shot description**: Naturally mention transitions and throughline elements within each shot's description
   > Shot 1 [0-2.5s] [Wide shot·backlit] (corresponds to P1) **Dissolve carries over from the end of the previous segment.** Fixed camera. Three cow silhouettes walk slowly to the right in golden morning light...

2. **Appended note at the end** (only when there is a large amount of information):
   > The full piece uses hard cuts as the primary transition, with dissolves for establishing shots. Golden rim light continuously traces the edges of cattle in every shot. The warm golden ranch wide shot of P9 transitions naturally into the next segment.

---

## III. Per-shot description formula

### Seven-element formula

```
[Time code][Shot size + Angle] + [Camera movement] + [Subject action] + [Environment/lighting change] + [Character dialogue (if any)] + [Transition direction]
```

### Writing tips

- **Verbs are king**: The core of a video prompt is the verb — sweep across, rise, rotate, push in, billow, dissipate
- **Gradual beats sudden**: Use "gradually," "slowly," "progressively" to describe the change process
- **Specific beats abstract**: `rotates 30°` is better than `slowly rotates`
- **Causal chain**: Camera movement triggers subject change; subject change influences lighting response
  - Example: `product pushes toward the lens` → `smoke billows and spreads with the push speed` → `warm light gradually shifts to deep golden tones`

---

## IV. 15-second standard pacing

### Four-segment pacing model

| Segment | Duration | Function | Rhythm |
|------|------|------|------|
| **Establishing** | 0-3s | Establish scene/atmosphere | Slow |
| **Development** | 3-7s | Unfold narrative/display | Medium |
| **Climax** | 7-12s | Emotion/action peak | Fast |
| **Closing** | 12-15s | Whitespace/coda/CTA | Decelerate |

### Non-standard pacing

| Variant | Structure | Use case |
|------|------|------|
| **Slow burn** | 5s establishing + 5s development + 3s climax + 2s close | Atmospheric shorts, art films |
| **Impact** | 1s establishing + 4s development + 8s climax + 2s close | Action films, game CG |
| **Loop** | Establish→climax→establish→climax→close | Music MV, rhythm-driven |
| **Flashback** | Climax→flashback development→return to climax→close | Suspense, twist narratives |

---

## V. Multi-grid reference format

Video prompts can directly reference panel positions from the multi-grid image:
- By panel number: `(corresponding to storyboard panel P1)`, `(corresponding to P5-P7)`
- By row-column position: `(corresponding to Row 2, Column 3)`

Reference example:

```
Shot 1 [0-2s] [Wide shot·overhead] (corresponds to P1) Product rests centered in the frame; warm gold side light sweeps slowly...
Shot 2 [2-4s] [Medium shot·side low-angle] (corresponds to P2) Product rotates slowly, facets reflecting changing light and shadow...
```

Multiple panels corresponding to a single shot:
```
Shot 3 [4-8s] [Medium shot·eye level] (P3→P4 transition) Product pushes toward the lens, scene gradually shifts from the P3 state to P4...
```

---

## VI. Cross-segment continuity for multi-segment video

### Cross-segment consistency elements

| Element | Requirement |
|------|------|
| **Style declaration** | All segments share the same style and constraint declaration |
| **No background music** | Must be written for every segment |
| **Character appearance** | Maintained by referencing the same asset image |
| **Color continuity** | End color tone of previous segment ≈ opening color tone of next segment |
| **Motion continuity** | Character movement direction does not jump between segments |

### Segment independence

Each video prompt segment is fed into the video model individually; the model has no knowledge of other segments. Each segment's Phase numbering starts from Phase 1 and the time code starts from 0s — these do not carry over from the previous segment. Do not reference events from other segments within a segment's description (e.g. "back to the earlier balcony," "everything as before," "more soft mist compared to the previous segment"). Cross-segment consistency is achieved by repeating the same style declaration and product description, not by text references.

### Segment transition types

Transition types describe the **editing-level** visual transition strategy (used to guide post-production splicing) — they are not instructions to reference other segments in the text:

| Transition type | Use case |
|---------|------|
| **Action carry-over** | Continuous narrative |
| **Atmospheric continuation** | Emotional shorts |
| **Scene jump** (fade out/fade in) | Multi-scene narratives |
| **Callback echo** | Loop/elevation narratives |

---

## Part 3: Cinematic Product Breakdown

---

### I. Video prompt structure

TVC product videos use a Multi-Phase structure.

#### Standard Phase structure

```
 [Number] ([Start]s-[End]s): [Phase name]
├─ Camera movement: [movement method + speed + direction]
├─ Product state: [current product form/dynamic change]
├─ Feature reveal: [core selling point demonstrated in this phase]
├─ Lighting design: [light source type + direction + change]
├─ Material focus: [material/quality emphasized in this phase]
└─ Visual effects: [particles/energy flow/digital overlay, etc.]
```

#### Pacing principles

| Phase type | Typical duration | Rhythm | Role |
|---------|---------|------|------|
| Suspense opening | 1-2s | Extremely slow / static | Build anticipation, hint at product silhouette |
| Disassembly/unfolding | 2-3s | Slow → accelerating | Show internal structure, convey technical depth |
| Feature activation | 1-2s | Burst | Screen Activation, Digits Ticking, Sensor Glow |
| Burst rotation | 1-2s | Fast | 360° full-surface product display |
| Macro dive | 1-2s | Ultra-slow | Material quality finale, establish premium feel |
| Brand freeze frame | 1-1.5s | Static | Logo + Slogan + product final pose |

#### Format requirements

- **Style declaration** always ends with "No background music"
- **Phase numbers** start from 1 and increment; exact seconds are noted in parentheses
- **Seconds are continuous**: the end second of the previous Phase = the start second of the next Phase, no gaps or overlaps

---

### II. Component disassembly/assembly animation

#### 1. Floating Disassembly

```
The product floats centered in the frame; components begin to slowly separate —
the outer shell shifts and floats to the upper left,
the lens module rotates and separates to the right,
the mainboard floats and unfolds downward,
the battery pack slides out to the rear.
Faint blue energy lines connect all components, suggesting internal coordination.
Background is pure black; component surfaces are precisely outlined by side light.
```

#### 2. Exploded View

```
The product instantly explodes open; all components radiate outward from the central axis to their positions —
Top: lens component floats and rotates; glass lens refracts rainbow light patches;
Middle: mainboard and chipset expand horizontally; circuit traces emit faint green pulse light;
Bottom: battery module and thermal system sink vertically; metal heat fins reflect sharp silver highlights.
The overall composition is a symmetrical Exploded View with a strong industrial design aesthetic.
```

#### 3. Precision Assembly Snap-back

```
Components begin high-speed convergence — the thermal module locks in first, causing a micro-vibration of metal contact;
the mainboard slides precisely into its slot, circuits instantly lighting up with pulse light;
the lens module rotates and threads in,
a streak of highlight flashes across the glass surface;
the outer shell snaps closed last, a white light flash at the seam —
the product returns to its complete form, surface gleaming like new.
```

**Pacing note**: Disassembly takes 2-3 seconds (slow); Precision Assembly Snap-back takes 0.8-1.2 seconds (fast). The speed contrast creates impact.

---

### III. Feature visualization design

#### 1. Screen Activation

```
The product screen starts from a completely black state;
a single pixel lights up from the center,
its glow spreading outward in ripples;
screen content gradually emerges —
interface elements appear in sequence, icons sliding in from below;
the screen's glow illuminates the front of the product and surrounding environment,
casting a colorful screen reflection on the tabletop.
```

#### 2. Digits Ticking

```
The frame focuses on the product screen; digits begin rapid jumping —
the number next to the battery icon climbs at high speed from 00:00:00,
digits rolling like an old flip clock, each digit with faint motion blur;
finally freezing at 04:00:00, digits pulsing with a golden glow —
suggesting extended battery life. The entire sequence completes in 1.5 seconds.
```

#### 3. Sensor Glow

```
The sensor area on the product's surface begins emitting faint light —
the infrared sensor lights up with a dim red pulse;
the LiDAR emits green scanning lines;
multiple sensors activate in sequence, their light points fading in and out like breathing —
suggesting the product is sensing its surroundings. Light forms colorful reflections on the product's metal surface.
```

#### 4. Energy Flow

```
A blue energy line is injected from the charging port,
flowing at high speed along the circuit board trace paths inside the product,
branching, converging, and branching again — illuminating the chips and components along the way;
finally converging into the battery module, the battery icon shifting from red to full green,
emitting an expanding pulse wave of energy.
```

---

### IV. Material macro system

#### Material macro quick reference

| Material type | Macro description keywords | Lighting pairing |
|---------|-------------|---------|
| Brushed metal | Dense parallel brush marks, each scratch reflecting light at a different angle | Side light at 45°, slow sweep |
| Glass refraction | Light refracts into rainbow dispersion after passing through; edge micro-prism effect | Backlight / transmitted light |
| Carbon fiber weave | Cross-weave forming a regular diamond pattern | Low-angle side light |
| Liquid fluid | Viscous liquid flowing slowly, liquid surface reflecting like a mirror | Top light + ambient reflection |
| Ceramic glaze | Warm and lustrous like jade; micro-bubbles faintly visible beneath the glaze layer | Soft diffused light |
| Leather texture | Pores, creases, and wear marks; hand-stitched edges | Warm side light |
| Anodized aluminum | Fine matte texture; subtle color shifts at different angles | Gradient light sweep |

#### Material macro camera movement

```
The lens approaches the product surface to extreme macro (simulating a macro lens at 1:1 magnification ratio),
slowly gliding along the direction of the material's texture;
depth of field is extremely shallow, with only a millimeter-level focal plane;
the focus shifts as it glides, sequentially revealing different layers of material detail —
from brush marks to chamfer highlights to seam precision;
finally the lens slowly pulls out, material details gradually converging into the product's complete silhouette.
```

---

### V. Five/Six-stage pacing model

Standard pacing for a pure product showcase TVC:

```
Ultra-slow reveal → Floating Disassembly → Precision close-up → Feature activation → Macro dive → Brand freeze frame
```

| Stage | Rhythm | Camera movement | Product state |
|------|------|------|---------|
| **Ultra-slow reveal** | Extremely slow / static | Fixed → micro push | Rim light gradually traces outline from full black |
| **Floating Disassembly** | Slow → accelerating | Arc orbit | Components separate, interior exposed |
| **Precision close-up** | Burst | Multi-angle rapid cut | Components snap back at high speed |
| **Feature activation** | Medium pulse | Push in to close-up | Screen Activation / Sensor Glow |
| **Macro dive** | Ultra-slow | Macro glide | Material micro-detail magnified |
| **Brand freeze frame** | Static | Snap pull-back → freeze | Product in perfect form + logo |

#### Inter-phase transition design

- Ultra-slow reveal → Floating Disassembly: rim light illuminates full product → components "breathe" with micro-vibration → separate
- Floating Disassembly → Precision close-up: components pause 0.3s in silence → suddenly accelerate snap-back
- Precision close-up → Feature activation: snap-back moment produces a white light flash → screen spreads from that light point
- Feature activation → Macro dive: screen pixel → lens penetrates → enters the material micro world
- Macro dive → Brand freeze frame: material texture gradually blurs → snap pull-back to wide shot

---

### VI. Complete Multi-Phase product video examples

#### Example 1: Action camera (10 seconds, 5 Phases)

**Product**: High-end action camera, highlighting waterproofing, ultra-wide angle, superior stabilization

```
Phase 1 (0s-2s): Dark suspense reveal
Camera movement: Static → micro push
Product state: Against a pure black background, a sharp rim light begins glowing from the product's edge, slowly tracing the square silhouette of the action camera.
Lighting design: Rim Light traces a 270° arc from behind; the front is nearly all black — only the outline is visible.
Material focus: As the rim light sweeps past, the brushed aluminum body texture is faintly visible.

Phase 2 (2s-4s): Floating Disassembly
Camera movement: Arc orbit, from front to 3/4 overhead
Product state: Camera components begin to float and separate — the waterproof outer shell drifts upward, revealing the precise internal structure;
the ultra-wide angle lens module rotates and separates forward, the multi-layer coated glass refracting rainbow light patches;
the OIS gyroscope module floats and rotates on display. Blue energy lines connect all components.
Lighting design: Side light gradually rises, precisely illuminating each separated component.
Feature reveal: Multi-layer coating structure of the ultra-wide angle lens; the OIS gyroscope module.

Phase 3 (4s-5.5s): Feature activation
Camera movement: Fast push in to screen close-up
Product state: Components snap back at high speed (0.5s), outer shell snaps shut with a white light flash;
rear screen instantly lights up, interface displays a POV extreme sports view (first-person skydiving perspective);
waterproof icon in the upper left of the screen glows blue.
Lighting design: Screen glow becomes the primary light source, illuminating the front of the product and surrounding environment.
Feature reveal: Screen display quality; waterproofing capability hinted.

Phase 4 (5.5s-7.5s): Burst rotation
Camera movement: High-speed 360° arc orbit
Product state: Camera floats centered in the frame, rotating at high speed to display all surfaces —
front lens, side buttons, bottom tripod mount, top record button.
Each surface is successively illuminated by a tracking light during rotation.
Lighting design: Tracking light rotates; highlights always lock onto key features as they rotate past.
Material focus: During rotation, the contrast between the brushed aluminum texture and the rubber anti-slip grip zone is clearly visible.

Phase 5 (7.5s-10s): Macro dive + Brand freeze frame
Camera movement: Ultra-fast push into the lens glass surface → penetrate the lens assembly → snap pull-back to wide shot
Product state: Lens dives into the inside of the camera lens, passing through multi-layer coated glass (light refracts and disperses between the elements),
```

```
passes over the CMOS sensor surface (pixel array macro), then snaps back to a wide shot —
product floats centered in the frame; brand logo and slogan emerge below.
Lighting design: Internal light refracts during penetration; after pulling back, returns to Low-key studio lighting for the freeze frame.
Material focus: Optical dispersion of the lens coating; micro pixel array of the CMOS sensor.
```

#### Example 2: Luxury serum (10 seconds, 5 Phases)

**Product**: High-end skincare serum, highlighting gold ingredients, luxurious quality, anti-aging repair

```
Phase 1 (0s-2s): Luxury curtain reveal
Camera movement: Slow tilt down
Product state: At the top of the frame, against a pure black background, a drop of golden serum slowly falls.
The droplet surface reflects the entire surrounding environment; the liquid is viscous and full,
with a honey-like filament quality. The falling droplet leaves a golden light trail.
Lighting design: A single overhead spotlight tracks the droplet — the droplet appears like a tiny golden planet.
Material focus: The viscosity of the serum, surface tension, luminous refraction.

Phase 2 (2s-4s): Bottle appears
Camera movement: Arc orbit, from side to 3/4 front
Product state: The golden droplet falls into the serum bottle opening below, ripples spreading outward;
camera tilts down to reveal the entire bottle — frosted glass body, golden liquid moving gently inside;
the metal cap reflects sharp highlights; the bottle body has embossed brand patterns.
Lighting design: Side light at 45° from the left; the glass body produces translucent light and shadow layers;
the liquid inside refracts warm amber light.
Material focus: Semi-transparent quality of the frosted glass; mirror reflection of the metal cap.

Phase 3 (4s-6s): Liquid flow macro
Camera movement: Extreme macro push into the bottle's glass surface
Product state: Lens approaches the bottle body, penetrating the frosted glass layer and entering the liquid world inside —
tiny gold leaf particles float and flow within the golden serum,
forming slow convection vortices; gold leaf glints in the light.
Lighting design: Back-transmitted light passes through the liquid; gold leaf particles appear like floating stars.
Feature reveal: Visualization of golden micro-particle active ingredients.

Phase 4 (6s-8s): Skin imagery
Camera movement: Steady lateral slide + shallow focus transition
Product state: Frame transitions to an abstract macro skin image — a smooth skin texture surface.
A drop of serum lands on the skin, rapidly penetrating and spreading; the spreading path emits a faint golden glow;
the skin texture becomes smoother and finer as it spreads (visual metaphor: anti-aging repair).
Lighting design: Soft warm diffused light; SSS subsurface scattering effect on the skin surface.
Feature reveal: Visualization of penetration absorption and skin repair effects.

Phase 5 (8s-10s): Brand freeze frame
Camera movement: Slowly pull back to medium shot, freeze
Product state: The product bottle is placed slightly right of center in the frame; a dried flower/gold leaf serves as foreground accent on the left.
The bottle body is lit by warm side light; background is a dark gradient (deep brown → black).
Brand logo elegantly emerges on the left side of the frame; slogan lines below in a thin serif font.
Lighting design: Classic beauty advertising lighting — soft primary light + side rim light + bottom fill light.
```

#### Example 3: Avant-garde silver bracelet (10 seconds, 5 Phases)

**Product**: Hand-forged silver bracelet, highlighting independent attitude, craft quality, avant-garde design
**On-screen strategy**: Character present — female wrist/hand close-ups (no face), wearing minimal black clothing, clean skin

```
Phase 1 (0s-2s): Craft origin — forging
Camera movement: Macro static → slow push
Product state: Pure black background. A raw rough silver block in the center of the frame. Side light slowly rises,
tracing the hammer-mark texture on the silver block's surface. The block's edges begin to radiate a faint heated red glow —
suggesting it was just taken from the forge. Irregular depressions from hand-hammering are visible on the surface;
each mark is the craftsman's signature.
Lighting design: Single-side hard light, emphasizing the roughness of the silver block. Faint red light penetrates upward from the bottom.
Material focus: The granular texture of raw silver; the irregular texture of hammer marks.

Phase 2 (2s-4s): Transformation — from raw silver to finished piece
Camera movement: Fast push → dissolve transition
Product state: Lens fast-pushes into the silver block surface macro — silver grains fill the frame;
dissolve transitions to the finished bracelet's macro close-up: the same silver, but the surface has been polished to
a matte brushed finish; the hinged structure between links casts precise shadows under side light.
Lighting design: Light source direction is consistent before and after the transition (side light), achieving material change but lighting continuity.
Material focus: Matte brushed silver surface; the precise gap at the link hinge.

Phase 3 (4s-6s): Wearing — wrist appears
Camera movement: Slow pull back → micro arc shift
Product state: Lens slowly pulls back from the bracelet macro; the silver chain gradually comes fully into view —
it encircles a woman's wrist. The wrist slowly rotates; the silver chain flows with the gesture;
links produce subtle metallic glint reflections. The wrist skin is clean, nails colorless;
the edge of a black sleeve just reveals the wrist.
Lighting design: Side light enters from one side of the wrist; silver chain reflections form flowing light bands; skin tones in warm ivory.
Material focus: Tactile contrast between silver and skin — cold hard metal against warm skin.

Phase 4 (6s-8s): Attitude — avant-garde stance
Camera movement: Tracking hand movement
Product state: Hand rises slowly from the bottom of the frame; fingers slightly spread in a relaxed pose —
the silver chain on the wrist droops naturally with gravity, one side close to the skin, the other hanging naturally.
The palm lightly clenches and then opens; the silver chain shifts slightly on the wrist, light and shadow changing.
Background transitions from pure black to blurred concrete gray — suggesting an architectural aesthetic space.
Lighting design: Side light remains primary; faint ambient scattered light appears in the background.
Dynamic focus: Natural drape and flowing light of the silver chain with the gesture.

Phase 5 (8s-10s): Freeze frame
Camera movement: Slow push back to macro → still
Product state: Wrist is still, slightly left of center in the frame; silver chain rests naturally at the wrist's narrowest point.
Lens slowly pushes to a silver chain close-up — final freeze frame on a single link macro:
matte brushed surface, precise gap at the hinge, silver outline traced by side light.
The right side of the frame has generous whitespace for brand identity placement.
Lighting design: Returns to the single-side hard light of the opening, creating a beginning-to-end echo. Frame is clean, restrained, with sufficient whitespace.
```

---

## Part 4: Brand World shots

---

### I. Brand World ↔ Product World switching techniques

Brand World is the product's usage context; Product World is studio close-ups. The two worlds alternate repeatedly in a TVC — the quality of the switching determines the sophistication of the ad.

#### Three core switching techniques

##### Technique 1: Match Cut motion transfer

**Brand World → Product World**:

```
[Brand World] The skier launches off the slope, body spinning in the air —
at the moment of reaching 180° of rotation, cut seamlessly to —
[Product World] The product appears against a pure black background with the same angular velocity of rotation,
continuing the momentum to complete a 360° display, decelerating to a freeze frame at the 3/4 side angle.
```

**Product World → Brand World**:

```
[Product World] The product screen lights up, glow spreading outward to all edges of the frame —
at the moment the glow fills the entire frame, cut seamlessly to —
[Brand World] A vast snow mountain panorama gradually reveals from the white overexposure;
an off-road vehicle races through the snow, the white snow spray seamlessly matching the white of the screen glow.
```

**Prompt template**:
```
[Subject of the previous world] is performing [specific movement] in the frame —
at the moment [movement reaches a specific position/angle/speed], cut seamlessly to —
[next world] continues the momentum with the same [movement direction/angular velocity/velocity vector],
[subsequent frame development]. The [shape/movement trajectory/speed] of the two frames perfectly matches; the shot flows without interruption.
```

##### Technique 2: Scale Shift

**Macro → Micro**:

```
[Brand World] Aerial shot looking down on the city night, thousands of lights twinkling —
the lens dives rapidly toward one glowing point in the city —
[Product World] After piercing through layers of scale, the glowing point becomes a single pixel on the product screen,
the lens stabilizes in a product screen macro; interface details clearly visible.
```

**Micro → Macro**:

```
[Product World] Lens pressed close to the product surface in macro; material texture fills the frame —
the lens suddenly snaps back, pulling away at extreme speed —
[Brand World] Product texture gradually morphs into aerial ground texture (desert cracks / farmland geometry),
revealing the product is situated within a vast natural landscape.
```

##### Technique 3: Medium Penetration

**Penetrating the product → Emerging into Brand World**:

```
[Product World] Lens facing the front of the lens assembly, beginning to slowly push in —
passing through the first layer of coated glass (rainbow dispersion appears on the surface),
passing through the second lens element (light refracts and bends),
passing through the CMOS sensor array (the micro world of the pixel matrix) —
[Brand World] After emerging, the frame is a magnificent landscape as seen from the camera's perspective,
suggesting "the world as seen through the product's eyes."
```

**Brand World → Penetrating the product**:

```
[Brand World] The serum slowly drips from a fingertip —
at the moment the droplet falls into the bottle opening, the lens follows the droplet into the bottle —
[Product World] Enters the micro world of liquid inside the bottle;
gold leaf particles float and flow like stars in amber-colored liquid.
```

#### Switching frequency and rhythm control

| Video duration | Recommended switch count | Rhythm strategy |
|---------|------------|---------|
| 10s | 1-2 times | Brand World open → Product World close |
| 15s | 2-3 times | Brand → Product → Brand → freeze frame |
| 30s | 4-6 times | Free traversal; Brand World leads in first half, Product World leads in second half |

**Switching rhythm principles**:
- After each switch, stay in the new world at least 2-3s before switching back
- The final switch must be **into Product World** — the ultimate landing point of a TVC is always the product itself

---

## Part 5: TVC Duration Templates

---

### I. TVC 30s dual-segment pacing template

#### Template A: Brand World traversal 30s

```
═══ First segment (0-15s): Brand World leads, establishing emotion ═══

Phase 1 (0-3s): Brand World opening
  Wide-angle establishing shot of extreme sports/lifestyle scene, establishing the world-view and energy.
  Fast-paced camera movement (aerial/tracking/handheld), subject in motion.

Phase 2 (3-6s): Product first appearance
  [Match Cut] Scene motion → product rotation.
  Product slowly arcs on display at a 3/4 angle; rim light traces its form.
  First reveal of the product in full.

Phase 3 (6-10s): Brand World escalation
  [Match Cut] Product material texture → scene element texture.
  Scene escalates (more extreme/more dynamic/more emotional);
  product appears naturally in use (handheld/worn/integrated into environment).

Phase 4 (10-15s): Feature reveal + inter-segment bridge
  [Match Cut] Scene action → product feature activation.
  Product feature visualization: Screen Activation / Sensor Glow.
  Closing action leaves a bridge point for the next segment (e.g., mid-rotation / mid-glow, not concluded).

═══ Second segment (15-30s): Product leads, closing brand ═══

Phase 5 (15-19s): Carry-over + deep disassembly
  Carries over the momentum from the end of the previous segment. Product Floating Disassembly;
  components separate to display internal structure, conveying technical depth.

Phase 6 (19-23s): Precision close-up + burst rotation
  Components snap back at high speed → burst 360° rotation display.
  Speed goes from ultra-fast (snap-back) to fast (rotation) to gradually slower.

Phase 7 (23-27s): Macro dive
  Lens dives into the product surface macro — material texture, chamfer precision,
  reflection and refraction of light on the surface. Ultra-slow camera movement, quality finale.

Phase 8 (27-30s): Brand freeze frame
  Snap pull-back to wide shot; product in perfect freeze frame.
  Logo + Slogan emerge. Frame is clean and premium.
```

#### Template B: Pure product film 30s

```
═══ First segment (0-15s): From darkness to light, revealing the full form ═══

Phase 1 (0-3s): Dark suspense
  Full black. Rim light gradually rises, tracing the product silhouette.
  Extremely slow rhythm, building anticipation.

Phase 2 (3-7s): Light awakening
  Primary light slowly rises; product emerges from darkness.
  Arc orbit from side to 3/4 front; first full appearance from all angles.

Phase 3 (7-11s): Floating Disassembly
  Components separate on display; arc orbit with depth-of-field shifts to focus each component individually.
  Blue energy lines connect all components, suggesting internal coordination.

Phase 4 (11-15s): Precision close-up
  Components snap back in a burst, each part "clicking" into place.
  White light flash at the moment of snap-back → reserved for Screen Activation in the next segment.

═══ Second segment (15-30s): From activation to freeze frame ═══

Phase 5 (15-19s): Feature activation
  Carries over the white light from snap-back → screen spreads and lights up from that light point.
  Interface elements emerge; Digits Ticking; sensors activate and glow one by one.

Phase 6 (19-23s): Burst rotation
  High-speed 360° arc orbit; tracking light locks onto key feature surfaces as they rotate past.
  Each surface illuminated in turn during rotation (front → side → bottom → back).

Phase 7 (23-27s): Macro dive
  From rotation decelerating → lens dives into material macro.
  Extremely shallow depth of field reveals material layers one by one (brushed marks → chamfer → seam → coating).
  Ultra-slow camera movement for the finale.

Phase 8 (27-30s): Brand freeze frame
  Material texture gradually blurs → snap pull-back to wide shot freeze frame.
  Product in perfect pose + Logo + Slogan.
```

#### 30s dual-segment bridge design

| Bridge strategy | Description | Use case |
|---------|------|------|
| **Momentum carry-over** | Movement at the end of the first segment continues at the start of the second | All types |
| **Light causality** | Lighting effect at the end of the first segment becomes the light source at the start of the second | Pure product type |
| **Scene penetration** | Lens penetrates the product → emerges into a new scene | Brand World type |
| **Emotional springboard** | End of first segment builds tension → start of second segment bursts | Needs climax impact |

---

### II. TVC 15s compact pacing

#### Compressed five-stage model

| Stage | Duration | Function | Product state |
|------|------|------|---------|
| **Flash reveal** | 0-2s | Establish product impression in minimum time | Rim light lights up quickly / Match Cut entry |
| **Core selling point** | 2-6s | Focus on 1-2 core features | Feature activation / disassembly display (choose one) |
| **Visual climax** | 6-10s | Most impactful visuals | Burst rotation / extreme scene / macro spectacle |
| **Emotional anchor** | 10-13s | Leave one memory point | Extreme macro / emotional high point |
| **Brand freeze frame** | 13-15s | Logo + product + Slogan | Product in final form, freeze frame |

#### 15s iron rules

- **Single focus principle**: 15s delivers only 1 core memory point
- **No empty shots**: Every frame contains product or brand-related information
- **Transitions are content**: Match Cut is itself information delivery
- **2s freeze frame rule**: The final 2s must be a static freeze frame

#### 15s compact example (wireless earbuds)

```
Style: tech minimalist / pure black + pearlescent white + ice-blue breathing light / Low-key studio / no background music product@product multi-view image advertisement

Phase 1 (0-2s): Case opening reveal
The charging case in a pure black background; the lid slowly opens — the ice-blue breathing light inside activates.
Two earbuds float up slightly from the charging slots on magnetic levitation.
Lens micro-pushes from the front. The arc of the opening lid guides the eye upward.

Phase 2 (2-6s): Floating + feature activation
The two earbuds have fully left the charging case, floating and rotating in the frame.
The left earbud's cross-section renders a transparent view — internal chipset circuits emit pulse light;
the noise-canceling microphone array activates one by one with green indicator dots (suggesting active noise cancellation).
The right earbud's surface touch control zone lights up with an ice-blue arc (suggesting touch operation).

Phase 3 (6-10s): Burst rotation + macro
The two earbuds rotate at high speed toward each other in a 360° full display —
rotation decelerates as the lens urgently pushes to the earbud shell macro;
the nano-level particle texture of the pearlescent white ceramic surface fills the frame;
as side light sweeps past, color shifts subtly from pure white to faint blue iridescence.

Phase 4 (10-13s): Return to charging case
Lens snaps back. The two earbuds slowly descend back into the charging case;
the moment of magnetic alignment emits a faint white pulse.
The lid slowly closes; the brand logo on the surface's arc is illuminated by rim light.

Phase 5 (13-15s): Brand freeze frame
The charging case rests at a 3/4 low angle, centered in the frame.
A sliver of ice-blue breathing light glows through the case lid gap.
Brand logo emerges above; slogan lines below in fine type.

Lighting requirements: Full piece Low-key pure black background; product self-illumination (breathing light / indicator light / pulse light)
is the primary light source, supplemented by precise rim light tracing product edges.
```

---

## Appendix: Product video prompt self-check list

- [ ] **Every Phase has precise second markers** (total duration = sum of all Phases)
- [ ] **Camera movement has speed variation** (rhythm contrast between fast and slow)
- [ ] **At least one Phase contains material macro**
- [ ] **At least one Phase contains feature visualization**
- [ ] **Lighting has a narrative arc** (has changes and progression)
- [ ] **Has Match Cut or visual transition** (Phases have momentum/color continuity)
- [ ] **End Frame elements are minimal** (only product + logo + slogan)
- [ ] **Material descriptions have physical detail** (not "metallic quality" but "brushed texture forming flowing highlights under side light")
- [ ] **Product state has a change arc** (from static → disassembly → activation → display → freeze frame)
- [ ] **Brand tone is consistent**
