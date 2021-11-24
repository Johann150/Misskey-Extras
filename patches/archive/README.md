# Misskey Patches

Older patches that are not relevant for the lastest vesion of Misskey any more.

These might still be interesting e.g. if you are running an older version of
Misskey.

## List of Patches

1. [Truncate Profiles](#Truncate-Profiles)
2. [Collapsible Threads](#Collapsible-Threads)

## Truncate Profiles

* **Author**: Toast, Johann150
* **Date**: 2021-08-03
* **Misskey Version**: 12.84.4 - 12.87.0
* **Description**: Patch which truncates profiles that are too long for the database.

This problem was resolved in Misskey version 12.88.0 with pull requests
misskey-dev/misskey#7629 and misskey-dev/misskey#7642.

Especially Pleroma allows for very long profiles.
This can cause issues with federation for affected profiles,
because misskey can not work with such users because they can not be stored
in the database.

There are multiple ways to fix this and an upstream fix is supposedly underway.
The easiest way for now, which is implemented with the included
[`misskey-truncate-v2.patch`](misskey-truncate-v2.patch) file, is to truncate
display names and bios to a size misskey can store.

Note however that for security reasons, user names (the `name` part in
`@name@example.com`) is not truncated but federation with such profiles is
still a hard fail. Otherwise, this could lead to malicious actors being able to
impersonate others.

## Collapsible Threads

* **Author**: Johann150
* **Date**: 2021-08-14
* **Misskey Version**: 12.87.0 - 12.97.0
* **Description**: Make sub-threads collapsible when viewing a note.

This patch adds some JavaScript to the Vue elements that make up the threads.
It allows you to click on the left margin of a thread (e.g. the bar on the left
that makes up a thread) to collapse it and its replies. You can of course also
click in the left margin of a direct reply of the note you are viewing to
collapse it.

This patch is no longer deemed necessary because Misskey no longer displays replies
at a depth of 5 or more.
