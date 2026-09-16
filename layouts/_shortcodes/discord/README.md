
# Discord Shortcodes

- To embed a Discord channel as a full chat client in pages, posts, blogs, etc use the following:
    `< discord/chatroom @@@@@@@@@@ ########## >`

     where `@@@@@@@@@@` is the **guild (server) ID** and `##########` is the
     **channel ID**

- To embed Discord's own server widget — member list plus a join link — use:
    `< discord/widget @@@@@@@@@@ >`

     where `@@@@@@@@@@` is the **guild (server) ID**

## Getting the IDs

Turn on Developer Mode in Discord (Settings → Advanced), then right-click the
server or channel and choose Copy ID. The guild's widget has to be enabled in
Server Settings → Widget for either shortcode to render.

## Changed in v0.5.0

`discord/chatroom` previously took **only** a channel ID and had a specific
guild hardcoded in its widgetbot URL, so every site using it embedded that one
server's chat regardless of the channel passed (issue #3). It now takes the
guild first, matching `discord/widget`.

Callers on v0.4.x need the guild ID added ahead of the existing channel ID.
