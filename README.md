# yalimohammadi.github.io

Custom Jekyll site for the academic homepage of Yeganeh Alimohammadi.

## How it works

This site is a single long-scrolling page (`index.html` → `_layouts/home.html`)
with a sticky top nav whose links jump to anchor sections. All content is
stored in `_data/*.yml` so the layout file rarely needs to be touched.

## File map

```
_config.yml              Site config — name, email, social links
_layouts/home.html       The single page layout (HTML + Liquid)
_includes/head.html      <head> tags (meta, SEO, CSS link)
_includes/pub.html       Publication partial (citation + links + abstract)
_data/
  news.yml               News section (top of homepage)
  publications.yml       Working papers, journals, conferences
  talks.yml              Invited talks, grouped by topic
  teaching.yml           Instructor + TA roles
  service.yml            PC, journal reviewing, seminar org
  students.yml           PhD students and mentees
  awards.yml             Honors
assets/css/style.css     All styles
index.html               Front-matter page that uses the home layout
```

## Updating content

Most updates only touch the data files. Add a new news item:

```yaml
# _data/news.yml
- date: "Jun 2026"
  text: |
    Your news text. HTML like <em>italic</em> or <a href="...">links</a> works.
```

Add a new publication:

```yaml
# _data/publications.yml — under working_papers:, journals:, or conferences:
  - authors: "Y. Alimohammadi, Coauthor One, Coauthor Two"
    title: "Paper title"
    venue: "Operations Research"    # journals/conferences only
    year: 2026                      # journals/conferences only
    arxiv: "2601.12345"             # arXiv ID — pill links to arxiv.org/abs/ID
    slides: "/files/slides-X.pdf"   # URL — pill links here
    video: "https://youtu.be/X"     # URL — pill links here
    abstract: |                     # click-to-expand abstract (markdown OK)
      Abstract text. Use **bold**, *italics*, [links](https://...).
      Blank line between paragraphs.
```

**Every paper has four pills**: arXiv, slides, video, abstract. The visual row stays uniform across the page.

Use `"#"` as the value for a field you don't have content for yet:

```yaml
slides: "#"      # renders a muted, non-clickable "TBD" pill
video: "#"
```

That way the row keeps the same shape on every paper while you collect URLs over time. Replace `"#"` with the real URL when you have it. Remove the field entirely if you never want that pill on that paper.

The arXiv pill always reads "arXiv" — the actual ID lives in the link target, not the visible label.

The template automatically bolds `Y. Alimohammadi` wherever it appears in
the authors string. If you want a different name format, edit
`author.short_name` in `_config.yml` and use that exact string in your
publications.

## Migrating from the existing AcademicPages setup

Replace the entire repo contents with these files, but keep:

```
images/profile.png       Your existing profile photo
files/cv_Yeganeh.pdf     Your existing CV
```

You can delete:

- `_layouts/` from AcademicPages (other than the new home.html)
- `_pages/` (all the AcademicPages pages — research, talks, teaching)
- `_includes/` from AcademicPages
- The old `_config.yml`
- `assets/` directories from AcademicPages

After replacing, push to GitHub. GitHub Pages will rebuild automatically.

## Running locally

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

If you don't want to install Ruby locally, just push to GitHub and view
the live site — GitHub Pages handles the build.

## Design notes

- **Aesthetic**: editorial newsroom — Georgia serif body, Helvetica labels,
  crimson accent (#8b1f1f) used sparingly on the italic surname, section
  markers, and link underlines.
- **Width**: max 760px content column for readability.
- **Sticky nav**: stays at the top of the viewport as you scroll. The
  links use anchor navigation (smooth-scrolled via CSS).
- **Mobile**: nav collapses to a vertical stack under 640px, photo moves
  above the name, justified text becomes left-aligned.
- **Print**: nav and footer hidden, accent colors fall back to black,
  page breaks avoided inside sections.
