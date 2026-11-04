<img src="assets/mark.svg" alt="" width="72" height="72">

# aertun.github.io

The manual for [aertun](https://github.com/aertun/aertun), the AI-agent
wind tunnel: breach-and-attack simulation for deployed agent stacks on a
complete detection engine, self-hosted in one binary:
**[aertun.github.io](https://aertun.github.io/)**.

A guide per page, each with the commands it describes as aertun prints them.
Every screen in the aertun console has a Help link to its guide.

## How it is built

```
src/pages/*.html   one guide each: a header comment, then the body
src/nav.txt        the menu, in order
src/layout.html    the frame around every page
assets/            the stylesheet, the one script, the mark, the font and the icons
gen/               the generator: Go, standard library only
sections.txt       every guide the aertun console links to
```

```sh
go run ./gen           # build every page, search.json, sitemap.xml, robots.txt and llms.txt
go run ./gen -check    # what CI runs: fail if anything differs from src/,
                       # a link lands nowhere, or a picture is missing
```

Each page's header sets its heading, its title and description for search
results (the generator refuses a title over about 60 characters or a
description outside 70 to 165), the console screens it is the Help for, and
the date it last changed. Pages carry JSON-LD (TechArticle and breadcrumbs; the
home page SoftwareApplication and WebSite), Open Graph cards and a canonical
URL.

## The contract with the application

A Help link is `https://aertun.github.io/SLUG/`, and `docSections` in
`internal/admin/nav.go` in the aertun repository lists the slugs.
`sections.txt` lists the same, and the build fails if one is not a page.
Renaming a guide means changing it in both repositories.

## Licence

The software and this manual are licensed under the Apache License 2.0; see
[LICENSE](LICENSE). The interface font is derived from Google Sans Flex (SIL
Open Font License 1.1, in `assets/fonts`), and the icons are Material Symbols
(Apache-2.0, in `assets/icons`).
