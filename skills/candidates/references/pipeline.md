# Candidate pipeline

## Identifiers

| ID | Meaning |
| --- | --- |
| `candidate_id` | Person in your org ATS |
| `candidate_job_id` | That person on a **specific** posted job (required for stage moves) |

## REST / MCP

| Action | REST | MCP |
| --- | --- | --- |
| List | `GET /candidates` | `list_candidates` |
| Profile | `GET /candidates/:id` | `get_candidate_profile` |
| Update / stage | `PATCH /candidates/:id` | `update_candidates` |
| Delete | — | `delete_candidates` |
| Bookmark | — | `bookmark_candidate`, `unbookmark_candidate` |
| Alerts | — | `get_candidate_alerts`, `set_candidate_alerts`, `list_candidate_alerts` |
| Notes | `/candidate-notes` | `create_candidate_notes`, `list_candidate_notes`, `update_candidate_notes`, `delete_candidate_notes` |
| Experience / education | candidate profile routes | `create_candidate_experience`, `create_candidate_education`, … |
| Applications (read) | `/jobs/post/:id/applications` | `list_job_applications`, `get_job_application` |

List filters: `limit`, `cursor`, `sort`, `q`, `location`, `stage_key`, `posted_job_id`, `bookmarked=true`.

Always paginate. Prefer webhooks over tight polling.
