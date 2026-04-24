# TVC Asset Image Generation Framework

> **Core Mission**: After the storyboard script is finalized and before generating storyboard keyframes, first produce a set of **visual asset images** — establishing the visual baseline for "talent, product, and location" across all subsequent frames.
> **In essence**: Asset images = the TVC's "casting + set dressing + product wardrobe." Just as you would cast actors, build sets, and style products before shooting a live-action ad — AI generation works the same way.
> **Only three types of assets**: character turnaround, product images, and scene images. Do not invent a fourth type.

---

## Part 1: Asset Planning — From Storyboard Script to Asset Checklist

> Once you receive the storyboard script, don't rush to generate it frame by frame. Scan the script and answer two questions:

### Question 1: Who appears on screen?

- **Product** → Product images are mandatory, no exceptions
- **People / Models** → Determine whether character asset images are needed:

| Dimension | Make character asset images | Only need on-screen talent standard description |
|---------|------------|-----------------|
| **Category path** | Identity brand world (fashion / styling / jewelry / luxury) → The look itself is the brand world; always required | Functional brand world (tech / tools) and the person is only a "user backdrop" |
| **Product placement strategy** | Lifestyle Film → Product stays on the person throughout, character appears across 5+ frames | Brand World Crosscut → Character appears in only a few brand world panels |
| **On-screen presence** | Lower body / hands / partial but **repeatedly across multiple frames** → High risk of accumulated styling inconsistency | Only 1–2 frames of wide-shot silhouettes / back-view crowd shots |

**Core logic**: The trigger for character assets is not "whether the face is visible," but "**whether the character's styling is a core visual element of this TVC**." In an Identity brand world, even if no full face appears in the entire film, the clothing / accessories / body language are the brand expression — they must be locked in with asset images.

### Question 2: Where is it shot?

- Scan all locations that appear in the storyboard and group them into several **visually distinct spaces**
- Produce one scene image for each distinct space (locking in the mood, color palette, and lighting key)
- If the entire film is shot in a studio (pure product cinematic) → scene images can be skipped, as the studio atmosphere is already locked in through the product images

### Generation Order

```
① Product images (highest priority — the product is the soul of the TVC)
② Character turnaround (if people appear — characters need to interact with the product, so know the product's look first)
③ Scene images (relatively independent, but the color palette should coordinate with the product images)
```

---

## Part 2: Definitions of the Three Asset Types

> **Default assumption: product reference images exist.** Real TVCs advertise products that already exist — official product images / physical photos / e-commerce photos almost certainly exist. "No product reference image" is the exception path (concept products / virtual products / early design stage) and is only activated when the user explicitly states the product is not yet physical.
>
> Whether a reference image exists determines the **prompt writing path** — the prompt structure differs completely between the two paths:
> - **Default path (reference image available)** → The prompt directly references "the product in the image / the person in the image" and **does not describe visual details** (appearance is locked by the reference image; extra description actually interferes with reproduction)
> - **Exception path (no reference image)** → The prompt must precisely describe appearance in text (materials, colors, shapes, etc.) — pure text-to-image
>
> **Do not block the workflow because the user lacks reference images.** Both paths can produce usable asset images — but product reference images should be proactively requested during the creative brief stage and should not be sought as an afterthought during pre-production.

### 2.1 Product Images

**Purpose**: Lock in the product's appearance, materials, color scheme, and proportions. All subsequent frames featuring the product reference this image.

**Reference image interaction**:
- Product reference images should have been confirmed during the creative brief stage (Phase 1); do not re-ask about the product during the pre-production stage
- If Phase 1 was skipped (Mode B/C bypassed the creative brief), ask here: "Does the product have official images / physical photos / e-commerce photos?" — the default assumption is "yes," not "does one exist?"
- After the user responds, generate the prompt according to the appropriate path directly; **do not ask for the image or wait for it to be provided**

**Two prompt paths**:

| Path | When to use | Prompt approach | Example |
|------|---------|-----------|------|
| **Default path (reference image available)** | Launched products, completed designs, any product with official visual assets | `Reference the image, generate [X] for this product` — do not describe the product's appearance | "Reference the image, generate a multi-view of this product. White background studio, consistent side light + rim light..." |
| **Exception path (no reference image)** | Concept products, virtual products, early design stage, user explicitly requests pure text-based product definition | Must precisely describe the product's appearance in text (materials, color scheme, shape, design features) | "White background studio, multi-view of a square amber glass perfume bottle, walnut cap, bottle etched with vertical ribbing..." |

**Core requirements** (shared by both paths):
- **White background / solid-color studio**: no environmental elements — lock in the product itself purely
- **At least two-light setup**: key light (side light for form definition) + fill light (rim light to separate from background)
- **Exception path additional requirement — materials must be written precisely**: not "metal casing," but "brushed-texture titanium casing with concentric CNC tooling marks visible at the chamfers"

**How many images? How to choose?**

| Option | When to use |
|------|-----------|
| **Product multi-view (TVC default)** | One image containing multi-angle full body + key detail close-ups. In TVC advertising, the product will always appear from multiple angles — multi-view is the standard first asset |
| Single Hero Shot | Only when the product appears from a single angle (extremely rare in TVC) |
| Additional material macro | When there is an extreme macro shot in the storyboard, add one additional macro on top of the multi-view |

For TVC advertising, **generate product multi-view by default.** Do not generate individual Hero Shots, side views, or macros separately — one multi-view locks in multiple angles and key details simultaneously, maximizing efficiency and consistency.

**Product multi-view prompt template**:

Default path (reference image available):
```
Reference the image, generate a multi-view of this product. White background studio, consistent side light + rim light.
Include the following angles: 3/4 classic angle full body, front full body, side full body, back full body,
and 2–3 key detail macro close-ups (e.g. cap / button / material texture / port — the most distinctive parts of the product).
Maintain consistent lighting direction and color temperature across all angles.
```

Exception path (no reference image):
```
White background studio, multi-view of [complete product appearance description]. Consistent side light + rim light.
Include the following angles: 3/4 classic angle full body, front full body, side full body, back full body,
and a macro close-up of [specific detail 1] and a macro close-up of [specific detail 2].
Maintain consistent lighting direction and color temperature across all angles.
```

### 2.2 Character Asset Images

**Purpose**: Lock in the character's body posture, clothing, accessories, and overall aura (and face, if applicable). All subsequent frames featuring that character reference this image.

**Three prompt paths**:

| Path | Trigger condition | Prompt approach |
|------|---------|-----------|
| **Face reference image + product / clothing reference image available** | User has provided model photos and product images | `(Image 1) model reference, (Image 2) product/clothing reference` — reference both images in the prompt; do not describe the character's appearance or product look |
| **Face reference image available, no product reference** | User has only provided a model photo | `Reference the image, generate [X] for the person in the image` — do not describe appearance, but describe clothing / styling in text |
| **No reference image** | User has no character reference at all | Must precisely describe appearance + posture + clothing + accessories in text — pure text-to-image |

**Core requirements** (shared by all paths):
- **White background, consistent lighting**: soft studio light, consistent lighting direction and color temperature across all angles
- **Clothing aligned with brand tone**: tech products pair with minimal urban style, tea beverages pair with natural linen style, avant-garde brands pair with dark tactical style
- **Expression stays neutral and natural**: specific emotions are added at the storyboard frame stage
- **No-reference path additional requirement — lock 2–3 key facial features**: e.g. "oval face, almond eyes, black chin-length straight hair" — too many details actually make it harder for AI to maintain consistency
- **No-reference path character description hierarchy**: `[Identity] + [Body type] + [Facial features] + [Complete clothing description] + [Accessories] + [Aura]`

**Character asset images are always full body**:

A character asset image = a casting & wardrobe reference. A real TVC director always looks at the complete person when casting — the decision to shoot only legs / hands / back is made during production, not during casting. Clothing is a complete styling system (top + bottom + shoes + accessories all in dialogue with each other); shooting only half the body loses the full context of the look.

| Is the face on screen | Asset image format | Notes |
|------------|----------|------|
| **Face included** | **Complete character turnaround**: face close-up + full body front + full body back | Standard format |
| **No face / face obscured** | **Styling showcase**: full body front + full body side + full body back + key accessory close-up | Face may be obscured / lower half of face / profile; focus is on locking in complete clothing and accessory look |
| Only 1–2 frames of wide-shot silhouette / back view | **No asset image** — use on-screen talent standard description instead | See Part 3 Character Consistency |

> **Generating half-body or partial character asset images is prohibited.** Even if only the lower body or hands appear in the storyboard, the asset image must be full body — the integrity of the styling determines the visual logic of every individual part.

**Character assets featuring the product must reference the product image**:

When the product is worn / on the wrist / held in hand (running shoes, watch, jewelry, jacket, glasses, handbag, etc.), the character asset image prompt **must reference the product multi-view already generated in pre-production**, so the character is shown wearing / holding the product. Method: in Nano Banana Pro's edit mode, upload the product multi-view, then reference it in the prompt using `(ImageN)` — `wearing the running shoes from Image 1` / `wrist wearing the watch from Image 1` / `wearing the jacket from Image 1`. Not referencing the product image = the product appearance on the character's feet / wrist / body is uncontrolled = storyboard consistency collapses downstream.

#### Character Asset Image Prompt Examples

**Example 1: Pure text generation (no reference image, face included) — traditional Chinese hanfu model**

```
A high-quality studio portrait character turnaround, including a face close-up, full body front, and full body back.
A beautiful young woman wearing an exquisite Tang-style hanfu in soft champagne gold and dusty rose tones, standing in full-length pose.
The hanfu fabric has a delicate silk texture, embellished with soft blue and pink floral embroidery and classical damask patterns.
A teal sash with an intricate jade-green clasp is tied at the waist. Her hair is styled in an elegant cloud chignon,
adorned with simple yet ornate floral hairpieces, pearl eardrops, and swaying tassel hairpins.
Her hands are folded gracefully at her waist, wide sleeves falling naturally, conveying an elegant and poised bearing.
The character looks directly into the camera, eyes clear, expression composed.
Pure white background, soft studio lighting, 8K resolution, hyper-realistic, extremely fine fabric texture.
```

**Example 2: Face reference image + clothing reference image — fashion styling multi-panel showcase**

```
Masterwork, 8K ultra-HD, photorealistic, 16:9 landscape composition, 4-panel fashion display layout,
Panel 1: A close-up portrait of the woman from Image 1, wearing the leopard print dress from Image 2, clean white background, soft studio lighting,
Panel 2: Full body front of the same woman, wearing the fitted long-sleeve V-neck leopard mini dress from Image 2,
holding the black mini handbag from Image 2, nude pointed-toe heels, standing naturally, white studio background,
Panel 3: Full body side of the same woman, same outfit, same bag, same shoes, standing naturally, white background,
Panel 4: Full body back of the same woman, same outfit, same bag, same shoes, standing naturally, white background,
Facial features fully consistent, hairstyle consistent (long wavy dark brown hair), accessories consistent (delicate silver necklace, small earrings, silver bracelet, rings),
skin tone consistent, professional fashion editorial style, uniform lighting, sharp focus, no distortion, no blur
```

> Key approach in Example 2: Use `(Image 1)` to lock the face / body type, use `(Image 2)` to lock the clothing / accessories appearance. The prompt only describes how the look is combined and what angles to show — visual details are handled by the reference images. Reinforce consistency in each panel with "the same woman" and "same outfit."

**Example 3: No face + product reference image — running shoe TVC model styling showcase**

```
Masterwork, 8K ultra-HD, photorealistic, 16:9 landscape composition, 4-panel athletic styling display layout,
Panel 1: Full body front of a beautiful, slender young Asian woman, black high ponytail,
wearing black high-waist fitted 7/8-length running tights (matte compression fabric, cuffs fitted just above the ankle),
light grey short fitted quick-dry top, feet in the white running shoes from Image 1, ultra-short invisible socks revealing slender ankles,
standing naturally with arms relaxed at sides, face tilted slightly downward showing only the jawline,
clean white background, soft studio lighting,
Panel 2: Full body side of the same woman, same outfit, feet in the white running shoes from Image 1,
standing naturally, showcasing the side seam cut of the running tights and the complete side profile of the Image 1 running shoes, white background,
Panel 3: Full body back of the same woman, same outfit, feet in the white running shoes from Image 1,
standing naturally, showcasing the back panel lines of the top and the seat-seam cut of the running tights, white background,
Panel 4: Close-up of the same woman's ankles and running shoes, the proportion relationship between the Image 1 white running shoes and slender ankles,
the woven texture of the upper is clearly visible, a strip of skin showing between the pant cuff and the shoe collar,
posture fully consistent, clothing fully consistent, hairstyle consistent (black high ponytail), skin tone consistent,
professional athletic editorial style, uniform lighting, sharp focus, no distortion, no blur
```

> Key approach in Example 3: **Each panel repeats `feet in the white running shoes from Image 1` or `the Image 1 white running shoes`** — mentioning the product reference only once makes it easy for AI to ignore; repeating in each panel ensures the product is rendered correctly in every angle. Follow the "same woman" and "same outfit" approach from Example 2 to reinforce consistency. The face is avoided by tilting the head down, but hair information is preserved.

**Product reference iron rule**: When a character wears or carries the product, **the product reference must be repeated in every panel of the prompt** (`feet in the [X] from Image 1` / `wrist wearing the [X] from Image 1`) — it cannot be mentioned only once at the start. A single mention does not carry enough weight for AI to correctly render the product in all angles.

### 2.3 Scene Images

**Purpose**: Lock in the visual atmosphere of the brand world — space, lighting, color palette, and time of day. All subsequent frames set in that location carry forward this visual key.

**Two prompt paths**:

| Path | Prompt approach | Example |
|------|-----------|------|
| **Reference image available** | `Reference the image, generate [X] based on the scene atmosphere in the image` — do not describe scene details | "Reference the image, generate a 16:9 wide empty establishing shot based on the scene atmosphere in the image, no people no product, maintain the same color palette and lighting key" |
| **No reference image** | Must precisely describe the space, color palette, lighting, and time of day in text | "16:9 wide, Nordic minimalist apartment living room at dawn, golden morning light pouring through floor-to-ceiling windows, white walls grey floors..." |

**Core requirements** (shared by both paths):
- **No people, no product**: scene images lock in "the space itself" — people and product are added in storyboard frames
- **Time of day and weather must be explicit**: the same tea garden at dawn with thin mist and at noon under harsh sun are completely different images
- **Color palette is the core deliverable**: the most important output of a scene image is the "color palette baseline"
- **Foreground / midground / background layering**: scenes must have spatial depth
- **Wide 16:9**

**How many images?**
- One image for each **visually distinct space** in the storyboard
- Different corners of the same space do not need to be done separately

---

## Part 3: Consistency — The Core Value of Asset Images

> The value of asset images is not "looking good" but "being referenceable." Subsequent storyboard frames reference asset images to ensure visual consistency throughout the film.

### Product Consistency

Based on the product image, establish a **product standard description** to be reused uniformly in all subsequent frame prompts:

```
[Product name], [core material] + [color scheme], [key design feature 1], [key design feature 2].
```

### Character Consistency

- **Asset image available**: subsequent frames use reference image (`the [character name] in the image` or `(ImageN)`) — do not re-describe appearance
- **No asset image (silhouette / wide shot where no asset is made)**: establish an **on-screen talent standard description** to be reused uniformly in all subsequent frames:
  `[Skin tone / ethnicity] + [body type] + [clothing style + color] + [key accessories]`
  Example: "Asian male, lean runner's build, black fitted 7/8-length running tights, dark grey quick-dry tank top, no accessories"
- Clothing / hairstyle / body type description remains unchanged; only expression and pose may vary

### Scene Consistency

- Across different shots in the same scene, color palette, light direction, and atmospheric effects remain consistent
- The scene image's color palette is the "baseline" — subsequent frames may fine-tune but must not jump to a different palette

### Cross-Asset Coordination

- Product color palette and scene color palette should coordinate — warm scenes pair with warm product lighting
- Character clothing color echoes the brand color / scene color
- All assets use the same unified visual style direction
