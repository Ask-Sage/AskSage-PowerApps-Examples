# Ask Sage PowerApps Examples

Thomas Cummings from the U.S. Army was kind enough to share with us and provide to the open source community some examples on how he used PowerApps (Power Automate) to automate various tasks using Ask Sage.

## Process AELW Emails

This workflow automates the processing of emails sent to the Army Enterprise LLM Workspace (AELW) shared mailbox (usarmy.ecma.mbx.army-genai@army.mil). The flow uses Ask Sage's AI capabilities to intelligently categorize incoming emails and route them appropriately.

**Key Features:**
- **Automatic Email Classification**: Uses Ask Sage's Gemini Flash model to categorize emails into predefined categories (Token Requests, Lunch and Learn Signups, Technical Support, Access Requests, Training Requests, etc.)
- **Token Request Handling**: For token requests from Army users, checks if the user exists in the tenant and sends appropriate responses
- **Lunch and Learn Automation**: Automatically forwards meeting invites for AI Lunch and Learn sessions to requesters
- **Teams Integration**: Posts adaptive cards to Microsoft Teams for human review before taking certain actions
- **Smart Filtering**: Only processes emails from .mil domains and marks processed emails as complete
- **User Stats Tracking**: Integrates with Ask Sage Admin API to check user statistics and token usage

The workflow triggers every minute when new emails arrive and uses AI to generate professional email responses while maintaining human-in-the-loop oversight for critical decisions.

## SharePoint Upload to Ask Sage

This workflow automates the ingestion of SharePoint documents into Ask Sage's knowledge base, organizing content by subject categories for improved AI retrieval and responses.

**Key Features:**
- **Bulk Document Processing**: Recursively processes all files from a SharePoint document library
- **Category-Based Training**: Automatically routes documents to specific Ask Sage datasets based on SharePoint metadata categories:
  - Architecture → CIO-Policy-Architecture dataset
  - Category Management/Cost Efficiencies → CIO-Policy-CatMgmtCE dataset
  - Cloud Management → CIO-Policy-CloudMgmt dataset
  - Cybersecurity → CIO-Policy-CyberSecurity dataset
  - Data Standards → CIO-Policy-DataStandards dataset
  - Governance → CIO-Policy-Governance dataset
  - HR Policy → CIO-Policy-HRPolicy dataset
  - Networks/IT Services → CIO-Policy-NetworkITServices dataset
  - Resources/IT Procurement → CIO-Policy-ResourcesITProc dataset
  - Roles and Responsibilities → CIO-Policy-ResourcesITProc dataset
- **Rate Limiting**: Includes 30-second delays between file uploads to prevent API throttling
- **Manual Trigger**: Initiated on-demand via button trigger for controlled document ingestion

This flow enables organizations to maintain up-to-date AI knowledge bases by automatically syncing SharePoint document repositories with Ask Sage's training datasets.

## AI Meeting Minutes

This sophisticated workflow automatically generates professional meeting minutes from uploaded audio/video recordings or transcripts using Ask Sage's AI capabilities.

**Key Features:**
- **Automatic Trigger**: Activates when new items are created in a designated SharePoint list
- **Multi-File Support**: Processes multiple attachments (audio, video, or transcript files) for comprehensive meeting analysis
- **AI-Powered Transcription**: Uses Ask Sage's Gemini 2.5 Pro model to extract detailed information from meeting recordings
- **Structured Minutes Generation**: Employs Gemini Pro to create formal meeting minutes including:
  - Meeting title, date, and attendees (grouped by organization)
  - Purpose/background summary
  - Topic-by-topic discussion summaries with timestamps
  - Action items and future meeting details
  - AI attestation statement for transparency
- **Document Generation**: Automatically creates a Microsoft Word document with the formatted meeting minutes
- **Token Usage Tracking**: Monitors and reports the number of inference tokens used for cost tracking
- **Email Delivery**: Sends the completed meeting minutes via email marked as CUI (Controlled Unclassified Information)
- **Cleanup**: Automatically removes processed attachments from SharePoint after completion
- **Error Handling**: Validates that attachments are present before processing and notifies users of any issues

The workflow includes human-in-the-loop review capabilities and maintains audit trails with timestamps for validation purposes, making it ideal for organizations requiring accurate, AI-assisted meeting documentation while maintaining compliance and transparency standards.