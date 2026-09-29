# autoDL-videogen-skill

Codex skill for generating video with AutoDL Art's MiniMax H3 ComfyUI workflows:

- Text-to-video: `minimax_h3_lightx2v_no_pic`
- Multi-image reference video: `minimax_h3_lightx2v_v5`
- First and last frame video: `minimax_h3_lightx2v`

The skill includes workflow input schemas, duration and resolution limits, result polling, and credential handling. See [SKILL.md](SKILL.md) for instructions and [workflow reference](references/workflows.md) for API details.

To install, copy this repository's files into a folder under `~/.codex/skills/`. Store the AutoDL ComfyUI token in an operating-system credential store or another local secret channel; do not commit it to this repository.
