# Offers (candidate → hire)

Offers attach to candidates before they become employees.

| Action | REST | MCP |
| --- | --- | --- |
| Create | `/offers` | `create_offer` |
| Update | `/offers` | `update_offer` |
| Delete | `/offers` | `delete_offer` |

Scope: `jobs:applications`.

Webhook types: `offer.created`, `offer.updated`, `offer.deleted`.

When converting a hired candidate into an employee record, continue with skill `employees` (`create_employee`).
