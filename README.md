# organizations-info-docs
# 📘 Organizations Info App

---

The **Organizations Info** app enhances Jira Service Management portals by displaying **organization-specific data** directly in the customer portal.  
It helps admins provide visibility of paid/spent hours, tasks, and structured data for each organization in a clear, business-focused view. This app is designed to allow integration with external systems (for example, a project management system) and display to the user’s organization how the progress of their requests is going.

---

## ⚙️ Features
- 📍 **Configurable placement** — display the info block in the **portal header** or **footer**.  
- 🔗 **Webtrigger integration** — securely push data from external systems using a token-protected API.  
- 🌍 **Multi-language support** — English, Ukrainian, and Russian (automatically adapts to the user’s Jira profile language).  
- 🔒 **Secure storage** — all data is stored in Atlassian Forge storage (meets *Runs on Atlassian* standards).  
- 🗂 **Dynamic tables** — columns and rows are built automatically from JSON keys (e.g. `summary`, `hours`, `status`).  
- 📊 **Hierarchical display** — supports EPIC → Subtasks structure.

---

## 🛠 Installation
1. Install the app to your Atlassian site:
2. In Jira, go to **“manage apps” page → left side menu → apps section → Organizations Info**.   
3. Configure placement and copy your Webtrigger URL + token.

---

## 📥 Data Input Format
The app receives data via a **Webtrigger API** as JSON with two fields:
- `key`: Organization ID.  
- `value`: Object with hours, metadata, and issues.  

### Example cURL
```bash
curl --location 'https://<your-webtrigger-url>' --header 'x-api-token: <YOUR_TOKEN>' --header 'Content-Type: application/json' --data '{
  "key": "org:34",
  "value": {
    "paidHours": "34",
    "spentHours": "35",
    "timestamp": "12-123-123",
    "rows": { "issues": [
        { "key": "BB-1",  "EPIC": "EPIC A", "Time spend": 5, "Status": "In Progress" },
        { "key": "BB-2",  "Task": "Subtask A1", "parentKey": "BB-1", "Time spend": 2.5 },
        { "key": "BB-3",  "Task": "Subtask A2", "parentKey": "BB-1", "Time spend": 2.5 }
      ] 
}}'
}'
```
You can send the POST request using any REST client .
Postman:
1. Select POST method.
2. Paste the webtrigger URL with the token.
3. In the Body tab, select raw → JSON, and provide the payload (example above).
4. Click Send.
After that, the updated info (organization, paid hours, spent hours, tasks) should appear in the app.  
---

## 👀 Portal View
When configured, customers linked to an organization will see:
- Paid hours & Spent hours summary.  
- Expandable organization block.  
- Dynamic issue table built from provided JSON.  
- Hierarchy (EPIC → Subtasks).  

---

## 🌍 Language Support
- English  
- Ukrainian  
- Russian  

---

## 🔒 Security
- Secure Forge storage.  
- Token-protected webtrigger for external updates.  
- Fully compliant with Atlassian’s **Runs on Atlassian** program.  

---

## 🛠 Troubleshooting
- **Block not visible** → check placement (header/footer) in settings.  
- **No data** → verify organization ID matches the one in Jira.  
- **403/424 webtrigger errors** → confirm you are sending the correct `x-api-token`.  
- Use **View Storage** in settings to debug JSON data.

---

## 🚀 Roadmap
- More languages  
- Customizable columns  
- Export/import of organization data  
- Extended analytics dashboards  

---

## 📄 License
This app is provided under the MIT License.  


