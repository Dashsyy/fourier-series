# Drawing Angkor Wat with circles

An animated page where a chain of spinning circles, a Fourier series, draws the flag of Cambodia, with Angkor Wat in the middle.

The flag's border, its two stripe lines and the temple outline are joined into one closed path and sampled at 2,048 evenly spaced points. Each point is treated as a complex number `x + iy`, and a fast Fourier transform turns the points into 2,048 rotating circles. The circles are sorted from largest to smallest and placed tip to tail, and the tip of the last circle draws the picture.

Only the `N` largest circles are used. `N` doubles every lap (1, 2, 4 … 2,048) and then starts again at 1, so you can watch the rough blob turn into the temple. The page also shows:

- **N** and the **error**: the average distance between the circles' curve and the true outline, as a percentage of the flag's width.
- **Play / Pause**: you can also click the canvas or press Space.
- **A slider** to jump to any N. With the slider focused, arrow keys step N by 1 and Page Up / Page Down double or halve it.
- **Colors**: fills in the flag's blue, red and white behind the drawing.
- **A light / dark toggle**. The page follows your system setting until you pick one.
- **A short explanation** of Fourier's idea, the Gibbs phenomenon, and where the same math is used (JPEG, MP3, MRI).

Everything is in one file, `index.html`: plain HTML, CSS and JavaScript, with no libraries and no build step.

## View it locally

Open `index.html` in any modern browser by double-clicking it. No server is needed.

## Publish on GitHub Pages

1. Create a new repository on GitHub and push `index.html` and `README.md` to the `main` branch:

   ```sh
   git init
   git add index.html README.md
   git commit -m "Fourier drawing of the Cambodian flag"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

2. On GitHub, open the repository's **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, then click **Save**.
4. After a minute or so the site is live at:

   ```
   https://<your-username>.github.io/<repo-name>/
   ```

GitHub Pages serves `index.html` as the home page automatically.
