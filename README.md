<h1>
  <span class="prefix"></span>
  <span class="headline">Deployment - GitHub Pages</span>
</h1>

## Deploying Your Browser Game with GitHub Pages

**Learning objective:** Publish your HTML, CSS, and JavaScript game so other people can play it using a link.

GitHub Pages hosts websites directly from GitHub repositories. These instructions are for our **plain HTML, CSS, and JavaScript** game projects.

## 1. Check your project files

Make sure your game works locally and that your latest code has been pushed to GitHub.

Your repository should have an `index.html` file at its top level, like this:

```text
my-game/
├── index.html  <--- index.html is not inside any other folders
├── css/
│   └── style.css
├── js/
│   └── app.js
└── assets/
    ├── images/
    │   └── cat.png
    ├── fonts/
    │   └── game-font.woff2
    └── sounds/
        └── click.mp3
```

> **Important:** The main HTML file must be named exactly `index.html` (lowercase) and be inside the folder you choose to publish.

## 2. Turn on GitHub Pages

1. Open your game's repository on **GitHub**.
2. Select **Settings**.
3. In the left menu, select **Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
5. Choose **main** as the branch and **/(root)** as the folder.
6. Click **Save**.
7. After the deployment finishes, return to **Settings → Pages** and click **Visit site**.

Your game's link will look like this:

```text
https://USERNAME.github.io/REPOSITORY-NAME/
```

For example, a repository named `memory-game` owned by `sara-dev` would be:

```text
https://sara-dev.github.io/memory-game/
```

Publishing can take up to **10 minutes**. Open the deployed game and test the buttons, images, sounds, and fonts.

## 3. Update your deployed game

After changing your code, push the changes to GitHub:

```bash
git add .
git commit -m "Update game"
git push
```

GitHub Pages will publish the updated files automatically. You do not need to repeat the setup.

> **Final check:** Test your game using the **GitHub Pages link**, not just Live Server. Make sure another person can open it and play.

## Reference

- [GitHub Docs: Configuring a publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [GitHub Docs: Renaming a repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/renaming-a-repository)
