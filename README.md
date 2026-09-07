# Tiny Fix LLC website

The static website for Tiny Fix LLC, an independent software company based in Seattle, Washington. It is designed to deploy directly to GitHub Pages with no build step or dependencies.

## Create the GitHub repository

1. On GitHub, create a new empty repository (for example, `tinyfix-site`). Do not add a README, `.gitignore`, or license during creation.
2. In this folder, initialize Git and set the repository URL:

```text
git init
git add .
git commit -m "Create Tiny Fix website"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/tinyfix-site.git
git push -u origin main
```

Replace `YOUR-USERNAME` and `tinyfix-site` with the repository details.

## Enable GitHub Pages

1. Open the repository on GitHub and go to **Settings > Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select the `main` branch and the `/ (root)` folder, then choose **Save**.
4. GitHub will provide a temporary Pages URL while the custom domain is being configured.

The `CNAME` file in this repository contains `tinyfix.app`. GitHub Pages uses it to associate the Pages site with that custom domain.

## DNS for tinyfix.app

At the domain registrar, use the records GitHub Pages currently recommends. Typically:

- Four A records for the apex domain (`@`) pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, and `185.199.111.153`.
- One CNAME record for `www` pointing to your GitHub Pages hostname, usually `YOUR-USERNAME.github.io`.

Remove conflicting records for `@` or `www`. GitHub's documentation is authoritative if its recommended IP addresses or setup changes.

## HTTPS and testing

After DNS propagation, return to **Settings > Pages**, confirm the custom domain is `tinyfix.app`, and enable **Enforce HTTPS** when GitHub makes that option available.

Test both hosts in a browser:

```text
https://tinyfix.app
https://www.tinyfix.app
```

Confirm that both load the site over HTTPS, that one host redirects or resolves consistently according to GitHub Pages' custom-domain behavior, and that `/privacy.html` and the external Bartender App link work. DNS changes can take time to propagate.

## Local preview

Because this is plain HTML, you can open `index.html` directly in a browser. For a closer match to GitHub Pages, run a local static server from this folder, for example:

```text
py -m http.server 8000
```

Then visit `http://localhost:8000` and stop the server with `Ctrl+C` when finished.
