# Social Campaign Calendar

A single-file, offline tool for planning, producing, approving and measuring the content of a social media campaign. It works in **English and Persian**, left-to-right and right-to-left, with **Gregorian and Solar Hijri (Jalali)** calendars.

No install, no server, no account, no tracking: download `index.html` and open it in your browser.

**[فارسی](README.fa.md)**

## Features

- **Calendar and day-by-day roadmap** built around the campaign's "day zero" (a launch, event or sale). Every date is stored relative to day zero, so moving it moves the whole plan.
- **Content detail** in four tabs:
  - **Main:** channels, type, date and time, owner, priority, deadline, blocker
  - **Brief:** goal, content pillar, audience, key message, hook, call to action, references
  - **Production and files:** caption, on-image text, links to files and versions
  - **Results:** views, engagement and clicks for each channel
- **Six-stage workflow:** Idea → Brief → In production → Awaiting approval → Approved → Published
- **Board** with one column per stage. Drag cards between columns.
- **Needs attention bar:** late work, upcoming deadlines, the approval queue, blocked items and posts whose publishing wasn't recorded, with bulk actions.
- **Dashboard:** stage progress, posts per day, channel and team tables, and performance by channel, content type, goal and pillar, plus top content and progress toward campaign targets.
- Search, filters, Excel (CSV) export and dark mode.

## Getting started

1. Open `index.html` above and click **Download raw file**, then open it in **Chrome** or **Edge**. No install, server or internet connection is needed.
2. In **Settings**, choose the language and calendar, name the main event, set day zero, and add your channels, team and content pillars.
3. Add content with **+ Add content**, or by clicking any day in the calendar.

## Language and calendar

- The button in the header switches between English and Persian. The campaign remembers its language, and the whole page flips direction with it.
- **Settings → Calendar** is automatic by default (Gregorian for English, Solar Hijri for Persian), or you can pick one. Gregorian weeks start on Monday with a Saturday–Sunday weekend; Solar Hijri weeks start on Saturday with a Thursday–Friday weekend.
- While a campaign has no content, the default channel, content type and pillar lists switch language too.

## Saving

Your data is saved **inside the HTML file itself**: the file is both the app and its database.

- In Chrome and Edge, click **Save** (or Ctrl+S) once and pick **this same file**. With **Autosave** on, every change is written to the file from then on. The next time you open the file, click **Resume autosave**.
- In Firefox and Safari, **Save** downloads a new copy, which you use to replace the old file.
- Your browser also keeps a recovery copy. If you close without saving, reopening the same file in the same browser brings your changes back.
- **Save as** starts a new campaign file, and **Load from another file** reads the data from another roadmap file.
- Design files aren't stored in the roadmap, only their links or paths.
- Each copy of the file has its own data, and copies don't merge. For team work, keep one main file.

## Privacy

The app makes no network requests and collects no analytics. The font and all code are embedded in the file, and your data never leaves your device.

## How the file is organized and how to contribute

Everything is in `index.html`: CSS, plain JavaScript (no dependencies, no build step), the font, and the data. The data sits in this block:

```html
<script type="application/json" id="roadmapData">{ … }</script>
```

Each content item is a JSON object. The main fields:

| Field | Meaning |
| --- | --- |
| `offset` | Publish day relative to day zero (`-3` = three days before) |
| `channels` | Channels it is published on |
| `stage` | `idea`, `brief`, `prod`, `review`, `approved` or `published` |
| `lead` | Deadline: days before publishing (`null` = the publish day itself) |
| `goal`, `pillar`, `audience`, `notes`, `hook`, `cta`, `ref` | The brief |
| `caption`, `overlay`, `assets`, `link` | Production and files |
| `perf` | Results: `[{ "ch": "Instagram", "v": 1200, "e": 80, "c": 30 }]` |

All interface text is in the `I18N` object near the top of the script. To add a language, copy the `en` entry, translate it, and add matching entries to `DEFAULTS`, `MONTHS`, `WD_NAMES`, `WD_SHORT` and `LANGS`.

Issues and pull requests are welcome.

## License

- Code: **MIT** © Myousefi-ir. See [LICENSE](LICENSE).
- Font: **Vazirmatn** by Saber Rastikerdar, under the **SIL Open Font License 1.1**. See [OFL.txt](OFL.txt).
- Channel logos (Instagram, LinkedIn, X and others) are trademarks of their owners and are used only to identify channels.
