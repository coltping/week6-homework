# week6-homework

This repository holds a Claude skill, `cac-mfh-audit.skill`, built from research into how Army Casualty Assistance Centers (CACs) handle Military Funeral Honors (MFH) requests.

The `.skill` file is on the `feature/skill` branch.

## What the skill is about

A Casualty Assistance Center is the garrison office that, among other duties, receives requests for military funeral honors from funeral directors and families. Each CAC publishes its own web page, request form, deadlines, and coverage area, and these vary widely between installations.

The skill packages a research workflow first done for the Fort Campbell CAC (101st Airborne Division) so that it can be repeated for any Army CAC without retyping the original questions. It is aimed at garrison or Directorate of Human Resources staff who brief leadership and need answers that are accurate, dated, and clear about what public data can and cannot show.

## What it accomplishes

Given an installation name or a question about a CAC, the skill directs Claude to:

1. **Pull the live CAC page and request form** and record the request channel, contacts, lead times, weekend and holiday cutoffs, confirmation standard, after-hours line, coverage area, what personal information the form asks for, and the page and form dates.
2. **Explain how families request honors**, using that installation's actual deadlines and contacts.
3. **Find stale and inconsistent content**, such as superseded forms still hosted, third-party sites reposting old rules, phone or email links that point to the wrong target, and conflicts between the page and the form.
4. **Describe the coverage area and demand**, using veteran population (Census ACS or VA VetPop) as the denominator and labelling any estimate for partial-state areas.
5. **Normalize workload** by annualizing a year-to-date MFH count the user provides and expressing it per 1,000 veterans.
6. **Compare with peer CACs** (by default Fort Stewart, Fort Drum, Fort Riley, and Fort Carson) in a process matrix and a demand table.
7. **Describe staffing indicators** from each page's phone directory, and point to where real headcounts live.
8. **Produce a Fix / Add / Remove list** for the CAC's website, plus actions outside the website.
9. **Outline how to get an obsolete form removed** from the garrison site and from search engines.

A narrow question gets only the steps it needs; a full audit uses all of them.

## Ground rules built into the skill

- Read the live garrison page, not search snippets.
- Never invent MFH volumes or staff headcounts; say when a figure is not published and where it can be obtained.
- Label every estimate and show the method.
- Date-stamp findings, because garrison pages change.
- Report defects plainly, as actionable fixes.

## Contents of the `.skill` file

A `.skill` file is a zip archive. This one contains:

| File | Purpose |
| --- | --- |
| `cac-mfh-audit/SKILL.md` | The skill's name, trigger description, principles, and nine-step workflow |
| `cac-mfh-audit/references/baseline-2026-09.md` | Snapshot captured 30 Sep 2026 of Fort Campbell and its peers (Stewart, Drum, Riley, Carson), to be re-verified against live pages before use |

## Using the skill

Install `cac-mfh-audit.skill` in Claude, then ask in a new chat, for example:

> Use my CAC funeral honors skill to update the research for Fort Campbell.

## Data sources

Public Army garrison pages on `home.army.mil`, U.S. Census Bureau (QuickFacts and ACS table S2101), VA VetPop, and HRC's CAC listing. The Fort Campbell MFH count in the baseline was provided by the author, not taken from a public source.
