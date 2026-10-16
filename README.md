# SHREE BILESHWER COMPUTERS — Admin

Gujarati responsive admin dashboard prototype.

## Features
- Responsive dashboard for desktop and mobile
- 14 content sections for education, jobs, schemes, farmer support, online forms, courses, news, results, and more
- Add, edit, search, and delete content entries
- Browser-local demo storage

## Run
Open `index.html` in a modern browser, or enable GitHub Pages in repository Settings → Pages.

## Important
The login screen is a demo only. Content is stored in the current browser and is not shared between devices. Supabase Authentication, database tables, and access policies must be configured before production use. The Android APK will be a later step after the shared database is connected.

## Supabase setup

The admin page now uses Supabase Auth and the shared `public.content_items` table.

1. In Supabase Dashboard, open **Authentication → Users**.
2. Create one user using your chosen admin email and a strong password. Do not share the password in chat.
3. After the user is created, return to ChatGPT and say **Admin user created**. The user must then be added to the private admin allowlist before sign-in is permitted.
4. Deploy this repository with GitHub Pages (**Settings → Pages**, branch `main`, folder `/ (root)`).

Security notes:
- The browser contains only the Supabase project URL and publishable/anon key; these are intended for client use with Row Level Security.
- Never put a `service_role` or secret key in this repository or browser code.
- `private.admin_users` has RLS enabled with no direct-access policies by design. Admin status is checked through the restricted database function.
- The Android app can share content by reading published rows from `public.content_items` and using the same Supabase project.
