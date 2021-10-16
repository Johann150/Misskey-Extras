# Misskey Plugins

A set of plugins you can apply to your Misskey web client to extend its
functionality.

All plugins can be installed by going to `Settings → Plugins → Install Plugins`
and pasting the plugin's code into the text box, one plugin at a time.

If you are on an older version of Misskey, you might also be interested in the
[archive](archive) of plugins that are not relevant for the latest version of
Misskey any more.

## List of Plugins

1. [DeepL Translate](#DeepL-Translate)
2. [Catify](#Catify)
3. [Note MFM Toggle](note-mfm-toggle)
4. [Sauce Nao](#SauceNao)

## DeepL Translate

* **Author**: Volpeon
* **Date**: 2021-08-08
* **Misskey Version**: 12.85.1
* **Description**: A simple plugin that gives you an automatic translation of a
post from any language into any other language via
[DeepL](https://deepl.com). The translation is displayed in a new tab. The
target langauge is English by default and can be changed in the plugin's
configuration. The setting requires an ISO-639-1 language code (such as "en"
or "de"). Wikipedia has a list of all codes:
https://de.wikipedia.org/wiki/Liste_der_ISO-639-1-Codes

## Catify

* **Author**: Volpeon
* **Date**: 2021-08-12
* **Misskey Version**: 12.87.0
* **Description**: This plugin provides features to make your Misskey
experience even more catty. Features include:

- Turn all users into cats wherever possible Nya-fi your outgoing posts so even
- non-Misskey users will see your meowing

All features are enabled by default, but can be disabled in the plugin
configuration.

## Note MFM Toggle

* **Author**: Volpeon, Johann150
* **Date**: 2021-08-10
* **Misskey Version**: 12.85.1
* **Description**: Toggle MFM on a note per note basis.

With this plugin, MFM can be toggled for specific notes from the three
dot menu of the note.

The plugin source is in [`note-mfm-toggle.aiscript`](note-mfm-toggle.aiscript).

The parser library and MFM stripping functionality was written by Volpeon.
Please note that this might not catch some MFM styles. (yet?)

## SauceNao

* **Author**: Volpeon, Puniko
* **Date**: 2021-08-13
* **Misskey Version**: 12.86.0
* **Description**: This plugin adds a button to each note that will try to reverse
image search with [SauceNao](http://saucenao.com) using the first attachment of that
note. Its based on fristi's pleroma-mod and uses Volpeon's Deepl Plugin as basis. 
This plugin is still a work in progress as it has space for lots of improvement.
