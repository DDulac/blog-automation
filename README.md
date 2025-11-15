# AI-Powered Blog Automation Workflow

**Transforms internal documentation into public blog posts using AI pair programming.**

This is the workflow I use to build in public. I document everything while building DeadWax, then transform those docs into blog posts using AI assistance with approval gates.

## What This Does

**Input:** Internal documentation (technical guides, implementation notes, audit reports)  
**Output:** Public blog posts in my voice + LinkedIn announcements  
**Method:** AI-assisted transformation with human approval at every step

No black-box automation. You approve every word before it ships.

---

## The 5-Phase Workflow

### Phase 1: Source Selection
- Point to a markdown doc in your project (e.g., `Help/Guides/GITHUB_SETUP.md`)
- AI confirms: "Transform this into a blog post?"
- You say yes or pick a different doc

### Phase 2: Draft Generation
- AI reads the source documentation
- Applies your voice profile rules (see `DAVE_VOICE_PROFILE.md`)
- Generates blog post markdown
- Shows you the full preview

### Phase 3: Approval Gate ⛔
**You're in control here.**

- Review the draft
- Options:
  - ✅ "Approve" → Proceeds to Phase 4
  - 🔄 "Change [specific thing]" → AI revises, shows new preview
  - ❌ "Scrap it" → Stops, no publish

You can iterate as many times as needed.

### Phase 4: Auto-Publish (When Approved)
Once you approve, automation kicks in:

1. **Create repository** (or use existing blog repo)
2. **Generate filename** from blog post title (e.g., `stop-vscode-breaking-razor.md`)
3. **Git commit** with descriptive message
4. **Git push** to GitHub
5. **Generate LinkedIn draft** linking to the post

All automatic. You just said "approve."

### Phase 5: LinkedIn Sharing
- AI generates LinkedIn post in your voice
- Includes link to GitHub blog post
- Hashtags: `#BuildingInPublic`, `#DotNet`, etc.
- Copy, paste, post

---

## What Gets Automated

✅ **Voice transformation** - Docs → blog style using your voice profile  
✅ **Git operations** - Commit, push, repo management  
✅ **File organization** - Naming, structure, metadata  
✅ **LinkedIn draft generation** - Announcement posts ready to copy

## What You Control

✅ **Source doc selection** - You pick what to share  
✅ **Draft approval** - Review and iterate until it's right  
✅ **Final publish decision** - Nothing goes live without your "approve"  
✅ **LinkedIn posting** - You manually post (keeps authenticity)

---

## Quick Start

### 1. Set Up Your Voice Profile

Create `DAVE_VOICE_PROFILE.md` (or use mine as a template):
- Define your writing tone
- Set sentence structure rules
- List phrases you use / avoid
- Add character voice integrations (optional)

See `DAVE_VOICE_PROFILE.md` in this repo for a full example.

### 2. Identify Source Docs

Look for docs you've written that have value for others:
- Setup guides
- Problem-solving walkthroughs
- Architecture decisions
- Audit reports
- Implementation notes

**Good candidates:**
- Solves a specific problem
- Took you time to figure out
- Would help someone else avoid that pain

### 3. Run the Workflow

**With AI pair programming:**
```
You: "Transform Help/Guides/GITHUB_SETUP.md into a blog post"
AI: [reads doc, applies voice profile, generates draft]
AI: "Here's the draft. Want to approve or revise?"
You: [review]
You: "Approve"
AI: [creates repo, commits, pushes, generates LinkedIn draft]
```

**Manual method:**
1. Read source doc
2. Apply voice profile rules manually
3. Write blog post
4. Create repo / commit / push yourself
5. Write LinkedIn post

Same result, more work.

### 4. Share

Copy the LinkedIn draft, post it, done.

Your blog post is live on GitHub. Link shared on LinkedIn. People read it.

---

## Repository Structure

```
blog-automation/
├── README.md              # This file
├── DAVE_VOICE_PROFILE.md  # Voice rules for transformations
├── WORKFLOW.md            # Detailed 5-phase process
├── examples/
│   ├── source-doc.md      # Before: Internal documentation
│   └── blog-post.md       # After: Public blog post
└── LICENSE                # MIT
```

---

## Examples

### Before: Internal Doc
```markdown
# GitHub Setup Guide

1. Create repository on GitHub
2. Initialize local git: `git init`
3. Add remote: `git remote add origin <url>`
4. Commit: `git add .; git commit -m "Initial commit"`
5. Push: `git push -u origin main`
```

### After: Blog Post (Dave's Voice)
```markdown
# Your First GitHub Repository (Without the Confusion)

I created my first public GitHub repo this week. Here's what I learned.

**TL;DR:** It's simpler than you think. Five commands. Done.

[... rest of blog post with personality, context, and helpful details ...]
```

Same information. Different audience. Different tone.

---

## Why This Exists

I'm building DeadWax (an ASP.NET Core supply chain system) and documenting everything along the way. I realized:

1. **I'm already writing** - Internal docs, guides, implementation notes
2. **Others could use this** - The problems I solve aren't unique
3. **Building in public** - Sharing the journey creates value
4. **AI pair programming** - I can transform docs faster with AI assistance

This workflow lets me:
- Document for myself (internal voice)
- Share with others (public voice)
- Do both without writing everything twice

---

## Who This Is For

**You might want this if:**
- You document your work internally
- You want to build in public
- You're comfortable with AI pair programming
- You want approval gates (no black-box automation)
- You prefer GitHub over traditional blog platforms

**This won't fit if:**
- You don't document your work
- You want fully automated publishing (no human review)
- You prefer Medium/Dev.to/Substack for hosting
- You don't use AI assistance

---

## Tech Stack

**Required:**
- Git + GitHub account
- Markdown editor (VS Code recommended)
- AI assistant with file access (GitHub Copilot, Claude, etc.)

**Optional:**
- LinkedIn account (for sharing)
- PowerShell (for automation scripts)

---

## Voice Profile

The `DAVE_VOICE_PROFILE.md` file defines how your internal docs get transformed into blog posts.

**Key elements:**
- **Tone:** Casual, direct, collaborative
- **Sentence structure:** Short. Punchy. Varied rhythm.
- **Avoid:** Corporate jargon, buzzwords, excessive formality
- **Include:** Real stories, specific examples, honest mistakes

See the full profile in this repo.

---

## Workflow Details

See `WORKFLOW.md` for the complete 5-phase process with decision trees and edge cases.

---

## FAQ

### Q: Do I need AI to use this?

**A:** No. You can apply the voice transformation manually. AI just speeds it up.

### Q: What if the AI-generated draft is terrible?

**A:** You're the approval gate. Say "revise" and give feedback. Iterate until it's right. Or scrap it.

### Q: Can I use this for non-technical content?

**A:** Yes. The workflow works for any transformation: docs → blog, notes → article, research → tutorial.

### Q: Why GitHub instead of Dev.to/Medium?

**A:** Personal preference. I like:
- Owning my content (Git history, full control)
- Clean markdown (no platform quirks)
- Engineers already hang out on GitHub

You can adapt this to publish anywhere.

### Q: How long does this take?

**Phase 1-3 (Draft + Approval):** 5-15 minutes  
**Phase 4 (Auto-publish):** 30 seconds  
**Phase 5 (LinkedIn):** 2 minutes

Total: ~10-20 minutes from doc to published post.

---

## Roadmap

**Current:** Manual workflow with AI assistance  
**Next:**
- [ ] PowerShell scripts for repo creation
- [ ] Template repository for quick starts
- [ ] Example transformations (10+ before/after pairs)
- [ ] Integration with LinkedIn API (auto-post drafts)

---

## Contributing

This is my personal workflow, but if you fork it and improve it, I'd love to see what you build.

**Ideas welcome:**
- Different voice profiles
- Additional automation scripts
- Platform integrations (Dev.to, Medium)
- Example transformations

Open an issue or PR.

---

## License

MIT License - Use it however you want.

---

## About

I'm Dave. I build DeadWax (ASP.NET Core supply chain system) and document the journey.

**Find me:**
- GitHub: [@DDulac](https://github.com/DDulac)
- DeadWax: [github.com/DDulac/DeadWax](https://github.com/DDulac/DeadWax)
- Blog posts: [github.com/DDulac](https://github.com/DDulac?tab=repositories)

**This workflow in action:**
- Blog #1: [Stop VS Code from Breaking Your Razor Files](https://github.com/DDulac/vscode-aspnet-core-settings/blob/main/BLOG_POST.md)
- Blog #2: (Coming soon - the post about this automation workflow)

---

*November 15, 2025*  
*#BuildingInPublic #AIpairprogramming #Documentation*
