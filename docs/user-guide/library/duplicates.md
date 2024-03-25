# Duplicate Detection #

Duplicate files are [automatically detected and skipped while indexing](originals.md) your library, so that they only appear once in search results and albums. Their SHA1 checksums and sizes are used for comparison.

!!! tldr ""
    Browsing and deleting duplicates through the web user interface is [planned for a future release](https://github.com/photoprism/photoprism/issues/1308).

## File Import

When [importing](import.md), files are first copied or moved from a temporary folder to the *originals* folder. In the process, duplicates are automatically skipped. "Move" also deletes them in the source directory as if they were successfully moved.

## Related Files

In addition to exact duplicates, there may be similar pictures and related sidecar files (with the same filename) in your library, for example:

- raw + jpg + xmp
- jpg + json
- original + edited version
- original + compressed version
- live and timelapse photos

Depending on your library settings, such files may be automatically grouped into stacks:

[Learn more ›](../organize/stacks.md){ class="pr-3 block-xs" } [Library Settings ›](../settings/library.md)
