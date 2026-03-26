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