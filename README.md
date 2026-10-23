# COMD Career Path Finder

An interactive planner for City Tech Communication Design students. Students check off the COMD courses they've finished and see which path they're closest to, the jobs it leads to, what employers ask for, and which classes to take next.

It is a planning tool, not a degree audit. Students should always confirm their plan with a COMD advisor and DegreeWorks.

## What's in this folder

| File | What it holds | Who edits it |
| --- | --- | --- |
| `data/role-content.json` | Job descriptions: a day on the job, why students should look into it, job board search terms, NYC employers, portfolio pieces | Faculty |
| `data/job-data.json` | Pay, number of jobs and outlook from the U.S. Bureau of Labor Statistics and O*NET | Updated automatically twice a year (May 15 and September 15) |
| `index.html` | The page itself, including the course list and the class-to-skill links | Department chair, after faculty review |

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

## Suggesting changes to courses or class-to-skill links

Open an issue (the **Issues** tab, then **New issue**) and describe the change. These links decide what students are told, so the chair makes those edits directly after review.

## Where the job data comes from

- [BLS Occupational Outlook Handbook](https://www.bls.gov/ooh/): pay, number of jobs, 10-year outlook, where people work
- [O*NET](https://www.onetonline.org/): the tasks, tools and skills employers ask for

Figures are national. Pay is the median across all experience levels, so first jobs usually start lower.
