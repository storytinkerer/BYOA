# The Adventure Library

Everything in this folder is what BYOA shows under **Our stories**. BYOA reads
`index.json` straight from GitHub, so a story is on everyone's shelf as soon as it is
pushed here. Nobody has to download anything new.

## Adding a story someone shared

1. Download their `.byoa.json` (BYOA's **Save to file**) from the Reddit thread.
2. Read and playtest it in BYOA first.
3. From the BYOA project folder run:

       python3 tool/library_add.py "Their Story.byoa.json" --repo path/to/BYOA

   This writes `library/<id>.byoa.json`, the cover as `library/<id>.png`, and adds or
   updates the entry in `index.json` (with chapters, words and endings counted).
   Adding the same story again raises its version, so players get an offer to update.
4. Commit and push. That's it.

`--clear-placeholders` removes the "coming soon" disks. `--remove <id>` takes a
story off the shelf.

## index.json

    {"byoa_library": 1, "stories": [ {
       "id": "run_gun", "title": "Run & Gun", "author": "Ian",
       "about": "A few lines.", "chapters": 3, "words": 9000, "endings": 4,
       "added": "2026-11-10", "v": 1,
       "file": "library/run_gun.byoa.json", "cover": "library/run_gun.png" } ] }

`color` (#rrggbb) picks the colour of the disk; without it BYOA picks one from the id.
`soon: true` marks a placeholder (no file needed).
