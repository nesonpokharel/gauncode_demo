# GaunCode Admin v1 — setup (about 30 minutes)

Your public site is `index.html` (same design, now reads published projects/stories). The founder panel is at `/admin/`.

## 1. Back up first
Netlify → your site → Deploys. The current live deploy is your backup. (Rollback: open an older deploy → **Publish deploy**.)

## 2. Create the database (Supabase, free)
1. supabase.com → New project. Save the database password somewhere private.
2. Open `supabase.sql`, copy everything (your founder account is already set inside).
3. Supabase → **SQL Editor** → New query → paste → **Run**.
4. **Authentication → Users → Add user**: your email + a strong password (tick "Auto confirm").
5. **Authentication → Sign In / Providers**: turn **OFF** "Allow new users to sign up".

## 3. Connect
1. Supabase → **Project Settings → API**. Copy the **Project URL** and the **anon / publishable** key.
2. Put them in `config.js`. Never paste a `service_role` or `secret` key anywhere.
3. Supabase → **Authentication → URL Configuration**: set Site URL to `https://gauncode.netlify.app` (or your domain).

## 4. Publish
Upload these files to your GitHub repo (same folder layout) and let Netlify deploy:
`index.html`, `config.js`, `admin/index.html`. (`supabase.sql` and `README.md` can stay out of the site.)

## 5. Use it
Open `/admin/` on your phone, log in, add a project or story, upload a photo, press **Publish**. It appears on the site immediately; no redeploy.

## Notes
- Draft items are invisible to visitors (enforced by the database, not just the buttons).
- Backup: Supabase → Table Editor → Export as CSV; Storage → download the `gauncode-media` photos.
- Lost access: Supabase → Authentication → Users → send password recovery.
