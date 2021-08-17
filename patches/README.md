# Misskey Patches

A set of patches you can apply to your Misskey instance to change or enhance
some functionality.

## List of Patches

1. [Truncate Profiles](#Truncate-Profiles)
2. [MFM search feature](#MFM-search-feature)
3. [Fix Leaky Mutes](#Fix-Leaky-Mutes)
4. [Collapsible Threads](#Collapsible-Threads)

## Truncate Profiles

* **Author**: Toast, Johann150
* **Date**: 2021-08-03
* **Misskey Version**: 12.84.4 - 12.85.1
* **Description**: Patch which truncates profiles that are too long for the database.

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

## MFM search feature

* **Author**: Johann150
* **Date**: 2021-08-10
* **Misskey Version**: 12.84.4 - 12.85.1
* **Description**: Patch to change the search engine used in MFM searches.

Misskey Flavoured Markup (MFM) allows to display a search bar in a post e.g.
like this:
```MFM
misskey [search]
```

By default, this will open a Google search.
There are two places in the source where this URL is stored, one for the
misskey web client UI and another for converting MFM to HTML for other
ActivityPub software.

The files which have to be changed are `src/mfm/to-html.ts` and
`src/client/components/google.vue`.

There are 3 different example patches for more privacy respecting search
engines. If you prefer another, they should enable you to choose a different
one too. In alphabetical order:

- [DuckDuckGo (`mfm-search-duckduckgo.patch`)](mfm-search-duckduckgo.patch)
- [MetaGer (`mfm-search-metager.patch`)](mfm-search-metager.patch)
- [Qwant (`mfm-search-qwant.patch`)](mfm-search-qwant.patch)

Note: It seems that there are provisions for a client setting for this, but
this is not currently implemented in the UI.

## Fix Leaky Mutes

* **Author**: Toast
* **Date**: 2021-08-13
* **Misskey Version**: 12.87.0
* **Description**: When you have muted someone, there was still a possibility
to encounter posts by that person or see posts which mention them thanks to
some loopholes in the way that the system checks whether or not to hide a
post. This patch fixes those issues.

## Collapsible Threads

* **Author**: Johann150
* **Date**: 2021-08-14
* **Misskey Version**: 12.87.0
* **Description**: Make sub-threads collapsible when viewing a note.

This patch adds some JavaScript to the Vue elements that make up the threads.
It allows you to click on the left margin of a thread (e.g. the bar on the left
that makes up a thread) to collapse it and its replies. You can of course also
click in the left margin of a direct reply of the note you are viewing to
collapse it.
