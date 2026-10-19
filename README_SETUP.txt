NEXTFREEDOOR REPLACEMENT FILES

Files:
- index.html: replacement site, keeping the dark green/gold design and adding Supabase auth/feed/comments/messages/media upload.
- logo.png: your supplied Next Free Door logo.
- supabase_setup.sql: supporting tables and Row Level Security/storage policies.

IMPORTANT BEFORE DEPLOYING
1. Open index.html in your editor.
2. Near the bottom, find:
   const SUPABASE_URL = "PASTE_YOUR_SUPABASE_PROJECT_URL_HERE";
   const SUPABASE_ANON_KEY = "PASTE_YOUR_SUPABASE_PUBLISHABLE_OR_ANON_KEY_HERE";
   Replace those two values with the Project URL and publishable/anon public key from Supabase -> Project Settings -> API.
   NEVER put a service_role or secret key in browser code.
3. Replace KOFI_URL with your actual Ko-fi page URL.
4. AdSense: the code includes a comment showing where the AdSense script goes. After Google approves the site, replace the sample client ID with your real ca-pub ID and place the AdSense ad unit code where you want ads displayed. Ads will not earn money until the site is approved and ads are served.
5. In Supabase SQL Editor, inspect your current table columns before running supabase_setup.sql. The script expects your existing posts/comments/messages tables to be broadly compatible with the schema described in the SQL comments. Make a backup first.
6. Supabase Auth -> URL Configuration: add https://www.nextfreedoor.com and https://nextfreedoor.com as allowed redirect URLs. Google OAuth must already be configured in Supabase/Google Cloud.
7. Deploy index.html AND logo.png together in the same root folder.

LIMITATIONS TO KNOW
- The “I'm a real person” checkbox is only a basic friction step, not strong bot protection. Use Cloudflare Turnstile or a server-verified CAPTCHA before trusting it against bots.
- The browser uses public post media URLs because community posts are public. Do not upload private/sensitive media.
- Messaging currently starts from the “Message neighbor” button on a post and requires a recipient user ID; the SQL policy restricts reading to message participants.
- AdSense and Ko-fi need your actual account URLs/IDs; none are guessed.
- The site does not have paid listings enabled; ads are free by default.
