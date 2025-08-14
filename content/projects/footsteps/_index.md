---
title: "Intermediate Project: Terrain-Aware Footsteps with FMOD (Unity Terrain)"
---

# Intermediate Project: Terrain-Aware Footsteps with FMOD (Unity Terrain)

**Purpose**  
Create a third-person footstep system that selects the correct FMOD footstep variant based on the dominant Unity Terrain texture under the player. The active texture index will be mapped to an FMOD parameter that switches materials (e.g., grass, rock, dirt).

---

**Prerequisites**  
- Unity project with a Terrain using at least 3 painted textures  
- FMOD for Unity integrated; a Footstep event with:
  - A parameter named `Material` (integer or labeled) that switches among surface types  
  - Variation (multi-instrument or scatterer) per material  
- A working third-person controller

---

**Learning Outcomes**  
- Query the active Terrain texture index at a world position  
- Map texture indices to an FMOD parameter to drive audio behavior  
- Trigger footsteps in sync with locomotion

---

**What You’ll Build**  
A scene where your character walks/runs across a Unity Terrain and the footsteps audibly change to match the surface.

The system should:  
- Read the dominant splatmap texture at the foot contact point (or character root)  
- Convert that texture index to an FMOD `Material` parameter value  
- Trigger the Footstep event in time with animation or movement

---

**Minimum Implementation Checklist**  
- Terrain setup: Paint at least 3 distinct textures into clearly separated zones  
- Detector: Given a `Vector3 worldPos`, find the Terrain, convert to splatmap UV, read splat weights, and return the index of the highest weight  
- Mapper: Translate texture index to FMOD parameter value via a serializable mapping  
- Footstep triggering: Trigger steps via animation events or a speed-based timer and set the `Material` parameter before playing the FMOD event  
- Edge cases: Default to a safe material if no Terrain is found and pick the dominant texture when multiple overlap

---

**Constraints**  
- Do not add separate colliders or tags for surfaces  
- Use the Terrain’s texture data for material detection  
- Keep mapping data editable in the Inspector

---

**Hints**  
- Use `Terrain.activeTerrain` to access the terrain  
- Convert world position to terrain local position, then to alphamap coordinates  
- Use `GetAlphamaps()` to fetch weights at a single texel and select the index with the largest weight  
- Inspector-based mapping makes it easy to adjust materials without changing code

---

**Deliverables**  
- Unity scene showing the system in action  
- Two scripts:
  - `TerrainTextureDetector`
  - `FootstepSurfaceDriver`  
- README including:
  - Texture-to-material mapping table  
  - Short explanation of triggering method  
  - Any known limitations

---

**Rubric (50 points)**  
- Detection correctness (15 pts): Correctly identifies the dominant texture index across painted terrain regions  
- FMOD integration (15 pts): Parameter changes result in correct surface sounds with variation  
- Timing and feel (10 pts): Footsteps align naturally with character movement  
- Documentation and organization (10 pts): README is clear, mapping is documented, and project is well-structured

---

**Extensions (Optional for Bonus)**  
- Blend top two textures into a weighted FMOD parameter  
- Per-foot sampling for boundary accuracy  
- Sync particle effects with footfalls for visual feedback
