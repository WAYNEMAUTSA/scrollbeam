# Roadmap

Where ScrollBeam is, and where it's headed. Phases are roughly sequential, not strict - things can move between them as priorities shift.

## Phase 0 - Core loop (done, v2.0.0)
- YouTube, Instagram, and TikTok handoff from Android to desktop.
- Firebase relay, Chrome extension, installable phone PWA.
- QR pairing, instant notifications, playlist fallback handling.

## Phase 1 - Harden for real users
The current version works, but assumes patience with rough edges. This phase removes the rough edges.
- [ ] iOS support via the Shortcuts app (Android-only today).
- [ ] Graceful handling of dead/expired links (deleted TikTok, expired Instagram Story).
- [ ] Support more than one paired desktop per phone.
- [ ] Publish to the Chrome Web Store so install doesn't require Developer Mode.
- [ ] Confirm and document Firefox/Edge compatibility.
- [ ] Record and link the setup walkthrough video.

## Phase 2 - Reduce setup friction
The long-term goal is minimum setup, maximum speed. Firebase is a reasonable default, not the ceiling.
- [ ] Local-network mode: phone and desktop talk directly over WiFi, no Firebase project required, when both are on the same network.
- [ ] Script or guided flow that creates the Firebase project and rules automatically, instead of manual console clicking.
- [ ] Signed, store-distributed builds so neither side needs a technical install process.

## Phase 3 - Expand what can be sent
- [ ] More platforms: X/Twitter, Reddit, Threads, Spotify.
- [ ] Generic fallback: any link that isn't a recognized platform still opens as-is, instead of failing.
- [ ] Real file sharing (not just links) - see KNOWN_LIMITATIONS.md and the earlier architecture discussion for why this is a separate effort, not a small addition.

## Phase 4 - Make it discoverable
Only once Phase 1 is solid - a rough first impression is worse than no launch at all.
- [ ] Simple landing page with a demo GIF.
- [ ] Launch posts: r/opensource, Show HN, Product Hunt.
- [ ] Tag a few "good first issue"s so outside contributors have an easy way in.

## Phase 5 - Agent integration (exploratory)
ScrollBeam's relay is, underneath the YouTube-specific logic, a small real-time signal bus between a phone and a desktop. That's useful to more than just a human sharing a link to themselves.
- [ ] Expose the relay as an MCP server with two tools: one to read "what is the user currently engaged with," one to push something to their desktop directly.
- [ ] Explore what this unlocks: an agent that summarizes what you're watching on request, or one that proactively surfaces something relevant as a real notification rather than chat text.

---

Contributions toward any unchecked item are welcome - see CONTRIBUTING via the issue templates, or open a discussion first if the approach needs talking through.