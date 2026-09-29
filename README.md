# autoDL-videogen-skill

Codex skill for generating video with AutoDL Art's MiniMax H3 ComfyUI workflows:

- Text-to-video: `minimax_h3_lightx2v_no_pic`
- Multi-image reference video: `minimax_h3_lightx2v_v5`
- First and last frame video: `minimax_h3_lightx2v`

The AutoDL skill includes workflow input schemas, duration and resolution limits, result polling, and credential handling. See [SKILL.md](SKILL.md) for instructions and [workflow reference](references/workflows.md) for API details.

This repository also includes [song-to-hype-mv](skills/song-to-hype-mv/SKILL.md), which uses imagegen and AutoDL MiniMax H3 to turn a supplied song into a finished MV. It calls for varied, nonrepeating scenes and timed subtitles; songs in a language other than Chinese receive original-language and Chinese subtitles.

To install, copy the repository root into `~/.codex/skills/autodl-minimax-h3-video/` and `skills/song-to-hype-mv/` into `~/.codex/skills/song-to-hype-mv/`. Store the AutoDL ComfyUI token in an operating-system credential store or another local secret channel; do not commit it to this repository.
