---
description: Today's job search with Roleford: status, new matches worth a look, and follow-ups due
argument-hint: "[skills, place or work mode]"
---

Use the `job-search` skill. Call `get_status`; if it isn't ready, give its link and stop. Then call `find_jobs` with
`newOnly` and the filters the user gave in $ARGUMENTS, and show the best few with why they fit. Then call
`list_applications` and say which follow-ups are due. Ask before unlocking anything.
