# Launching your Lab-notebook — step by step (personalized)

Everything here is done in a web browser. No command line, no installing
software. Budget ~30 minutes.

**Your details, filled in for you:**
- GitHub user: **DMugdha**
- Repo: **Lab-notebook** (already created, already Public ✅)
- Your site will be: **https://dmugdha.github.io/Lab-notebook/**
- Your editor will be: **https://dmugdha.github.io/Lab-notebook/admin/**
  (the capital "L" in Lab-notebook matters in the URL)

**Already done:** GitHub account, the Public repo, and the MIT license.
**Still to do:** upload the notebook files, turn on Pages, set up your login.

You'll use one extra free service, **DecapBridge**, only for login. You'll be
the sole account, so **only you can write; everyone can already read** the
public repo.

---

## Part A — Upload the notebook files into Lab-notebook

1. Go to **https://github.com/DMugdha/Lab-notebook**.
2. Click **Add file → Upload files**.
3. From the `cryo-et-eln` folder I gave you, drag in the **admin** folder, the
   **experiments** folder, and the **templates** folder.
   ⚠️ Drag the folders themselves, so they land at the top level of the repo —
   you want `Lab-notebook/admin/config.yml`, NOT
   `Lab-notebook/cryo-et-eln/admin/config.yml`.
   (You can also drag in `README.md` to replace the placeholder one — optional.
   Leave `SETUP-GUIDE.md` out of the repo if you like; it's just this guide.)
4. Click the green **Commit changes**.

Your repo should now show `admin/`, `experiments/`, `templates/`, plus the
`LICENSE` and `README.md` already there.

---

## Part B — Turn on the website (GitHub Pages)

5. In the repo, click **Settings** → **Pages** (left sidebar).
6. Under **Build and deployment → Source**, choose **Deploy from a branch**.
7. Set **Branch** to `main`, folder `/ (root)`. Click **Save**.
8. Wait ~1 minute, refresh. It should confirm your site at
   **https://dmugdha.github.io/Lab-notebook/**.
   Your editor is that address + **`/admin/`**.

---

## Part C — Create your login (DecapBridge)

**First, make a GitHub access token** (this is what lets the notebook save):

9. Go to **https://github.com/settings/tokens** → **Fine-grained tokens** →
   **Generate new token**.
10. Set:
    - **Repository access** → *Only select repositories* → pick **Lab-notebook**.
    - **Permissions** → **Contents: Read and write**, and
      **Pull requests: Read and write**.
    - **Expiration** → a long period (e.g. 1 year) so it doesn't lapse.
11. Click **Generate token** and **copy it** (you won't see it again).

**Then set up DecapBridge:**

12. Go to **https://decapbridge.com** and create a free account.
13. Dashboard → **Create New Site**.
14. Paste the **GitHub token** from step 11.
15. Enter your admin URL exactly:
    `https://dmugdha.github.io/Lab-notebook/admin/index.html`
16. Login type: choose **Classic** (email + password).
17. Click **Create site**. DecapBridge shows a small `backend:` block — **copy
    it.** It'll look about like this, with your real IDs:

    ```yaml
    backend:
      name: git-gateway
      repo: DMugdha/Lab-notebook
      branch: main
      identity_url: https://auth.decapbridge.com/sites/your-site-id
      gateway_url: https://gateway.decapbridge.com
    ```

---

## Part D — Point the notebook at your login

18. In the repo, open **`admin/config.yml`** and click the **pencil** to edit.
19. Replace the top `backend:` block (the lines from `backend:` down through
    `branch: main`) with the block DecapBridge gave you in step 17.
    Leave **everything from `media_folder:` downward untouched** — that's all
    your cryo-ET templates.
20. Scroll down, click **Commit changes**.

---

## Part E — Test it (you're the only writer)

21. Go to **https://dmugdha.github.io/Lab-notebook/admin/**.
22. Log in. You should see **Cryo-ET Experiments**. Create one, add a couple of
    workflow blocks, **Save** — then check `experiments/cryo-et/` in your repo;
    a new file will be there.
23. **Don't invite anyone** in DecapBridge. Because you're the only account,
    you're the only one who can write. That's the whole write-lock.

**How others read:** anyone can open
**https://github.com/DMugdha/Lab-notebook** and read every experiment under
`experiments/cryo-et/` — no login. They can view and copy, never change.

---

## If something doesn't work

- **"Not found" on login** → the admin URL in DecapBridge (step 15) doesn't
  exactly match your page. Recheck it, including the capital "L" and
  `/admin/index.html`.
- **Can log in but can't save** → the token is missing **Contents: Read and
  write**, or expired. Regenerate and update it in DecapBridge.
- **Page loads blank** → give Pages a few more minutes on the first deploy.

---

## Your access model, in one line

**You write; everyone reads.** You're the only login, so only you can add or
edit experiments; the Public repo lets anyone read them.
