# The Confident Connection — Website

A fast, responsive marketing + sales site, ready for **GitHub Pages**. The "Enroll" buttons
point to your **GoHighLevel** checkout; the free-guide form connects to your GoHighLevel form/webhook.

---

## Files
- `index.html` — the full one-page site (hero, problem, curriculum, pricing, opt-in, FAQ, CTA)
- `404.html` — friendly not-found page
- `CNAME` — (optional) put your custom domain here, e.g. `theconfidentconnection.com`

---

## 1) Publish to GitHub Pages (≈5 minutes)

1. Create a free account at github.com (if you don't have one).
2. Click **New repository**. Name it (e.g. `confident-connection-site`). Set it **Public**. Create.
3. On the repo page click **Add file → Upload files**. Drag in `index.html`, `404.html`
   (and `CNAME` if using a custom domain). Click **Commit changes**.
4. Go to **Settings → Pages**.
5. Under "Build and deployment", Source = **Deploy from a branch**. Branch = **main**, folder = **/ (root)**. Save.
6. Wait ~1 minute. Your site is live at `https://<your-username>.github.io/confident-connection-site/`.

### Custom domain (optional but recommended)
1. Buy your domain (Namecheap, Cloudflare, GoDaddy, etc.).
2. Edit the `CNAME` file to contain just your domain (one line), e.g. `theconfidentconnection.com`.
3. In your domain registrar's DNS, add:
   - Four `A` records pointing to GitHub Pages: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - A `CNAME` record for `www` → `<your-username>.github.io`
4. In **Settings → Pages**, enter your custom domain and enable **Enforce HTTPS**.

---

## 2) Wire the "Enroll" buttons to GoHighLevel

In GoHighLevel: build your **course** under Memberships, create an **Offer**, and build a
**Funnel/Order Form** (checkout) for each tier. Connect your payment provider (Stripe) inside GHL.

Then in `index.html`, replace the placeholder `href="#"` on each enroll button with your GHL
checkout URL. Buttons are marked with `data-checkout` and a tier label:

- `data-checkout="starter"` → your $47 order form URL
- `data-checkout="core"` → your $397 order form URL
- `data-checkout="vip"` → your VIP application/checkout URL
- the nav + hero + final buttons use `data-checkout` → point to your main ($397) order form

**Auto-grant course access:** in GHL, set the order form's product to **grant the Membership Offer**
on purchase, and add a Workflow: *Trigger = order submitted → grant offer → send welcome email with login*.
That's the "they buy → become a GHL customer with course access" flow, fully automated.

---

## 3) Connect the free-guide form to GoHighLevel

Two easy options:

**A. Embed a GHL form (simplest):** In GHL, build a form for the free guide. Copy its embed
code and replace the `<form id="optinForm">…</form>` block in `index.html` with the GHL embed.

**B. Post to a GHL webhook:** In a GHL Workflow, add an **Inbound Webhook** trigger. Copy the URL,
set it as the form's `action="..."`, and remove the placeholder `submit` handler at the bottom of
`index.html`. Add a Workflow step to email the guide automatically.

---

## Before you go live — quick checklist
- [ ] Replace `[Your Name]` and the hero photo placeholder with your real name + photo
- [ ] Swap all `data-checkout` button links for your GHL order-form URLs
- [ ] Connect the free-guide form (GHL embed or webhook)
- [ ] Update footer `Terms`, `Privacy`, `Refund Policy` links and the contact email
- [ ] Confirm pricing matches your GHL products
- [ ] Add real testimonials once you have them

> Want changes? Send them to me and I'll edit the file and hand it back ready to re-upload.
