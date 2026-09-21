
# Bandcamp Shortcodes

- To embed the player for a single track in pages, posts, blogs, etc use the following:
    `< bandcamp/track ########## >`

- To embed the player for a whole album or EP use:
    `< bandcamp/album ########## >`

     where `##########` is Bandcamp's **numeric** track or album ID. It is not
     in the URL: find it in the release page's *Share / Embed* dialog (the
     `track=` or `album=` value), or in the page source's `data-tralbum` JSON.

## Tracks on compilations

Use `bandcamp/track` for an artist's track on a label compilation, not
`bandcamp/album`. Bandcamp's album player ignores a requested starting track
(`track=` and `t=` are both ignored in album mode) and always opens on the
album's featured track. The track player still shows the compilation's title and
artwork, and links back to the track's own page.

## Colours

Set once per site in `hugo.yaml`, not per call:

```yaml
params:
  bandcamp:
    linkColor: "00d4ff"    # hex without '#'. Default 0687f5, Bandcamp's blue
    background: "333333"   # 333333 (dark) or ffffff (light). Default 333333
```

The player renders with a transparent background, so `background` only affects
the colour of its controls.

## Privacy

Bandcamp's player loads Google Analytics — third-party tracking, in the same
class as the YouTube and SoundCloud embeds in this collection.
