# The 5-Phase Blog Automation Workflow

**Detailed guide to transforming internal docs into public blog posts with AI assistance.**

This document covers the complete workflow, including decision trees, edge cases, and troubleshooting.

---

## Overview

**Goal:** Transform internal documentation into public blog posts without losing authenticity or control.

**Method:** AI-assisted transformation with human approval gates at critical steps.

**Time:** 10-20 minutes from source doc to published post (including review).

---

## Phase 1: Source Selection

### What You Do
1. Identify a candidate document from your internal docs
2. Tell AI: "Transform [filepath] into a blog post"
3. Confirm you want to proceed

### What AI Does
1. Reads the source document
2. Confirms file exists and is readable
3. Asks: "Ready to transform this into a blog post?"

### Decision Tree

```
Source doc exists?
├─ Yes → Proceed to Phase 2
└─ No  → Error: File not found
    ├─ Check filepath
    └─ Try again
```

### Good Source Docs

**✅ Works well:**
- Problem/solution guides
- Setup instructions
- Architecture decisions
- Implementation notes
- Audit reports
- Troubleshooting walkthroughs

**❌ Avoid:**
- Raw code dumps (no context)
- Meeting notes (too internal)
- Incomplete drafts
- Sensitive information

### Example Prompts

```
"Transform Help/Guides/GITHUB_CREATE_PUBLIC_REPO_WORKFLOW.md into a blog post"

"Turn the GDPR audit doc into a blog post about compliance"

"Make a blog post from the CSS optimization notes"
```

---

## Phase 2: Draft Generation

### What AI Does
1. Reads the entire source document
2. Loads your voice profile (`DAVE_VOICE_PROFILE.md`)
3. Applies transformation rules:
   - Shift tone: Internal → Public
   - Add narrative: Context, story, personality
   - Restructure: Make it scannable (headers, bullets, code blocks)
   - Enhance: Examples, FAQ, troubleshooting
4. Generates complete blog post markdown
5. Shows you the full preview

### Transformation Rules

**From internal docs:**
- Factual statements
- Step-by-step instructions
- Technical accuracy
- Minimal context

**To blog posts:**
- Same facts + personality
- Same steps + why they matter
- Same accuracy + storytelling
- Rich context for external readers

### What Gets Added

1. **Opening hook** - Grab attention in first 2 lines
2. **TL;DR** - Quick summary for skimmers
3. **Story/context** - Why you encountered this problem
4. **Character voices** (if using Sacred Ten integration)
5. **FAQ section** - Anticipated questions
6. **Wrap-up** - Clear next action
7. **Metadata** - Tags, date, links

### What Stays the Same

- Technical accuracy
- Code examples
- Core problem/solution
- Key insights

### Example Transformation

**Before (Internal Doc):**
```markdown
## Git Setup

Initialize repo:
git init
git remote add origin https://github.com/user/repo.git
git add .
git commit -m "Initial commit"
git push -u origin main
```

**After (Blog Post):**
```markdown
## Your First Git Push (Without the Terror)

I stared at the empty GitHub repo for 10 minutes before I figured this out.

Here's what worked:

1. **Initialize**: `git init`
   - Creates local Git repository
   - You'll see a `.git` folder appear (it's hidden)

2. **Connect to GitHub**: `git remote add origin https://github.com/user/repo.git`
   - Links your local repo to GitHub
   - Replace `user/repo` with your actual repo name

[... continues with personality and helpful context ...]
```

---

## Phase 3: Approval Gate

### What AI Does
1. Shows you the complete generated blog post
2. Asks: "Approve, revise, or scrap?"
3. Waits for your decision

### Your Options

#### Option A: Approve ✅
- Blog post looks good
- Voice sounds authentic
- Technical content is accurate
- → Proceeds to Phase 4 (Auto-publish)

**Example:**
```
You: "Approve"
AI: [runs Phase 4 automation]
```

#### Option B: Revise 🔄
- Something's off (tone, accuracy, structure)
- Give specific feedback
- AI revises and shows new preview
- Repeat until approved

**Example:**
```
You: "The opening is too formal. Make it sound like I'm explaining to a friend over coffee."
AI: [revises opening]
AI: "Here's the revision. Approve or revise again?"
You: "Better. But shorten the FAQ section."
AI: [shortens FAQ]
AI: "Updated. Approve?"
You: "Approve"
```

#### Option C: Scrap ❌
- Not working
- Wrong source doc
- Changed your mind
- → Stops workflow, nothing published

**Example:**
```
You: "Scrap it. This doc is too technical for a blog post."
AI: "Cancelled. Want to try a different source doc?"
```

### Red Flags (When to Revise)

🚩 **Tone issues:**
- Sounds too corporate
- Too formal / too casual
- Doesn't sound like you

🚩 **Content issues:**
- Missing key details
- Technical errors
- Too much/little context

🚩 **Structure issues:**
- Wall of text (needs more headers/bullets)
- Code blocks broken
- FAQ answers are vague

### Green Lights (When to Approve)

✅ Sounds like you wrote it  
✅ Technical details are accurate  
✅ External readers would understand it  
✅ You'd be proud to share it on LinkedIn  

---

## Phase 4: Auto-Publish

**This runs automatically when you approve.**

### Step 1: Repository Decision

**If blog repo exists:**
- Use existing repo
- Add new blog post file

**If no blog repo:**
- Create new repo (e.g., `blog-posts` or topic-specific)
- Initialize with README
- Add blog post file

### Step 2: Filename Generation

AI generates filename from blog post title:

```
Title: "Stop VS Code from Breaking Your Razor Files"
Filename: stop-vscode-breaking-razor-files.md

Title: "Your First GitHub Repository"
Filename: your-first-github-repository.md
```

Rules:
- Lowercase
- Hyphens instead of spaces
- No special characters
- `.md` extension

### Step 3: Git Operations

```bash
git add [filename].md
git commit -m "Add blog post: [title]"
git push origin main
```

All automatic.

### Step 4: Verify

AI confirms:
- ✅ File created
- ✅ Committed to Git
- ✅ Pushed to GitHub
- ✅ URL: `https://github.com/[user]/[repo]/blob/main/[filename].md`

### What Could Go Wrong

**❌ Git push fails:**
- Check GitHub authentication
- Verify repo exists
- Check branch name (main vs master)

**❌ File already exists:**
- AI appends timestamp to filename
- Or asks: "Overwrite existing file?"

**❌ Network issues:**
- Retry push manually: `git push`

---

## Phase 5: LinkedIn Draft

**AI generates a LinkedIn post linking to your blog.**

### What Gets Generated

1. **Hook** (first 2 lines grab attention)
2. **Context** (what you built/learned)
3. **Link** (to GitHub blog post)
4. **Hashtags** (#BuildingInPublic, #DotNet, etc.)
5. **Call to action** (optional)

### Example LinkedIn Draft

```
I spent 85 minutes at midnight fighting VS Code's formatter. Three settings fixed it.

Turned that debugging nightmare into a blog post so you don't have to suffer through it.

👉 https://github.com/DDulac/vscode-aspnet-core-settings/blob/main/BLOG_POST.md

If you're building ASP.NET Core apps in VS Code and the formatter keeps breaking your Razor files, this will save you hours.

#BuildingInPublic #DotNet #VSCode #ASPNETCore
```

### What You Do

1. **Review** the LinkedIn draft
2. **Copy** the text
3. **Paste** into LinkedIn
4. **Post**

No automation here - keeps it authentic.

### Customization

**Add:**
- Personal commentary
- Tag relevant people
- Additional hashtags
- Emojis (if that's your style)

**Remove:**
- Hashtags you don't like
- Call to action
- Anything that doesn't fit

---

## Workflow Diagram

```
┌─────────────────────┐
│  Phase 1: Select    │
│  Source Doc         │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  Phase 2: AI        │
│  Generates Draft    │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  Phase 3: YOU       │
│  Approve/Revise     │◄─┐
└──────────┬──────────┘  │
           │              │
      Approve?            │
       ├─ No (revise) ────┘
       └─ Yes
           │
           ▼
┌─────────────────────┐
│  Phase 4: Auto      │
│  Publish to GitHub  │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  Phase 5: LinkedIn  │
│  Draft Generated    │
└─────────────────────┘
```

---

## Time Breakdown

**Phase 1 (Selection):** 30 seconds  
**Phase 2 (Draft gen):** 2-3 minutes  
**Phase 3 (Review):** 5-10 minutes  
- First pass: 5 min
- Revisions: +2 min each

**Phase 4 (Auto-publish):** 30 seconds  
**Phase 5 (LinkedIn):** 2 minutes  

**Total:** 10-20 minutes

Compare to manual:
- Write blog post from scratch: 1-2 hours
- Format for platform: 10-15 minutes
- Create repo/commit/push: 5 minutes
- Write LinkedIn post: 10 minutes

**Manual total:** 1.5-2.5 hours  
**This workflow:** 10-20 minutes

**Savings:** 80-90% time reduction

---

## Edge Cases

### What if the source doc is 10,000 words?

**Option 1:** AI summarizes key points, creates shorter blog post  
**Option 2:** Split into series (Part 1, Part 2, etc.)  
**Option 3:** You manually extract relevant section first

### What if the blog post needs images/diagrams?

**Phase 2:** AI notes where images would help  
**Phase 3:** You add images during review  
**Phase 4:** Commit images along with markdown  

### What if I want to publish to multiple platforms?

**Phase 4:** Publish to GitHub (your source of truth)  
**Manual:** Copy to Dev.to, Medium, etc. as needed  

GitHub is canonical. Everything else is syndication.

### What if I change my voice profile?

**New posts:** Use updated voice profile automatically  
**Old posts:** Optionally regenerate with new voice  

Voice profile is version-controlled in Git.

---

## Troubleshooting

### "AI draft doesn't sound like me"

**Fix:** Revise your `DAVE_VOICE_PROFILE.md`  
- Add more examples of your writing
- Clarify tone rules
- Add "do/don't" examples

### "Technical details are wrong"

**Fix:** Revise during Phase 3  
- Point out specific errors
- AI corrects and regenerates
- Approve when accurate

### "Blog post is too long/short"

**Fix:** Give feedback during Phase 3  
- "Cut this to 1000 words max"
- "Add more examples in the FAQ"
- "Expand the troubleshooting section"

### "Git push failed"

**Fix:** Manual push  
```bash
cd [repo-directory]
git push origin main
```

Check:
- GitHub authentication
- Branch name
- Network connection

---

## Best Practices

### ✅ Do This

- Review every word before approving
- Test code examples locally
- Iterate until voice sounds authentic
- Check for technical accuracy
- Verify links work

### ❌ Avoid This

- Approving without reading
- Publishing sensitive internal info
- Skipping technical verification
- Using source docs with incomplete information
- Forgetting to update voice profile as your style evolves

---

## Next Steps

1. **Try it:** Pick a simple doc, run the workflow
2. **Refine:** Adjust voice profile based on results
3. **Iterate:** Build muscle memory
4. **Scale:** Transform multiple docs into blog series

---

*This workflow powers all my "Building in Public with AI" content.*
