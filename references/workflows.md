# AutoDL MiniMax H3 workflows

Source: API definitions and price tables supplied by the user on 2026-09-29. Paths are relative to `https://autodl.art`; verify the current host, authentication, and request method in AutoDL documentation before calling. The examples specify input fields and output shape, but not the HTTP method or authentication format.

All three workflows submit to `/api/v1/comfyui/comfyui_workflow/{workflow_id}` and query `/api/v1/comfyui/comfyui_workflow/result/{task_id}`. A completed response has `code: "Success"`, `data.status: "completed"`, `data.task_id`, and `data.results[]` entries with `url`, `type: "video"`, `file_type: "mp4"`, and `output_type: "output"`. Preserve `request_id` for troubleshooting when available. Other statuses and errors are unspecified; inspect actual responses.

## Multi-image reference video

Workflow: `minimax_h3_lightx2v_v5`. Submit path: `/api/v1/comfyui/comfyui_workflow/minimax_h3_lightx2v_v5`.

Required: `prompt` (string), `ref_image_0` (JPG, PNG, or WebP image URL).

Optional: `ref_image_1` through `ref_image_8` (same URL formats), `seed` (integer), `duration` (integer 1–10 seconds, default 5), `resolution` (default `768p竖`). Allowed resolutions: `480p竖`, `480p横`, `480p(1:1)`, `768p竖`, `768p横`, `768p(1:1)`, `1080p竖`, `1080p横`, `1080p(1:1)`.

## Text-to-video

Workflow: `minimax_h3_lightx2v_no_pic`. Submit path: `/api/v1/comfyui/comfyui_workflow/minimax_h3_lightx2v_no_pic`.

Required: `prompt` (string).

Optional: `duration` (integer 1–15 seconds, default 5), `resolution` (default vertical 768p; the supplied text says `768竖`, while the allowed value is `768p竖`). Allowed resolutions: `480p竖`, `480p横`, `480p(1:1)`, `768p竖`, `768p横`, `768p(1:1)`. No `seed` field is listed for this workflow.

## First and last frame video

Workflow: `minimax_h3_lightx2v`. Submit path: `/api/v1/comfyui/comfyui_workflow/minimax_h3_lightx2v`.

Required: `prompt` (string), `first_frame` and `last_frame` (JPG, PNG, or WebP image URLs).

Optional: `seed` (integer), `duration` (integer 1–15 seconds, default 5), `resolution` (default vertical 768p; the supplied text says `768竖`, while the allowed value is `768p竖`). Allowed resolutions: `480p竖`, `480p横`, `480p(1:1)`, `768p竖`, `768p横`, `768p(1:1)`.

## Price information supplied by the user

The supplied tables have two unlabeled price columns. Values below are yuan per generated second, in their original column order. Confirm the applicable column and current rate on AutoDL before estimating or submitting.

| Workflow | Resolution | Column 1 | Column 2 |
| --- | --- | ---: | ---: |
| Multi-image reference | 480p | ¥0.030 | ¥0.020 |
| Multi-image reference | 768p | ¥0.040 | ¥0.030 |
| Multi-image reference | 1080p | ¥0.090 | ¥0.050 |
| Text-to-video | 480p | ¥0.030 | ¥0.020 |
| Text-to-video | 768p | ¥0.040 | ¥0.030 |
| First and last frame | 480p | ¥0.030 | ¥0.020 |
| First and last frame | 768p | ¥0.040 | ¥0.030 |
