# 角色生成提示词模板

把用户的角色描述填入 `{{CHARACTER_BRIEF}}`，把需要保持的明确要求填入 `{{USER_CONSTRAINTS}}`；没有额外要求时删掉对应行。发送前替换所有占位符。默认使用一张内置样板并加上下方参考前缀；用户要求完全无图时只使用共用模板，不传图片。

用户只需说，例如：

> 生成一位拿着药瓶的炼金术士，紫色衣服，透明背景。

角色段可整理为：

> A town alchemist wearing a simple rounded purple outfit, holding one small potion bottle. Compact practical clothing and a clearly readable bottle; no extra laboratory equipment.

这些是输入示范，不代表已通过实测。完整测试以仓库实际保存的提示词、图片与记录为准。

## 默认参考模式前缀

先检查 [样板索引](../assets/style-anchors/README.md) 并查看选定图片。将这段放到共用模板前，并把该图作为唯一明确图片输入。输入路径使用实际安装位置，不能把示例路径当成可用文件。

```text
Input image: one bundled original character, used ONLY as the anatomy, pixel-cluster scale, outline and shading reference. Design a NEW character that belongs at the same map scale. Match its compact silhouette and tiny face closely. Replace its profession, costume, hair and prop with the requested character; do not copy its identity or show it beside the new character. Do not add finer illustration texture or larger eyes. Preserve discrete pixel steps and warm intermediate color clusters. Keep the background genuinely transparent with no glow, halo or floor shadow.
```

## 共用完整模板

```text
Use case: stylized-concept.
Asset type: one cozy JRPG town-map character, shown as an enlarged pixel-sprite inspection image.
Primary request: {{CHARACTER_BRIEF}}
Additional user constraints: {{USER_CONSTRAINTS}}

Composition: one isolated complete character, headwear through shoe soles visible, with clear transparent margins. Slight overhead three-quarter front view. Compact natural standing pose unless another pose is requested. No scenery, floor, ground shadow, glow, labels, text, border, or additional characters. Genuinely transparent background.

Shape language: approximately 2.0–2.1 heads tall. Rounded hair or headwear occupies about 45–50 percent of total height, with a small exposed face beneath it. Narrow shoulders, almost no visible neck, compact short torso, short arms and stubby legs, small thick shoes. Build the silhouette from full, rounded masses. The face uses tiny simple dark short-stroke eyes and minimal nose and mouth. No large glossy anime eyes, detailed irises, eyelashes, or individual fingers.

Pixel treatment: delicately finished small-map-sprite pixel art. About 46–50 logical pixels of visual detail from headwear to soles and 30–35 across the main body; this describes detail density, not a request to fabricate a specific output resolution. Enlarging the image must not add finer illustration details. Use clean connected pixel clusters, carefully shaped stepped contours and warm dark-brown outlines roughly one logical pixel thick. Rounded forms come from deliberate pixel stair steps and neighboring color clusters, never smooth vector curves or a pixelation filter.

Color and shading: harmonious lively costume colors, warm skin shading appropriate to the requested skin tone, broad readable base-color regions, a few deliberate shadow clusters, restrained highlights and gentle warm intermediate edge colors. Consistent soft upper-left lighting. Retain nuanced middle tones without destructive palette reduction. Keep every shape readable at tiny map scale.

Character identity: follow the requested occupation, clothing, hair, skin tone, expression and prop. Simplify fine costume details into readable shapes. Keep props modest in scale so the body remains visible. Do not add an elaborate inventory, ornamentation, patterns or story elements absent from the brief.

Avoid: tall thin proportions, large portrait-style faces, glossy anime eyes, long fine limbs, intricate garment folds, individual hair strands, scattered noise pixels, coarse 8-bit mosaic blocks, forced 32-pixel reduction, blanket dithering, blurred edges, airbrushed gradients, smooth painted curves, plastic 3D highlights, photorealism, fake checkerboard transparency.
```

## 调用与修改

- 真正透明背景还需要在生成工具支持时启用透明输出选项；提示词不能代替该选项。
- 多个独立角色各调用一次，分别保存角色输入、最终展开提示词、图片和是否使用参考图。
- 用户指定其他背景、视角或动作时修改对应段，不保留互相冲突的默认要求。
- 单次修正只解决最明显的偏差，如“小脸和短线眼睛”或“减少零碎高光”；其余比例、色块和角色身份保持稳定。
- 用户只要提示词时直接提供展开文本；需要实际图片时才调用当前环境可用的图像生成工具。工具不可用时说明限制，不声称已生成。
- 若为保持既有角色而编辑母版，明确告知使用了图片输入，记录编辑目标，并保持未请求修改的部位。
