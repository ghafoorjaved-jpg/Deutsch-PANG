# Deutsch-PANG — 60-Stage Pang-Style German Learning Game

A single-page mobile-first browser game inspired by classic Pang: move with the analog joystick, fire a rocket, read German word balloons, dodge bouncing hazards, and learn through English → German prompts.

## Included in this build
- 60 stages: 10 each for A1, A2, B1, B2, C1 and C2
- Start directly at any CEFR level
- German city/location scenes with German flag indicator
- Slow, readable glossy balloons with separate high-contrast German word cards
- English learning prompt and English meaning support
- Destructible hazard balloons that split into smaller, still-shootable balloons
- Rocket-style FIRE projectile with generated pop/firework sounds
- Wrong answer and player collision cost 1 life with warning sound
- Exactly 2 lives triggers one green +3 LIVES bonus balloon per stage
- Correct answer clears the stage and advances automatically
- Local progress, XP and streak persistence
- Analog joystick on the left and rocket FIRE button on the right
- Network-first service worker with versioned cache to reduce stale GitHub Pages builds

## GitHub Pages deployment
Upload these four files to the repository root:
- `index.html`
- `manifest.json`
- `service-worker.js`
- `README.md`

If an older version still appears on iPhone Safari after deployment, close the old tab and open the Pages URL in a private tab once. The new service worker is network-first and removes older caches after activation.
