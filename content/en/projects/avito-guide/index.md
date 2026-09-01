---
title: Interactive onboarding platform for a classifieds site
date: 2026-08-14
links:
  - type: site
    url: https://github.com/wadt3rr/avito-guide
tags:
  - Go
  - TypeScript
  - React
  - PostgreSQL
  - Docker
---

A team project from the Avito "Code Lab" hackathon: a system that guides users
through a product interface while they are working in it.

<!--more-->

The platform consists of an embeddable widget, a demo classifieds site, an
admin panel for managing onboarding scenarios, a backend API and completion
analytics.

My contribution:

- publication and targeting endpoints in Go: selecting a scenario by route,
  user context and priority;
- the embeddable TypeScript widget and its integration with the API;
- the demo classifieds site in React, with onboarding anchors and page context
  reported to the widget;
- deployment of the whole stack in Docker Compose and continuous integration
  on GitHub Actions.

The project reached the hackathon finals.
