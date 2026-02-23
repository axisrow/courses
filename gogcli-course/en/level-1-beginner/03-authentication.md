---
title: "Setting Up Authentication"
weight: 3
bookToc: true
---

# Setting Up Authentication

Before gogcli can access your Google data, you need to give it permission. This is a one-time setup.

## Step 1: Create OAuth2 Credentials

You need to create a "project" in Google Cloud Console that gogcli will use to talk to Google.

1. Go to [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
2. Create a new project (give it any name, like "gogcli")
3. Enable the APIs you need. At minimum, enable:
   - Gmail API
   - Google Calendar API
   - Google Drive API
4. Set up the **OAuth consent screen** — choose "External" and fill in the required fields
5. If your app is in "Testing" mode, add your email as a test user
6. Create an **OAuth client**:
   - Type: "Desktop app"
   - Download the JSON file

## Step 2: Store the Credentials

Tell gogcli where your credentials file is:

```bash
gog auth credentials ~/Downloads/client_secret_XXXXX.json
```

This stores the credentials securely. You only need to do this once.

## Step 3: Authorize Your Account

Now link your Google account:

```bash
gog auth add you@gmail.com
```

A browser window will open asking you to sign in and grant permissions. After you approve, gogcli stores a refresh token in your system's secure keychain.

### No Browser? Use Manual Mode

If you're on a remote server without a browser:

```bash
gog auth add you@gmail.com --services user --manual
```

This prints a URL. Open it in any browser, approve access, then paste the redirect URL back into the terminal.

## Step 4: Test It

Set your default account and try a command:

```bash
export GOG_ACCOUNT=you@gmail.com
gog gmail labels list
```

If you see a list of Gmail labels (like INBOX, SENT, SPAM), congratulations — authentication is working!

## Where Are Tokens Stored?

gogcli uses your operating system's secure storage:

- **macOS**: Keychain Access
- **Linux**: GNOME Keyring or KWallet
- **Windows**: Credential Manager

If no system keychain is available, gogcli uses an encrypted file. Set a password with:

```bash
export GOG_KEYRING_PASSWORD='your-secret-password'
```

## Check Your Auth Status

```bash
gog auth status    # Show current auth details
gog auth list      # List all stored accounts
```

## Next Steps

In the next lesson, you'll run your first real commands with gogcli.
