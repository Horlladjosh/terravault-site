# Rebuilding this site with Claude Code — first-timer guide

Claude Code is a tool that runs in your computer's **terminal** and edits real code in a
folder on your machine. You give it this handoff folder, and it builds the site for you.

---

## 1. Install it (one time)

1. Install **Node.js** (v18+) if you don't have it — https://nodejs.org (download the LTS).
2. Open your terminal:
   - **Mac:** press ⌘+Space, type "Terminal", hit enter.
   - **Windows:** Start menu → type "PowerShell" → open it.
3. Install Claude Code by pasting this and pressing enter:
   ```
   npm install -g @anthropic-ai/claude-code
   ```
4. You'll need a Claude account (Pro/Max or API credits). The first run walks you through
   signing in.

Official setup docs: https://docs.anthropic.com/en/docs/claude-code

## 2. Put the handoff folder somewhere you can find it

Unzip the download. Move the `design_handoff_terravault_site` folder to an easy spot,
e.g. your Desktop.

## 3. Start Claude Code in a project folder

In the terminal, go to where you want the *new website* to live and start Claude:
```
cd Desktop
mkdir terravault-site
cd terravault-site
claude
```
`cd` = "change directory" (move into a folder). `mkdir` = make a new folder. `claude`
launches the assistant — you're now chatting with it, right in the terminal.

## 4. Give it the handoff and your first instruction

Copy the handoff folder into (or next to) this project so Claude can read it, then paste a
prompt like this into Claude Code:

> I want to build a marketing website. In the folder
> `design_handoff_terravault_site` there's a README.md and HTML design references plus
> screenshots. Please read the README first, then scaffold a new **Astro** site and
> recreate every page in `design_files/` pixel-for-pixel, following the design tokens and
> screen specs in the README. Use shared components for the nav and footer. Set up the
> routes so the pages link to each other. Ask me if anything is unclear before you start.

(Swap "Astro" for React/Next, Vue, or whatever you prefer — if you're unsure, Astro is the
simplest for a mostly-static marketing site. You can just add "recommend a framework for a
beginner" and let it choose.)

## 5. Work with it

- Claude will propose commands and file changes and **ask permission** before running
  them — read what it's doing and approve when it looks right.
- When it finishes a chunk, ask it to **run the site locally** so you can see it:
  > Start the dev server and tell me the URL to open.
  Then open that `http://localhost:...` link in your browser.
- Iterate in plain English: "the hero heading should be bigger", "swap the placeholder
  photos for the images in this folder", "the FAQ accordion isn't opening".

## 6. Good follow-up prompts

- "Replace all the Unsplash/Pexels placeholder media with real files I'll put in
  `/public/images` — tell me the exact filenames you expect."
- "Make it responsive for mobile."
- "Add a real form backend for the Book a Consult page."
- "Help me deploy this to Vercel/Netlify."

---

### Tips for your first time
- **Go one page at a time** if it feels like a lot: "Start with just the Home page, then
  we'll do the rest."
- You don't need to know the code — describe what you want and what looks wrong.
- If Claude gets confused, point it back at the source: "Re-read `README.md` and
  `design_files/Enterprise.dc.html` for the exact spec."
- Everything is just files in your folder — nothing breaks that you can't undo (especially
  if you set up Git; Claude can do that for you: "initialize a git repo and commit after
  each page").
