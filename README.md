# Dawn Makes Motion

A DUSK Supply plugin for Claude Code and Cowork that runs faceless YouTube channels end to end: niche research, branding, 90-day planning, scripting, narration and captions, rendering (Remotion + FFmpeg), Shorts clipping, heuristic scoring and pre-publish QA.

The plugin holds the commands, skills, agents and safety gates. The rendering engine lives in a separate template repository that `/setup-engine` clones into your project with your approval: [DUSK-supply/dawn-makes-motion-template](https://github.com/DUSK-supply/dawn-makes-motion-template).

## Install

```
/plugin marketplace add DUSK-supply/dawn-makes-motion
/plugin install dawn-makes-motion@dusk-supply
```

Then, in an empty project folder:

```
/dawn-makes-motion:setup-engine
```

With your approval at each step, setup checks Node 24, npm, git and ffmpeg; clones the engine template; runs `npm ci`; optionally installs the Higgsfield CLI and skills for image/video generation (you complete sign-in in your browser); optionally installs local whisper.cpp for transcription; then validates and writes `output/engine-status.md`. A session-start check reminds you while anything is missing.

## Requirements

- Claude Code or Cowork
- Node 24, npm, git; ffmpeg for render, clip and caption steps
- Optional API keys in the project's `.env` (never committed): `ELEVENLABS_API_KEY`, `PEXELS_API_KEY`, `PIXABAY_API_KEY`, and an LLM key for headless use. The core workflow needs no paid service.

## Commands

| Command | Does | Needs shell |
|---|---|---|
| `setup-engine` | First-run setup: prerequisites, engine template, Higgsfield, optional extras | yes |
| `init-channel` | Channel identity, brand tokens, strategy pack, first 12 ideas | no |
| `plan-content` | 13-week hypothesis plan with checkpoints and calendar | no |
| `script-video` | Brief, sources, sourced script, scene manifest, visual notes | no |
| `build-video` | Narration (generated or your recording), render, captions, ffprobe report | yes |
| `clip-shorts` | Standalone vertical Shorts from your own long-form render | yes |
| `qa-publish` | Originality, sourcing, disclosure, licence and stock-share gate; never uploads | no |
| `score-viral` | Heuristic packaging/retention score (not a prediction) | no |

Skills: niche-research, brand-identity, 90-day-planning, scriptwriting, packaging, shorts-clipping, policy-and-monetisation-qa.
Agents: strategist, researcher, producer, editor, compliance (read-only).

## Safety gates

Hooks block, with a readable reason, when:

- a script is written without a channel config, brief and source list (`pre-script-check`);
- a render starts without ffmpeg or a schema-valid scene manifest (`pre-render-check`);
- a video is approved or packed for upload with a failed QA report or undisclosed affiliate links (`pre-publish-check`).

Paid generation, stock downloads and installs always ask first. Nothing is uploaded or posted by the plugin. Every downloaded stock clip gets a row in the channel's `assets/LICENSES.md`.

## Limits

- Scores are heuristics; nothing here guarantees views, monetisation or income.
- You are responsible for YouTube policies, disclosure rules and the law where you publish. Platform rules quoted in the plugin are marked VERIFY until checked against official sources.
- English-language content only.

## Licence and credits

MIT. Copyright (c) 2026 DUSK Supply, operated by DUSK Enterprises. See [LICENSE](LICENSE).
Parts of the narration, caption alignment, provider and stock-footage engines are adapted from MoneyPrinterTurbo (MIT): see [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Support

hello@dusk.supply
