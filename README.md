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
under Layouts and presses **Save my layout as a file**. That writes a small JSON
file to their downloads folder, named for them and the date, which they email to
whoever is collecting layouts.

To build the comparison, use **Open layout files from your computer** and select
one or several at once. The table at the bottom shows where every section sits in
each person's version. **Save all as one file** writes the whole collection out
as a single JSON file; opening that file later restores the comparison.

**Copy my link** is the alternative when email attachments are awkward: it encodes
the whole arrangement in a URL, and opening that URL loads the layout. Links point
at wherever this page is hosted, so settle on a home before circulating them.

No accounts, sign-in, or server are involved. The collection lives in the browser
tab, so save it to a file before closing.

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
