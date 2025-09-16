---
title: "VO Editing"
---

#### Reference Video
For a visual and detailed guide, refer to the video: [Recording and Processing Voiceover or Narration in REAPER](https://www.youtube.com/watch?v=eTNo3yrWGww).

#### Preparation
1. **Download Material**: Ensure you have downloaded [this VO](max-vo.wav) recording to follow along with the editing process in class.
2. **Set Project Parameters**: Confirm that your project is set to 48kHz, 24-bit to avoid mismatches later.
3. **Save a New Project**: Create and save a new project before beginning edits to keep your work organized.

### Noise Removal with ReaFir
1. **Add ReaFir Plugin**: In Reaper, add the ReaFir plugin to your track.
2. **Configure Plugin**: Refer to the provided settings image, and set up your ReaFir plugin accordingly.
   1. ![](reafir.png)
3. **Build Noise Profile**:
   1. Select a part of the recording where only background noise is present (no vocals).
   2. Play this part to allow ReaFir to analyze and build a noise profile.
   3. Once the profile is built, uncheck the option "Automatically build noise profile."
4. **Apply Noise Reduction**: ReaFir will now use the built profile to remove the background noise throughout your recording.
5. **Review**: A/B compare by toggling the plugin on/off to ensure you’ve reduced noise without introducing metallic or watery artifacts.

### Editing
1. **Split Tracks**: Divide your track into separate media items, each representing a phrase or line of dialogue.
2. **Add Fades**: 
    1. Add a fade-in at the start of each item. 
    1. Add a fade-out at the end of each item. 
    1. Ensure the option "Auto-crossfade media items when editing" is enabled in Reaper.
3. **Remove Clicky Noises**:
   1. Identify and remove mouth noises made by the VO artist.
   1. Use the action "Item: Split items at time selection" (Shortcut: Shift + S) for precision.
   1. Replace the removed segment with **room tone** (a short duplicated section of natural silence from the VO track) rather than total silence. This keeps the background consistent and avoids creating distracting dead air.
4. **Ripple Editing (Optional)**:
   1. Enable ripple editing if you need to remove a part of an item and adjust the timing.
   1. Use a razor edit (Option + Right-click drag) to select and remove the undesired part.
5. **Glue Items**: Once satisfied with the edits, glue the items back together to consolidate your changes and simplify the rendering process.

### Effects
1. **EQ**: Apply ReaEQ and configure a high pass filter (around 80–100 Hz) to eliminate unnecessary low frequencies from the voice.
2. **Compression**: Add ReaComp, set a ratio of 4:1, and enable auto makeup gain.
3. **Multiband Compression**: Implement ReaXComp to compress each frequency range of the voice separately.
   - Set a 4:1 ratio for each band.
   - Activate "program dependent release."
   - Use "solo current band" for focused adjustments and set thresholds as needed.
4. **Limiter**: Incorporate ReaLimit and set a brickwall ceiling at -5 dB.
5. **Metering**: Place JS: Loudness Meter Peak/RMS/LUFS (Cockos) on your master track to monitor levels before exporting.
   - Standard LUFS targets:
     - **Podcasts / online spoken word**: around -16 LUFS
     - **Broadcast**: around -23 LUFS
     - **YouTube**: around -14 LUFS  

### Rendering
1. **Review Rendering Settings**:
   1. ![](rendering.png)
2. **Note on Mono Files**: Pay attention to the option _tracks with only mono media to mono files_. Use this to render mono tracks as mono files, saving storage space without compromising quality.
3. **File Naming**: Save rendered files with clear names (e.g., `narration_final.wav`, `line03_character.wav`) for asset management.

### Quick Reference Shortcuts
- Split Item: **S**  
- Split at Time Selection: **Shift + S**  
- Razor Edit: **Option + Right-click drag**  
- Glue Items: **Cmd/Ctrl + Shift + G**  
- Toggle Ripple Editing: **Alt + P**  
- Fade Handles: Hover near top corner of item and drag  

---

These step-by-step instructions are designed to guide you through the VO editing process in Reaper efficiently. For additional tips on removing mouth noises, you can watch [How To Remove Mouth Noises In Your Recordings](https://www.youtube.com/watch?v=r5ki_fo2rlk).

> Extra time?
> Lets edit one of these VOs as a class
> [Freesound](https://freesound.org/search/?q=voice+over&f=&s=Automatic+by+relevance&si_tags=0&si_name=0&si_description=0&si_packname=0&si_sound_id=0&si_username=0&d0=60&d1=*&ig=0&r=0&g=1&dp=0&cm=0&mm=0)

