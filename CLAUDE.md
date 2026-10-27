# COMD Career Path Finder and Career Map

Read this before changing anything in this repository.

## Source of truth

This repository is the single source of truth for COMD course and career data. Copies anywhere else (claude.ai artifacts, chat drafts, Google Docs, earlier versions) may be out of date. If a copy disagrees with this repo, the repo wins. Update the repo first, then regenerate any copy from it.

| What | Where |
| --- | --- |
| Course list, which line each course belongs to, offered or not, retired courses | `data/career-map.json` (`courses`, `retired`) and the `C` list in `index.html`. Keep both in sync; the check fails if they differ. |
| Entry-level NYC jobs, their 3 strategy + 4 skills plans, internship and senior project focus, NYC pay | `data/career-map.json` (`jobs`) |
| Job descriptions written by faculty | `data/role-content.json` |
| BLS / O*NET pay and outlook (updated automatically) | `data/job-data.json` |
| Skill chart: the job skills each class builds, and each job's skill list | `data/course-skills.json`. The Path Finder builds each job's skills from it, and `skill-chart.html` shows it to faculty. `index.html` keeps a backup copy in its `course-skills` block; refresh that copy when the chart changes. |
| Path Finder job names, lines and O*NET sources | `ROLES` in `index.html` |
| Not-offered courses in the Path Finder | `OFF` in `index.html`. Must match `"offered": false` in `data/career-map.json`; the check fails if they differ. |
| Magazine job cards, course combinations, pay and outlook | `career-magazine.html` (written by hand). Course lists come from the skill chart; figures come from `data/job-data.json`. |

## Course decisions (chair, October 2026)

- Retired. Never list or recommend these: COMD 3507, 3540, 3316, 3292, 3532. They are in `retired` in `data/career-map.json`, and the check fails if any of them appear in the pages or data.
- Not offered recently. Show them faded, never recommend them: COMD 3530, 3652 (`"offered": false` in `data/career-map.json`, `OFF` in `index.html`). Students can still check them off in the Path Finder if they took them.
- COMD 3662 is Strategic Content Creation (the catalog still says Rich Media). It serves Advertising, Graphic Design and Motion, not Web/UX.
- COMD 3402 Brand Strategy for Creatives is a strategy course in marketing and strategic thinking, not logos or brand identity systems (that is 3501). It serves graphic design, copywriting and art direction, not Illustration.
- COMD 3711 Vector Art Editing sits under Illustration.
- COMD 3505 Special Topics in GD alternates between expressive typography and wayfinding.
- COMD 3562 UX/UI is always offered.
- The courses every BFA student takes (3504, 4701, 4730, 4801, 4830, 4900) are called "Studio courses" on every page and in the PDF (not "Senior studio"). Keep them in the skill chart with the skills they build (teamwork, presenting, running projects), and show those skills in the Path Finder as "In studio". They never change which electives are recommended, and they stay out of the Career Map's job plans and the magazine's course lists. Mention only that the internship and senior project should point at the student's target job.
- Use the five current concentrations (Advertising, Graphic Design, Motion, Illustration, Web / UX). Don't reference any proposed track restructure in these pages.

When the chair changes a course decision, update this list in the same commit as the data change.

## Pages

- `index.html`: the live Path Finder (start from your classes). Embedded on the department WordPress site. Change it only with the chair's approval.
- `career-map.html`: the Career Map (start from a job). A separate page, so it doesn't replace the original.
- `career-magazine.html`: the student-facing career magazine. It has no data feed, so any course or figure change must be copied into it by hand in the same pull request.
- `skill-chart.html`: the skill chart for faculty (by class or by job). Not linked from the student hub.
- `hub.html`: one address for all three pages, with a tab for each. It holds no course or career data, so it needs no change when the data changes. If a page is added, renamed or removed, update its tab.

All three pages must agree. When a course is retired, renamed, moved to another line, or marked not offered, update `index.html`, `data/career-map.json` and `career-magazine.html` together. When `data/job-data.json` changes, update the magazine's pay and outlook figures.

## Jobs

The same nine jobs appear on every page, under the same names: Graphic designer, Junior art director, Copywriter and content strategy, Motion designer, Video editor, Illustrator, Visual & UX designer, Front-end developer, Creative producer. The `ROLES` list in `index.html` holds those names, and each job's skill list lives in `data/course-skills.json` under the same name. The Career Map can list several entry-level titles under one job (its `role` field), but every job needs at least one Career Map entry and a magazine spread. When a job is added, renamed or removed, change `index.html`, `data/course-skills.json`, `data/career-map.json` and `career-magazine.html` in the same pull request. The check fails if a job is missing from the Career Map or the magazine.

## Skill chart

`data/course-skills.json` is the one place to say which classes build which job skills. To update a class, edit its `builds` list, copying each skill word for word from that job's list under `jobs`. A skill can come from more than one class. Update `updated` to the date of the change. The data check fails if a skill is misspelled, a job skill has no class, a class is retired, or a job name doesn't match the Path Finder.

Faculty review the chart in a spreadsheet (COMD Skill Chart: Faculty Review), not on GitHub. The spreadsheet is a review copy made from `data/course-skills.json`: faculty mark each class-skill link Keep, Remove or Reword and add missing links. Once the chair approves the changes, copy them into `data/course-skills.json` in a pull request, and the Path Finder and `skill-chart.html` update from it. After that, make a fresh review copy from the repo for the next round instead of editing the old one.

## Footnote

Every page (Path Finder, Career Map, magazine) and the Path Finder PDF carry the same footnote. Its exact text lives in `data/footnote.txt`. When the chair changes it, update `data/footnote.txt`, `index.html` (the page footer and `NOTE` for the PDF), `career-map.html` and `career-magazine.html` in the same pull request. The check fails if any page doesn't match.

## PDF resource links

The Resources box on page 2 of the Path Finder PDF links to these pages. Every link must be up to date: before each semester's advisement period, and whenever City Tech moves a page, click each one and fix any that are broken or point to an old page. The links live in `index.html` (search for "Resource links").

- DegreeWorks degree audit: https://www.citytech.cuny.edu/registrar/degreeworks.aspx
- CUNYfirst registration: the CUNY login page (ssologin.cuny.edu)
- City Tech College Catalog: https://citytech.catalog.cuny.edu/
- Writing Intensive course list: https://www.citytech.cuny.edu/gen-ed/writing-intensive.aspx
- Academic Calendar: https://www.citytech.cuny.edu/registrar/academic-calendar.aspx
- Professional Development Center: https://www.citytech.cuny.edu/pdc/ (use this link anywhere a page mentions the PDC)
- COMD advisement and Sophomore Review: https://openlab.citytech.cuny.edu/comd-advisement/
- COMD Career Path Finder: https://comd-citytech.github.io/comd-career-path-finder/hub.html

The Find Your Advisor block below it links to https://openlab.citytech.cuny.edu/comd-advisement/find-your-advisor/ and communicationdesign@citytech.cuny.edu.

## Writing

Students are the audience: sophomores choosing a concentration and juniors picking electives. Use plain language. No em dashes.

## Before you finish

The data check in `.github/workflows/check-data.yml` runs on every pull request. Run its Python locally, and it must print "All data files look good." Each job plan needs exactly 3 strategy and 4 skills courses, all offered.
