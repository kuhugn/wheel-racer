# Genesis submission checklist — Wheel Racer

Reference: <https://squeekchain.com/genesis/code> (read 2026-11-04).

## Before submitting

- [x] Game live at a public URL: <https://kuhugn.github.io/wheel-racer/>
      (GitHub Pages, enabled 2026-11-04 — the final DNS verify still needs
      Hùng's own custom domain; github.io cannot take the DNS record)
- [x] Public GitHub repository with this code + README:
      <https://github.com/kuhugn/wheel-racer>
- [ ] Genesis profile ready: wallet verified (a normal wallet, not a
      smart-contract wallet) + X account linked

## Direct submission (free)

1. Start the submission on the Genesis page and note the three values given:
   - [ ] DNS record → add to the domain's DNS
   - [ ] Page tag → replace the `SQUEEKCHAIN-GENESIS-TAG` comment in
         `index.html` `<head>` with it
   - [ ] Repository line → add to `README.md`
2. Push, wait for the site to redeploy, click **Verify**.
3. Auto-checks (complete build + Squeekchain integration) run first; team
   review lists the project on the board; Swarm Review (IMD AI panel)
   decides the *Squeek of Approval*.

## Keep it alive

Verification is re-checked daily — the live site, the repository and the
DNS record must stay up or the project (and its badge) drops.

## Notes for reviewers (what to try)

- Race while the wheel spins: your kart's top speed tracks the real RPM
  shown in the HUD gauge and the side panel.
- Press **Simulate nap**: the engine dies for 12 s while the ghost keeps
  racing — hold SPACE to pedal through it.
- The ghost's pace is not random per player: it is seeded by the settled
  round + block height in the settlement anchor, and the panel links the
  settlement transaction so the seed can be verified on Sepolia Etherscan.
