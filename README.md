# n8n

# Setting Up Gmail Node in n8n

To use the Gmail node in n8n, you'll need to configure OAuth2 authentication. Here's a step-by-step guide:

## Prerequisites
- An n8n instance (self-hosted or cloud)
- A Google Cloud Project
- A Gmail account

## Setup Steps

### 1. Create Google Cloud Project
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the Gmail API:
   - Navigate to "APIs & Services" > "Library"
   - Search for "Gmail API" and enable it

### 2. Configure OAuth Consent Screen
1. In Google Cloud Console, go to "APIs & Services" > "OAuth consent screen"
2. Select "External" (for development) or "Internal" (for GSuite)
3. Fill in required details (app name, user support email, developer contact info)
4. Add required scopes (see step 3 below)
5. Add test users (your email address) if using "External"

### 3. Create OAuth Credentials
1. Go to "APIs & Services" > "Credentials"
2. Click "Create Credentials" > "OAuth client ID"
3. Select "Web application" as application type
4. Add authorized redirect URIs:
   - For self-hosted n8n: `https://your-n8n-domain.com/oauth2-credential/callback`
   - For n8n.cloud: `https://app.n8n.cloud/oauth2-credential/callback`
5. Click "Create" and note your Client ID and Client Secret

### 4. Configure Gmail Node in n8n
1. In n8n, add a Gmail node to your workflow
2. Click on the "Create New" button next to "Credential for Gmail API"
3. Select "OAuth2 API" as credential type
4. Fill in the details:
   - Client ID: From Google Cloud Console
   - Client Secret: From Google Cloud Console
   - Authorization URL: `https://accounts.google.com/o/oauth2/v2/auth`
   - Access Token URL: `https://oauth2.googleapis.com/token`
   - Scope: Add required scopes (see below)
   - Auth URI Query Parameters: `access_type=offline&prompt=consent`
   - Authentication: "Header" (default)

### Common Gmail Scopes
- Read-only: `https://www.googleapis.com/auth/gmail.readonly`
- Send only: `https://www.googleapis.com/auth/gmail.send`
- Full access: `https://www.googleapis.com/auth/gmail.modify`
- For labels: `https://www.googleapis.com/auth/gmail.labels`

### 5. Authenticate
1. Click the "Connect" button in the credential setup
2. You'll be redirected to Google to authorize access
3. After authorization, you'll be redirected back to n8n

## Using the Gmail Node
Once authenticated, you can use the Gmail node to:
- Send emails
- Read emails
- Manage labels
- Create drafts
- And more

## Troubleshooting
- If you get "redirect_uri_mismatch", double-check your authorized redirect URIs
- For "invalid_grant" errors, you may need to re-authenticate
- Ensure you've added your email as a test user if using external app type

Would you like more specific information about any particular part of this setup?