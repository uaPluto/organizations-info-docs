# organizations-info-docs
📘 Organizations Info App — User Manual
1. Overview
The Organizations Info app enhances Jira Service Management portals by showing organization-specific data directly in the customer view. Admins can control placement, manage content via secure storage, and push updates from external systems using webtriggers.
2. Installation
1. Deploy the app to your Atlassian site via admin or Forge CLI.
2. Verify installation in Jira Administration → Manage apps.
3. Open Project Settings → Apps → Organizations Info to configure.
3. Settings Page
On the settings page you can:
- Manage block placement (header or footer).
- Copy Webtrigger URL & Token for external integration.
- View storage records (Storage Debug).
- Clear all records if reset is needed.
4. Data Format
The app expects JSON payloads with:
- key: Organization ID.
- value: Object with hours, metadata, and issues.

Example cURL:

curl --location 'https://<your-webtrigger-url>' \
--header 'x-api-token: <YOUR_TOKEN>' \
--header 'Content-Type: application/json' \
--data '{ "key": "1", "value": { "paidHours": "40", "spentHours": "35", "rows": { "issues": [ { "key": "BB-1", "summary": "EPIC A", "hours": 5, "status": "In Progress" } ] } } }'
5. Portal View
Customers linked to an organization will see:
- Paid and Spent hours summary.
- Expandable block with organization info.
- Dynamic table built from JSON keys.
- Hierarchical support (EPIC → Subtasks).
6. Language Support
The app adjusts automatically based on user profile language:
- English
- Ukrainian
- Russian
7. Security
All data is stored in Forge secure storage.
Webtrigger updates require x-api-token.
App meets Runs on Atlassian standards.
8. Troubleshooting
- Block not visible: check placement and context.
- No data shown: verify org ID in storage.
- Webtrigger errors: ensure token is correct.
- Debug: use View Storage option.
9. Future Enhancements
Planned updates:
- More languages
- Custom columns
- Export/import data
- Analytics dashboards
