---
name: klipstr
description: Run clipping with Klipstr - find trending videos, clip links into short vertical clips, trim and post them, check results. Use when the person mentions Klipstr, klipping or clipping.
---

# Clipping with Klipstr

Klipstr turns long videos into short vertical clips with captions, and posts them to the
person's own connected accounts. You run the work from this chat with the Klipstr tools. The
person can watch and change anything on the Clipping page in the app at any time; you are the
operator, the page is where they watch and override.

The tools come from the Run My Ads connector. The person signs in with their account the first
time a tool is used. If you see `load_toolset` but no clipping tools, call
`load_toolset` with toolset `clipping`, then continue in a new chat.

## The tools
- `list_trending_videos`: what is worth clipping now. Lists: `klip` (long videos and streams
  to clip), `viral` (short clips taking off), `creators` (who is winning), `followed`.
  Filter by niche and platform.
- `start_clipping`: clip a pasted link, or a Trending item by its `trending_key`.
- `list_clips`: every clipped video and its status; with a `source_ref`, its finished clips.
- `change_clip`: move a clip's start or end one sentence earlier or later, or bring back a
  removed clip.
- `remove_clip`: take a clip out of the set.
- `post_clips`: post now or schedule clips to the person's connected accounts.
- `update_followed_creators`: follow or unfollow YouTube channels and Twitch streamers.
- `get_clip_results`: how posted clips did.

## Rules you must follow
1. **The rights question is the person's to answer.** When `start_clipping` on a Trending
   item returns a question, ask the person that exact question and wait. Only their own yes
   counts. Never answer it for them, never assume it, and never carry a yes from one video to
   another. A link the person pasted themselves has no question. If the tool says clipping a
   Trending pick is not available from chat, send the person to Klip this on the Clipping page.
2. **Preview before posting.** Call `post_clips` without `confirm` first, show the person what
   goes where and when, and post with `confirm: true` and the preview's `confirm_token` only
   after they say yes to that preview. If anything changes, preview again.
3. **Warnings are the person's call.** If posting returns a warning (for example the same clip
   was already posted to that account), tell them in your own words. Send `post_anyway: true`
   only if they say to.
4. **Say what is true.** If a job is still running, say so and check again later. If a
   platform does not report results yet, say that. If no account is connected, give them the
   connect link the tool returns.
5. **Files are uploaded in the app.** A video file cannot come through this chat. Send the
   person to the Clipping page to upload it.

## First use
Ask once what they clip: streams, gaming, sports and fights, podcasts and interviews, comedy,
or other. Pass it as `niche` when you start a clip; it sets the clip length, layout and
caption look.

## The daily routine
1. `list_clips`: what is running and what is ready.
2. `list_trending_videos` for their niche: suggest up to three to clip, with views and age,
   and pass on the rights notice the tool returns.
3. `start_clipping` for each one they pick (relay the rights question for Trending items).
4. When ready, `list_clips` with the `source_ref`: show each clip's headline, length, why it
   was picked and whether it passed its checks (with the reason if not), with the watch link.
   Offer to move a start or end by one sentence, or remove a clip.
5. `post_clips`: preview, then post or schedule after their yes.
6. Next day: `get_clip_results`, then say which clips did best and suggest more like them.

"Clip this and post it" is one request, but it still holds the person's own answers: their
rights answer for a Trending pick, then their yes to the post preview. An earlier "post it"
is neither. Never show the person refs or keys; they are for tool calls only.

## What a good clip looks like
You cannot change layout, titles, caption look or effects from chat; the only changes are
moving a clip's start or end by one sentence, removing a clip, or bringing it back. Use this
to choose which videos to clip and which clips to post, not to promise edits.
- A clip is a person people follow plus the thing they are doing or reacting to. Trailers,
  promos and footage with nobody in it are not clips.
- Short wins: most good clips are 30 seconds or less. Streams 8-45 s; fight edits and
  facecam gameplay up to 60 s; comedy and podcast answers can run to 60 s. Over 80 s rarely
  works.
- Text on screen in the first second: the first spoken words as a caption, or a title.
- End on the reaction, punchline or outcome. No end card, no "follow for more".
- Streams and gaming: the creator's face and the gameplay stacked, or a fixed title over
  the clip. Name the creator in the title.
- Sports and fights: the best moments show faces, then the action, the finish and the
  celebration.
- Podcasts: tight on the speaker, the first words as a caption from the start, end on the
  closing line.
- Within one account the moment matters more than the edit. Pick the strongest moment first.
