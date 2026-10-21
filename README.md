# Desk Duel

An original, minimalist pen-fighting game. No build step, backend, runtime dependencies, external fonts, or asset downloads. All gameplay, styling, procedural desk/pen artwork, and synthesized sound live in `index.html`.

## Play / host

Open `index.html` directly, or upload it and `assets/og-banner.png` to any static host (GitHub Pages, Netlify, Cloudflare Pages, or your own web server). The game works from a subdirectory as well as the domain root.

Local preview:

```sh
python3 -m http.server 8000 --bind 0.0.0.0
```

### Social-sharing setup

The included banner is 1200 × 630 PNG. Before publishing:

1. Change both `og:image` and `twitter:image` in `index.html` from `assets/og-banner.png` to the **absolute public HTTPS URL** of that file.
2. Add `<meta property="og:url" content="YOUR_PUBLIC_GAME_URL">` and `<link rel="canonical" href="YOUR_PUBLIC_GAME_URL">` using your actual final URL.
3. Keep the banner publicly accessible without authentication. Social crawlers cache previews; refresh their cache after updating it.

No invented production domain is baked in. The HTML alone is sufficient for gameplay; the PNG is separate because social crawlers need a publicly hosted image.

## Features

- Pull-back flick controls for mouse, pen, and touch, with power and direction preview.
- Canvas physics: friction, pen collisions, momentum transfer, and angular response.
- Computer opponent with three difficulty settings, or same-device two-player play.
- Alternating round starters, scorekeeping, draws, rematches, and confirmed score reset.
- Keyboard controls: focus the desk, left/right to aim, up/down for power, Space to shoot; Escape cancels aiming.
- Optional synthesized audio, fullscreen where supported, native sharing/copy link.
- Responsive desktop and mobile desk layouts, semantic dialogs, focus indicators, live turn announcements.

A pen loses when its **center** leaves the desk. If both leave in one shot, the round is a draw. Scores are session-only. Multiplayer is local, not online. The canvas game is visually oriented, though shots support keyboard input.

## Reference review and originality

The reference page at https://shunneklabs.app/games/pen-fight/ was readable through page extraction. Observed: computer duels, pull-back-and-release instructions, eight-pen selection, levels, Classic/Real choices, four difficulties, equal-level/mirror rules, leaderboard, stats, and settings. Its bundles and visual/runtime behavior were not directly inspected because outbound access to that host was blocked. No claims are made about its internal physics.

Desk Duel uses the general school-desk pen-fighting concept, not copied source or artwork. It removes the selection/progression lobby, uses equal pens, puts the board directly on the page, and adds local pass-and-play. The typography, green/terracotta palette, desk illustration, copy, branding, and code are original to this implementation.

## REA setup

Requested source cloned to `/home/user/rea`. The official `rea-agents` npm package, version 6.7.0, was installed separately at `/home/user/rea-cli`; invoke `/home/user/rea-cli/node_modules/.bin/rea --help`. Its CLI was verified. No MCP integration was registered in Arena, and the blocked reference site prevented REA bundle analysis. REA is not a dependency of the game.

## Validation

JavaScript syntax checked. Headless Chromium smoke checks covered desktop rendering, help/settings dialogs, local mode, keyboard shot and turn transition, reset, difficulty selection, mobile overflow, and pointer drag shooting. No browser errors occurred in these checks. Additional platform-specific testing is recommended for iOS fullscreen/audio and social preview crawlers after deployment.
