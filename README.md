# 🎯 AI Lead Qualification CRM (Make.com Automation)

An automated lead qualification, scoring, and routing pipeline designed for training companies and modern sales teams. Built on **Make.com**, this workflow ingests lead inquiries from **Google Forms**, analyzes and scores them using **OpenAI (GPT-5 nano)**, and intelligently routes them across **Slack** and structured **Google Sheets** CRM databases.

---

## 🏗️ Workflow Architecture

```text
                                  ┌──► [Score >= 8] ──────► [ Slack Notification ] (High Quality)
                                  │
[ Google Forms ] ──► [ OpenAI ] ──┼──► [Score 5-7]  ──────► [ Google Sheets: CRM_Leads ] (Medium Quality)
 (watchResponses)   (GPT-5 nano)  │
                          │       ├──► [Score < 5]  ──────► [ Google Sheets: Lead_Archive ] (Low Quality)
                          │       │
                          │       └──► [All Leads]  ──────► [ Google Sheets: Lead_Log ] (Audit Log)
                          │
                          └── (On AI Error) ──────────────► [ Google Sheets: Lead_Archive ] (Manual Review)
