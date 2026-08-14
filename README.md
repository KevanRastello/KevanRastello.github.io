# kevanrastello.github.io

Personal academic site — research, publications, teaching, and a growing set of
interactive explainers. Built with [Quarto](https://quarto.org).

## How it works

You edit `.qmd` files (Markdown + math + code), Quarto renders them into `docs/`,
and GitHub Pages serves `docs/` on the `main` branch. There is no server and no
build service involved — rendering happens on your machine.

## One-time setup

1. **Confirm Quarto is installed.** It ships with recent RStudio. In a terminal:
   `quarto --version`
2. **Point GitHub Pages at `docs/`.** On GitHub, go to
   *Settings → Pages → Build and deployment*, set **Source** to
   *Deploy from a branch*, branch **main**, folder **`/docs`**, and Save.
3. Push. The site appears at <https://kevanrastello.github.io> within a minute or
   two.

## Everyday workflow

```bash
quarto preview     # live preview in your browser, auto-reloads as you edit
quarto render      # build the site into docs/
```

In RStudio, opening any `.qmd` gives you a **Render** button that does the same
thing.

Then commit and push — **including the `docs/` folder**, since that's what
GitHub serves:

```bash
git add -A
git commit -m "Update site"
git push
```

> The most common way to break this site is to edit a `.qmd`, push, and forget to
> render first. If a change doesn't show up online, that's almost always why.

## Adding a new resource

1. Copy `resources/_template.qmd` to `resources/your-topic.qmd`.
2. Fill in the front matter — `title`, `description`, `date`, `categories`.
3. Write the page.
4. Render.

It appears on the Resources listing automatically, sorted by date, with category
filters. There is no index to maintain.

Files and folders starting with `_` are ignored by Quarto, which is why the
template doesn't show up as a page.

## Interactive figures

The explainers use [Observable JS](https://quarto.org/docs/interactive/ojs/) —
`ojs` cells that run in the reader's browser. Sliders come from `Inputs.range()`,
plots from `Plot.plot()`. Nothing is precomputed and no server is needed; the
maths runs live as the reader drags a slider.

Note that the model logic in these cells is JavaScript, not R. For an explainer,
that's usually a short function. If you need something that genuinely requires R
packages, the alternative is
[Shinylive](https://quarto.org/docs/blog/posts/2022-10-25-shinylive-extension/),
which runs real Shiny in the browser via WebAssembly — at the cost of a large
first-load download.

## R code chunks

By default, R code appears in plain ` ```r ` blocks: highlighted but not executed,
so the site renders on any machine. To have Quarto actually run a chunk and embed
its figure, change the fence to ` ```{r} `. You'll then need R and the relevant
packages installed wherever you render.

## Layout

```
_quarto.yml            site config, navbar, theme
styles.scss            custom styling
index.qmd              home page
research.qmd           research projects
publications.qmd       papers, preprints, software
teaching.qmd           courses and supervision
talks.qmd              talks and posters
cv.qmd                 CV (web version + link to PDF)
contact.qmd            contact details
resources/
  index.qmd            auto-generated listing page
  _template.qmd        starting point for new resources (ignored by Quarto)
  logistic-growth.qmd  worked example
assets/                images, figures, CV PDF
docs/                  rendered output — generated, but committed
```

## Things still to fill in

Every page carries a highlighted placeholder box marking what needs your input.
Search the source for `placeholder-note` to find them all, and delete each box as
you fill in that page.

Also still to add:

- `assets/profile.jpg` — a photo (then update the image path in `index.qmd`)
- `assets/cv.pdf` — your CV
- Google Scholar and ORCID links in `contact.qmd` and `publications.qmd`
