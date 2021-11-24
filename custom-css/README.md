# Misskey Custom CSS

Custom CSS tweaks you can apply to your web client to change how Misskey looks
or behaves.

## List of Custom CSS

1. [Post Replies on Hover](#Post-Replies-on-Hover)
2. [MFM on Hover](#MFM-on-Hover)
3. [Post Replies slide out](#Post-Replies-slide-out)
4. [Hide "You" in Mentions](#Hide-You-in-Mentions)
5. [Hide Profile Icon in Mentions](#Hide-Profile-Icon-in-Mentions)
6. [Stop Blinking Notification Dots](#Stop-Blinking-Notification-Dots)

## Post Replies on Hover

* **Author**: Volpeon
* **Date**: 2021-09-25
* **Misskey Version**: 12.91.0
* **Description**: A custom CSS snippet to declutter the timeline, similar to
how Pleroma displays replies.

- Parent posts are hidden by default
- When you hover a post, the parent post will be shown
- To avoid any erratic behavior, the parent post appears on top of the preceding post, covering it
- For better visibility, the hovered post will be highlighted

## MFM on Hover

* **Author**: Fristi, Volpeon, Robflop
* **Date**: 2021-08-23
* **Misskey Version**: 12.89.0
* **Description**: A custom CSS snippet which stops MFM animations until you
are hovering over the post. This makes it much less annoying to browse your
timeline if someone has made a post with MFM that causes the post's contents
to go outside of the post itself.

## Post Replies slide out

* **Author**: Johann150
* **Date**: 2021-08-23
* **Misskey Version**: at least since 12.83.4
* **Description**: Alternate way to collapse parent posts that does not allow
overflow.

- Parent posts are shortened to the user name and first line of content.
- When you hover over the parent post, the main post will slide down to make
  the rest of the parent post visible.

## Hide "You" in Mentions
* **Author**: Amolith
* **Date**: 2021-10-25
* **Misskey Version**: 12.94.1
* **Description**: Hide the tiny text next to your handle that says "You" when someone mentions you:

```
.me {
  display: none;
}
```

## Hide Profile Icon in Mentions
* **Author**: Amolith
* **Date**: 2021-10-25
* **Misskey Version**: 12.94.1
* **Description**: Hide the profile picture icon next to a handle in a post:

```
.icon {
  display: none;
}
```

## Stop Blinking Notification Dots
* **Author**: Striker
* **Date**: 2021-11-23
* **Misskey Version**: 12.96.1
* **Description**: Stop the blinking dots indicating you have unread notes.
