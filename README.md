# Parishram Hunt: 3D Coaching Campus Prop Hunt (Android Studio Edition)

[![Platform](https://img.shields.io/badge/Platform-Android%20Studio%20%7C%20Kotlin%20%7C%20Java%20%7C%20NDK-green.svg)](https://developer.android.com/studio)
[![3D Format](https://img.shields.io/badge/Format-glTF%202.0%20Binary%20(.glb)-blue.svg)](https://www.khronos.org/gltf/)
[![License](https://img.shields.io/badge/License-MIT-orange.svg)]()

> Complete 3D realistic assets, map coordinates layout, and Master Game Design Prompt for building **Parishram Hunt** — a 3D Prop Hunt action game set in an authentic Indian Coaching Institute campus (Patna / Kota style).

---

## 📁 Repository Contents

| File / Folder | Description |
| :--- | :--- |
| **[`ParishramHunt_Master_Game_Design_Prompt.txt`](./ParishramHunt_Master_Game_Design_Prompt.txt)** | **The Complete Master Implementation Prompt**. Feed this directly to an AI (Claude / ChatGPT / Gemini) in Android Studio to generate the complete Kotlin/Java game code. |
| **[`ParishramHunt_3D_Assets.zip`](./ParishramHunt_3D_Assets.zip)** | Pre-packaged all-in-one archive containing all 3D models, textures, icons, and layout JSON for instant import into `app/src/main/assets/`. |
| **[`/Characters`](./Characters)** | Rigged & textured 3D character models (`Hunter_Character.glb`, `Prop_Student_Character.glb`, `Hunter_Blaster.glb`). |
| **[`/Map`](./Map)** | Full 2-floor Coaching Building (`CoachingCenter_Shell.glb`) + `map_props_layout.json` (exact coordinates for 100+ prop placements). |
| **[`/Props`](./Props)** | 30 realistic coaching props in glTF `.glb` format (Patna benches, doubt desks, water bottles, backpacks, cycles, chairs, stools, etc.). |
| **[`/Textures`](./Textures)** | PBR material textures (Albedo, Normal, Roughness, Metalness) in `.png` format. |
| **[`/UI_Icons`](./UI_Icons)** | Android app icon assets (Standard & Adaptive Icon layers). |
| **[`/WebPreview`](./WebPreview)** | Three.js interactive 3D WebGL viewer (`index.html`) to preview all models & campus layout in a browser or WebView. |

---

## 🎮 Game Concept & Rules

- **Theme:** Indian Coaching Institute (Classrooms, Doubt Counter, Library, Faculty Room, Cycle Stand, Cafeteria, Reception, Stairs).
- **Match Flow:**
  1. **Hide Phase (60s):** Hunters are blinded at the main campus gate. Disguised student props explore rooms, target objects, and morph into props, locking rotation to blend in.
  2. **Hunt Phase (300s / 5 min):** Hunters equipped with Chalk Blasters hunt disguised students. Shooting static world objects inflicts a **-5 HP Wrong-Hit Penalty** (preventing blind spray-and-pray).
  3. **Abilities:**
     - **Props:** Morph disguise, Rotation Lock, Whistle / Taunt (+50 pts), Decoy Clone, Stun Flash Wave.
     - **Hunters:** Chalk Blaster, Proximity Radar Ping, Sprint Boost, Fatal Shot Cinematic Kill-Cam.
  4. **Winning Conditions:** Props win if at least one survives until time expires; Hunters win if all props are eliminated.

---

## 🛠️ Android Studio Quickstart (Using Sceneview / Filament)

### 1. Place Assets in Project
Copy the `Characters`, `Map`, `Props`, and `Textures` folders into your Android project's:
```
app/src/main/assets/
```

### 2. Add Sceneview Dependency (`app/build.gradle.kts`)
```kotlin
dependencies {
    implementation("io.github.sceneview:sceneview:2.2.1")
    implementation("com.google.android.filament:filament-android:1.43.0")
    implementation("com.google.android.filament:gltfio-android:1.43.0")
}
```

### 3. Load Map & Parse Coordinates
```kotlin
// Load 2-Floor Coaching Center Shell
val campusNode = sceneView.modelLoader.createModelInstance(
    fileLocation = "Map/CoachingCenter_Shell.glb"
)
sceneView.addChildNode(campusNode)

// Parse map_props_layout.json to spawn props at exact X, Y, Z coordinates
val jsonString = context.assets.open("Map/map_props_layout.json").bufferedReader().use { it.readText() }
val layout = Gson().fromJson(jsonString, PropLayoutFile::class.java)

for (prop in layout.props) {
    val propNode = sceneView.modelLoader.createModelInstance("Props/${prop.glb_file}")
    propNode.position = Float3(prop.position.x, prop.position.y, prop.position.z)
    propNode.rotation = Float3(prop.rotation_euler.x, prop.rotation_euler.y, prop.rotation_euler.z)
    propNode.scale = Float3(prop.scale.x, prop.scale.y, prop.scale.z)
    sceneView.addChildNode(propNode)
}
```

---

## 📜 Full Specification Prompt

Read the complete engineering prompt with dual-zone mobile input math, procedural audio PCM synthesis formulas, and offline bot state machines in:
👉 **[`ParishramHunt_Master_Game_Design_Prompt.txt`](./ParishramHunt_Master_Game_Design_Prompt.txt)**
