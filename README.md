# ManiacGaming.Online - Interactive Effects Guide

## Project Overview
**ManiacGaming**: AI gaming coach and analytics platform

**Domain**: maniacgaming.online  
**Theme**: Competitive gaming / Chaos → Discipline  
**Colors**: Black (#0a0a0a), Aggressive Red (#ff3333)

---

## Visual Effects

### Background Animation
**Triangle Chaos Grid** - Inverted chaos/order philosophy

**Effect Type**: SVG-based triangle grid with chaos→order→chaos cycle

### Pattern Structure
- **Triangles**: 40×40px, alternating up/down orientation
- **Pattern**: ▲▼▲▼ (col + row) % 2 determines direction
- **Base color**: Dark red-brown (#4a1a1a)
- **Initial state**: CHAOTIC (random rotations, random orientations)

### Auto Wave Pulse
- **Trigger**: Automatic, every 2.5-6 seconds (random interval)
- **Initial State**: Triangles in random chaos
  - Random rotations (0-360°)
  - Random orientations (up/down regardless of grid position)
- **Wave Behavior**:
  - Wave originates from random position
  - **Chaos → Order**: Triangles align to proper ▲▼▲▼ pattern
  - Rotation → 0° (perfect alignment)
  - Color flash red (#ff3333)
  - Scale increases (1.0 → 1.2)
- **After Wave**: Return to chaos
  - Random rotations again
  - Random orientations again
  - Entropy restored
- **Duration**: 600ms alignment, then back to chaos
- **Visual**: Order imposed momentarily, then chaos reclaims

### Click Interaction
- **Trigger**: User clicks anywhere on background
- **Behavior**:
  - Wave originates from click position
  - **Stronger order effect**: 
    - Scale 1.3x (vs 1.2x auto)
    - Perfect ▲▼▲▼ alignment
    - Bright red flash
  - Convert chaos → order at click point
  - Propagates outward by distance
  - Then returns to chaos
- **Duration**: 600ms per triangle
- **Visual**: Player imposes discipline/control, then loses it

### Technical Implementation
```javascript
// Initial chaos setup
triangles.forEach(tri => {
    tri.rotation = Math.random() * 360;
    tri.orientation = Math.random() > 0.5 ? 'up' : 'down';
});

// Wave brings order
function orderWave(startCol, startRow) {
    triangles.forEach(tri => {
        const orderedOrientation = (tri.col + tri.row) % 2 === 0 ? 'up' : 'down';
        const distance = calculateDistance(tri, start);
        
        setTimeout(() => {
            tri.orientation = orderedOrientation; // Correct pattern
            tri.rotation = 0; // Aligned
            tri.color = '#ff3333';
            tri.scale = 1.2;
            
            setTimeout(() => {
                // Return to chaos
                tri.rotation = Math.random() * 360;
                tri.orientation = Math.random() > 0.5 ? 'up' : 'down';
                tri.scale = 1;
            }, 600);
        }, distance * 50);
    });
}
```

---

## Philosophy: Chaos ↔ Order

### Metaphor
**Gaming = taming chaos**
- Base state: Chaos (unpredictable enemies, random events)
- Player input: Order (strategy, discipline, control)
- Reality: Chaos returns (you can't maintain perfect control)

### Visual Representation
```
Chaos (default)     →    Order (wave)     →    Chaos (after)
Random rotations    →    Perfect ▲▼▲▼     →    Random again
Random orientations →    Grid aligned     →    Random again
```

**Player's role**: Momentarily impose order through clicks, but chaos is inevitable

---

## Interaction Levels

### Passive (Auto Waves)
- Chaos briefly becomes order
- Represents AI/system trying to organize
- Order is temporary
- Chaos is the natural state

### Active (Click)
- **You** impose order
- Stronger effect (scale 1.3 vs 1.2)
- **You** are the discipline
- But even your control fades

---

## Comparison to Other Sites

| Site | Philosophy | Effect |
|------|-----------|--------|
| **ManiacGaming** | Chaos → Order → Chaos | Player imposes control temporarily |
| ModUrWall | Order → Chaos → Order | Wave disrupts, then settles |

**Inverted concepts:**
- ManiacGaming: Order is the exception
- ModUrWall: Chaos is the exception

---

## Color Palette

| Element | Color | Hex | Usage |
|---------|-------|-----|-------|
| Background | Black | #0a0a0a | Pure black |
| Text | White | #ffffff | High contrast |
| Accent | Aggressive Red | #ff3333 | Triangles when ordered |
| Base | Dark Red-Brown | #4a1a1a | Triangle base color |
| Dim | Dark Gray | #666666 | Secondary text |

**Ultra-competitive aesthetic**: High contrast, aggressive red, no softness

---

## Technical Details

### Triangle Orientation Logic
```javascript
// Correct pattern (order state)
isUpward = (col + row) % 2 === 0;
points = isUpward ? "20,5 38,35 2,35" : "20,35 38,5 2,5";

// Chaos state (random)
points = Math.random() > 0.5 ? upPoints : downPoints;
```

### Distance Propagation
```javascript
distance = √[(col₂-col₁)² + (row₂-row₁)²]
delay = distance × 50ms
```

---

## User Experience Flow

1. **Landing**: Chaotic triangle field (unpredictable)
2. **Observation**: Auto waves briefly organize (system attempts order)
3. **Interaction**: Click imposes your discipline (player control)
4. **Reality**: Chaos returns (gaming truth: you can't control everything)
5. **Message**: "where chaos meets discipline" - both are necessary

---

## Design Philosophy

**Theme**: Competitive gaming + Chaos theory
- Triangles = aggressive, sharp (vs soft hexagons)
- Chaos default = unpredictability of competition
- Order moments = skill/discipline in gameplay
- Return to chaos = humility (even pros lose control)
- Click = you are the discipline

**Not about winning, about managing chaos**

---

**Last Updated**: 2024-12-17  
**Status**: Live  
**Latest Version**: `maniacgaming-scrollable.html`  
**Tagline**: "where chaos meets discipline"
