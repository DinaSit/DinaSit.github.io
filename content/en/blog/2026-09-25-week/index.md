---
title: "Weekly notes: what does not get translated"
summary: A bilingual version of the site, and an observation about where the line between translatable and untranslatable data runs.
date: 2026-09-04
authors:
  - me
tags:
  - Studies
  - Hugo
  - Localisation
---

## How the week went

The sixth and final stage of the project: making the site bilingual. It took
more work than the previous four stages combined, and almost all of it was
moving files and translating text.

Done:

- two languages described in the configuration, each with its own title,
  description and menu
- Russian content moved into a separate directory, an English one created
- six project entries and two blog posts translated
- an English profile of the site owner added

## What I took away

The main thing translation gave me was a forced split of the data into
translatable and untranslatable parts. I had never drawn that line before.

The owner profile holds about twenty fields. Translating it revealed that far
from all of them change. Biography, role, interests, skill group names — yes.
The ORCID identifier, profile addresses, study dates, proficiency levels, the
words `C++`, `Python`, `Docker` — no, they are the same in any language.

What I found most interesting is that the theme had already accounted for
this. I went into its code to work out where the translation should go, and
found the following logic: the main data file is read first, then the
language-specific one is merged on top of it, if present. In other words, a
translation lists only the fields that changed; the rest are inherited.

This is not a matter of convenience but a claim expressed in code: a
translation is not a second copy of the data but a partial override of the
first. Had the file needed to be duplicated in full, every edit would have to
be made twice, and the two copies would inevitably drift apart.

The second observation is that translation comes in two different kinds.
Interface strings — "Read more", "On this page", month names — are translated
by the theme itself, which ships dictionaries for them. Content is translated
by the author. The first comes for free once a locale is declared; the second
does not come at all.

## Closing the project

This concludes the individual project. Over six stages an empty template turned
into a site with a biography, work experience, skills, awards, links to
academic profiles, six projects and a dozen blog entries — in two languages and
published automatically on every commit.
