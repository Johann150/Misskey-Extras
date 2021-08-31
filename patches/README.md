# Misskey Patches

A set of patches you can apply to your Misskey instance to change or enhance
some functionality.

If you run an older version of Misskey, you might also be interested in the
[archive](archive) of patches that are not relevant for the latest version of
Misskey any more.

## List of Patches

1. [MFM search feature](#MFM-search-feature)
2. [Fix Leaky Mutes](#Fix-Leaky-Mutes)
3. [Collapsible Threads](#Collapsible-Threads)
4. [Compact Notifications](#Compact-Notifications)

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

## Compact Notifications

* **Author**: Johann150
* **Date**: 2021-08-23
* **Misskey Version**: since 12.64.2
* **Description**: Remove text of replied-to posts from notifications.

The text of replied to or renoted notes is not shown in the notifications bar,
i.e. instead of 'reply RE: post' the notification is just 'reply'.

## Compatibility Keyoxide

* **Author**: sousuke0422
* **Date**: 2021-08-31
* **Misskey Version**: since 12.68.0
* **Description**: You will be able to register with Keyoxide.

It is treated as a mastodon in Keyoxide specification.

Ported from ayuskey 5.11.0.
