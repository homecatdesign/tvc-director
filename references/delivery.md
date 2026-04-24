# TVC Output Formats & Iteration Knowledge Base

> **Responsibility**: Output format templates for prompts + Iteration optimization guide.
> **Not covered here**: Creative strategy (see treatment.md), prompt engineering (see shot-language.md), storyboarding and video (see storyboard.md).

---

## Part 1: Output format templates

Output format templates for single frames, sequences, TVC product asset sequences, Multi-Phase video prompts, and End Frame.

---

## I. Mode 1: Single keyframe prompt

Use when the user needs to generate a **single specific frame**.

**Output structure**:

```
### Keyframe: [Title]
**Purpose**: [The role of this image in the video — opening frame / closing frame / transition frame / character design / environment design]
**Aspect ratio**: [16:9 / 9:16 / 1:1 / recommended based on purpose]

**Nano Banana Pro prompt**:
[Complete prompt ready to copy and use directly]

**Reference image requirement**: [Whether the user has provided a reference image. Yes → note "Provided, generate with attached image"; No → note "No reference image, generate from text description only"]

**Generation notes**: [Generation considerations specific to this image, such as parts that may require multiple rounds of fine-tuning]
```

---

## II. Mode 2: Keyframe sequence prompts

Use when the user needs to generate **a set of keyframes** for a complete storyboard script.

**Output structure**:

```
## Keyframe sequence: [Project name]

### Generation order and dependencies
| No. | Keyframe | Type | Dependencies | Priority |
|-----|----------|------|--------------|----------|
| 1 | ... | Character design | None | ★★★★★ |
| 2 | ... | Environment concept | None | ★★★★★ |
| 3 | ... | Narrative composition | Depends on #1, #2 | ★★★★☆ |
| ... | ... | ... | ... | ... |

### Consistency anchors
- **Character consistency**: [How to maintain character consistency across multiple images]
- **Environment consistency**: [How to maintain a unified environment style]
- **Color tone consistency**: [How to maintain the color palette across the entire set]

---

### Frame 1: [Title]
(Same single-frame structure as Mode 1)

### Frame 2: [Title]
...
```

---

## III. Sequence generation order

1. **Characters before scenes**: Character design images (three-view / close-up) are generated first; subsequent scene images can reference the character reference
2. **Environment before composition**: Standalone environment concept images come first; narrative compositions are generated after both character and environment are confirmed
3. **Global before detail**: Wide shots / full panoramas first to establish the overall atmosphere, then generate close-ups / detail shots
4. **Key frames > transition frames**: Climax frames, opening frames, and freeze frames take priority; transition frames come last

---

## IV. Consistency maintenance strategy

### Character consistency

- Generate character three-view / design reference images first to establish a visual baseline
- Reference the character reference image in subsequent scene images using `[Character name] in the image` or `Image 1`
- Keep clothing, hairstyle, and body type descriptions consistent for the same character across different scenes
- If special changes occur (injury, costume change), explicitly note the points of change

### Environment consistency

- Different angles / shots of the same scene maintain the same material, color tone, and atmosphere descriptions
- Use unified environment keywords to lock down the style
- Generate an environment concept image first to establish the baseline, then reference it in narrative compositions

### Color tone consistency

- Use a unified art style direction (A/B/C/D/E) across the full set of keyframes
- Color tone changes should follow the color arc design in the creative treatment
- Keep the same core words in the art style anchor section of each frame's prompt

---

## V. Mode 3: TVC product asset sequence

Use when you need to build a **product visual asset library** for a TVC commercial. Product assets are the cornerstone of the TVC visual system — all subsequent scenes, video prompts, and End Frame rely on product assets as visual anchors.

**Output structure**:

```
## Product asset sequence: [Product name]

### Product asset list
| No. | Asset type | Purpose | Priority |
|-----|------------|---------|----------|
| 1 | Product Hero Shot | Lock down the primary product visual | ★★★★★ |
| 2 | Product material macro | Lock down material texture | ★★★★☆ |
| 3 | Brand world environment | Lock down the scene atmosphere | ★★★★☆ |
| 4 | Product interaction close-up | Lock down usage actions / gestures | ★★★☆☆ |
| 5 | Product packaging / accessories | Lock down brand peripheral elements | ★★★☆☆ |
| ... | ... | ... | ... |

### Product consistency anchors
- **Product appearance**: [Precise description of the product's shape, proportions, and signature design features]
- **Material / lighting**: [Product surface material type, reflective properties, recommended lighting approach]
- **Brand color**: [Specific color values or descriptive definitions for primary / secondary / accent colors]

---

### Asset 1: Product Hero Shot
**Purpose**: Lock down the primary product visual, serving as the reference baseline for all subsequent product appearances
**Aspect ratio**: 16:9

**Nano Banana Pro prompt**:
[Complete prompt ready to copy and use directly]

**Reference image requirement**: [Whether the user has provided a product reference image. Yes → note "Provided, generate with attached image"; No → note "No reference image, generate from text description only"]

**Generation notes**: [Generation considerations specific to product rendering, such as material precision, Logo legibility, etc.]

---

### Asset 2: Product material macro
...

### Asset 3: Brand world environment
...
```

**Key points**:

- The product Hero Shot is the highest-priority asset and must be generated and confirmed first
- All subsequent keyframes and video prompts involving the product should reference the Hero Shot as the visual anchor
- The brand world environment image is used to lock down the atmosphere baseline for scenes where the product appears; subsequent scene frames refine from this foundation

---

## VI. Mode 4: TVC Multi-Phase video prompts

Use when you need to generate **multi-phase prompts ready for direct use in video generation tools** for a TVC storyboard segment. Each Segment corresponds to one cell in the multi-Grid storyboard.

**Output structure**:

```
## TVC video prompt: [Project name] · Segment [N] ([Time period])

**Corresponding Grid**: Grid [N]
**World type**: Product world / Brand world / Crossover
**Duration**: [X]s

**Multi-Phase video prompt**:
Style: [Overall visual style description — tone, color palette, texture]
Phase 1 (0-Xs): [Movement / action / frame content description]
Phase 2 (X-Ys): [Movement / action / frame content description]
Phase 3 (Y-Zs): [Movement / action / frame content description]
...
Lighting requirement: [Lighting tone for this segment — natural light / studio light / special effects light, etc.]

**Opening keyframe reference**: [Asset number or name of the corresponding keyframe]

**Transition notes**:
- Transition from previous segment: [How the visual / movement / emotional flow carries from the previous segment's closing frame to this one's opening frame]
- Transition to next segment: [How this segment's closing frame sets up the opening frame of the next segment]
```

**Key points**:

- The opening frame of each Segment should be anchored by an already-generated keyframe asset, ensuring the starting frame of the video is controllable
- Phase divisions are based on the movement rhythm within the shot, not mechanical equal-time splits
- Transition notes are critical for TVC fluidity — ensure that movement direction, color tone, and emotional arc do not break between segments
- The world type label allows quick identification of whether the segment follows product-display logic or brand-narrative logic

---

## VII. Mode 5: End Frame output

Use when you need to generate the **closing freeze frame (End Frame)** of a TVC commercial. The End Frame is the final visual landing point of the entire ad, carrying brand memory and the call to action.

**Output structure**:

```
### End Frame: [Product name]
**Purpose**: TVC closing freeze frame
**Aspect ratio**: 16:9
**Text overlay area**: [Describe the reserved space for Logo and Slogan — e.g., "Top 1/3 of the frame left blank for centered Logo, bottom 1/5 area reserved for Slogan"]

**Nano Banana Pro prompt**:
[Complete prompt ready to copy and use directly — the frame must reserve space for text overlay; core visual elements should not occupy the text areas]

**Reference image requirement**: [Whether brand VI reference images, Logo files, etc. are needed]

**Generation notes**: [End Frame-specific generation considerations, such as controlling blank areas and ensuring brand color accuracy]

**Post-production overlay guide**:
- **Logo position**: [Specific area description, e.g., "Slightly above center of frame, spanning 30% of frame width"]
- **Slogan position**: [Specific area description, e.g., "Directly below Logo, ~40px gap from Logo"]
- **Recommended font style**: [Font style suggestion matching the brand tone, e.g., "sans-serif / modern / handwritten"]
- **Recommended text color**: [Text color recommendation based on the background color of the frame]
```

**Key points**:

- The End Frame prompt must deliberately reserve space for text overlay — this is the core distinction from ordinary keyframes
- The frame should be clean, premium, and restrained; avoid complex scenes that compete with the product for visual attention
- Brand color representation in the End Frame must be highly precise; referencing the brand VI manual is recommended
- The post-production overlay guide provides designers with an actionable layout plan, reducing back-and-forth communication costs

---

## VIII. TVC sequence generation order

TVC commercial asset generation follows a **product-first, layer-by-layer** order, ensuring visual consistency radiates outward from the core:

1. **Product before scenes**: The product Hero Shot is generated first to lock down the product's visual baseline (form, material, lighting). All subsequent frames involving the product use this as the reference anchor
2. **Product before brand world**: After all product assets are confirmed, generate the brand world's environments, atmospheres, and narrative scenes. Avoid generating scenes first, which can cause disconnection between product and environment styles
3. **Multi-Grid before video prompts**: After all multi-Grid storyboard keyframes are locked down, generate Multi-Phase video prompts segment by segment. Keyframes are the visual anchor for video prompts — the order cannot be reversed
4. **End Frame last**: The End Frame is generated last, after all visual directions are locked. At this point the TVC's color tone, texture, and brand expression are fully defined, allowing the End Frame to precisely close out the overall tone of the piece

---

## Part 2: Iteration optimization guide

Single-variable iteration principles, 11 common failure modes and fixes, fine-tuning techniques, and version management.

---

## I. Core iteration principles

### 1. Single-variable principle

Each iteration modifies only **one variable** and observes the effect. If you change three things at once, you cannot determine which change made the difference.

| Approach | Effect |
|----------|--------|
| ❌ Changed composition + lighting + color tone all at once | Cannot attribute the cause; may fix one thing and break two others |
| ✅ Change only the lighting description first | Clearly determines whether lighting is the root issue |
| ✅ After confirming lighting is OK, then adjust composition | Progressively converge on the target |

### 2. Addition/subtraction principle

The first step in fixing a problem is determining whether it's "too much of something" or "not enough of something":

- **Unwanted elements appearing** → Subtraction: remove words that may suggest those elements
- **Missing a desired effect** → Addition: add more specific descriptive words
- **Effect is going in the wrong direction** → Replacement: swap in words with more precise meaning

### 3. Position-weight principle

In Nano Banana Pro, **words that appear earlier in the prompt carry higher weight**. If a certain effect is not strong enough:
- **Move the corresponding description to an earlier position**
- Or **place the most important image quality / style anchors at the very beginning**

### 4. Avoiding "getting worse with every iteration"

| Trap | How to avoid |
|------|-------------|
| Fine-tuning the same sentence over a dozen times | If more than 3 rounds of fine-tuning produce no result, step back and analyze the root cause |
| Adding too many words trying to fix one problem | A longer prompt is not necessarily better — simplify and start fresh |
| Swinging from one extreme to the other | Don't jump directly from "too dark" to "bright"; use an intermediate state as a transition |
| Forgetting previously successful versions | Keep the prompt text from each iteration so you can always roll back |

---

## II. Common failure modes and fixes

### Mode 1: Image too bright / not dark enough

**Symptom**: You specified "extremely dim," but the result is still too bright or has unreasonable light sources.

**Root cause analysis**:
- The description contains words that imply light sources (e.g., "torch," "lamp," "sunlight," etc.)
- The "dim" description is not strong enough
- You didn't explicitly say "almost completely dark"

**Fix**:
```
Add: extremely dim environment / almost completely dark environment / most of the space swallowed by deep shadow
Add: light falls off extremely rapidly
Remove: any words that might imply additional light sources (torches, lamps, bright [X])
Front-load: move "extremely dim" to the very beginning of the description
```

### Mode 2: Unwanted objects appear

**Symptom**: Objects appear in the frame that were never requested (e.g., unwanted torches, people, furniture, etc.).

**Root cause analysis**:
- Certain descriptive words imply those objects (e.g., "cave" may automatically generate torches)
- Context implication (e.g., "hall" may automatically generate furniture)

**Fix**:
```
Method 1: Directly remove descriptions that may imply the unwanted object
Method 2: If the object still appears after removal, add an exclusion instruction at the end of the description
Method 3: Replace vague spatial type words with more specific spatial descriptions
```

**Example**: Don't want torches
```
❌ A dimly lit underground cave hall
✅ An extremely dim underground abyss hall, no artificial light sources of any kind, only faint blue bioluminescence
```

### Mode 3: Not enough sense of space / not grand enough

**Symptom**: You described "grand," but the generated space looks small and flat.

**Root cause analysis**:
- Lacking vertical dimension description (ceiling / dome)
- Lacking atmospheric perspective (mist, dust)
- Viewpoint is not extreme enough
- Lacking reference objects to provide a sense of scale

**Fix**:
```
Add: the ceiling soars into the sky, disappearing into heavy darkness (vertical dimension)
Add: the air is filled with extremely thick volumetric fog, making the distance fade into nothingness (atmospheric perspective)
Add: an extremely low angle to emphasize the terrifying height of the space (extreme viewpoint)
Add: massive biological pillars like towers of Babel support the darkness (reference object + scale metaphor)
```

### Mode 4: Character face looks bad / distorted

**Symptom**: The character's face is deformed, unnatural, or diverges too much from the reference image.

**Root cause analysis**:
- The facial description is too complex for the AI to satisfy all requirements simultaneously
- No reference image was provided
- The lighting conditions are unfavorable for the face (too dark or too complex mixed lighting)

**Fix**:
```
Strategy 1: Simplify the facial description, keeping only the 1-2 most essential features
Strategy 2: Upload a character reference image and reference it with "[Character] in the image"
Strategy 3: Use face-friendly lighting — side light / backlit semi-silhouette works better than flat frontal lighting
Strategy 4: For keyframes (not design sheets), use a side profile / semi-silhouette to avoid frontal face detail
```

### Mode 5: Color tone is wrong

**Symptom**: The frame's color tone doesn't match expectations (too warm / too cool / too saturated / not saturated enough).

**Root cause analysis**:
- The color tone description is not specific enough
- The light source color contradicts the target color tone
- Art style anchor words imply a different color tone

**Fix**:
```
Specify tone words clearly: desaturated cool gray-blue / blood orange deep red / amber warm gold / cool blue-green
Ensure light source color is consistent: if you want a cool tone, the light source should also be blue/white, not warm yellow
Check style anchors: certain style words carry a built-in tone tendency (e.g., Golden Hour automatically skews warm)
```

### Mode 6: Composition is scattered / subject is not prominent

**Symptom**: The frame has no focal point, elements are distributed chaotically, unclear where to look.

**Root cause analysis**:
- No composition rule was specified
- Too many elements with equal visual weight were described
- Lacking depth-of-field control

**Fix**:
```
Add explicit composition: subject positioned at the [position] third / center-symmetric composition
Reduce elements: remove non-core elements to let the subject stand out
Add depth of field: extremely shallow depth of field, focus on [subject], everything else out of focus / bokeh
Specify visual guidance: use [light / road / lines] to guide the eye to the subject
```

### Mode 7: Material texture is insufficient / looks fake

**Symptom**: Metal looks like plastic, skin looks like wax, fabric looks like cardboard.

**Root cause analysis**:
- Material description is too vague
- Lacking microscopic physical details
- Lighting is not complex enough (missing reflections, subsurface scattering, etc.)

**Fix**:
```
Metal: add "brushed texture," "worn sheen," "micro-oxidation marks"
Skin: add "pores," "subtle sweat beads," "natural uneven blush with skin tone variation"
Fabric: add "weave texture," "folded wrinkles," "frayed / worn edges"
Universal: add "wet reflective sheen" (adding a layer of moisture to any surface makes it feel more real)
```

### Mode 8: Image looks flat / lacks depth

**Symptom**: The frame looks like a flat texture map, lacking spatial depth.

**Root cause analysis**:
- Lacking foreground/midground/background layering
- No atmospheric perspective effect
- All elements are on the same focal plane

**Fix**:
```
Add layering: Foreground: [out-of-focus element]. Midground: [subject]. Background: [environment]
Add atmosphere: the air is filled with volumetric fog / dust particles
Add depth of field: specify the focal point position; other layers naturally fall out of focus / bokeh
Add lighting layers: strong light up close fading to darkness in the distance, or backlight to create depth
```

### Mode 9: Too much CG feel / doesn't look like live-action

**Symptom**: You wanted a live-action / real person look, but the result resembles 3D modeling / CG rendering. Skin is too smooth, lighting too even, the whole image has a "digital" feel.

**Root cause analysis**:
- Art style anchor words lean toward CG (e.g., "ultra-realistic cinematic style" is interpreted by the model as "ultra-realistic CG rendering")
- Three-view / character sheet formats are inherently design/modeling concepts; the model naturally tends toward CG output
- Missing photographic anchor words to pull the result toward the live-action / real person direction
- The image quality anchor words and art style anchor words point in contradictory directions

**Fix**:
```
Core replacement: replace all CG-direction anchor words with live-action / real person direction anchor words
  ❌ ultra-realistic cinematic style / AAA game 3D style
  ✅ live-action, cinematic photography, real skin pore texture, natural lighting

Add live-action reinforcement words (choose as needed):
  + real skin pore texture (forces live-action / real person skin micro-detail)
  + natural lighting (avoids CG-style uniform lighting)
  + RAW photo texture (unretouched original photography feel)
  + cinematic film color (film-grain color tone)

Check and remove all CG-direction words:
  Remove: "master-level CG rendering," "Unreal Engine 5 render," "AAA game," etc.
```

**Example**:
```
❌ Erwin character three-view... art style is ultra-realistic cinematic style.
✅ Erwin character three-view... live-action, cinematic photography, real skin pore texture, natural lighting.
```

### Mode 10: Too much live-action feel / want CG but it's too realistic

**Symptom**: You want an AAA game CG texture, but the result looks too much like a real photo, lacking the polished and stylized quality of CG.

**Root cause analysis**:
- Art style anchor words lean toward live-action / real person direction
- Used anchor words such as "live-action" and "photography"
- Missing CG-direction anchor words

**Fix**:
```
Core replacement: replace live-action / real person direction anchor words with CG-direction anchor words
  ❌ live-action, cinematic photography
  ✅ AAA game 3D style / master-level CG rendering

For more polished CG:
  ✅ Unreal Engine 5 render, subsurface scattering skin, PBR materials, global illumination

Remove all live-action / real person direction words:
  Remove: "live-action," "real skin pore texture," "natural lighting," "RAW photo," etc.
```

### Mode 11: Style is inconsistent / oscillating between live-action and CG

**Symptom**: Results are unstable between live-action and CG — within the same batch some look like live-action and some like CG, or within a single image some areas look like live-action and others like CG.

**Root cause analysis**:
- Art style anchor words internally contradict each other in direction (simultaneously containing live-action-type and CG-type keywords)
- Image quality anchors and art style anchors point in inconsistent directions
- Ambiguous words like "ultra-realistic cinematic image quality" are not constrained by a clearly stated direction

**Fix**:
```
Diagnose: review all style / image quality related words in the prompt and label their directional alignment
  Live-action / real person direction words: live-action, cinematic photography, skin pores, natural lighting, RAW photo
  CG direction words: AAA game, CG rendering, Unreal Engine, PBR materials
  Ambiguous words (watch out): ultra-realistic cinematic image quality, cinematic color grading, 8K ultra-HD

Fix: ensure all direction words point in the same direction
  ❌ ultra-realistic cinematic image quality... AAA game 3D style... real skin pore texture
  ✅ live-action, cinematic photography... real skin pore texture, natural lighting (all live-action / real person direction)
  ✅ master-level CG rendering, 8K ultra-HD resolution... AAA game 3D style (all CG direction)
```

---

## III. Fine-tuning techniques

### Effect patterns when adding words

| Word added | Typical effect |
|-----------|----------------|
| "extremely," "intensely" | Amplifies the effect of the descriptor that immediately follows |
| "faint," "subtle" | Reduces the intensity of a light source or effect |
| "thick," "dense" | Increases the density of fog / smoke / dust |
| "almost completely dark" | Dramatically darkens the overall image |
| "disappearing into darkness" | Makes the edges of distant / high elements fade out |
| Specific numbers (e.g., "60 meters") | Helps the AI establish a sense of scale |
| Frame proportion (e.g., "occupying 70% of the frame") | Precisely controls element size |

### Effect patterns when removing words

| Word removed | Typical effect |
|-------------|----------------|
| Remove extra light source descriptions | Image becomes darker |
| Remove specific objects | That object disappears (though not guaranteed — AI may infer from context) |
| Remove color adjectives | AI selects color tone on its own (may be unstable) |
| Remove composition instructions | AI composes randomly (not recommended) |

### Word replacement techniques

| Original word | Replace with | Effect change |
|--------------|-------------|---------------|
| dim | extremely dim / almost completely dark | Darker |
| grand | extremely grand, ceiling soaring into the sky | More sense of space |
| blue light | faint blue light source | Light weakened |
| mist | extremely thick volumetric fog | Fog denser |
| wide angle | wide-angle lens, extremely low angle | More extreme perspective |

---

## IV. Iteration workflow

### Standard iteration process

```
1. First generation: use the complete prompt
   ↓
2. Evaluate the result: compare against the target image, identify gaps
   ↓
3. Diagnose the problem: which dimension has the issue?
   - Color tone? Lighting? Composition? Subject? Environment? Material?
   ↓
4. Single-variable modification: change only the description for the problem dimension
   ↓
5. Second generation: observe the change
   ↓
6. If OK → move on to fine-tuning the next dimension
   If not OK → return to step 3, try a different fix strategy
   ↓
7. More than 3 ineffective modifications → step back and check whether the fundamental approach is the problem
```

### Quick diagnosis checklist

When results are unsatisfactory, run through the following checklist item by item:

- [ ] **Is the art style direction correct?** → Check whether the art style anchor words point in the right direction (live-action / CG / engine-level); check for contradictory direction words
- [ ] **Is image quality up to standard?** → Check whether image quality anchor words are at the very front
- [ ] **Is the subject correct?** → Check whether the subject description is clear and accurate
- [ ] **Is the sense of space correct?** → Check the scale and atmospheric effects in the environment description
- [ ] **Too bright or too dark?** → Check the number of light sources, intensity, and brightness/darkness descriptor words
- [ ] **Is the color tone correct?** → Check color descriptor words and light source colors
- [ ] **Is the composition correct?** → Check whether composition instructions are explicit
- [ ] **Are there any unwanted elements?** → Check whether any descriptor words imply unwanted objects
- [ ] **Is the material texture sufficient?** → Check whether there are microscopic physical detail descriptions
- [ ] **Is the spatial layering sufficient?** → Check whether there is foreground/midground/background layering and depth-of-field control

---

## V. Practical path from failure to success — example

### Example: Dark underground hall

**Goal**: An extremely dim, grand underground space with only faint blue light.

**Attempt 1**:
```
An underground cave hall, dim, blue light. AAA game style.
```
❌ Result too bright, space not grand enough, torches appeared.

**Diagnosis**: Description too simple; "cave" implied torches; "dim" not strong enough.

**Attempt 2**:
```
An extremely grand underground abyss hall, ceiling soaring into the sky. Environment extremely dim, almost completely dark. Faint blue light source. AAA game master-level image quality.
```
❌ Space became larger but texture is insufficient, lacks volumetric feel.

**Diagnosis**: Missing atmospheric effects and material description.

**Attempt 3**:
```
An extremely grand underground abyss hall, the ceiling soaring into the sky, disappearing into heavy darkness. AAA game master-level image quality. Environment extremely dim, almost completely dark. A faint blue light source traces the majestic contours of the space. The air is filled with extremely thick volumetric fog. The walls are covered in moist, reflective chitinous shell textures; massive biological pillars like towers of Babel support the darkness. Wide-angle lens, an extremely low angle to emphasize the terrifying height of the space.
```
✅ Achieved the target effect.

**Key improvements**: Added volumetric fog (sense of space), material description (texture), extremely low angle (sense of height), "disappearing into darkness" (sense of infinite extension).

---

## VI. Version management tips

To avoid "getting worse with every iteration" or "forgetting a previously good version," it is recommended to:

1. **Number each prompt**: v1, v2, v3...
2. **Record what changed each time**: v2 vs v1 = added volumetric fog description
3. **Mark satisfaction**: ★★★☆☆
4. **Keep the best version**: always able to roll back to the previous best state
5. **Record successful patterns**: when a certain combination of descriptions produces great results, document it as a template for future use
