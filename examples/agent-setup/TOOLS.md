# TOOLS.md - Tool SOP Index

## ⚠️ URL Routing — DO NOT skip this

**Before calling `web_fetch` on ANY URL, check this table:**

| Domain | `web_fetch` works? | Use instead |
|--------|-------------------|-------------|
| `x.com`, `twitter.com` | ❌ NEVER | `https://api.fxtwitter.com/<user>/status/<id>` via `web_fetch`, or xAI `x_search` via `exec` |
| `reddit.com` | ❌ Usually blocked | SearXNG: `curl localhost:8899/search?q=site:reddit.com+QUERY&format=json` |
| JS-heavy / Cloudflare | ❌ Often fails | `browser` tool or Safari via osascript |

Full routing SOP: `ops/playbooks/tools/sops/web-search.md`

---

Tool index only. Before using a tool for the first time, check the Tools Playbook
(`ops/playbooks/tools/tools-playbook.md`) and the linked SOPs before inventing a new way to do it.
The workflow may already exist.

## Tool Reference

- Opik (observability) -> `ops/playbooks/tools/sops/opik-local-selfhost.md`
- 1Password -> `ops/playbooks/tools/sops/1password.md`
- KeePassXC agent vault -> `ops/playbooks/tools/sops/keepassxc-vault.md`
- Secret handling (anti-leak) -> `ops/playbooks/tools/sops/secret-handling.md`
- Sudo access -> `ops/playbooks/tools/sops/1password.md`
- Nostr / nak CLI -> `skills/nipslip/` (skill, canonical) + `docs/sovereign-tech/nostr-ops.md` (identity/policies)
- Web search -> `ops/playbooks/tools/sops/web-search.md`
- Model switching -> `ops/playbooks/tools/sops/model-switching.md`
- Safari browsing -> `ops/playbooks/tools/sops/safari-browsing.md`
- Telegram formatting -> `ops/playbooks/tools/sops/telegram-formatting.md`
- X / Twitter fetching -> `ops/playbooks/tools/sops/web-search.md`
- URL fallback (markdown.new) -> `ops/playbooks/tools/sops/web-search.md`
- mflux (local image gen) -> `ops/playbooks/tools/sops/mflux.md`
- Lightning / Alby Hub -> `docs/sovereign-tech/lightning-bitcoin-ops.md`
- Lightning Lottery -> `docs/sovereign-tech/lightning-lottery.md`
- Hevy workout writeback -> `ops/playbooks/tools/sops/hevy-workout-writeback.md`
- Tor (proxy + .onion access) -> `ops/playbooks/tools/sops/tor-ops.md`
- NymVPN -> `ops/playbooks/tools/sops/nymvpn.md`
- Tailscale -> `ops/playbooks/tools/sops/tailscale.md`
- [LOCAL_MACHINE_SLUG] / local host -> `ops/playbooks/tools/sops/local-host.md`
- SearXNG -> `ops/playbooks/tools/sops/web-search.md`
- Workspace Inbox -> `ops/playbooks/tools/sops/workspace-inbox.md`
- Email -> `ops/playbooks/tools/sops/email.md`
- Session recovery -> `ops/playbooks/tools/sops/session-recovery.md`
- Rehydration after restart -> `ops/playbooks/tools/sops/rehydration-after-restart.md`
- Session miner -> `ops/playbooks/tools/sops/session-miner.md`
- OpenClaw upgrade cutover -> `ops/playbooks/tools/sops/openclaw-upgrade-cutover.md`
- Self-assessment -> `ops/playbooks/tools/sops/self-assessment.md`
- Dan Martell KB -> `ops/playbooks/tools/sops/dan-martell-kb.md`
- Browser auth & account login -> `ops/playbooks/tools/sops/browser-auth.md`
- BlueBubbles (transport) -> `ops/playbooks/tools/sops/bluebubbles.md`
- BlueBubbles group chat flow/mention gating -> `ops/playbooks/tools/sops/bluebubbles-group-chat.md`
- Isolated agents runtime -> `ops/playbooks/delegation/sops/isolated-agents-runtime.md`
- Package / skill install -> `ops/playbooks/tools/sops/package-install-verification.md`
- Morning review protocol -> `ops/playbooks/decisions/sops/decision-session-mining.md`

## Node Access

- Node name: `[AGENT_SLUG]'s [LOCAL_MACHINE_SLUG]`
- Verify exact name with `openclaw devices list` if needed
- Use `bash -l -c` or source the shell env when env vars matter

## [LOCAL_MACHINE_SLUG] Guardrail

- OpenClaw runs on the [LOCAL_MACHINE_SLUG] (`[LOCAL_HOST_IP]`)
- Do not SSH into `[LOCAL_HOST_IP]` from inside the local agent session
- Do not ping `[LOCAL_HOST_IP]` to check if it is online while responding from that same host
- Do not report the [LOCAL_MACHINE_SLUG] as offline while responding from it
- Use `exec` directly for local commands
- Old host: `[OLD_HOST_SLUG]` (`[OLD_HOST_IP]`)
