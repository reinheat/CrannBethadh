# Crann Bethadh — Quartz site setup

Turns your vault repo into a published website at
**https://reinheat.github.io/CrannBethadh** using Quartz (Obsidian-friendly:
wikilinks, graph view, backlinks, search, dark mode).

Your notes stay exactly where they are. Nothing about your Obsidian setup
changes — the site builds straight from the vault root, and every push
rebuilds it automatically.

## Steps (on your Windows machine)

1. Extract this zip into `C:\Users\logan\Documents\Crann Bethadh`, so the
   files sit next to your notes (you'll see `quartz/`, `package.json`,
   `quartz.config.yaml`, `.github/`, etc. alongside `Essays/`,
   `Reflections/`, ...).
2. Optional: delete `Test.md` from the vault — otherwise it becomes a
   public page on the site.
3. In Obsidian, use Obsidian Git to commit everything and push.
   (Or `git add -A && git commit -m "Add Quartz site" && git push`.)
4. On GitHub, open the repo → **Settings** → **Pages**. Under **Source**,
   select **GitHub Actions**.
5. Make the repo public: **Settings** → **General** → scroll to
   **Danger Zone** → **Change visibility** → **Make public**.
   (Free GitHub accounts only get Pages on public repos.)
6. Go to the **Actions** tab — you'll see "Deploy Quartz site to GitHub
   Pages" running. First build takes a few minutes (`npm ci`).
7. Visit **https://reinheat.github.io/CrannBethadh**.

## After setup

Just write notes and push like normal. Every push rebuilds and redeploys
the site — nothing else to do.

- Your vault `README.md` becomes the site's homepage.
- Wikilinks to notes that don't exist yet render as "create this page"
  stubs, same as a digital garden.
- To change the look: edit `quartz.config.yaml` (title, colors, fonts)
  and push. The `obsidian` template was used, so link style is
  Obsidian-shortest-path.

## Cleanup

Delete this `SETUP.md` file after you're done — if you push it, it becomes
a page on the site.

## If the build fails

Check the Actions tab → the failed run → the failed step's log. The common
cause is a hiccup in `npx quartz plugin install`; re-running the workflow
(re-push or "Re-run jobs") usually clears it.
