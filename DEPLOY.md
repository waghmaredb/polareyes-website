# Deploying polareyes.ai

The repository root is the whole website: static files, no server, no database, no cookies.
Upload its contents to the root of any static host.

## Recommended: Cloudflare Pages (free, about 15 minutes)

Cloudflare also gives you free email forwarding for hello@polareyes.ai.

1. **Create the site.** In the Cloudflare dashboard, open *Workers & Pages* and create a *Pages* project connected to the GitHub repository `waghmaredb/polareyes-website`. Production branch: `main`. Build command: none. Output directory: `/`. You get a preview address like `polareyes.pages.dev`; open it and check the page.
2. **Move polareyes.ai's DNS to Cloudflare.** Add `polareyes.ai` as a site in Cloudflare (Free plan), then change the domain's nameservers at your registrar to the two Cloudflare gives you. This usually takes effect within an hour.
3. **Connect the domain.** In the Pages project, open *Custom domains* and add `polareyes.ai`, then `www.polareyes.ai`. Cloudflare creates the DNS records and the HTTPS certificate.
4. **Turn on email.** Under `polareyes.ai`, open *Email Routing* and forward `hello@polareyes.ai` to your inbox. Send a test email before launch; the site's early-access button points there.

## Alternative: AWS, alongside the demo

1. Create a private S3 bucket and upload the root files (`index.html`, `fonts/`, `og.png`, `favicon.svg`, `robots.txt`, `sitemap.xml`, `polareyes-logo.svg`).
2. Create a CloudFront distribution with that bucket as origin (Origin Access Control), default root object `index.html`.
3. Request an ACM certificate for `polareyes.ai` and `www.polareyes.ai` in **us-east-1** and attach it to the distribution.
4. Point the domain at the distribution: an alias A record in Route 53, or CNAME/ALIAS records at your registrar.

## After it is live

- Paste `https://polareyes.ai` into LinkedIn's Post Inspector to load the social card (`og.png`).
- Submit `https://polareyes.ai/sitemap.xml` in Google Search Console.
- With the GitHub connection, every push to `main` redeploys the site.
