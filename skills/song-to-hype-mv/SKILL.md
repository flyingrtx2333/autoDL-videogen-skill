---
name: song-to-hype-mv
description: Turn a supplied song or song clip into a finished, beat-synced high-energy music video using imagegen for visual frames and AutoDL MiniMax H3 for animated shots. Use for requests to make a 高燃剪辑 MV from music; not for an image-only storyboard or silent video.
---

# Song to high-energy MV

Produce a playable MP4 with the requested song as its soundtrack. Use **both** the installed `imagegen` and `autodl-minimax-h3-video` skills for visual production; read their current instructions when invoked. Follow the latter's live API, pricing, workflow, and credential rules. Do not treat still images, submitted jobs, or unassembled clips as a finished MV.

## Source and edit plan

- Accept a local audio file, an attached song, or an accessible authorized audio source. If the user gives only a title and no usable audio can be obtained, ask for the file or an accessible link; do not guess the recording or substitute a different performance. Preserve the supplied recording unless the user requests an audio edit.
- Determine the audio duration, musical sections, major beats, downbeats, builds, and drops by listening and using local audio analysis where helpful. Mark a timecoded edit plan. Follow requested lyrics, story, style, aspect ratio, and duration; otherwise infer visual motifs from the music without inventing literal lyric scenes.
- Design energetic pacing through shot length, motion, transitions, and contrast. Place the strongest visual changes on musical accents and vary pace across sections; avoid mechanically cutting on every beat. Keep a consistent visual identity across shots.
- Budget enough distinct source shots to cover the requested duration before generating. Favor more short, varied segments over stretching a small set of scenes. Give each planned shot a unique subject, setting, action, or camera angle, and spread close, medium, and wide views across the timeline. Do not fill the second half with unused tails of scenes already shown in the first half; repeat a scene only for a clearly intentional musical or story motif.
- Keep a shot-use ledger in the edit plan: each source clip's timeline positions, the portion used, and any deliberate repetition. Before rendering, check that the planned timeline has enough nonrepeating footage and revise the plan or generate more shots when it does not.
- Plan subtitles from the actual vocal timing. Use supplied or embedded lyrics as the primary text; otherwise transcribe and verify against the audio. Do not invent words or place lyrics over instrumental passages. For a non-Chinese song, show the original language and a faithful Chinese translation together; for a Chinese song, use Chinese subtitles unless the user requests another language.
- Estimate the number and total seconds of AutoDL generations before submitting jobs. A normal MV request authorizes ordinary generation. If the full plan is an unusually costly batch, show the approximate cost and a smaller workable edit before asking the user to choose. Do not purchase credits or silently switch providers.

## Generate footage

1. Use the built-in `image_gen` path from `imagegen` to create the key images needed for the shot plan. Keep subjects, palette, location logic, and aspect ratio coherent. Inspect each selected image and save every project-bound final in the MV workspace.
2. For `minimax_h3_lightx2v_v5`, a local image can be encoded as a `data:image/jpeg;base64,...` value in `ref_image_0`; this worked in a completed AutoDL job on 2026-09-30. Resize and encode large PNG frames as reasonable JPEGs first, and never log the base64 payload. Check the live workflow form before relying on this format because the service can change. For other workflows, use only their documented input method. Never put filesystem paths in API fields or invent an upload endpoint. If no supported image route is available, preserve the frames and plan and explain the blocker.
3. Animate the selected frames with the AutoDL workflow matching the shot: first and last frame for a planned transition, multi-image reference for a consistent subject or setting, or text-only only when a shot genuinely has no image input. Use the workflow's allowed duration, resolution, and required fields. Keep source task IDs, generated MP4s, and a shot-to-timeline map. A successful submission can still be `QUEUED`; the tested result endpoint returned `SUCCESS` with a video URL only after completion. Download results promptly because the URLs expire.
4. Review generated footage for subject continuity, motion, aspect ratio, artifacts, and fit with the music. Replace only shots that materially fail; verify a prior task's state before retrying to avoid duplicate charges.

## Assemble and deliver

- Use local video editing tools such as FFmpeg to trim, sequence, crop, vary speed where suitable, and synchronize the generated footage to the timecoded plan. Keep the song as the audio bed, with deliberate start/end trims and fades only when useful. Avoid prominent generated clip audio unless requested. Build the complete requested duration from varied scenes; adjacent close-ups and wide shots from one source can add pace, but do not count them as new scenes.
- Align each lyric line to the sung phrase, including any source-audio trim. For bilingual subtitles, put the original text and Chinese translation on separate readable lines with consistent order, contrast, and safe margins. Save an editable timed subtitle file and deliver an MP4 with visible subtitles; inspect timing, spelling, clipping, and legibility across bright and dark shots.
- Save a final MP4 and the reusable edit plan in a user-facing workspace location. Check that the file opens, has nonzero duration, contains audio, matches the requested aspect ratio, and stays in sync at representative beats and section changes. Review representative frames and the ending before declaring completion.
- Audit source reuse against the rendered timeline, especially the second half. Inspect a contact sheet spanning the whole video and replace repeated-looking or misplaced shots before delivery.
- Report the final file path, music segment used, visual style, and any material limitations. Distinguish generated images, completed AutoDL shots, and the assembled final MV if work stops early.
