# Flaxio Investment Limited website

Static website for flaxioinvestment.com, hosted on cPanel.

## Editing

The pages are generated. Do not edit `index.html` or the page folders directly.

1. Edit the source:
   - `src/template.html`: layout, styles, scripts and all page content
   - `src/services.json`: text for the 11 service detail pages
2. Rebuild:

   ```
   python build.py
   ```

   This writes `index.html`, `about/`, `services/` (plus one folder per service),
   `sectors/`, `contact/`, `cookie-policy/`, `404.html` and `sitemap.xml`.

3. Preview locally with `python -m http.server 8000` and open http://localhost:8000
   (opening the files directly in the browser will not load images, because
   paths start with `/`).

## Uploading to cPanel

Upload these into `public_html` (cPanel > File Manager, or zip and extract):

- `index.html`, `404.html`, `.htaccess`, `robots.txt`, `sitemap.xml`
- the folders `about/`, `services/`, `sectors/`, `contact/`, `cookie-policy/`, `assets/`

`src/`, `build.py` and `README.md` are not needed on the server (the `.htaccess`
blocks them if they are uploaded anyway). `.htaccess` is a hidden file: in File
Manager, turn on Settings > Show Hidden Files.

Once the SSL certificate is active, uncomment the HTTPS redirect at the top of
`.htaccess`.

## Contact form

Set `WEB3FORMS_KEY` in `src/template.html` (free key from https://web3forms.com)
and rebuild, so enquiries arrive by email. Without it, the form opens the
visitor's email app. The "Send via WhatsApp" button works without any setup.
