
# Instagram Shortcodes

- To link an Instagram post from pages, posts, blogs, etc use the following:
    `< instagram/post ########## >`

     where `##########` is the Instagram post ID — the part after `/p/` in the
     URL. For `https://www.instagram.com/p/DdVBnCxGKUm/` the ID is `DdVBnCxGKUm`.

## Card by default, embed on request

By default this renders a **link card** — no third-party JavaScript, nothing
loaded from Meta. Use the named form to change that:

```
< instagram/post id="DdVBnCxGKUm" caption="Photos and clips from the day" >
< instagram/post id="DdVBnCxGKUm" embed="true" >
```

`embed="true"` loads Instagram's `embed.js` and renders the real inline embed.
That puts Meta's script and cookies on every page using it, so it is opt-in per
call. Prefer the card unless the media genuinely needs to play in place.

Hugo does not allow mixing positional and named parameters in a single call, so
use the bare positional form on its own, or the named form when you want
`caption` or `embed`.

## Why the card can't show the picture

Meta retired the public oEmbed endpoint. There is no way to fetch the image,
video, or thumbnail without `embed.js` or an authenticated app token — so the
card links out rather than pretending it can render the media.

## Styling

This module ships no CSS, same as the rest of the collection. The card emits:

```
a.instagram-card
  span.instagram-card-label   "Instagram"
  span.instagram-card-text    caption, or "View this post on Instagram"
  span.instagram-card-cta     "Open →"
```

A starting point:

```css
.instagram-card {
  display: flex;
  align-items: baseline;
  gap: 0.75rem;
  padding: 1rem 1.25rem;
  border: 1px solid #1e2d3d;
  text-decoration: none;
}
.instagram-card:hover { border-color: #00d4ff; }
.instagram-card-label {
  font-size: 0.7rem;
  letter-spacing: 2px;
  text-transform: uppercase;
}
.instagram-card-text { flex: 1 1 auto; }
.instagram-card-cta { font-size: 0.8rem; white-space: nowrap; }
```
