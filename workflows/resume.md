---
description: Read the last session history to quickly get up to speed on recent work
---

# Resume: Get Up to Speed

This workflow reads the most recent session history to understand what was worked on, what's in progress, and what the next steps are.

## Steps

### 1. Quick Scan: Read Recent Briefs

// turbo
```bash
echo "=== Recent Session Briefs ===" && for dir in $(ls -1t .agent/history/ | head -5); do echo ""; echo "📁 $dir"; cat ".agent/history/$dir/BRIEF.md" 2>/dev/null || echo "(no brief)"; done
```

This gives a quick overview of the last 5 sessions. Use the keywords to decide which sessions are relevant.

### 2. Read the Most Recent Full Session

// turbo
```bash
cat .agent/history/$(ls -1t .agent/history/ | head -1)/session.md
```

This reads the full `session.md` from the most recent session.

### 3. (Optional) Read a Specific Session by Keyword

If you spotted a relevant session in the briefs, read its full content:

```bash
cat .agent/history/<session-dir>/session.md
```

### 4. (Optional) Read Multiple Full Sessions

If you need deeper context:

// turbo
```bash
for dir in $(ls -1t .agent/history/ | head -3); do
  echo "=== $dir ==="
  cat ".agent/history/$dir/session.md"
  echo ""
done
```

### 5. Check for Any Additional Session Files

Some sessions may have additional context files (artifacts, plans, etc.):

// turbo
```bash
ls -la .agent/history/$(ls -1t .agent/history/ | head -1)/
```

---

## What to Look For

When reviewing session history, focus on:

| Section | Why It Matters |
|---------|----------------|
| **What We Built** | Understand new files and features |
| **Key Debugging** | Learn about tricky issues and their solutions |
| **Known Issues** | Avoid re-encountering the same problems |
| **Next Steps** | Know what's pending or incomplete |
| **How to Resume** | Get practical commands to start working |

---

## After Reading

1. **Create a new session** following the GEMINI.md rules:
   ```bash
   mkdir -p .agent/history/$(date +%Y%m%d-%H%M%S)_{adhoc_or_description}
   ```

2. **Start your session.md** to track today's work

3. **Reference the previous session's next steps** as your starting point
