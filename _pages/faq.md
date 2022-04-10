---
layout: page
title: FAQ
include_in_header: true
---

# Can I edit my files with Orgro?

No, Orgro is a pure viewer. Editing may come in the future, but probably not any
time soon.

# Can Orgro access my files?

Orgro can directly open files accessible by the standard file-opening mechanisms
on Android and iOS, including files within third-party apps that implement
appropriate file-providing APIs. As of 2020-6-8 that includes apps like Dropbox
(iOS only) and Google Drive.

For other apps, you should be able to send your file to Orgro with the standard
“share” or “open in” feature.

# Can Orgro sync with Dropbox?

Orgro doesn’t have a concept of “syncing”: you open a file to view its contents,
and then you close it. No persistent data derived from the file is retained that
must be kept “in sync”.

You can open files stored in Dropbox via the file picker or by sharing to Orgro
from inside the Dropbox app.

# How does Orgro compare to other apps like [Orgzly](http://www.orgzly.com/) and [beorg](https://beorgapp.com/)?

Orgro is a pure viewer for Org Mode files with arbitrary content. Orgzly and
beorg are better thought of as task/agenda managers that use Org Mode files for
data import/export.

# How can I use relative links between Org Mode files?

## Requirements

Orgro v1.18.0 and later supports relative links between Org Mode files under
certain conditions:

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

2. On Android support for relative links depends on your OS version:

   - Android 8 Oreo and later: full support
   - Android 5 Lollipop through 7 Nougat: partial support
     - Links pointing "up" the filesystem hierarchy (`..`) are not supported
     - Resolving relative links may be slow
   - Android 4.4 and earlier: no support

3. The way you opened the file also matters: files opened by intent on Android
   do not support relative links.

## Granting permissions

To allow Orgro to resolve a relative link to another Org Mode file, you must
grant Orgro directory access permissions.

When a file contains relative links and Orgro does not yet have the right
permissions, a banner will appear at the top of the document prompting you to
grant access.

Tap Grant Access to open a directory picker. Choose a directory high enough in
the hierarchy that it contains both 1) the file you opened and 2) the files
linked to.

If all goes well, the banner will disappear and relative links will open on top
of the starting document.
