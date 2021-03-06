# Permanode Attributes

While a permanode can have any arbitrary attributes and values (and
each value can be single-valued or multi-valued), the following are
the conventional attributes and values used by the various tools,
search, FUSE, and web UI.

"tag": (multi-valued)

    a set of zero or more keywords (or phrases) indexed completely, for
    searching by tag. No HTML.

"title": (single-valued)

    A name given to the permanode. No HTML.

"description": (single-valued)

    An account of the permanode. It may include but is not limited to:
    an abstract, a table of contents, or a free-text account of the
    resource. No HTML.  As of 2013-12-28, not very defined yet.

"camliContent": (single-valued)

    when a permanode is a file, the camliContent is set to the fileref
    (the blobref of the "file" schema blob)

"camliContentImage": (single-valued)

    when a permanode has camliContent set, but the camliContent is of
    a non-image, the camliContentImage points to a "file" schema's
    blobref of an image representation of the content. For instance,
    this might be the cover art of an MP3 file or a thumbnail of a
    spreadsheet.

"camliMember": (multi-valued)

    when the permanode represents a set (unordered, unkeyed), the
    parent permanode (the container set) has a camliMember set to the
    permanode of each child element.

"camliPath:$dirent_name" (single-valued)

    when the permanode represents an associative container, each keyed
    child permanode blobref is pointed to by the "camliPath:$key"
    attribute on the parent.  This is used by the FUSE client, and
    respected in the UI (browser, publishing code), etc.

"camliNodeType" (single-valued)

    when the application needs to note the type of a permanode before
    any other attributes (like those above) are added which would otherwise
    imply its type, the camliNodeType lets applications be specific.
    This should only be used if another attribute can't imply it.
    Currently only used by FUSE to indicate the difference between a new
    file and a new directory permanode.  Known values include:

        * "directory". this permanode will have "camliPath:$key"
          attributes later.
        * "file". this permanode will have a "camliContent" later. for
          now, it should be treated as if it's an empty, 0-byte file.

"camliDefVis" (single-valued)

    Can be "hide". Experimental. Affects default visibility in web UI.

"xattr:$attr_name" (single-valued)

    when a permanode represents a file or directory visible to FUSE,
    "xattr:$x" is used to store the value for extended attribute "x".
    Extended attribute data may contain any arbitrary bytes, so values
    are base64 encoded.

"camliRoot" (single-valued)

    TODO: doc

"camliImportRoot" (single-valued)

    TODO: doc
