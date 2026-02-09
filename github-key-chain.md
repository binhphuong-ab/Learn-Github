# GitHub Keychain Authentication Guide

**Created:** 2026-02-09  
**Purpose:** Documentation of how Git authenticates with GitHub using macOS Keychain

---

## 🔑 Overview

This repository uses **macOS Keychain** to securely store and automatically use GitHub credentials for push/pull operations. This means you don't need to enter your password every time you interact with GitHub.

---

## ⚙️ Current Configuration

### Git Credential Helper
```bash
credential.helper=osxkeychain
```

**Location:** Configured in two places:
1. System-level: `/Applications/Xcode.app/Contents/Developer/usr/share/git-core/gitconfig`
2. User-level: `/Users/hothingocle_mac/.gitconfig`

### Repository Remote
```
origin: https://github.com/binhphuong-ab/Learn-Github.git
```

### Keychain Information
- **Keychain Location:** `/Users/hothingocle_mac/Library/Keychains/login.keychain-db`
- **Server:** github.com
- **Protocol:** HTTPS
- **Account ID:** 44321042
- **Created:** August 13, 2025
- **Last Modified:** August 13, 2025

---

## 🔐 How It Works

### Authentication Flow

1. **First Time Push/Pull**
   - Git requests GitHub credentials
   - You enter your GitHub username and Personal Access Token (PAT) or password
   - Git stores these credentials in macOS Keychain

2. **Subsequent Push/Pull**
   - Git automatically retrieves credentials from Keychain
   - No manual authentication required
   - Seamless push/pull operations

### Security Features

✅ **Encrypted Storage** - Credentials are encrypted in macOS Keychain  
✅ **User-Specific** - Only accessible by your macOS user account  
✅ **Protected by Mac Password** - Requires your Mac login to access  
✅ **Automatic** - No need to store passwords in plain text

---

## 🚀 What You Can Do

With this setup, you can easily:

- ✅ **Push** to any repository you have write access to
- ✅ **Pull** from any repository you have read access to
- ✅ **Clone** private repositories under your account
- ✅ **Fetch** updates without re-authentication

**All without entering your password each time!**

---

## 📋 Repository Access

You can push/pull to:

1. **Your Own Repositories**
   - All public repositories
   - All private repositories
   
2. **Collaborator Repositories**
   - Any repo where you're added as a collaborator
   
3. **Organization Repositories**
   - Any repo in organizations you belong to (with appropriate permissions)

---

## 🔧 Managing Your Credentials

### View Credentials in Keychain Access

1. Open **Keychain Access** app on Mac
2. Search for "github.com"
3. You'll see your stored GitHub credentials

### Update Credentials

If you need to update your GitHub token:

```bash
# Remove old credentials
git credential-osxkeychain erase
host=github.com
protocol=https
[Press Enter twice]

# Next push/pull will prompt for new credentials
```

### Check Credential Helper

```bash
git config --get credential.helper
# Should output: osxkeychain
```

---

## 🛡️ Security Best Practices

### ✅ DO:
- Keep your Mac password secure
- Use Personal Access Tokens (PAT) instead of passwords
- Set expiration dates on your PATs
- Give PATs only the permissions they need

### ❌ DON'T:
- Share your Mac login with others
- Use the same PAT for multiple purposes
- Store credentials in plain text files
- Push credentials to repositories

---

## 🆘 Troubleshooting

### "Authentication Failed" Error

1. Your token may have expired
2. Repository permissions may have changed
3. Credentials might be outdated

**Solution:**
```bash
# Clear credentials and re-authenticate
git credential-osxkeychain erase
host=github.com
protocol=https
```

### Checking Current Remote

```bash
git remote -v
# Should show your GitHub repository URL
```

### Verifying Keychain Entry

```bash
security find-internet-password -s github.com
# Shows your stored GitHub credentials (without password)
```

---

## 📚 Additional Resources

- [GitHub Personal Access Tokens](https://github.com/settings/tokens)
- [Git Credential Storage](https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage)
- [macOS Keychain Access Guide](https://support.apple.com/guide/keychain-access)

---

## 💡 Summary

Your Git setup is configured to:
- Use HTTPS for GitHub connections
- Store credentials securely in macOS Keychain
- Automatically authenticate for all Git operations
- Keep your credentials encrypted and protected

**This is a secure and convenient way to work with GitHub on macOS!** 🎉
