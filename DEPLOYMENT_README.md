# YAKAMA Electrical Services — production starter

Brand: YAKAMA Electrical Services  
Service area: Sivasagar, Assam  
WhatsApp: +91 7578062607  
Languages: Hindi, English, Assamese

## What this bundle contains
- `index.html`: responsive customer site, service cards, booking form, technician application form, language switcher, WhatsApp handoff, local demo admin and CSV exports.
- `supabase_schema.sql`: starter database tables and row-level security policies for public form submissions and admin-only access.

## Important status
This is a deployment-ready starter, NOT a live deployment. You must create/configure your own hosting and Supabase project. The HTML does not contain credentials yet. The local demo admin is not secure and is not a substitute for a production admin login. Do not publish sensitive customer records in a public repository.

## Step 1 — Create Supabase database
1. Sign in at https://supabase.com/ and create a project.
2. Save the database password privately.
3. Open SQL Editor in the Supabase project.
4. Paste and run `supabase_schema.sql`.
5. In Project Settings / API, copy the Project URL and the publishable/anon key. Never use the `service_role` or secret key in browser code.
6. Configure an admin user using Supabase Auth. For the policies in this SQL, an administrator must have `app_metadata.role = "admin"` set through a trusted admin/server-side workflow. Never allow public users to set this value themselves.
7. Until a secure in-site admin interface is built, review requests through the Supabase dashboard. Do not rely on the HTML's local demo admin for live records.

## Step 2 — Connect the site to Supabase
1. Open `index.html` in a text editor.
2. Find `SUPABASE_URL='PASTE_SUPABASE_PROJECT_URL_HERE'`.
3. Replace the placeholder with your Supabase Project URL.
4. Find `SUPABASE_ANON_KEY='PASTE_SUPABASE_PUBLISHABLE_OR_ANON_KEY_HERE'`.
5. Replace it with the public publishable/anon key from your project.
6. Keep `DEFAULT_OWNER_WHATSAPP='917578062607'` as-is, or change it only if the business number changes.
7. Do not add a service-role/secret key to `index.html`.
8. Test a booking and a technician application. Confirm the records appear in Supabase tables `booking_requests` and `technician_applications`. Confirm public visitors cannot read those tables.

## Step 3 — Publish with GitHub Pages (free static hosting)
1. Create a new GitHub repository. For a simple public brochure site, a public repo is easiest; remember that all files in a public repo are visible. Do not commit private data, passwords or service-role keys.
2. Upload `index.html` to the repository root. Do not upload real customer data.
3. Open repository Settings → Pages.
4. Under Build and deployment, choose Deploy from a branch; select `main` and `/(root)`, then Save.
5. Wait for GitHub Pages to publish. It will show the site URL in Settings → Pages.
6. Open the public URL on a phone and test Hindi, English, Assamese, booking and technician forms.
7. If using a custom domain later, configure it in Pages and add the DNS records provided by GitHub.

## Before real customer launch
- Add a secure in-site admin login (Supabase Auth) and admin-only screen to view, update statuses, approve technicians and manage the directory. The bundled local admin is device-only.
- Add server-side rate limiting / CAPTCHA or an anti-spam check to prevent automated form abuse.
- Add a privacy policy and terms; collect only data needed to arrange service and restrict access to phone numbers.
- Verify technician identity, references, experience and electrical safety competence before listing them as approved.
- Test mobile display, all three languages, WhatsApp link, form validation, database inserts, and access policies.
- GitHub Pages only hosts static frontend files; it does not run server code. Supabase provides the database/auth backend.
