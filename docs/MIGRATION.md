# Publishing and migration

This repository is the source of truth for the interactive visualization pages at [yiliu30.github.io/viz](https://yiliu30.github.io/viz/). The original Hugo website is maintained in [yiliu30/yiliu30.github.io](https://github.com/yiliu30/yiliu30.github.io).

## Layout

- `viz/*.html`: standalone visualization pages, preserving their existing filenames and public URLs.
- `viz/admin.html`: browser-based upload/editor tool, targeting this repository.
- `data/viz_tags.json`: tags for the gallery index.

## Publish a new or updated visualization

You can add or update an HTML file under `viz/` through GitHub, or use the hosted [visualization editor](https://yiliu30.github.io/viz/admin.html). The editor requires a GitHub fine-grained token restricted to **yiliu30/inference-viz** with Contents: Read and write. Do not commit or share this token.

To change tags, edit `data/viz_tags.json` (filenames must match exactly).

The personal Hugo site checks out this repository during deployment and mirrors `viz/` into its `static/viz/`, then uses the tag metadata to build the gallery index. Publication on the old URL is not instantaneous: the website's scheduled GitHub Pages deployment or a manual workflow run must complete.

## Shared GitHub navigation

The Hugo website adds a compact **Back to gallery** / **Star project** bar to each published visualization automatically. Its [build-time injector](https://github.com/yiliu30/yiliu30.github.io/blob/main/scripts/inject_viz_nav.py) runs **after** Hugo builds the site and changes only the generated files under `public/viz/`.

- No navigation code is added to the original `viz/*.html` sources in this repository.
- **Back to gallery** returns to the unchanged [visualization index](https://yiliu30.github.io/viz/). **Star project** links to this repository.
- New visualizations get the same links on their first successful website deployment.
- The editor (`viz/admin.html`) is excluded, and the injector can safely be rerun.

## Local Hugo preview

From a clone of `yiliu30.github.io`, check out this repository at `.viz-source` and run:

```bash
git clone https://github.com/yiliu30/inference-viz.git .viz-source
rsync -a --delete .viz-source/viz/ static/viz/
cp .viz-source/data/viz_tags.json data/viz_tags.json
python3 scripts/generate_viz_dates.py
hugo server
```

**Migration safeguards:** the original Hugo repository retains its tracked visualization files as a fallback. The build replaces them only in the GitHub Actions workspace, so all previous `/viz/<filename>.html` URLs remain valid.
