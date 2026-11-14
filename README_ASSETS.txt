================================================================================
PARISHRAM HUNT - 3D ASSETS EXPORT PACKAGE (FOR ANDROID STUDIO / NATIVE 3D)
================================================================================

This package contains all realistic 3D models, textures, animations/rig targets,
props, environment architecture, and coordinate placement data for building 
"Parishram Hunt" (Coaching Campus 3D Prop Hunt Game) in Android Studio.

DIRECTORY STRUCTURE:
--------------------------------------------------------------------------------
1. /Characters
   - Hunter_Character.glb      : Complete 3D humanoid character for the Hunter team.
   - Prop_Student_Character.glb: Complete 3D student character for the Prop team.
   - Hunter_Blaster.glb        : 3D Chalk Blaster weapon attached to Hunter hand.

2. /Map
   - CoachingCenter_Shell.glb  : Complete 2-story coaching campus building shell 
                                 (Ground Floor + 1st Floor: Classrooms, Doubt Counter,
                                  Library, Faculty Room, Cycle Stand, Corridors, Stairs).
   - map_props_layout.json     : Exact 3D world coordinates (X, Y, Z), rotations (pitch,
                                 yaw, roll), and scales for all 100+ prop placements 
                                 and room labels. Can be parsed directly in Kotlin/Java.

3. /Props (30 glTF 2.0 Binary models - standard .glb)
   - Prop_Backpack_Navy.glb, Prop_Backpack_Red.glb
   - Prop_BookStack.glb, Prop_Bucket.glb, Prop_CardboardBox.glb
   - Prop_Chair_Blue.glb, Prop_Chair_Red.glb, Prop_CoffeeMug.glb
   - Prop_Cycle_Black.glb, Prop_Cycle_Blue.glb, Prop_Cycle_Red.glb
   - Prop_DeskLamp.glb, Prop_DoubtDesk.glb
   - Prop_Dustbin_Blue.glb, Prop_Dustbin_Green.glb
   - Prop_FireExtinguisher.glb, Prop_GasCylinder.glb, Prop_Helmet.glb
   - Prop_LunchBox.glb, Prop_OfficeChair.glb, Prop_PatnaBench.glb
   - Prop_PlasticStool.glb, Prop_PottedPlant.glb, Prop_Printer.glb
   - Prop_ShoeRack.glb, Prop_TeaKettle.glb
   - Prop_WaterBottle_Blue.glb, Prop_WaterBottle_Green.glb
   - Prop_WaterCooler.glb, Prop_WoodenCrate.glb

4. /Textures
   - PBR Materials (Albedo, Normal, Roughness) in standard PNG format:
     pbr_concrete_albedo.png, pbr_concrete_normal.png
     pbr_tile_albedo.png, pbr_tile_normal.png, pbr_tile_rough.png
     pbr_wood_albedo.png, pbr_wood_normal.png, pbr_wood_rough.png
     pbr_granite_albedo.png, pbr_granite_normal.png
     pbr_wall_cream.png, pbr_wall_normal.png, pbr_wall_skirt.png
     pbr_notice_board.png, pbr_whiteboard_notes.png, pbr_gate_sign.png, etc.

5. /UI_Icons
   - ParishramHuntIcon.png             : 512x512 High-res app logo.
   - ParishramHuntIcon_AdaptiveBg.png  : Android Adaptive Icon background layer.
   - ParishramHuntIcon_AdaptiveFg.png  : Android Adaptive Icon foreground layer.

6. /WebPreview
   - index.html: Interactive Three.js WebGL 3D previewer to inspect the full campus 
                 and prop interactions in any browser or Android WebView!

FORMAT COMPATIBILITY FOR ANDROID STUDIO:
--------------------------------------------------------------------------------
- Models are in standard glTF 2.0 Binary (.glb) format.
- Loadable in Android Studio using:
  * Google Filament (io.github.sceneview:sceneview or com.google.android.filament)
  * LibGDX (gdx-gltf library)
  * Android NDK (OpenGL ES 3.0 / Vulkan with tinygltf or assimp)
  * Android WebView with Three.js / Babylon.js / Model-Viewer
================================================================================
