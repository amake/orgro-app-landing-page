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
"share" or "open in" feature.

## Can Orgro sync with Dropbox?

Orgro doesn't have a concept of "syncing": you open a file to view its contents, and then you close it.

You can open files stored in Dropbox via the file picker (iOS only, due to
[limitations of the Android
app](https://www.dropboxforum.com/t5/Discuss-Dropbox-Developer-API/why-using-Intent-ACTION-OPEN-DOCUMENT-does-not-list-the-Dropbox/td-p/209654))
or by sharing to Orgro from inside the Dropbox app.

# How does Orgro compare to other apps like [Orgzly](http://www.orgzly.com/) and [beorg](https://beorgapp.com/)?

Orgro is a pure viewer for org-mode files with arbitrary content. Orgzly and
beorg are better thought of as task/agenda managers that use org-mode files for
data import/export.
