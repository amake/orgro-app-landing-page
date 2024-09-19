---
layout: page
title: FAQ
include_in_header: true
---

# Can I edit my files with Orgro?

Yes! Orgro has support for plain-text editing, where you edit raw markup.

It also has a limited set of “structured” editing features, namely:

- Toggling checkboxes on list items (`[ ]` ↔︎ `[X]`)
- Cycling `TODO` keywords on headlines (`TODO` → `DONE` → none ↩︎)

When Orgro has write permissions to the current file, it will ask if you want to
save changes. Click “Always” or “Just this time” to allow saving. Orgro will
auto-save a few seconds after the last change; look for the Snackbar
notification.

**Important:** When saving, Orgro will recreate the original file from its
in-memory representation. In doing so it will attempt to limit changes to only
the parts you have edited, but it is possible that it may alter other parts as
well. In particular, non-semantic white space may not be preserved.

**You are recommended to keep backups of your files in case Orgro mangles
them.** Please [report](https://github.com/amake/orgro/issues) any issues you
find.

# Can Orgro access my files?

Orgro can directly open files accessible by the standard file-opening mechanisms
on Android and iOS, including files within third-party apps that implement
appropriate file-providing APIs. As of 2022-4-10 that includes apps like Dropbox
and Google Drive.

For other apps, you should be able to send your file to Orgro with the standard
“share” or “open in” feature.

# Can Orgro sync with Dropbox?

Orgro doesn’t have a concept of “syncing”: you open a file to view its contents,
and then you close it. No persistent data derived from the file is retained that
must be kept “in sync”.

You can open files stored in Dropbox via the file picker or by sharing to Orgro
from inside the Dropbox app.

# How does Orgro compare to other apps like [Orgzly](http://www.orgzly.com/) and [beorg](https://beorgapp.com/)?

Orgro is a general-purpose viewer and editor for Org Mode files with arbitrary
content. Orgzly and beorg are better thought of as task/agenda managers that use
Org Mode files for data import/export.

# How can I use links between Org Mode files?

## Requirements

Orgro v1.18.0 and later supports links between Org Mode files under certain
conditions:

1. Your files must be stored in a location that allows obtaining directory
   permissions. Many major third-party apps do not support this.

   Storage providers known to support directory permissions include:

   - iOS
     - Local storage
     - iCloud Drive
     - [Working Copy](https://workingcopyapp.com/)
   - Android
     - Local storage
     - [Seafile](https://www.seafile.com/en/features/)

   Storage providers known to *not* support directory permissions as of
   2021-4-26 include:

   - Dropbox (all platforms)
   - Google Drive (all platforms)

   If in the directory picker's source selector your app is grayed out (iOS) or
   does not appear at all (Android) then it probably does not support the
   required APIs.

2. On Android support for links depends on your OS version:

   - Android 8 Oreo and later: full support
   - Android 5 Lollipop through 7 Nougat: partial support
     - Links pointing "up" the filesystem hierarchy (`..`) are not supported
     - Resolving relative links may be slow
   - Android 4.4 and earlier: no support

3. The way you opened the file also matters: files opened by intent on Android
   do not support relative links.

## Granting permissions

To allow Orgro to resolve a link to another Org Mode file, you must grant Orgro
directory access permissions.

When a file contains external file links and Orgro does not yet have the right
permissions, a banner will appear at the top of the document prompting you to
grant access.

Tap Grant Access to open a directory picker. Choose a directory high enough in
the hierarchy that it contains both 1) the file you opened and 2) the files
linked to.

If all goes well, the banner will disappear and file links will open on top of
the starting document.

# Can I filter a document like with `org-match-sparse-tree`?

Orgro v1.37.0 and later support filtering a document to produce a “sparse tree”.
See the [Orgro
manual](https://github.com/amake/orgro/blob/master/assets/manual/orgro-manual.org#sparse-trees)
for general information.

The query language supported by Orgro is a subset of the full language described
in the [Matching tags and
properties](https://orgmode.org/manual/Matching-tags-and-properties.html)
section of the Org manual. In particular:

- Regex is not supported
- Date/time-type property values are not supported
- Group tags are not expanded
- Trailing TODO clauses (delimited by `/`) are not supported
- Tags and properties are not inherited; in other words the matching behavior is
  consistent with `org-use-tag-inheritance` and `org-use-property-inheritance`
  both being `nil`
