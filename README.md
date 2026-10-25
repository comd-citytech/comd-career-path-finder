# COMD Career Path Finder

An interactive planner for City Tech Communication Design students. Students check off the COMD courses they've finished and see which path they're closest to, the jobs it leads to, what employers ask for, and which classes to take next.

It is a planning tool, not a degree audit. Students should always confirm their plan with a COMD advisor and DegreeWorks.

## What's in this folder

| File | What it holds | Who edits it |
| --- | --- | --- |
| `data/role-content.json` | Job descriptions: a day on the job, why students should look into it, job board search terms, NYC employers, portfolio pieces | Faculty |
| `data/job-data.json` | Pay, number of jobs and outlook from the U.S. Bureau of Labor Statistics and O*NET | Updated automatically twice a year (May 15 and September 15) |
| `index.html` | The page itself, including the course list and the class-to-skill links | Department chair, after faculty review |
| `career-map.html` | Career Map prototype: pick an entry-level job and see the 3 strategy and 4 skills courses for it. Separate page; `index.html` is unchanged | Department chair, after faculty review |
| `career-magazine.html` | "Where COMD @ City Tech Takes You": the student-facing career magazine. Nine jobs, what each pays, which are growing, the courses that count twice, and the designer-to-creative-director ladder. Standalone page; nothing else depends on it | Department chair, after faculty review |
| `hub.html` | One address for all three pages. A tab bar on top switches between the Path Finder, the Career Map and the magazine. It holds no data of its own | Department chair |
| `data/career-map.json` | Career Map content: courses (with an `offered` flag), entry-level NYC jobs, their course plans, internship and senior project focus, NYC pay | Faculty suggest edits; chair approves |

### Editing the Career Map

Open `data/career-map.json` and edit it the same way as `role-content.json`. Each job needs exactly 3 `strategy` and 4 `skills` course codes. If a course hasn't been offered recently, set `"offered": false`. It stays on the map, faded, and the check flags any job plan that still recommends it. To retire a course for good, add its code to `"retired"` and remove it from both pages. The check fails if a retired course shows up anywhere, or if the two pages' course lists don't match.

`CLAUDE.md` lists the current course decisions. Claude reads it before working in this repo, so the same rules apply in every chat.

## How faculty suggest an edit

You need a free GitHub account. You do not need to install anything.

1. Open `data/role-content.json` in this repository.
2. Click the pencil icon (Edit this file) at the top right of the file.
3. Find your job. The short codes are: `gd` graphic designer, `ad` art director, `cw` copywriter, `mo` motion designer, `il` illustrator, `ux` UX/UI and web designer.
4. Type your text between the quote marks. For lists, follow the pattern `["first item", "second item"]`.
5. Click **Commit changes**, choose **Create a new branch and start a pull request**, and add a short note about what you changed.

The chair reviews the suggestion and publishes it. A check runs on every suggestion and flags it if the file's formatting is broken, so a typo can't break the live page.

**Quick formatting rules**

- Keep text inside straight double quotes: `"like this"`.
- If your text needs a double quote inside it, type `\"`.
- Every item in a list needs a comma after it, except the last one.

## The career magazine

`career-magazine.html` is the student-facing read. The Path Finder is a tool students open when they are planning a semester; the magazine is something they read, share, and show their families. It covers nine jobs rather than six, adds the courses that feed more than one career, and ends with the designer to art director to creative director ladder.

Three jobs on it are proposed additions pending faculty review: front-end web developer, video editor, and creative producer. They are in the Path Finder already. The Career Map has a video editor plan; front-end developer and creative producer don't have Career Map plans yet.

The course lists on each job card come from the courses the Path Finder links to that job, leaving out courses not offered recently. When a course changes in `index.html` or `data/career-map.json`, update the magazine in the same pull request. The data check fails if a retired course appears on any of the three pages.

Every figure links out to its source on the BLS or O*NET page it came from, so a student or a reviewer can check any number without leaving the page. Pay figures are refreshed each fall from the same release that updates `data/job-data.json`.

## One address for all three pages

`hub.html` puts the Path Finder, the Career Map and the magazine behind three tabs: **Start from my classes**, **Start from a job** and **Explore careers**. Each page loads the first time a student opens its tab and keeps its place after that. The three pages themselves are unchanged.

- Link to a tab with `hub.html#pathfinder`, `hub.html#map` or `hub.html#magazine`.
- Link to a job in the Career Map with `hub.html#map/` plus the job's id from `data/career-map.json`, for example `hub.html#map/web-designer`.
- When the Career Map or the magazine links to the Path Finder, the hub switches tabs instead of opening the Path Finder inside the other tab.

The selected page fills the window under the tabs and scrolls on its own. That keeps the magazine's section menu and the Path Finder's side panel pinned as students scroll. To embed it on WordPress, give the frame a fixed height close to the screen height:

```html
<iframe src="https://comd-citytech.github.io/comd-career-path-finder/hub.html"
  title="COMD Career Tools" style="width:100%;height:90vh;min-height:640px;border:0"></iframe>
```

## Suggesting changes to courses or class-to-skill links

Open an issue (the **Issues** tab, then **New issue**) and describe the change. These links decide what students are told, so the chair makes those edits directly after review.

## Where the job data comes from

- [BLS Occupational Outlook Handbook](https://www.bls.gov/ooh/): pay, number of jobs, 10-year outlook, where people work
- [O*NET](https://www.onetonline.org/): the tasks, tools and skills employers ask for

Figures are national. Pay is the median across all experience levels, so first jobs usually start lower.
