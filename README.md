# Modular Cryo-ET Electronic Lab Notebook

A no-database lab notebook where every experiment is a versioned file in a
GitHub repo. Researchers build an experiment by adding template **blocks**
(sample prep, milling, acquisition, reconstruction, ...) and reordering them.
Each save is a git commit — timestamped, auditable, and owned by the lab.

## What's in here

- `admin/config.yml` — **the template.** Defines every cryo-ET block and its
  fields. This is the file you edit to change the notebook.
- `admin/index.html` — loads the editor UI from a CDN. No install, no build.
- `templates/cryo-et-blocks.md` — the same blocks in plain language.
- `experiments/cryo-et/` — where saved experiments land, one file each.
  A filled example is already in there.
- `uploads/` — images attached in experiments get committed here (created
  automatically on first upload).

## How researchers create an experiment

1. Go to `your-site-url/admin/` and log in with GitHub.
2. Click **New Cryo-ET Experiment**, fill the header (title, date, sample ID).
3. Under **Workflow blocks**, click **Add** and pick a block (e.g.
   *Tilt-Series Acquisition*). Fill its fields. Add as many blocks as needed
   and drag to reorder.
4. Save. The editor writes a Markdown file and commits it to the repo.

## How to launch it (one-time setup)

1. Create a GitHub repo and upload these files (drag-and-drop in the browser
   works — no command line needed).
2. In **Settings -> Pages**, set the source to your `main` branch. GitHub gives
   you a public URL. Your editor lives at `<that-url>/admin/`.
3. In `admin/config.yml`, change the `repo:` line to your `owner/repo`.
4. Connect GitHub login for the editor. This is the one piece that needs a small
   auth helper (a GitHub OAuth app + a tiny hosted token exchanger). Tell me
   which hosting you'll use and I'll hand you the exact ready-made setup.

## Copy model vs shared instance

Right now the config uses the **copy model**: each lab copies this repo and
commits to its own. That's the safest fit for a public, open notebook — every
lab owns its data.

For **one shared instance** that you invite people into (they log in without
needing their own GitHub repo), swap the backend in `config.yml` to:

```yaml
backend:
  name: git-gateway
  branch: main
```

...and enable an identity/invite service. Good for a single lab; not for the
open internet.

## Adding more subjects later

Cryo-ET is one collection. To add single-particle cryo-EM, negative stain, or
any other subject, copy the `cryo_et` collection in `config.yml`, rename it, and
swap in its blocks. That's the modular payoff — new subjects are just more
collections, new steps are just more blocks.
