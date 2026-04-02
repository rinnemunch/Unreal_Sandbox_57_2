# Project 1 - Enum Driven Material State System

## 🖼️ Preview

![Project 1](Media/1.gif)

## 🧱 Features

**Enhanced Input Setup**

- IA_ColorSwap input action created using Axis1D (Float)
- Single input action used to drive multiple states
- Number keys 1–4 mapped inside IMC_Default
- Scalar modifiers applied to generate distinct values per key
  - Key 1 → 1.0 (Default)
  - Key 2 → 2.0 (Red)
  - Key 3 → 3.0 (Blue)
  - Key 4 → 4.0 (Green)

**Enum-Based State System**

- E_CharacterMaterial enum created to represent material states
  - Default
  - Red
  - Blue
  - Green
- CurrentMaterialType variable added to character blueprint
- Enum used as the single source of truth for visual state

**Material Organization**

- Dedicated folders created for each color variation
  - Red / Blue / Green
- Quinn material instances duplicated and organized per state
- Base Color Tint enabled and adjusted per material instance
- Matching material pairs maintained for both mesh slots

**Centralized Update Function**

- UpdateMaterial function created to handle all material logic
- Switch on E_CharacterMaterial used to drive behavior
- Each state applies a full material pair to the character mesh
- Two Set Material nodes used per state
  - Element 0 → Material 01
  - Element 1 → Material 02
- Logic separated from input for clarity and scalability

**Input to State Flow**

- IA_ColorSwap triggered event drives logic execution
- Action Value converted using Truncate (Float → Int)
- Switch on Int maps values to enum states
- Enum updated based on input selection
- UpdateMaterial function called after each state change

---

## 🚀 Result

A clean, reusable enum-driven system where input controls state, and state drives behavior.

The character updates instantly when pressing keys 1–4, demonstrating a scalable pattern for handling gameplay states such as materials, animations, weapons, or UI logic. 

---

# Project 2 – First Person Zoom System

## 🖼️ Preview

![Project 2](Media/2.gif)

## 🧱 Features

**Camera Zoom System**

- Field of View driven zoom mechanic  
- Smooth transition between default and zoomed states  
- Adjustable FOV values for different gameplay scenarios  

**Timeline-Based Interpolation**

- Timeline used to control zoom duration  
- Length set to 0.30 seconds for responsive feel  
- Forward play on input press, reverse on release  

**Float Track Animation**

- Custom float track (Inspect_Track) drives zoom alpha  
- Values range from 0 → 1 for full interpolation control  
- Auto interpolation for smooth ease in and ease out  

**Lerp Integration**

- Lerp (Float) blends between two FOV values  
- A = 90 (default camera view)  
- B = 60 (zoomed view)  
- Timeline output connected to Alpha for smooth blending  

**Input Handling**

- Simple keyboard input for triggering zoom  
- Press → zoom in  
- Release → zoom out  

**Reusable Blueprint Logic**

- Implemented inside BP_FirstPersonCharacter  
- Easily transferable to other character types  
- Works with both First Person and Third Person setups  

---

## 🚀 Result

A clean and reusable first person zoom system that smoothly transitions using a Timeline and Lerp. The setup avoids harsh camera jumps and provides a polished feel suitable for aiming, inspecting objects, or enhancing player control.

--- 

# Project 3: Quixel Megascans Asset Import System

## 🖼️ Preview

![Project 3](Media/3.gif)

## 🧱 Features

**Quixel / Fab Integration**

- Accessed Quixel assets through the Fab marketplace inside Unreal Engine
- Used “Add to Project” workflow for direct asset importing
- Logged into Epic account to sync asset library

**Megascans Asset Workflow**

- Imported high-quality scanned assets (rocks, food, props, etc.)
- Automatically generated materials and textures on import
- Assets organized inside `Content/Fab/Megascans` directory

**Asset Validation System**

- Identified usable assets via standard formats (FBX, GLB)
- Avoided unsupported assets labeled:
  - UEFN (Unreal Editor for Fortnite)
  - Reference-only content
- Ensured compatibility with standard Unreal Engine projects

**Library & Content Management**

- Added assets to Fab Library for reuse across projects
- Accessed assets through Content Drawer → Fab tab
- Maintained clean folder structure for scalability

**Quality Control & Optimization**

- Selected asset quality levels:
  - Raw / High / Medium / Low
- Balanced visual fidelity with performance impact
- Noted storage and performance considerations for high-detail assets

**Scene Integration**

- Dragged static meshes directly into the level
- Adjusted:
  - Scale
  - Rotation
  - Positioning
- Quickly prototyped realistic environments using Megascans

---

## 🚀 Result

Successfully implemented a reliable workflow for importing and validating Quixel Megascans assets in Unreal Engine, while avoiding incompatible UEFN content and maintaining optimized project performance. 

--- 

# Project 4: Dual Directional Light Lighting System

## 🖼️ Preview

![Project 4](Media/4.gif)

## 🧱 Features

**Multi-Light Directional Setup**

- Added a second Directional Light to the scene for enhanced lighting control
- Configured dual-light system to simulate multiple light sources (sun + fill)
- Maintained compatibility with Unreal’s sky and atmosphere system

**Forward Shading Configuration**

- Resolved multiple directional light conflict warning
- Set Forward Shading Priority to ensure proper light contribution
- Prevented rendering issues with volumetric fog, water, and translucency

**Atmosphere Light Index System**

- Primary light set to Atmosphere Sun Light Index 0
- Secondary light set to Atmosphere Sun Light Index 1
- Enabled Unreal’s dual-sun support for advanced lighting setups

**Dynamic Lighting Control**

- Set both lights to Movable for real-time adjustments
- Controlled primary light using:
  - CTRL + L (viewport rotation)
- Controlled secondary light using:
  - CTRL + SHIFT + L
- Used manual transform rotation when viewport controls failed

**Lighting Composition & Positioning**

- Positioned lights to shape highlights and shadow direction
- Used secondary light as fill to enhance contrast
- Balanced scene lighting for stylized or realistic results

**Color Temperature System**

- Enabled Use Temperature for both lights
- Applied contrasting values:
  - Cool light (12000K) for ambient sky tone
  - Warm light (1700K) for sunset-style highlights
- Created visual depth through warm vs cool contrast

**Performance Awareness**

- Noted performance cost of movable lights
- Encouraged balancing quality with runtime efficiency

---

## 🚀 Result

Implemented a flexible dual directional lighting system that provides full control over scene mood, contrast, and realism using independent light sources and temperature-based color blending.

--- 

# Project 5: Landscape Layer Blend Painting System

## 🖼️ Preview

![Project 5](Media/5.gif)

## 🧱 Features

**Landscape Creation & Setup**

- Created new level using Basic template
- Generated landscape using default settings
- Sculpted terrain with height variation for painting visibility

**Layered Landscape Material**

- Created `M_LandscapeMaterials` for multi-texture blending
- Added Landscape Layer Blend node for paintable layers
- Defined multiple layers with clear naming conventions (no spaces)

**Texture Blending System**

- Connected Base Color textures to corresponding layer inputs
- Duplicated Layer Blend node for Normal map support
- Linked outputs to material Base Color and Normal inputs

**Material Optimization**

- Enabled Fully Rough to remove unwanted surface reflections
- Ensured natural appearance for grass and rock materials

**Layer Info & Paint System**

- Generated layers using “Create Layers from Assigned Materials”
- Created Weight-Blended Layer Info assets for smooth transitions
- Stored Layer Info assets in organized `LandscapeMaterials` folder

**Landscape Painting Workflow**

- Painted secondary texture layers directly onto terrain
- Blended textures dynamically for natural transitions
- Observed real-time material updates during painting

**Scalable Material System**

- Built foundation for adding additional texture layers
- Maintained reusable structure for complex environment design

---

## 🚀 Result

Implemented a fully functional landscape painting system using layer blend materials, enabling smooth multi-texture terrain blending and scalable environment creation workflows.
