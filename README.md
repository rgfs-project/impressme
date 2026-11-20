# Strange Attractors

A zero-dependency, real-time visualizer for chaotic dynamical systems. Thousands of particles are integrated every frame and drawn as glowing trails, so each streak is a real trajectory through the system's state space.

Open `index.html` in any modern browser. Nothing to install, no build step.

## Systems

| System | Type | Notes |
| --- | --- | --- |
| Lorenz | 3D flow (RK4) | Classic butterfly; `σ`, `ρ`, `β` |
| Rössler | 3D flow (RK4) | Folded band; `a`, `b`, `c` |
| Thomas | 3D flow (RK4) | Cyclically symmetric; `b` |
| Clifford | 2D map | Iterated map; `a`, `b`, `c`, `d` |
| De Jong | 2D map | Iterated map; `a`, `b`, `c`, `d` |

Every parameter has a slider. **Randomize** samples new parameters across each system's stable-to-chaotic range, which is where most of the interesting shapes live.

## Controls

- **Drag** to rotate 3D systems. **Scroll** to zoom.
- **Space** pause / play
- **R** randomize parameters
- **E** reseed particles
- **S** save the current frame as PNG
- **H** hide / show the control panel

## How it works

- Flow systems are integrated with classic fourth-order Runge-Kutta. Maps are iterated directly.
- Particles that diverge, collapse to a fixed point, or get randomly refreshed are reseeded, which keeps the image alive indefinitely.
- Color is driven by speed (normalized by an adaptive maximum), depth along the view axis, or particle index. Five palettes are included.
- Trails come from a translucent fade over an additive (`lighter`) composite, so dense regions glow naturally.
- The canvas is HiDPI-aware (capped at 2×).

## Files

- `index.html`: the entire application, with inline CSS and JavaScript.
- `README.md`: this file.
