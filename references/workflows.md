# AutoDL MiniMax H3 workflows

Source: API definitions supplied by the user on 2026-09-29, supplemented by [AutoDL's ComfyUI API documentation](https://autodl.art/docs/comfyui_api/) and a completed `minimax_h3_lightx2v_v5` call on 2026-09-30. Paths are relative to `https://autodl.art`; verify current details before calling. The documentation specifies POST JSON and an `Authorization` header containing the raw token.

All three workflows submit to `/api/v1/comfyui/comfyui_workflow/{workflow_id}` and query `/api/v1/comfyui/comfyui_workflow/result/{task_id}`. A completed `minimax_h3_lightx2v_v5` response had `code: "Success"`, `data.status: "SUCCESS"`, `data.task_id`, and `data.results[]` with a temporary video URL. User-supplied examples used `completed`; inspect the actual status and results rather than relying on one spelling. Preserve `request_id` for troubleshooting when available.

## Multi-image reference video

Workflow: `minimax_h3_lightx2v_v5`. Submit path: `/api/v1/comfyui/comfyui_workflow/minimax_h3_lightx2v_v5`.

Required: `prompt` (string), `ref_image_0` (JPG, PNG, or WebP image URL or base64 data URI). A `data:image/jpeg;base64,...` value was accepted and produced completed jobs on 2026-09-30.

Optional: `ref_image_1` through `ref_image_8` (same image formats; base64 handling for these optional fields was not separately tested), `seed` (integer), `duration` (integer 1–10 seconds, default 5), `resolution` (default `768p竖`). Allowed resolutions: `480p竖`, `480p横`, `480p(1:1)`, `768p竖`, `768p横`, `768p(1:1)`, `1080p竖`, `1080p横`, `1080p(1:1)`.

## Text-to-video

Workflow: `minimax_h3_lightx2v_no_pic`. Submit path: `/api/v1/comfyui/comfyui_workflow/minimax_h3_lightx2v_no_pic`.

Required: `prompt` (string).

Optional: `duration` (integer 1–15 seconds, default 5), `resolution` (default vertical 768p; the supplied text says `768竖`, while the allowed value is `768p竖`). Allowed resolutions: `480p竖`, `480p横`, `480p(1:1)`, `768p竖`, `768p横`, `768p(1:1)`. No `seed` field is listed for this workflow.

## First and last frame video

Workflow: `minimax_h3_lightx2v`. Submit path: `/api/v1/comfyui/comfyui_workflow/minimax_h3_lightx2v`.

Required: `prompt` (string), `first_frame` and `last_frame` (JPG, PNG, or WebP image URLs).

Optional: `seed` (integer), `duration` (integer 1–15 seconds, default 5), `resolution` (default vertical 768p; the supplied text says `768竖`, while the allowed value is `768p竖`). Allowed resolutions: `480p竖`, `480p横`, `480p(1:1)`, `768p竖`, `768p横`, `768p(1:1)`.

## Price information supplied by the user

The [live AutoDL workflow page](https://autodl.art/large-model/comfyui) labeled the columns high-peak (08:00–24:00) and off-peak (00:00–08:00) on 2026-09-30. Values below are yuan per generated second. Confirm the current rate before estimating or submitting.

| Workflow | Resolution | Peak | Off-peak |
| --- | --- | ---: | ---: |
| Multi-image reference | 480p | ¥0.030 | ¥0.020 |
| Multi-image reference | 768p | ¥0.040 | ¥0.030 |
| Multi-image reference | 1080p | ¥0.090 | ¥0.050 |
| Text-to-video | 480p | ¥0.030 | ¥0.020 |
| Text-to-video | 768p | ¥0.040 | ¥0.030 |
| First and last frame | 480p | ¥0.030 | ¥0.020 |
| First and last frame | 768p | ¥0.040 | ¥0.030 |
