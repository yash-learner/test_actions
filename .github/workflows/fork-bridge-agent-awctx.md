---
on:
  workflow_dispatch:
    inputs:
      aw_context:
        description: "Agent caller context JSON (item_type/item_number/comment_id)"
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

# Fork bridge Stage 3 — aw_context variant (target: triggering)

This run carries no custom inputs. Everything you need is in your GitHub context
block above, populated from `aw_context`.

Reply to the pull request review comment identified in that context — use the
**comment-id** and **pull-request-number** shown there — by calling
`reply_to_pull_request_review_comment` with:
- `comment_id` = the comment-id from your context
- `pull_request_number` = the pull-request-number from your context
- `body` = "✅ aw_context variant — resolved from ambient context, target: triggering (no target:'*')."

Do not take any other action.
