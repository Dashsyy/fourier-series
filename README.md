# Drawing Angkor Wat with circles

The flag of Cambodia, with Angkor Wat in the middle, drawn by a chain of spinning circles (a Fourier series).

Live: https://dashsyy.github.io/fourier-series/

## The logic

1. **One closed path.** The flag (ratio 16:25) is described as line segments: the border, the two stripe lines, and the outline of Angkor Wat. The temple has a five-tier stepped base, three staircases, a gallery wall and three towers. Only its left half is defined as points; the right half is a mirror image. All of these are joined into a single closed loop, so a few segments are walked twice.
2. **2,048 evenly spaced points.** The loop is resampled to 2,048 points spaced equally along its length.
3. **Points as complex numbers.** Each point `(x, y)` becomes `x + iy`, and a fast Fourier transform turns the 2,048 points into 2,048 terms. Each term is a circle: its size is the radius, and its frequency is how many times it spins per lap.
4. **Biggest first.** The circles are sorted by radius, largest first, and placed tip to tail. The tip of the last circle is the pen, and it leaves the trail.
5. **N doubles every lap.** Only the `N` largest circles are used. `N` goes 1, 2, 4 … 2,048, then starts again at 1. Few circles give a rounded blob. Sharp corners like the towers and stairs need many small, fast circles, which is the Gibbs phenomenon at work.
6. **Error.** The error is the average distance between the curve drawn with `N` circles and the true path, shown as a percentage of the flag's width. With all 2,048 circles it is essentially zero.
