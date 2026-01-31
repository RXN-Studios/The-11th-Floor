# Technical Requirements (Java Focus)

This document outlines the architectural logic required to facilitate the "Architectural Gaslighting" mechanics.

## 🔳 Grid System
The game utilizes a robust **2D array system** where each cell holds complex metadata:
* **Tile Type:** Wall, Floor, Warp Trigger, Anchor Point.
* **Metadata:** Room dimensions and procedural "Theme" tags.
* **Warp Trigger:** Boolean flags that signal the engine to swap the tile data.

## 🌀 Non-Euclidean Logic (The "Turn-Around" Script)
To create impossible spaces, the engine uses **Lazy Loaded Geometry**:
* When a tile moves out of the player's visibility radius, the underlying array data is swapped.
* If a player moves in a straight line for a set number of units, the path behind them is replaced with a wall or an entirely different room layout.

## 🌫️ Visibility Engine
A custom **"Fog of War"** layer determines which tiles are safely hidden from the player's view. This prevents "pop-in" and ensures the environment shifts only when it is not being observed.

## 🗃️ State Management
The engine tracks:
* **Documented vs. Active Anomalies:** To manage player progression and "Lock" earned points.
* **Grounding Levels:** To trigger visual tearing, flickering lights, and audio hallucinations.
