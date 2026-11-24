<h1>
  <span class="headline">Deployment - GitHub Pages</span>
  <span class="subhead">Troubleshooting</span>
</h1>
## Troubleshooting

### The website shows a 404 error

- Check that **Settings → Pages** is publishing from `main` and `/(root)`.
- Check that `index.html` is in the root of the repository, not inside another folder.
- Check that your repository is public (for typical free student accounts).
- Give the deployment time to finish. Look in the **Actions** tab if it reports a failure.

### My images, fonts, sounds, or CSS are missing

**Use relative paths.** A GitHub Pages project lives inside its repository URL, not at the website's main `/` address.

Assuming the folder structure above, these paths work:

**In `index.html`:**

```html
<link rel="stylesheet" href="./css/style.css" />
<script src="./js/app.js" defer></script>
<img src="./assets/images/cat.png" alt="A cat" />
```

**In `css/style.css`:**

```css
.game-board {
  background-image: url("../assets/images/cat.png");
}

@font-face {
  font-family: "GameFont";
  src: url("../assets/fonts/game-font.woff2") format("woff2");
}
```

**In `js/app.js`, when changing an image or playing audio:**

```js
catImageEl.src = './assets/images/cat.png';
const clickSound = new Audio('./assets/sounds/click.mp3');
```

These JavaScript paths are relative to the **web page's URL**, not the location of `app.js`.

**Avoid this common mistake:**

```html
<img src="/assets/images/cat.png" alt="A cat" />
```

The leading `/` searches from `https://USERNAME.github.io/`, instead of from your game folder. This can work locally and fail after deployment.

The same path rules apply to **images, locally stored fonts, sounds, CSS, and JavaScript files**. Google Fonts loaded from Google's URL do not need a local asset path.

### Do dots in filenames cause problems?

**Usually, no.** These are valid:

- `./assets/images/cat.png` — `./` means "start in the current folder."
- `../assets/images/cat.png` — `../` means "go up one folder."
- `cat.v2.png` — an extra dot in the middle of a filename is allowed.

But **avoid filenames or folder names that begin with a dot or underscore**, such as `.cat.png` or `_images`, because GitHub Pages' default Jekyll processing can leave them out of the published site.

For fewer problems, use simple lowercase filenames with hyphens, such as `cat-sprite.png` or `game-font.woff2`.

### A file works on my computer but not on GitHub Pages

- **Check capitalization:** `Cat.png` and `cat.png` are different names on GitHub Pages.
- **Check the folder:** `assets/cat.png` is different from `assets/images/cat.png`.
- **Check the extension:** `.jpg`, `.jpeg`, `.png`, and `.webp` are not interchangeable.
- **Check GitHub:** Make sure you committed and pushed the image, font, or sound file—not just the code that uses it.
- **Check DevTools:** Open the browser's **Console** or **Network** tab. A `404` for an asset usually means the URL is wrong or the file is missing.

### I renamed my repository from `project-1`. Did I break anything?

**No.** Your code and Git history remain intact, and GitHub normally redirects pushes to the renamed repository. But the **GitHub Pages address changes**, and the old Pages address **does not redirect**.

For example:

```text
Before: https://sara-dev.github.io/project-1/
After:  https://sara-dev.github.io/memory-game/
```

1. In **Settings → Pages**, use the **new** website URL.
2. Change any hardcoded references to `/project-1/` in your HTML, CSS, or JavaScript. Relative paths (`./assets/...`) usually need no change.
3. Update the deployed link in your `README.md` and project submission.
4. Optional but recommended: update the Git remote in your local project folder:

   ```bash
   git remote -v
   git remote set-url origin https://github.com/USERNAME/NEW-REPOSITORY-NAME.git
   git remote -v
   ```

   Replace `USERNAME` and `NEW-REPOSITORY-NAME` with your information.