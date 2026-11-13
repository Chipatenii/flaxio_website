# Flaxio Investment Limited website

Static website for flaxioinvestment.com, hosted on cPanel.

## Editing

The pages are generated. Do not edit `index.html`, `about.html` and the other page files directly.

1. Edit the source:
   - `template.html`: layout, styles, scripts and all page content
   - `services.json`: text for the 11 service detail pages
2. Rebuild:

   ```
   python build.py
   ```

   This writes `index.html`, `about.html`, `services.html`, one file per service
   (`ppe.html`, `sulphuric-acid.html` ...), `sectors.html`, `contact.html`,
   `cookie-policy.html`, `404.html` and `sitemap.xml`.

3. Preview locally with `python -m http.server 8000` and open http://localhost:8000
   (opening the files directly in the browser will not load images, because
   paths start with `/`).

## Uploading to cPanel

Upload these into `public_html` (cPanel > File Manager, or zip and extract).
Everything sits directly in `public_html`; `assets/` is the only folder:

- all the `.html` files except `template.html`
- `.htaccess`, `robots.txt`, `sitemap.xml`
- the `assets/` folder

`template.html`, `services.json`, `build.py` and `README.md` are not needed on the server (the `.htaccess`
blocks them if they are uploaded anyway). `.htaccess` is a hidden file: in File
Manager, turn on Settings > Show Hidden Files.

Once the SSL certificate is active, uncomment the HTTPS redirect at the top of
`.htaccess`.

## Contact form

Set `WEB3FORMS_KEY` in `template.html` (free key from https://web3forms.com)
and rebuild, so enquiries arrive by email. Without it, the form opens the
visitor's email app. The "Send via WhatsApp" button works without any setup.
