# Misskey Patches

A set of patches you can apply to your Misskey instance to change or enhance
some functionality.

If you run an older version of Misskey, you might also be interested in the
[archive](archive) of patches that are not relevant for the latest version of
Misskey any more.

## List of Patches

1. [MFM search feature](#MFM-search-feature)
2. [Fix Leaky Mutes](#Fix-Leaky-Mutes)
3. [Compact Notifications](#Compact-Notifications)
4. [Compatibility Keyoxide](#compatibility-keyoxide)
5. [Extend emoji list](#Extend-emoji-list)
6. [Star is Like](#Star-is-Like)

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

## Compact Notifications

* **Author**: Johann150
* **Date**: 2021-08-23
* **Misskey Version**: 12.97.1
* **Description**: Remove text of replied-to posts from notifications.

The text of replied to or renoted notes is not shown in the notifications bar,
i.e. instead of 'reply RE: post' the notification is just 'reply'.

## Compatibility Keyoxide

* **Author**: sousuke0422
* **Date**: 2021-08-31
* **Misskey Version**: since 12.68.0
* **Description**: You will be able to register with Keyoxide.

Keyoxide uses application/json for authentication, so add support for it.
It is treated as a mastodon in Keyoxide specification.

Ported from ayuskey 5.11.0.

## Extend Emoji list

* **Author**:Johann150
* **Date**: 2021-11-24
* **Misskey Version**: 12.97.1
* **Description**: Add some aliases and new emojis to the builtin emoji list.

Adds the "pudding" synonym to the custard emoji, and also newly adds regional
indicator emojis to the list. These are displayed as letters if alone. Note
that these become the national flags if put next to each other, so the
behaviour might be confusing to some people.

## Star is Like

* **Author**: Johann150
* **Date**: 2022-03-19
* **Misskey Version**: since 12.99.0
* **Description**: Turns Star reactions into ordinary ActivityPub likes.

⚠️ Depending on when you read this, you may also need to patch the issue
[misskey-dev/misskey#8428](https://github.com/misskey-dev/misskey/pull/8428)
for this to always behave correctly.

With this patch, all star reactions will be turned into an ordinary like
activity which will allow you to star a post from Pleroma. Since Mastodon
only understands likes anyway, its behaviour will not change. Star reacts
may be displayed as a thumbs up reaction on other Misskey instances.
