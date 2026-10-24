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
| Job-to-skill-to-course links for the Path Finder | `ROLES` in `index.html` |
| Not-offered courses in the Path Finder | `OFF` in `index.html`. Must match `"offered": false` in `data/career-map.json`; the check fails if they differ. |
| Magazine job cards, course combinations, pay and outlook | `career-magazine.html` (written by hand). Course lists come from `ROLES`; figures come from `data/job-data.json`. |

## Course decisions (chair, October 2026)

- Retired. Never list or recommend these: COMD 3507, 3540, 3316, 3292, 3532. They are in `retired` in `data/career-map.json`, and the check fails if any of them appear in the pages or data.
- Not offered recently. Show them faded, never recommend them: COMD 3530, 3652 (`"offered": false` in `data/career-map.json`, `OFF` in `index.html`). Students can still check them off in the Path Finder if they took them.
- COMD 3662 is Strategic Content Creation (the catalog still says Rich Media). It serves Advertising, Graphic Design and Motion, not Web/UX.
- COMD 3711 Vector Art Editing sits under Illustration.
- COMD 3505 Special Topics in GD alternates between expressive typography and wayfinding.
- COMD 3562 UX/UI is always offered.
- Leave out the courses every BFA student takes (3504, 4701, 4730, 4801, 4830, 4900) from job plans. Mention only that the internship and senior project should point at the student's target job.
- Use the five current concentrations (Advertising, Graphic Design, Motion, Illustration, Web / UX). Don't reference any proposed track restructure in these pages.

When the chair changes a course decision, update this list in the same commit as the data change.

## Pages

- `index.html`: the live Path Finder (start from your classes). Embedded on the department WordPress site. Change it only with the chair's approval.
- `career-map.html`: the Career Map (start from a job). A separate page, so it doesn't replace the original.
- `career-magazine.html`: the student-facing career magazine. It has no data feed, so any course or figure change must be copied into it by hand in the same pull request.

All three pages must agree. When a course is retired, renamed, moved to another line, or marked not offered, update `index.html`, `data/career-map.json` and `career-magazine.html` together. When `data/job-data.json` changes, update the magazine's pay and outlook figures.

## Writing

Students are the audience: sophomores choosing a concentration and juniors picking electives. Use plain language. No em dashes.

## Before you finish

The data check in `.github/workflows/check-data.yml` runs on every pull request. Run its Python locally, and it must print "All data files look good." Each job plan needs exactly 3 strategy and 4 skills courses, all offered.
