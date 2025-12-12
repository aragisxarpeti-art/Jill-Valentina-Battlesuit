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

### Exporting your plugin (ESP/ESL)
- In the Creation Kit, load your working file, then choose **File → Save** and enter a name such as `MidnightGuardian.esp`.
- To keep load order light, open **File → Data**, highlight your plugin, and tick **ESL** if it meets the compact form ID requirements. This keeps it light like an ESL while staying in ESP format.
- Reopen the plugin and confirm your ARMA/ARMO and COBJ entries still resolve correctly after ESL flagging.

## Chemistry Station crafting recipe
Follow these Creation Kit steps so the player can build the suit at a Chemistry Workbench:

1. **Create a category keyword**
   - Make a new `KYWD` (e.g., `ap_GuardianGear`) with `WorkbenchChemistry` as the parent if you want a dedicated submenu.
   - Add this keyword to the suit's `COBJ` record so the recipe appears under **Guardian Gear** at the Chemistry Station.

2. **Build the constructible object (COBJ)**
   - Duplicate an existing combat armor recipe (e.g., `co_Armor_Combat_Torso_Mk1`).
   - Set **Created Object** to your ARMO record and **Created Object Count** to `1`.
   - Add a **Workbench Keyword** of `WorkbenchChemistry`.
   - Include a **BNAM** category keyword: your new `ap_GuardianGear` (or reuse a generic armor keyword if you prefer).

3. **Define ingredients and conditions**
   - Suggested components for a balanced cost:
     - 4x Adhesive
     - 6x Ballistic Fiber
     - 6x Leather
     - 2x Aluminum
   - Add a condition requiring `HasPerk Armorer` rank 2 (optional) to keep it mid-game gated.

4. **Save and test**
   - Load the plugin, visit a Chemistry Workbench, open **Guardian Gear**, and craft the suit.
   - Verify the item appears in inventory and equips with the correct models and materials.

7. **In-game testing**
   - Verify first-person meshes render correctly.
   - Test with common animation packs to confirm no clipping during sprint, melee, and idle poses.
   - Adjust weight slider support and body morphs as needed.

## Packing BA2 archives
Use Archive2 (installed with the Creation Kit) to compress assets while keeping the plugin modular:

1. Launch **Archive2** and choose **File → New**. Select `General` archive type for meshes/materials and `Textures` for texture ba2s.
2. Drag your folders into the window using the in-game paths:
   - `Meshes/MidnightGuardian/Armor/`
   - `Materials/MidnightGuardian/Armor/`
   - `Textures/MidnightGuardian/Armor/`
3. Save each archive alongside your plugin as `MidnightGuardian - Main.ba2` (for meshes/materials) and `MidnightGuardian - Textures.ba2` (for textures).
4. Open your plugin in the Creation Kit or FO4Edit and confirm the mesh/material paths point to the same folder names you packed so the BA2 files resolve correctly.

## Manual install to the Steam Data folder
If you want to deploy without a mod manager:

1. Locate the game: typically `Steam/steamapps/common/Fallout 4/Data/`.
2. Copy the following into `Data/`:
   - `MidnightGuardian.esp` (or ESL-flagged plugin)
   - `MidnightGuardian - Main.ba2`
   - `MidnightGuardian - Textures.ba2`
3. Launch Fallout 4 or your mod manager and make sure the plugin is enabled in the load order.
4. Start the game, craft the suit at a Chemistry Workbench under **Guardian Gear**, and verify the meshes/materials load from the BA2 archives.

## Nexus Mod Manager packaging
- Folder structure inside the archive:
  - `Data/Meshes/MidnightGuardian/Armor/` (NIF + TRIs)
  - `Data/Textures/MidnightGuardian/Armor/` (DDS)
  - `Data/Materials/MidnightGuardian/Armor/` (BGSM)
  - `Data/MidnightGuardian.esp` (or ESL-flagged plugin)
  - Optional: `Data/MidnightGuardian - Main.ba2` and `Data/MidnightGuardian - Textures.ba2` if you are shipping archives instead of loose assets
- Include a README with installation and uninstall steps.
- Zip the `Data` folder; NMM users can install directly via "Add mod from file".

## Naming and lore snippet
- **In-game name:** "Midnight Guardian Suit"
- **Description:** "A tactically tuned stealth suit with subdued plating and cobalt stitch highlights."
- Avoid direct references to other franchises; keep names and descriptors generic.

## Credits and permissions
- Credit any base body or tool authors per their licenses.
- If using third-party textures or normal maps, ensure they are licensed for redistribution.

