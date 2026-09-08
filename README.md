# USC Anthropology — site structure prototype

A working prototype for restructuring the USC Dornsife Department of Anthropology
website. Two static pages, no build step, no dependencies.

| File | What it is |
| --- | --- |
| `index.html` | The proposed structure: seven sections, twenty-plus pages, populated from real site content |
| `current-site.html` | A replica of the site as it stands today, for comparison |

Each page has three tabs: **Site** to click through the structure, **Menu editor**
to rearrange it, and **Build notes** listing corrections made, open questions, and
pages still needing content.

## Publishing to GitHub Pages

Create an empty repository on GitHub first, then from this folder:

```sh
git init
git add .
git commit -m "Anthropology site structure prototype"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
git push -u origin main
```

Then in the repository: **Settings → Pages → Build and deployment**, set Source to
"Deploy from a branch", branch `main`, folder `/ (root)`, and save. The site
appears at `https://YOUR-USERNAME.github.io/YOUR-REPO/` within a minute or two.

If the repository is public, anyone with the link can see it. For a departmental
draft you may prefer a private repository, which requires a paid plan for Pages,
or keeping it local and opening `index.html` in a browser directly. It works fine
from the filesystem.

## Editing content

All page content lives in one block near the top of the `<script>` in
`index.html`, in `page("id", { ... })` calls. Fields:

- `title`, `kicker`, `url` — heading, section label, and the URL the page would have
- `prov` — where the content came from: carried over, rewritten, or new
- `body` — array of paragraphs
- `list` / `list2` + `list2head` — label and description pairs
- `blocks` — grouped lists, used for the awards page's year headings
- `out` — outbound links, as `[label, url]` pairs
- `note` — an editorial note explaining a change
- `flag` — an open question needing someone's decision
- `stub` — marks a page with no source content yet

The menu itself is the `LIVE` array further down, a list of sections each with a
`kids` array. Changing it there changes the default structure; changing it in the
Menu editor changes only your browser session.

## Committee layouts

The **Layouts** tab is for comparing arrangements across several people. Each
person opens the page, rearranges the menu in the Menu editor, enters their name
under Layouts and presses **Save and copy my link**. That produces an ordinary
URL with the whole arrangement encoded in it, which they email to whoever is
collecting them. Opening the link loads that person's layout.

To build the comparison, paste each incoming link into the box and press **Add a
colleague's**. The table at the bottom shows where every section sits in each
person's version. **Copy all as JSON** saves the whole collection so it survives
a refresh.

No accounts, sign-in, or server are involved; the layout travels in the URL. The
collection itself lives in the browser tab, so export it before closing.

The Menu editor also has **Copy structure** and **Load structure** for moving a
single arrangement in and out as JSON.

## Status

The Build notes tab is the current worklist. In summary:

- Degree inventory reconciled to the Majors & Minors overview, with Archaeology &
  Heritage Studies added back under its current name
- Paused MA in Visual Anthropology removed from the menu and the About page
- Administration and contact corrected, with Dornsife Social Sciences Hub staff added
- New Research section, since the live site has no research pages at all
- Honors and awards organized by year rather than overwritten each spring
- Six pages remain stubs, mostly experiential learning and people rosters

Several items still need a decision from the department rather than an edit. Those
are marked CHECK in the interface.
