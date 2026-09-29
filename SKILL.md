---
name: autodl-minimax-h3-video
description: Generate MiniMax H3 text-to-video, multi-image reference video, and first/last-frame video through AutoDL Art's ComfyUI API. Use for video requests that specify AutoDL MiniMax H3.
---

# AutoDL MiniMax H3 video

Use [AutoDL Art's ComfyUI page](https://autodl.art/large-model/comfyui) for current availability, authentication, and pricing. Read [references/workflows.md](references/workflows.md) for the three user-provided API schemas and allowed values. Confirm live documentation when practical because the service can change.

## Choose a workflow

- Text only: `minimax_h3_lightx2v_no_pic`.
- One to nine reference images: `minimax_h3_lightx2v_v5`. This is multi-image reference generation; the images are not defined as ordered video frames.
- Explicit first and last frames: `minimax_h3_lightx2v`. Both image URLs are required.
- Honor an explicitly named workflow when its required inputs are available. Explain any mismatch before choosing another workflow. Treat requests for multiple modes as separate jobs.

## Generate

1. Gather the prompt and the selected workflow's required image URLs. Upload local images through the service's supported method before submission; do not put filesystem paths in URL fields. Keep image order stable for `ref_image_0` through `ref_image_8`.
2. Translate subject, action, setting, camera motion, style, and aspect ratio into supported controls. Validate duration and resolution against the selected workflow's schema. Use defaults only when they fit the request.
3. Check the current displayed cost before submission. The user-provided price table has two unlabeled price columns, so do not assume which rate applies. A direct video request authorizes an ordinary generation; ask before an unusually costly batch, a purchase, or a change of account or provider.
4. Submit to the selected workflow endpoint using existing authenticated access and the site's current authentication instructions. Do not invent a token header or upload endpoint. Follow the credential guidance below.
5. Capture `data.task_id` and query `/api/v1/comfyui/comfyui_workflow/result/{task_id}` until completion or clear failure. A `code` of `Success` in an example response does not alone establish that the video is ready; inspect `data.status` and `data.results`. Before retrying, confirm the earlier job is no longer running to avoid duplicate charges.
6. Save the MP4 output to a user-facing location when possible. Verify that it opens, has nonzero duration, and visibly matches the requested mode and content. Report submission, generation, and visual review as distinct results.

If access, a required input, or a workflow is unavailable, state exactly what is missing and preserve the prepared prompt and settings. Do not claim that submission alone produced a video or silently switch providers.

## API credentials

Do not ask for an API key when the skill is merely loaded or when the user only wants planning, prompts, or documentation. At the first API call, check whether authenticated access is already available. If a key is needed, ask the user to configure it locally through the service's supported method. Prefer an operating-system credential store; a process-scoped environment variable is acceptable for a single session. Do not automatically persist the key as a user or machine environment variable, because those values can be read from the local environment or registry. Do not ask the user to paste the key into chat.

Read credentials only at call time, pass them using the authentication scheme documented by AutoDL, and never print, record, commit, or return them. If no suitable local credential channel is available, explain the setup needed and stop before submitting the job.
