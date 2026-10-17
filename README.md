# SHREE BILESHWER COMPUTERS — Admin Website

Gujarati, mobile-friendly admin dashboard for managing the content shown in the SHREE BILESHWER COMPUTERS app.

## Included features

- One admin account using Supabase Authentication
- 14 content sections: અભ્યાસ અને શિક્ષણ, સરકારી નોકરી ભરતી, સરકારી યોજનાઓ, ખેડૂત સહાય, Online અરજી, કોર્સ, દૈનિક અપડેટ, અમારા વિશે, જાહેરાત, NEWS, હાલમાં ચાલુ ભરતી, ડિગ્રી પાસ ભરતી, પરીક્ષા રિજલ્ટ, and Online ફોર્મ Center
- Add, edit, search, publish/unpublish, and delete content
- Upload and preview JPG, PNG, WEBP, and GIF images (up to 5 MB)
- Shared content database with the Android app using Supabase
- Responsive mobile and desktop layout

## Deploy on GitHub Pages

1. Open this repository on GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **GitHub Actions**.
4. Open **Actions** and run **Deploy Admin Website to GitHub Pages** if it does not run automatically after this workflow is added.
5. Once the workflow succeeds, open the website URL shown in the deployment summary.

## Supabase setup

The dashboard connects to the existing Supabase project and uses the public client key only. Do not add a service-role or secret key to this repository.

1. In **Supabase → Authentication → Users**, create the single admin user using your chosen admin email and a strong password.
2. Ensure that user's auth UUID is present in `private.admin_users`. Admin authorization is checked by the database function; do not add a password to SQL or to this repository.
3. In **Authentication → URL Configuration**, add the deployed GitHub Pages website URL to **Site URL** and **Redirect URLs** if required by the project's auth settings.
4. Confirm the `content-images` Storage bucket exists and is public for image viewing. Uploading, editing, and deleting files is restricted to authenticated admins by Storage policies.
5. The `public.content_items` table must have Row Level Security enabled. Published content is readable publicly; insert, update, and delete are restricted to admins.

## Content fields

- Most sections: title, description, optional link, optional image, publish toggle.
- દૈનિક અપડેટ: date, weekday, and update text.
- અમારા વિશે: information text.
- જાહેરાત and NEWS: description plus optional image.
- પરીક્ષા રિજલ્ટ and Online ફોર્મ Center: title/name and optional link.

## Security notes

- Never commit an admin password, service-role key, or Supabase secret key.
- The Supabase client key in browser code is intended for public use; database and Storage permissions must be enforced by RLS and policies.
- If the admin password was ever shared in a chat or public place, change it in Supabase Authentication before using the deployed site.

## Android app

The Android app reads published rows from the same `public.content_items` table. After saving and publishing an entry in the admin website, refresh the app to verify it appears.
