# Bharat Singh Lovewanshi — Portfolio

A responsive static portfolio built with semantic HTML, CSS, and vanilla JavaScript. It retains the original dark navy, blue, and cyan visual design. `index.html` is the deployment entry point; `favicon.svg` is the local site icon.

## 1. Run locally

1. Open this folder in a terminal.
2. and do go live to run html file

The contact form intentionally does **not** claim to submit successfully from a local preview. Real submissions require a deployed Netlify site with form detection enabled and `netlifyFormsEnabled: true` in `portfolioConfig`.

## 2. Configure personal URLs

In `index.html`, edit `const portfolioConfig` near the beginning of the script at the bottom. Replace empty strings with real values:

- `email`: your real email address. It is checked with a practical email-format expression before the `mailto:` link is enabled.
- `netlifyFormsEnabled`: keep `false` until the site is deployed on Netlify and form detection is enabled; then set it to `true` and redeploy.
- `githubProfile`: your GitHub profile URL.
- `linkedinProfile`: your LinkedIn profile URL.
- `resumePdfUrl`: a public URL to the actual PDF, such as a `.pdf` URL or supported Google Drive/Docs, Dropbox, or OneDrive share URL. The code checks the URL shape only; it cannot prove the file is a PDF or publicly accessible. Test it signed out before sharing.
- `projects.pensionMamaRepo` / `projects.pensionMamaDemo`
- `projects.ccmsRepo` / `projects.ccmsDemo`
- `projects.employeeRepo` / `projects.employeeDemo`

Use full `https://` URLs for profile, resume, and project links (the validator accepts HTTP or HTTPS, but HTTPS is recommended). Blank, malformed, or unsupported values remain visibly disabled, have an accessible explanation, and have no destination until configured. External HTTP/HTTPS links open in a new tab with `noopener noreferrer`. The resume URL is checked for a plausible PDF/share URL shape, not fetched or verified by this code. A syntactically valid URL does **not** prove that the destination is a PDF or that visitors can access it. The resume opens in a new tab; a browser may preview the PDF rather than download it, depending on the hosting service's response headers. Test the URL in a private/incognito browser window while signed out to ensure it is a real PDF and public.

## 3. Contact form — Netlify Forms setup

The contact form uses Netlify's static HTML form detection. If JavaScript does not run, the initial status still explains that submission requires JavaScript and a configured Netlify deployment. It includes required Name, Email, Subject, and Message fields, native email validation, a honeypot field, an accessible status message, and a duplicate-submission guard. Its status distinguishes a local preview, disabled configuration, sending, success, and failure. A network or non-success HTTP response shows an error; the fallback mentions Email Me only when a valid email address is configured. A success message is shown only after the POST endpoint returns a successful HTTP response. The form is not verified as working until a real hosted test submission is visible in Netlify Forms.

1. Deploy this folder to Netlify (instructions below) with `netlifyFormsEnabled: false` initially.
2. In the Netlify site dashboard, open **Forms** and enable form detection if prompted.
3. Trigger a new deploy so Netlify scans the static HTML form. Its name is `portfolio-contact`; the markup includes `data-netlify="true"`, `netlify-honeypot="bot-field"`, and the hidden `form-name=portfolio-contact` field.
4. In `index.html`, change `netlifyFormsEnabled: false` to `netlifyFormsEnabled: true`, save, and redeploy. Do not enable it before the deployed form is detected.
5. Open the **public HTTPS URL** in a normal browser window. Submit a test using an email address you control and a clear test subject/message. The page should show “Sending your message…” and only show success after the POST response is successful.
6. Open **Netlify Dashboard → your site → Forms → `portfolio-contact`** and verify that the test submission is listed. Configure notification emails in the site's form settings if desired.
7. Repeat once from a private/incognito window if practical. Verify the required fields and invalid email are rejected before sending; do not send an empty test.
8. If the form is missing or the submission does not appear, confirm form detection is enabled, redeploy, inspect the browser Network panel for the POST to `/` and its HTTP status, and check the Netlify Forms dashboard. Do not rely on the form until a real hosted test submission is visible in Netlify.

**Local preview is not a hosted submission test.** With `netlifyFormsEnabled: false`, the form should display a clear disabled-preview message and must not claim success. A successful HTTP response alone is not proof that the message appears in the dashboard; verify the saved submission there.

No API key or private credential is needed in the HTML. Do not put secrets in a static website.

### Google Forms alternative

If you prefer Google Forms, create a form with the same fields, set its responder permissions as needed, then link to it with a clearly labeled external button. A normal Google Form is a hosted form, not an embedded API; do not claim a submission succeeded on this portfolio unless the visitor has actually completed and submitted the Google Form. The included form is currently wired for Netlify Forms, so do not simply paste a Google Form URL into the Netlify form configuration.

## 4. Publish using Netlify

1. Make sure `index.html`, `favicon.svg`, and `README.md` are together in the root of the folder you upload.
2. Configure the real URLs in `portfolioConfig` and save `index.html`.
3. Visit https://app.netlify.com/drop and sign in if prompted.
4. Drag the extracted `bharat-portfolio` folder into the deployment area and follow the on-screen instructions.
5. Copy the public `*.netlify.app` URL from the Netlify dashboard.
6. Enable form detection as described above and redeploy if needed.
7. Test the public URL, contact form, resume, and all configured links before submitting the URL to Handshake AI Skills Studio.

No build command is required. The website is static HTML/CSS/JavaScript and has not been deployed by this project-editing step.

## 5. Local checks versus hosted checks

### Automated/static checks
- HTML parser checks for duplicate IDs/attributes and broken internal anchors; JavaScript syntax checks; local asset existence; form markup and required field attributes; responsive breakpoints; and reduced-motion CSS.
- Link URL/email validators can be tested against valid and invalid values without publishing.

### Can be checked in a local browser
- Navigation menu behaviour, including closing/resetting its expanded state when resized to desktop width; keyboard focus, disabled-link behaviour, form native validation, responsive overflow at representative viewport widths, and JavaScript console errors.
- With `netlifyFormsEnabled: false`, the form should show a preview-disabled message and must not claim success.

### Must be checked after deployment
- Whether Netlify detects the form, accepts a real submission, and lists it under **Forms → `portfolio-contact`**.
- Whether optional submission notification emails are configured and arrive.
- Whether your actual resume PDF and every configured external URL are public and accessible while signed out.
- Whether the public HTTPS site loads in a private browser window and there are no failed asset requests or JavaScript errors.
- Actual mobile, tablet, and desktop rendering in real browsers/devices. Static CSS checks alone do not prove rendering quality.

## 6. Final Handshake submission checklist

- [ ] Configure your real email, GitHub, LinkedIn, resume PDF, and any available project URLs.
- [ ] Add Pension Mama technology tags only after confirming the technologies were actually used.
- [ ] Replace the CCMS individual-contribution note with the modules you personally worked on; do not claim the whole team's work as your own.
- [ ] Deploy to Netlify and verify the public URL.
- [ ] Enable Netlify Forms detection and redeploy.
- [ ] Submit a test contact message and confirm it appears in Netlify Forms.
- [ ] Check Email Me opens a message addressed to the correct email.
- [ ] Test the resume and every configured project/profile link in a private browser window.
- [ ] Test the mobile menu and layout at mobile, tablet, and desktop widths.
- [ ] Check browser developer tools for JavaScript errors and failed asset requests.
- [ ] Submit only the verified public URL to Handshake AI Skills Studio.

### Handshake AI Skills Studio submission

1. Open the **Ship Your First Personal Site** task in Handshake AI Skills Studio.
2. Paste the verified public `https://…netlify.app` URL into the task's website/URL submission field.
3. Submit the task using the action shown in that task. If the task requests evidence, provide only evidence you actually captured; do not claim the contact form works unless the hosted submission is visible in Netlify Forms.
4. Reopen the public URL in a private browser window and confirm it loads without a sign-in before considering the submission complete.
