# How to Put Your Site Online

Hi Walter. This guide is short on purpose. Just follow it top to bottom. You don't need any technical skills. There are **four parts** total — about an hour of work spread over a couple of sittings.

---

## Part 1 — Connect the Inquiry Form to Email (15 minutes)

The website has a beautiful inquiry form, but it needs a free service called **Formspree** to actually send the submissions to your email. You only have to do this once.

**Step 1.** Go to **formspree.io** in your browser. Click **Get Started**.

**Step 2.** Sign up using **mohan@walterlankatravels.com** as your email address. This is important — Formspree will send all inquiries to whatever email you sign up with. Verify your email when they send a verification link.

**Step 3.** After signing in, click **+ New Form**. Give it a name like "Walter Lanka Travels Inquiries." Click **Create Form**.

**Step 4.** Formspree will show you a form endpoint URL that looks like this:
```
https://formspree.io/f/xyzabc123
```
The part after `/f/` is your form ID (in this example, `xyzabc123`). **Copy this whole URL.**

**Step 5.** Now open the `index.html` file on your computer (use Notepad on Windows, TextEdit on Mac, or any text editor). Press **Ctrl+F** (or Cmd+F on Mac) and search for:
```
YOUR_FORM_ID
```

You'll find one match. The line looks like:
```html
<form id="inquiryForm" class="form-wrap" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

Replace `YOUR_FORM_ID` with the form ID Formspree gave you (just the part after `/f/`, like `xyzabc123`). The line should now read:
```html
<form id="inquiryForm" class="form-wrap" action="https://formspree.io/f/xyzabc123" method="POST">
```

Save the file. The form will now send inquiries to mohan@walterlankatravels.com whenever someone submits it.

> **Free tier:** Formspree allows 50 submissions per month for free. Plenty for starting out. If you ever exceed that, they'll let you know.

---

## Part 2 — Edit Your Contact Details (5 minutes)

Still in `index.html`, do the following find-and-replaces:

1. Search for `94XXXXXXXXX` — there are **3 spots**. Replace with your WhatsApp number including country code, no spaces, no `+` sign. Example: `94771234567`

2. Search for `+94 XX XXX XXXX` — there are **3 spots**. Replace with your readable phone number. Example: `+94 77 123 4567`

3. The email `mohan@walterlankatravels.com` is already filled in throughout the site, so you don't need to change that — unless you want a different email shown publicly.

Save the file.

---

## Part 3 — Upload to GitHub (10 minutes)

**Step 1.** Go to **github.com** and click **Sign up** (or sign in if you have an account). Free account is fine.

**Step 2.** Once logged in, click the **+** icon in the top right and choose **New repository**.

**Step 3.** Fill in:
- **Repository name:** type exactly `walterlankatravels.com` (yes, including the .com)
- Set it to **Public**
- Tick the box for **Add a README file**
- Click **Create repository**

**Step 4.** On the repository page, click **Add file** → **Upload files**.

**Step 5.** Open the folder I gave you on your computer. Select ALL the files inside (`index.html`, `logo.png`, `CNAME`, and the `photos` folder). Drag them into the GitHub upload area.

**Step 6.** Scroll down and click the green **Commit changes** button.

Done with Part 3. ✅

---

## Part 4 — Turn On GitHub Pages and Connect Your Domain (10 minutes + waiting)

### Turn on GitHub Pages

**Step 1.** On your repository page, click the **Settings** tab at the top.

**Step 2.** In the left sidebar, click **Pages**.

**Step 3.** Under "Build and deployment":
- **Source** should say "Deploy from a branch"
- **Branch** dropdown — choose **main**, keep folder as `/ (root)`
- Click **Save**

**Step 4.** Wait about 1–2 minutes. Refresh the page. You'll see a green message: "Your site is live at..."

### Connect your domain

**Step 5.** Go to wherever you bought walterlankatravels.com (GoDaddy, Namecheap, Hostinger, etc.). Sign in.

**Step 6.** Find the **DNS settings** for your domain. It might be called "DNS Management," "Manage DNS," or "DNS Records."

**Step 7.** Add these records. Delete any existing A records first if there are any pointing somewhere else.

| Type  | Name | Value |
|-------|------|---------------------|
| A     | @    | 185.199.108.153     |
| A     | @    | 185.199.109.153     |
| A     | @    | 185.199.110.153     |
| A     | @    | 185.199.111.153     |
| CNAME | www  | YOUR-USERNAME.github.io |

⚠️ For the CNAME row, replace `YOUR-USERNAME` with your actual GitHub username.

**Step 8.** Save the DNS changes. Now you wait. DNS changes take **anywhere from 30 minutes to 24 hours**. Most of the time it's under 2 hours.

**Step 9.** While waiting, go back to your GitHub repo → Settings → Pages. In the **Custom domain** field, type `walterlankatravels.com` and click **Save**. Once it's verified, tick **Enforce HTTPS** when it becomes available (it might take a few hours).

When everything is ready, visiting walterlankatravels.com will show your site, and inquiries from the form will email straight to mohan@walterlankatravels.com. 🎉

---

## What's on the Site

- Your logo and brand colors throughout
- An About section with a photo of you with travelers at Sigiriya
- Six tour themes (Beaches, Safari, Cultural, Hill Country, Pilgrimage, Blended) with real photos for the most popular ones
- The full 10-day blended itinerary with click-to-expand days
- Three TripAdvisor reviews (Seyara, Barney, Florent) on a Reviews section
- An inquiry form with everything you asked for: name, email, country, dates, group size, hotel category, rooms
- A floating WhatsApp button on every page
- Phone, email, and WhatsApp buttons under the form as backup contact methods

## What If Something Goes Wrong?

**The form submission shows an error** — Most likely you haven't replaced `YOUR_FORM_ID` with your real Formspree ID, or your Formspree account hasn't verified the destination email yet. Re-check Part 1, Step 5, and confirm the verification email Formspree sent you.

**The site shows but my domain isn't working** — DNS just hasn't spread yet. Wait. Check tomorrow.

**I made a mistake editing index.html and broke something** — On GitHub, click into `index.html`, click the pencil icon, paste in a fresh copy from the original folder I gave you, commit. Fixed.

**I want to update text later** — On GitHub, click into `index.html`, click the pencil icon to edit, make your changes, scroll down, commit. The site updates automatically in about 1 minute.

**I want to swap a photo later** — Just upload a new photo to the `photos` folder on GitHub with the same filename as the one you're replacing. Or upload with a new name and update the matching `<img src="photos/...">` in `index.html`.

**Test the form before going live** — Open `index.html` in your browser by double-clicking it. Fill out the form, submit. If your Formspree ID is correctly set up, you'll get an email at mohan@walterlankatravels.com. Formspree will ask you to confirm the first inquiry — that's normal, it's a one-time anti-spam step.

---

## That's It

Four parts. A couple of coffees. Site is live. Inquiries land in your inbox.

If you get stuck on any specific step, screenshot what you see and ask me. I'll walk you through it.

Take care of yourself, Walter. One small step at a time.
