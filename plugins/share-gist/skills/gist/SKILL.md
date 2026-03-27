---
name: gist
description: >-
  Create a secret GitHub gist from a file and return a shareable URL. Use when
  the user says "create a gist", "share this as a gist", "gist this file",
  "get a shareable link", "share this document", or wants to share a file with
  someone who doesn't have access to the private repo.
user-invocable: true
allowed-tools: Bash, Read
argument-hint: <file-path> [description]
---

# Share as Secret GitHub Gist

Create a secret (unlisted) GitHub gist from a file and return a shareable URL.

**Secret gists are not private** — anyone with the URL can view the content.
They are unlisted: not indexed by search engines, not shown on your profile.
Use them to share documents with people outside your GitHub org.

## Arguments

- `$0` — File path (required). The file to upload as a gist.
- `$1` — Description (optional). If omitted, the H1 heading from the file is used.

## Steps

### 1. Validate inputs

Check that `$0` was provided:

```bash
if [ -z "$0" ]; then
  echo "Usage: /share-gist:gist <file-path> [description]"
  echo "Example: /share-gist:gist knowledge/my-doc.md"
  exit 1
fi
```

Check the file exists and is non-empty:

```bash
if [ ! -f "$0" ]; then
  echo "Error: File not found: $0"
  exit 1
fi

if [ ! -s "$0" ]; then
  echo "Error: File is empty: $0"
  exit 1
fi
```

Check `gh` is installed and authenticated:

```bash
if ! command -v gh &>/dev/null; then
  echo "Error: gh CLI not found. Install from https://cli.github.com"
  exit 1
fi

if ! gh auth status &>/dev/null 2>&1; then
  echo "Error: gh CLI not authenticated. Run: gh auth login"
  exit 1
fi
```

### 2. Determine the description

If `$1` is provided, use it directly.

Otherwise, extract the first H1 heading from the file:

```bash
DESC=$(grep -m1 '^# ' "$0" | sed 's/^# //')
```

If no H1 heading is found, use the filename (without path or extension) as the description:

```bash
[ -z "$DESC" ] && DESC=$(basename "$0" | sed 's/\.[^.]*$//')
```

### 3. Create the secret gist

```bash
URL=$(gh gist create "$0" -d "$DESC")
```

Gists are secret by default — no `--public` flag is used.

### 4. Copy URL to clipboard and report

On macOS, copy to clipboard:

```bash
echo "$URL" | pbcopy 2>/dev/null && COPIED=true || COPIED=false
```

Report the result to the user:

- Display the URL as a clickable link
- If clipboard copy succeeded, confirm it was copied
- Include the file path and description used
- Remind the user about the secret gist access model

**Example output:**

```
✅ Gist created: https://gist.github.com/username/abc123def456

📋 Copied to clipboard

File: knowledge/my-research-doc.md
Description: My Research Document

ℹ️  This is a secret gist — anyone with the URL can view it,
   but it won't appear in search results or on your profile.
```

## Error Handling

| Error | Response |
|-------|----------|
| `gh` not found | Direct to https://cli.github.com to install |
| Not authenticated | Tell user to run `gh auth login` |
| File not found | Show the path that was tried, suggest checking with `ls` |
| File too large (>10 MB) | Warn about the limit, suggest splitting the file |
| `gh gist create` fails | Show the raw error output from `gh` |

## Security Note

Secret gists provide **unlisted** access only — not private. Do not use this
skill to share credentials, API keys, tokens, or other sensitive information.
