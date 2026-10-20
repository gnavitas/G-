# G+

A Tampermonkey userscript for Facebook, Instagram, TikTok and X.

It hides the like, comment, share and repost buttons if you don't want to see them, lets you watch Instagram and Facebook stories without showing up in the viewer list, and adds download buttons for stories, posts and videos. All of it lives in one file.

I wrote it because I was tired of juggling four different extensions that each did one small thing, and half of them broke every time a site changed its layout. This one will break too, sometimes. More on that further down.

## What each site gets

| Site | Can hide | Extras |
|---|---|---|
| Instagram | Hearts (button, count and the "liked by" line), reposts, comments, send, bookmark | Anonymous story view, story download (one or all), post download (photos and videos, carousels included) |
| Facebook | Likes, comments, share, reactions | Anonymous story view, story download (one or all) |
| TikTok | Likes, comments, bookmark, share | Download button above the like button |
| X | Reposts, likes, comments, bookmark | Download button on posts with photos or videos (grabs everything in the post) |

Every toggle is per site, so turning something off on X doesn't touch Facebook.

## Install

1. Install [Tampermonkey](https://www.tampermonkey.net/).
2. Newer Chrome and Edge builds won't run userscripts until you allow them. Go to `chrome://extensions` (or `edge://extensions`), open Tampermonkey's details and turn on **Allow user scripts**. On older versions it's the **Developer mode** switch instead.
3. Open `social-toolkit.user.js` on GitHub, click **Raw**, and Tampermonkey will offer to install it.
4. Reload Facebook, Instagram, TikTok or X.

The first time you download something, Tampermonkey may ask to connect to a CDN domain. Allow it. The script already lists the domains it needs, so you shouldn't get asked again.

## Using it

Move your mouse to the bottom-left corner of the page. A small **G+** button fades in. Click it and you get the panel with the toggles for whatever site you're on.

- **Theme** at the top of the panel is Auto, Light or Dark. Auto follows the site.
- **Pick & hide** lets you click any element on the page and hide it. It's the escape hatch for when a site changes something and a toggle stops working. **Reset** brings everything you picked back.

Where the download buttons end up:

- **Instagram and Facebook stories:** two icons under the "..." button in the story viewer. The first saves the story you're on, the second saves all of that person's stories.
- **Instagram posts:** a download icon right after the paper plane.
- **TikTok:** a Save button above the like button.
- **X:** a download icon at the end of the action row, only on posts that have media.

Files are named `username-date-platform.ext`, like `someone-2026-10-20-instagram.mp4`. When there's more than one file they get `-1`, `-2` and so on.

## Anonymous story view

This works by blocking the request that tells Instagram or Facebook you've seen a story. It's on by default. If you flip it, reload the story page before opening a story, otherwise the old setting is still active.

Don't rely on it for anything where being seen would actually matter. The sites change how they report views and this can stop working without warning.

## Quality

The script picks the biggest file the site hands over. On Instagram and TikTok that's usually up to 1080p. Both sites sometimes keep their best version as separate video and audio streams that need merging, and a userscript can't do that, so in those cases you get the best single file instead.

X photos are saved at original size.

## Things that don't work well

- Facebook stories that are only text on a coloured background have no photo or video behind them, so there's nothing to download. The button tells you that.
- Facebook plays some story videos as a stream, and working out which one you're on takes a few guesses (progress bar, video length, what Facebook says you viewed). If it can't tell, use the "all stories" button. Let the story play for a few seconds first so the data has loaded.
- The Instagram and Facebook selectors look for English button labels. If your interface is in another language, the hide toggles on those two probably won't match.
- Sites rename things constantly. If a toggle stops working, try **Pick & hide** first.

I've mostly tested this on Edge with Tampermonkey. Other browsers should be fine but I haven't spent much time there.

## If something breaks

Open an issue. The most useful thing you can send is the HTML of the broken element: right-click it, choose **Inspect**, then right-click the highlighted line and copy it. Mention the site and what you expected to happen.

## Disclaimer

This is for personal use. Hiding buttons is harmless, but anonymous story viewing and downloading content go against the terms of service of these platforms, and what you download belongs to whoever posted it. Don't re-upload other people's stuff. Use it at your own risk. I'm not affiliated with Meta, TikTok or X.

## License

MIT. Do what you like with it.
