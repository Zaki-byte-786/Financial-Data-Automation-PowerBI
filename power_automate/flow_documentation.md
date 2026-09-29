# Financial Data Automation – Flow Documentation

## End-to-End Automation Flow

**Outlook → Power Automate → Google Drive → Python + Google Drive API → Power BI → Power BI Service**

### 1. Outlook – Receive Financial Data Emails
- The survey team sends financial data files through Outlook.
- Emails related to the project are identified using the keyword **“Credit Score”**.
- The relevant emails are processed automatically.

### 2. Power Automate – Automate File Handling
- Power Automate monitors the Outlook mailbox.
- It identifies emails matching the required subject/keyword.
- Attachments are processed automatically.
- The received files are uploaded to the designated Google Drive folder.

### 3. Google Drive – Central File Storage
- Google Drive acts as the centralized storage location for the incoming files.
- Files uploaded by Power Automate are available for downstream processing.
- This removes the need to manually download and combine files.

### 4. Python + Google Drive API – Data Ingestion
- Python connects to Google Drive using the Google Drive API.
- The script identifies the files in the designated folder.
- CSV and Excel files are downloaded programmatically.
- Pandas loads the files into DataFrames.
- The required files can then be combined and prepared for analysis.

### 5. Power BI – Data Transformation and Dashboard
- The processed data is brought into Power BI.
- Power Query is used for cleaning and transformation.
- Data modeling and required calculations are performed.
- The final dashboard presents the financial analysis and business insights.

### 6. Power BI Service – Automatic Refresh
- The completed Power BI report is published to Power BI Service.
- A scheduled refresh is configured.
- The dataset is refreshed automatically at the required time.
- The dashboard therefore reflects the latest available data without requiring the complete process to be performed manually.

## Overall Architecture

```text
┌─────────────┐
│   Outlook   │
│  Email Data │
└──────┬──────┘
       │
       ▼
┌─────────────────┐
│ Power Automate  │
│ Filter & Upload │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│   Google Drive  │
│  Central Storage│
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│ Python + Google │
│   Drive API     │
│   + Pandas      │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│     Power BI    │
│ Transformations │
│    & Dashboard  │
└──────┬──────────┘
       │
       ▼
┌─────────────────┐
│  Power BI       │
│     Service     │
│ Auto/Scheduled  │
│     Refresh     │
└─────────────────┘
```

## Business Process

**Manual Process:**
Receive files → Download files → Combine files → Clean data → Build/update dashboard → Share insights

**Automated Process:**
Receive files → Automatic email filtering → Automatic upload → Programmatic data ingestion → Power BI transformation → Automatic dashboard refresh
