# Jill-Valentina-Battlesuit

Fallout 4 armour concept inspired by modern tactical outfits. This repository documents a copyright-safe, black recolor variant suitable for female characters and ready to package for Nexus Mod Manager.

## Concept overview
- **Name:** Midnight Guardian Suit
- **Palette:** Matte black cloth with charcoal plates and subtle cobalt stitching.
- **Lore blurb:** "A tactically tuned stealth suit with subdued plating and cobalt stitch highlights."

## What this repository provides
- Design guidelines and workflow notes for modeling, texturing, and configuring the suit in Fallout 4.
- Packaging guidance for Nexus Mod Manager users.

## Quick build checklist
1. Block out and retopologize the armor in Blender with performance-friendly polycount.
2. Paint black/cobalt textures; export DDS (BC7 for color, BC5 for normals) and author BGSM materials.
3. Skin and weight the mesh in Outfit Studio to the female body reference.
4. Duplicate a vanilla combat armor record in the Creation Kit, point to your meshes/materials, and add a Chemistry Station recipe under "Guardian Gear" with ingredients (e.g., adhesive + ballistic fiber + leather).
5. Package the Data folder (Meshes, Textures, Materials, ESP/ESL) into a zip for NMM installation.

## Detailed workflow
See [`docs/MIDNIGHT_SUIT.md`](docs/MIDNIGHT_SUIT.md) for step-by-step notes on visuals, materials, skinning, plugin setup, and packaging.

## Visual preview and install guide
See [`docs/VISUAL_PREVIEW.md`](docs/VISUAL_PREVIEW.md) for an ASCII silhouette, color legend, and Nexus Mod Manager download/installation steps.

## Licensing
This repository contains documentation only. Ensure any assets you create respect the licenses of the tools and base bodies you use.
