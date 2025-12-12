# Midnight Guardian Suit Concept

This document outlines a copyright-safe, black recolor armour concept inspired by modern tactical gear for female characters in Fallout 4. The suit is named **Midnight Guardian Suit** to avoid reusing trademarked names.

## Visual direction
- **Palette:** Matte black primary fabric with subtle charcoal panel lines and dark grey armor plates. Small cobalt accent stitching on seams for definition without bright highlights.
- **Materials:**
  - Soft-shell base layer with a light hex pattern normal map for added depth.
  - Semi-gloss polymer chest/shoulder plates with micro-scratches.
  - Low-roughness visor or goggles with a faint blue tint.
- **Silhouette notes:** Form-fitting bodysuit with armored forearms, thigh guards, and a compact utility belt. Avoid distinctive franchise emblems or stars—use generic hex or chevron motifs instead.

## Suggested asset workflow
1. **Base body reference**
   - Export the CBBE or vanilla female body from Outfit Studio as reference.
   - Maintain slot assignments (e.g., 33 for body, 41 for hair accessories) to avoid clipping.

2. **Modeling and retopology**
   - Block out the armor plates in Blender using subdivision-friendly topology.
   - Keep polycount comparable to vanilla combat armor for performance.
   - Apply sharp edges for hard-surface sections; bake supporting normal maps from a high-poly mesh.

3. **Texturing (black recolor)**
   - Paint albedo in Substance Painter or GIMP: near-black (RGB ~15-20) cloth, darker plates (RGB ~8-10), cobalt thread accents (RGB ~35-45, 60-70, 90-110).
   - Bake normal, AO, curvature; export BC7 (linear) DDS for color and BC5 for normal.
   - Create a mask map (R=metallic, G=roughness, B=AO) to tune micro-roughness on plates vs cloth.

4. **Material setup**
   - Use `Material Editor` to create BGSM files:
     - Cloth: higher roughness (~0.55), no environment mapping.
     - Plates: lower roughness (~0.18), subtle env map strength (~0.2).
   - Reference your DDS textures with unique paths, e.g., `Textures\MidnightGuardian\Armor\`.

5. **Skinning and weight painting**
   - In Outfit Studio, conform the mesh to the body reference and copy weights.
   - Inspect deformation at shoulders, hips, and knees; correct any collapsing with manual painting.

6. **ESP/ESL plugin setup**
   - Duplicate a vanilla combat armor ARMA/ARMO record in the Creation Kit.
   - Replace model paths with your new meshes and BGSM materials.
   - Assign crafting recipe at the Chemistry Station under a new constructible object category "Guardian Gear".

7. **In-game testing**
   - Verify first-person meshes render correctly.
   - Test with common animation packs to confirm no clipping during sprint, melee, and idle poses.
   - Adjust weight slider support and body morphs as needed.

## Nexus Mod Manager packaging
- Folder structure inside the archive:
  - `Data/Meshes/MidnightGuardian/Armor/` (NIF + TRIs)
  - `Data/Textures/MidnightGuardian/Armor/` (DDS)
  - `Data/Materials/MidnightGuardian/Armor/` (BGSM)
  - `Data/MidnightGuardian.esp` (or ESL-flagged plugin)
- Include a README with installation and uninstall steps.
- Zip the `Data` folder; NMM users can install directly via "Add mod from file".

## Naming and lore snippet
- **In-game name:** "Midnight Guardian Suit"
- **Description:** "A tactically tuned stealth suit with subdued plating and cobalt stitch highlights."
- Avoid direct references to other franchises; keep names and descriptors generic.

## Credits and permissions
- Credit any base body or tool authors per their licenses.
- If using third-party textures or normal maps, ensure they are licensed for redistribution.

