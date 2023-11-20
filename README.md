# decryptedappstore-action

Download decrypted IPA files from https://armconverter.com/decryptedappstore

## Setup

- Go to https://armconverter.com/decryptedappstore and log into an iOSGods account
- Open your browser's dev tools, navigate to "Storage" and copy the value for the "session" cookie
- Create a new repository secret named `SESSION_TOKEN` (or something similar) and paste the session cookie as the value

Eventually your decryptedappstore session will expire and you'll need to run through this process again

## Inputs
```yaml
inputs:
  appstore_url:
    description: AppStore URL for the app you want to download
    required: true
    type: string
  cache:
    description: Cache downloaded IPAs
    default: true
    type: boolean
  path:
    description: Path to download the ipa to
    required: true
    type: string
  token:
    description: Your decryptedappstore session token
    required: true
    type: string
  version:
    description: Version of the app to download
    default: latest-available
    type: string
```

## Example

```yaml
steps:
  - name: Download IPA
    uses: level3tjg/decryptedappstore-action@main
    with:
      appstore_url: "https://apps.apple.com/us/app/youtube-watch-listen-stream/id544007664"
      path: App.ipa
      token: "${{ secrets.SESSION_TOKEN }}"
```