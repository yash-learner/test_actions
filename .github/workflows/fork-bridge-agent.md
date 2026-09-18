---
on:
  workflow_dispatch:
    inputs:
      pr:
        description: PR number
        required: true
        type: string
      comment_id:
        description: review comment id to reply to
        required: true
        type: string
permissions:
  contents: read
  pull-requests: read
engine:
  id: copilot
safe-outputs:
  reply-to-pull-request-review-comment:
    max: 1
---

# Fork bridge Stage 3 — reply off explicit inputs

This run was dispatched with a PR number and a review-comment id (no PR event context).

Post exactly one reply to review comment `${{ github.event.inputs.comment_id }}`
on pull request #`${{ github.event.inputs.pr }}`, by calling
`reply_to_pull_request_review_comment` with:
- `comment_id` = `${{ github.event.inputs.comment_id }}`
- `pull_request_number` = `${{ github.event.inputs.pr }}`
- `body` = "✅ gh-aw driven off explicit inputs — fork-bridge Stage 3 works."

Do not take any other action.
