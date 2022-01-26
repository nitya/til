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

---