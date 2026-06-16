<p align="center">
  <img src="social-media-skill-logo-transparent.png" alt="Social Media Content Creation Skills Logo" width="200">
</p>

# Social Media Content Creation Skills for AI Agents

A public repository of agent skills tailored for content creators, founders, and social media managers. When added to your development environment, these skills enable AI coding agents (such as Claude Code, Cursor, Windsurf, and Vercel Skills) to brainstorm niche-specific ideas, write high-engagement short-form video scripts, generate hooks, and map out viral content playbooks based on real-world patterns.

---

## How Skills Work

Skills are structured Markdown documents following the [Agent Skills specification](https://agentskills.io). They supply AI agents with domain-specific knowledge, workflows, templates, and boundaries.

```
                    ┌──────────────────────────────────────────────┐
                    │     social-media-content-creation-skill      │
                    │               (Main Directory)               │
                    └──────────────────────┬───────────────────────┘
                                           │
                                           ▼
                    ┌──────────────────────────────────────────────┐
                    │        short-form-content-structures         │
                    │   (Generates TikTok, Reels, & Shorts scripts) │
                    └──────────────────────────────────────────────┘
```

---

## Available Skills

| Skill | Description |
| :--- | :--- |
| [account-growth-by-follower-tier](skills/account-growth-by-follower-tier/) | A framework for tailoring your social media organic content strategy based on your current follower count, focusing on the right actions at each growth stage. |
| [b2b-b2c-content-creation](skills/b2b-b2c-content-creation/) | Guidelines, script templates, and prompts for tailoring social media content to B2B (authority/results) and B2C (emotional/relatable) audiences. |
| [carousel-content-structures](skills/carousel-content-structures/) | Helps brainstorm, plan, and script high-performing slide-by-slide carousel posts (LinkedIn and Instagram) using 8 proven structures. |
| [facebook-retention-conversion-ads](skills/facebook-retention-conversion-ads/) | A guide for setting up and scaling high-converting Facebook and Meta Ads by amplifying high-performing organic short-form videos to preserve social proof. |
| [short-form-content-structures](skills/short-form-content-structures/) | Helps generate short-form scripts, hooks, and video concepts using 10 proven viral content structures (e.g., countdown lists, Peak Life formats, Bracket Battles, nostalgic remember hooks). |
| [short-form-content-maxing](skills/short-form-content-maxing/) | A guide to personal brand strategy and the 70-20-10 content ratio to build audience trust, double down on viral outliers, and post daily. |
| [short-form-video-formats](skills/short-form-video-formats/) | A guide for planning, scripting, and formatting short-form videos into Yap (natural/conversational), Educational (highly visual/edited), and Storytelling (narrative-driven) pillars. |
| [zero-to-tenk-sprint](skills/zero-to-tenk-sprint/) | A 30-day growth sprint framework to launch a personal brand and scale from zero to 10k followers using outlier research, batch filming, and multi-platform publishing. |

---

## Installation

### Option 1: AI Agent Prompt (Recommended for Agent IDEs)

If you are using an AI coding assistant (like Cursor, Windsurf, or VS Code with Claude), you can ask it to install the skill for you:

> **Prompt:** "Please install the social media content creation skill from github.com/davideak22/Social-Media-Content-Creation-Skill into my skills folder."

The agent will automatically create the `.agents/skills` folder and place the structures files there.

### Option 2: Claude Code Plugin (Native)

You can install these skills directly through Claude Code's built-in plugin system:

```bash
# Add the marketplace to your active Claude Code session
/plugin marketplace add davideak22/Social-Media-Content-Creation-Skill

# Install the social media content creation plugin
/plugin install social-media-content-creation-skill
```

### Option 3: CLI Installation (Global Developer Shell)

Use Vercel's `skills` CLI tool to download and install these skills directly into your project's agent path:

```bash
# Install all skills in this repository
npx skills add davideak22/Social-Media-Content-Creation-Skill
```

This installs them to your `.agents/skills/` directory and creates the appropriate symlinks.

### Option 4: Git Submodule

If you want to keep the skills up-to-date and track them in your project, add the repo as a git submodule:

```bash
git submodule add https://github.com/davideak22/Social-Media-Content-Creation-Skill.git .agents/skills-social
```

### Option 5: Clone and Copy

Simply clone the repository and copy the folders to your local agent skills path:

```bash
git clone https://github.com/davideak22/Social-Media-Content-Creation-Skill.git
mkdir -p .agents/skills
cp -r Social-Media-Content-Creation-Skill/skills/* .agents/skills/
```

---

## How to Use

Once installed, your AI agent will automatically trigger the appropriate skill based on your request. Try asking:

* *"Help me brainstorm 5 video concepts for my fitness app niche using viral structures."*
* *"Write a TikTok script about learning React using the countdown or Peak life format."*
* *"I need a Hook and CTA for a Short about coffee productivity maxing."*

You can also run validation on any skills you add or edit locally:

```bash
bash validate-skills.sh
```

---

## Contributing

We welcome new skills built on real-world content creation success! To contribute:
1. Fork the repository.
2. Create a new directory under `skills/` (e.g., `skills/my-new-skill/`).
3. Add a `SKILL.md` with proper YAML frontmatter matching `AGENTS.md` rules.
4. Run `bash validate-skills.sh` to ensure it passes specification formatting.
5. Open a Pull Request.

---

## License

[MIT](LICENSE) - Feel free to use, modify, and distribute these skills in your personal or commercial workflows.
