# Known Limitations

## Playlist position is not preserved end-to-end

When sharing from the YouTube Android app, the share sheet only ever includes
one of the following, never both:

- The specific video and timestamp (no playlist/queue info)
- The playlist (no specific video or position)

This has been tested directly: sharing from inside a playing video (within a
saved playlist) drops the playlist info. Sharing from the playlist listing
itself drops the specific video and position. This also affects YouTube's
auto-generated "Mix" queues (list IDs starting with RD), which never include
a usable timestamp or position since the queue is regenerated each time.

This appears to be a limitation of the YouTube Android app's share sheet
itself, not something this project can work around - there is no public API
or alternate share method that exposes all three pieces (video, playlist,
position) together.

### Current behavior

- Sharing a specific video (even one that's part of a playlist) resumes that
  video at its timestamp, but opens standalone rather than reloading the full
  queue.
- Sharing a playlist opens that playlist from its first video.

If YouTube changes this behavior in a future app update, or if a reliable
workaround is found, this document will be updated.