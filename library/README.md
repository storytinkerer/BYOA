# The Adventure Library

Everything in this folder is what BYOA shows under **Our stories**. BYOA reads
`index.json` straight from GitHub, so an adventure is on everyone's shelf as soon as it is
pushed here. Nobody has to download anything new.

## Adding an adventure someone shared

1. Download their zip from the Reddit thread. It is the zip BYOA's **Download story**
   makes: chapter scripts, README, story texts, and the floppy in `disk/`.
2. Run it on your BYOK first.
3. From the BYOA project folder run:

       python3 tool/library_add.py "their-story.zip" --repo path/to/BYOA

   This copies the zip to `library/<id>.zip`, the floppy to `<id>-label.png` and
   `<id>-spine.png`, and adds or updates the entry in `index.json` (chapters, words and
   endings are counted from the story, the genres and the size come from the zip). Adding
   the same story again raises its version.
4. Commit and push. That's it.

`--clear-placeholders` removes the "coming soon" disks. `--remove <id>` takes an
adventure off the shelf.

## index.json

    {"byoa_library": 1, "stories": [ {
       "id": "run_gun", "title": "Run & Gun", "author": "Ian",
       "about": "A few lines.", "chapters": 3, "words": 9000, "endings": 4,
       "added": "2026-11-10", "v": 1, "color": "#2D4B52",
       "genres": ["Thriller", "Mystery"], "bytes": 48213,
       "zip": "library/run_gun.zip",
       "label": "library/run_gun-label.png", "spine": "library/run_gun-spine.png" } ] }

`color` (#rrggbb) is the colour of the disk; without it BYOA picks one from the id.
`genres` are one or two of Adventure, Mystery, Sci-fi, Fantasy, Horror, Thriller, Comedy,
Drama, Romance, Historical (anything else is ignored). `bytes` is the size of the zip, shown
next to DRIVE A:. `soon: true` marks a placeholder (no zip needed).
