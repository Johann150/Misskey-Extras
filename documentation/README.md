# Misskey Documentation

Additional documentation explaining how to do things or highlighting important
things to know which aren't yet well-documented in the main project. Tips and
tricks go here.

## Table of Contents

1. [ActivityPub Signging](#ActivityPub-Signing)
2. [AiScript source in pages](#aiscript-source-in-pages)
3. [Worker Processes](#worker-processes)
4. [Memory for yarn build](#memory-for-yarn-build)
5. [MFM Editor](#mfm-editor)

## ActivityPub Signing

* **Author**: Johann150
* **Date**: 2021-08-10
* **Misskey Version**: at least since 12.84.3 until 12.85.1
* **Description**: Resolve some federation issues with other AP software.

Some other ActivityPub Software can have issues federating with Misskey with
the default settings. This is because especially with Mastodon, signing
ActivityPub requests is necessary.

Because of this you should enable the `signToActivityPubGet` option in
`.config/default.yml`. This option should already be on the last line of the
example configuration included with misskey.

## AiScript source in pages

* **Author**: Johann150
* **Date**: 2021-08-10
* **Misskey Version**: at least since 12.84.3 until 12.85.1
* **Description**: What to do to embed AiScript source code in a misskey page.

When embedding AiScript source code in a Misskey page inside a code block as
part of a MFM section, the AiScript code sometimes appears to get modified by
Misskey.

To avoid this, you can add another section of type "Multiline Text Input" to
your page and put the source code in the default value. This is done through
the "+"-Button at the end of the "Contents" section, and selecting the
appropriate section type in the resulting popup.

## Worker Processes

* **Author**: Normandy
* **Date**: 2021-08-12
* **Misskey Version**: 12.87.0 (likely applies to earlier versions as well)
* **Description**: Setting the number of worker processes

By default, Misskey uses 1 worker process. If you are experiencing performance
issues, try setting `clusterLimit` in `.config/default.yml` to the number of CPU
cores available to Misskey. Feel free to play around with the number a little
to find one that results in optimal performance.

**Note:** this isn't recommended by the Misskey developers due to potentially higher
RAM utilization. *Your mileage may vary.*

## Memory for `yarn build`

* **Author**: Normandy
* **Date**: 2021-08-20
* **Misskey Version**: 12.88.0
* **Description**: Deadling with memory issues for `yarn build`

When installing or upgrading Misskey, the `yarn build` step may run out of
memory on systems with 2GB or less RAM. There's a few things you can try to do
in this case:
1. If you're running in a VM, you may want to temporarily increase your RAM to
   4GB or higher. This may cost extra if you're renting from a cloud provider.
   If you don't want to deal with the extra cost permanently, you can scale back
   down after running `yarn build`.
2. Increase the heap size for NodeJS. Do this by setting the following environment
   variable: `NODE_OPTIONS=--max-old-space-size=1536`
3. Add swap space by creating a swapfile of at least 1GB. A guide on how to do this
   can be found here: https://linuxize.com/post/create-a-linux-swap-file/

You may have to use both options 2 and 3 if you are on a very memory
constrained system. Keep in mind Misskey itself needs 1GB RAM minimum
to operate well. 

## MFM Editor

* **Author**: Puniko
* **Date**: 2021-08-25
* **Misskey Version**: 12.88.0
* **Description**: An MFM editor was created to allow easy experimentation and 
crafting of MFM Art. It can be found at: https://mfm.absturztau.be/
