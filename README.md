# EVERMIND

A personal AI study workspace for learning, organizing assignments, and keeping useful study context in one private place.

## Current features

- Responsive onboarding with optional schoolwork samples and a skip path
- Supabase email sign-up and sign-in
- Private per-user file storage with a 15 MB per-file limit
- AI Tutor connected through a protected Supabase Edge Function
- Image attachments sent to the vision-capable tutor through short-lived signed URLs
- PDF, DOCX, and TXT text extraction in the browser for tutor questions
- Persistent conversations and chat history
- Assignment tracker with due dates, completion, and deletion
- User-controlled Memory notes plus AI-generated suggestions requiring approval\n- Google Docs OAuth, document reading, answer preview, and user-confirmed insertion\n- Focus timer, session notes, profile/theme settings, and JSON data export
- Row Level Security on EVERMIND data tables

## Architecture

- **Frontend:** static HTML, CSS, and JavaScript hosted on GitHub Pages
- **Accounts, database, and private storage:** Supabase
- **AI gateway:** Supabase Edge Function `evermind-ai`
- **AI provider:** OpenRouter, called only from the Edge Function

The browser contains only the Supabase publishable key. The OpenRouter key must remain in the Supabase Edge Function secret named `OPENROUTER_API_KEY`; never add it to this repository or frontend code.

## Supabase setup

The current frontend is configured for the Supabase project used by this deployment. In Supabase Auth → URL Configuration, set both the Site URL and an allowed Redirect URL to:

`https://jjaidenn.github.io/HOMEWORKBOT/`

Make sure the Edge Function secret `OPENROUTER_API_KEY` is configured. The `evermind-ai` function requires a signed-in Supabase user.

## Run locally

Serve this folder with a static web server. The app uses browser ES modules and Supabase Auth redirects, so opening the HTML file directly with a `file://` URL is not a complete test of sign-in.

## Current limitations / next work

- Google Docs requires the Docs API enabled and a Google OAuth 2.0 Web client ID with this site authorized. Add the public client ID in Settings → Google Docs.
- Google access tokens stay in memory for the current browser session.
- Image understanding uses the attached image; scanned PDFs may need to be uploaded as images if the PDF has no selectable text.
- Learning memory is user-managed notes today; automatic memory summaries can be added later.

## Deployment

Deploy the repository root as a static GitHub Pages site. After each commit, allow Pages a moment to publish the new version.
