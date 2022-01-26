# Setup Docsify Blog on GitHub Pages

Explains how _this_ site was scaffolded with [Docsify](https://docsify.js.org/#/more-pages) and hosted on [GitHub Pages](https://pages.github.com/)


## 1. Scaffold `docs` with Docsify

In root of GitHub repository:

```
// Initialize docs/ folder 
$ docsify init ./docs 

// Preview docsify site locally
$ docsify serve docs
```
---

## 2. Create initial content

The `README.md` file in any folder acts as the default _index.md_ equivalent for that route on the hosted site.

Create one folder for each top-level category, and create a default README.md at root and each folder level for now. You can create additon subfolders and content files as you go.

```
$ mkdir Technology Topic Skill
$ touch README.md Technology/README.md Topic/README.md Skill/README.md
```

---

## 3. Configure Docsify setup

The _index.html_ file contains all the setup configuration parameters in the `window.$docsify` object - this is what it starts off as. 

```
    window.$docsify = {
      name: '',
      repo: ''
    }
```

You can also customize behavior by adding [plugins](https://docsify.js.org/#/plugins) - typically using `<script>` elements at the bottom of the file.

Check the [current file](docs/index.html) to see all changes made - including in `<head>` section where you can modify default theme and style.

---

## 4. Configure Sidebar, Navbar, Coverpage

Create the following files:

```
$ cd docs/
$ touch _coverpage.md _sidebar.md _navbar.md
```

Set relevant properties (`loadSidebar`, `loadNavbar`, `loadCoverpage`) to _true_ in the `window.$docsify` object in _index.html_. 

Customize those files using [navbar](https://docsify.js.org/#/custom-navbar), [coverpage](https://docsify.js.org/#/cover) and [sidebar](https://docsify.js.org/#/more-pages?id=sidebar) guidance. Check out the [repo](https://github.com/nitya/til) to view my configurations.

---

## 5. Deploy to GitHub pages

This is the easy part. Go to the [Settings > Pages](https://github.com/nitya/til/settings/pages) section of your GitHub Repo.

Select `Branch:main` and folder `docs/` and save. That's it.

You should see a message like ` Your site is ready to be published at https://nitya.github.io/til/` next time you visit the page.

Just commit the changes you've made, wait till Github automatically builds and deploys it (hint: look at [Actions](https://github.com/nitya/til/actions) tab on your repo) -- then visit that [pages URL](https://nitya.github.io/til/) - et voila!

_Note: The `pages build and deployment` action may take a while to complete. You can click on the action to view individual steps and progress._

---

## 6. Map to custom domain

This is not a Docsify thing - it's a GitHub + DNS configuration thing. I use [Google Domains](https://domains.google/) as my provider. I followed [these steps](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) to add a custom domain to GitHub Pages.

 * Added _til.nitya.dev_ as Custom Domain under `Settings > Pages` in GitHub. This adds a CNAME file to the root of my `docs/` folder.
 * On my DNS provider (Google Domains) I went to the page for the registered domain (nitya.dev) and clicked `Manage custom records`. Then `Create new record` with 
    - Host name = til
    - Type = CNAME
    - TTL = 3600 (default)
    - Data = nitya.github.io

Specfically note that _Data_ points to the user-level github.io page and not to the specific project-scoped path. 

That's it! Wait till settings kick in and you should be done. (Hint: Check again till you see a _"TLS certificate is being provisioned. This may take up to 15 minutes to complete."_ message on the Pages dashboard indicating that DNS changes have propagated.)

Once this is done - do check the "Enforce HTTPS" box on GitHub pages to make sure this site is served only over a secure HTTP connection. It's just good practice. The entire process took about 5 mins.

Visit the site `https://til.nitya.dev` and see the difference!

---

