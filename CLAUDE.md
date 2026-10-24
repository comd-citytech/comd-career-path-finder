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

## Course decisions (chair, October 2026)

- Retired. Never list or recommend these: COMD 3507, 3540, 3316, 3292, 3532. They are in `retired` in `data/career-map.json`, and the check fails if any of them appear in the pages or data.
- Not offered recently. Show them faded, never recommend them: COMD 3530, 3652 (`"offered": false`).
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

## Writing

Students are the audience: sophomores choosing a concentration and juniors picking electives. Use plain language. No em dashes.

## Before you finish

The data check in `.github/workflows/check-data.yml` runs on every pull request. Run its Python locally, and it must print "All data files look good." Each job plan needs exactly 3 strategy and 4 skills courses, all offered.
