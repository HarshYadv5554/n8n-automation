# Welcome Email Generator - n8n Automation

## Google Sheet Link
[https://docs.google.com/spreadsheets/d/1upDXiGpuL8F-vSC8tzzK66Tf9kTihvEoQqAjbjQySLY/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1upDXiGpuL8F-vSC8tzzK66Tf9kTihvEoQqAjbjQySLY/edit?usp=sharing)

This project demonstrates an n8n workflow that automatically generates personalized welcome emails using the Llama-3 model from OpenRouter and updates a Google Sheet.

## Prerequisites

1. n8n instance (local or cloud)
2. Google Cloud Platform account with Google Sheets API enabled
3. OpenRouter API key (free tier)

## Setup Instructions

### 1. Google Sheet Setup
1. Create a new Google Sheet named "Welcome Email Generator"
2. Add the following columns:
   - email (unique)
   - name
   - status (default: "not-send")
   - content (leave blank)
3. Add at least 5 rows of dummy data
4. Make the sheet publicly viewable and share the link

### 2. Credentials Setup in n8n
1. Google Sheets:
   - Go to n8n Credentials
   - Add new Google Sheets OAuth2 credentials
   - Follow the OAuth2 flow to authorize n8n

2. OpenRouter:
   - Go to n8n Credentials
   - Add new HTTP Request credentials
   - Add your OpenRouter API key in the headers:
     ```
     Authorization: Bearer YOUR_OPENROUTER_API_KEY
     ```

### 3. Workflow Import
1. Download the `workflow.json` file
2. In n8n, go to Workflows
3. Click "Import from File"
4. Select the downloaded `workflow.json`

### 4. Running the Workflow
1. Open the imported workflow
2. Verify all credentials are properly set
3. Click "Execute Workflow" to test
4. The workflow will:
   - Read rows with status "not-send"
   - Generate personalized emails using Llama-3
   - Update the sheet with generated content
   - Mark rows as "send"

## Testing
1. Add test data to the Google Sheet
2. Run the workflow
3. Verify that:
   - Emails are generated
   - Content is written back to the sheet
   - Status is updated to "send"
   - Previously processed rows are skipped

## Troubleshooting
- Check n8n execution logs for detailed error messages
- Verify API credentials are valid
- Ensure Google Sheet permissions are correct
- Check OpenRouter API rate limits and quota

## Notes
- The workflow uses the free tier of Llama-3 model
- No actual emails are sent; content is only written to the sheet
- The workflow automatically skips processed rows 