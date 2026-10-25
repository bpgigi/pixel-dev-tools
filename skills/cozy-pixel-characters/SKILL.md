---
name: cozy-pixel-characters
description: Generate soft, rounded Japanese town RPG pixel-style characters from a short character description. Use for chibi overworld NPCs, transparent full-body character assets, and matching character variants with warm shading and deliberate pixel clusters.
license: MIT
---

# Cozy Pixel Characters

Turn a short role description into a single soft, rounded town RPG character. The user only needs to describe the character. By default, use **one bundled style anchor** to improve consistency; tell the user that an included sample supplies the visual style. This skill supplies art direction; it does not train a model or guarantee identical results across generators.

## Build the character brief

Keep the requested profession, appearance, clothing, colors, prop, expression, count, and background. Fill unspecified details conservatively. Default to one full-body character, a simple standing pose, a slight overhead three-quarter front view, and transparent background. Do not ask for details that can reasonably be chosen.

Read [the style guide](references/style-guide.md) and fill [the prompt template](references/prompt-template.md). Preserve the small map-character scale: about two heads tall, a small exposed face, tiny dark eyes, short limbs, a full rounded silhouette, warm brown outlines, and clean stepped pixel clusters. Roundness comes from cluster shapes and deliberate intermediate colors, not blur.

## Generate

Use the host's image-generation tool. In Codex, prefer the built-in `image_gen` tool and request true transparency when appropriate. The host's image-generation instructions govern tool arguments and output handling. If no image tool is available, explain that limitation and return the completed prompt; do not claim an image was generated or silently start a paid API workflow.

- Default `bundled-reference` mode: read [the anchor index](assets/style-anchors/README.md), select one sample for the closest clothing silhouette, inspect that PNG, and pass it explicitly as a style/anatomy reference. Use the reference prefix in the prompt template. Transfer proportions, cluster scale and shading; change identity and outfit to match the user. Do not attach multiple samples by default.
- If the user asks for **no image inputs**, use `text-only` mode: pass no reference-image paths or prior-image count. Do not silently use gallery images, earlier chat images, or a hidden style anchor. In a chat containing images, disclose that the chat is not an isolated text-only test; use a fresh context to evaluate that claim.
- If the user supplies a reference, inspect it and use it for the stated purpose instead of the bundled default. Record `user-reference` mode. Any image-conditioned output is reference-guided, even when the user did not upload the reference themselves.
- If the tool cannot accept the bundled image, explain that fallback and use the text-only template only with the limitation disclosed.
- Generate distinct requested characters as separate assets. Keep the style section stable and change the character brief.
- Save the original transparent PNG in the requested destination or current project. Preserve the generated alpha. Keep any resized preview separate from the master.

## Inspect and deliver

Inspect the actual image, both enlarged and at a small map-like display size. Check the requested character details, two-head proportions, small face and eyes, rounded stepped outline, clean shading clusters, complete hands/prop/feet, and actual transparency. Read image dimensions and alpha when image-inspection tools are available; an on-image checkerboard is not transparency.

If a clear defect appears, make a targeted correction with the same style constraints. Avoid repeated whole-image redraws that gradually smooth the pixel texture. Preserve useful attempts; after two corrective attempts, report the remaining defect rather than silently looping.

Deliver the saved image, a concise visual description, and the prompt or a prompt-file link. Record the expanded prompt, input-image use, generator, attempt count, actual image dimensions, and review findings with the output. Do not invent a model name, seed, or exact pixel grid the tool did not report.

Describe large generated outputs as **pixel-style character masters** unless a native sprite grid has actually been verified. The 46–50-pixel detail-density target is art direction, not a claim that the PNG is 48×48 or ready for a game engine. Do not automatically shrink to 32×32, limit the palette, sharpen, or smooth the result.

## When the user asks for animation or an exact sprite grid

This version generates static character masters. Continue an explicitly requested animation/export task using suitable tools, while clearly identifying any unimplemented step. Keep the approved master immutable. Derive each frame from that master or a common palette and grid; use integer pixel placement and nearest-neighbor display. Inspect temporal consistency, foot placement, and pixel texture. Do not claim a static PNG is an animation, or a resampled illustration is a hand-cleaned native sprite.
