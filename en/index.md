---
layout: page
title: Privacy Policy
lang: en
---

*This is a reference translation. The [Japanese version]({{ site.baseurl }}/ja/) is the
authoritative text; if there is any discrepancy between the two, the Japanese version prevails.*

- Effective date: September 12, 2026
- Last updated: October 6, 2026

## 1. Introduction

Streamtheon ("the Extension") is a Chrome extension developed and provided by an individual
developer, chkrym ("we" or "the Developer"). This policy explains what data the Extension
handles, why it handles it, and where that data is stored.

The most important thing to know about the Extension is this:

**We operate no servers. The data the Extension handles is stored locally on your device
(in Chrome's `chrome.storage.local`) and is never transmitted to the Developer or to any
third party.** The Extension contains no analytics, no usage tracking, and no crash
reporting of any kind.

The one exception is the settings you create (your lists, hidden items, notification
settings, and display settings): these may be synced through Chrome's sync feature
(`chrome.storage.sync`) to **your own Google Account**, and carried over to other devices
where you use Chrome with the same account (see §3). This is done by a mechanism built into
Chrome, and even then the Developer never receives your data.

This policy applies only to the Extension as distributed on the Chrome Web Store. External
services you reach from the Extension, such as YouTube, Twitch, and the Google Form used to
send feedback, are governed by their own privacy policies (see §4).

- Developer: chkrym
- Contact: chkrym.dev@gmail.com

## 2. Data We Handle and Why

The table below lists all data the Extension handles. The "Category" column uses the data
categories defined by the Chrome Web Store.

| Data | Category | Source | Purpose | Storage |
| --- | --- | --- | --- | --- |
| Twitch access token | Authentication information | Twitch authorization screen (with your approval) | To query Twitch's API on your behalf for the channels you follow and their live status | On your device only |
| Twitch user ID and login name | Personally identifiable information | Twitch API | To identify whose data to request, and to show the connected account in the settings screen | On your device only |
| A hash of the value that distinguishes the account currently selected on YouTube (converted so that the original value cannot be recovered; the account ID itself is not stored) | Personally identifiable information | youtube.com pages (§5) | To notice when you switch accounts on YouTube, and rebuild the list from the subscriptions of the account you switched to | On your device only |
| Channels you follow on Twitch and their live streams (channel name, icon, stream title, viewer count, category) | Website content | Twitch API | To display the stream list, sort channels into your lists, calculate the live count shown on the Extension's toolbar icon, and show desktop notifications (see below) | On your device only |
| Channels you are subscribed to on YouTube, and live or upcoming streams (channel name, icon, video title, thumbnail, scheduled start time) | Website content | Pages on youtube.com (see §5) | Same as above | On your device only |
| Lists you create, hidden-item settings, notification settings (which channels and lists to notify you about, and which upcoming streams to notify you about when they start), and display settings (theme, sort order, view mode) | — (settings you create within the Extension) | Your own actions | To restore your settings the next time you open the Extension, and, when Chrome sync is on, to carry your settings over to your other devices | On your device; also synced to your Google Account when extensions are included in Chrome sync (see §3) |
| Internal operating state (IDs of videos already seen, timestamps of the last fetch, back-off state when access is rate-limited, the notification baseline (URLs of the live streams seen at the last check), and the settings sync status (such as why the last upload failed)) | — (internal data required to operate) | The Extension itself | To avoid fetching the same information repeatedly and to keep requests to each service to a minimum; to avoid notifying you twice about the same stream; to tell you in the settings screen when syncing is not working | On your device only |

The Extension handles no data beyond what is listed above. In particular, it does not read
your browsing history, your location, anything you type, or the contents of other tabs or
websites.

### Desktop notifications

The Extension can show a desktop notification when a channel you follow or subscribe to
starts streaming.

- Notifications are shown only for the channels and lists you turn on in the settings
  screen, and for upcoming streams you turn on with "Notify for this stream" in the stream
  list. **All notifications are off by default**
- Notifications are displayed through Chrome's and your operating system's notification
  features. Their contents (channel name, stream title, platform name, list name, and the
  channel icon and stream thumbnail images) may remain in your operating system's
  notification center as history; how that history is handled depends on your operating
  system's settings
- The images in a notification are fetched by the Extension from each service's content
  delivery network at the time the notification is shown (see §4). They are only embedded
  in the notification and are not stored

## 3. Where Data Is Stored and for How Long

All data is stored in Chrome's local extension storage (`chrome.storage.local`). This is an
area on your own device, and the Developer has no access to it.

- Stream information and channel lists retrieved from each service are **cached**, and are
  overwritten with fresh content after a period of time
- Your Twitch access token, the lists you create, and your settings are kept until you
  delete them (see §7) or uninstall the Extension

### Syncing settings with Chrome sync

The settings you create are also saved to the storage area used by Chrome's sync feature
(`chrome.storage.sync`). What is and is not synced:

- **Synced**: your lists, hidden items (hidden channels and streams), notification
  settings, and display settings
- **Not synced**: your Twitch access token, your Twitch user ID and login name, the hash
  that distinguishes your YouTube account, the channel
  lists and stream information retrieved from each service, internal operating state, and
  the list currently shown on each device. As before, these are stored only on your device
  (in `chrome.storage.local`)

Whether syncing happens is governed by your Chrome settings. Only if you are signed in to
Chrome and "Extensions" is included in what Chrome syncs are the settings above saved to
your own Google Account and copied to other devices where you use Chrome with the same
account. If sync is off, your settings stay on your device.

- To stop syncing, turn off "Extensions" in Chrome's sync settings
- Data synced to your Google Account is handled according to your Chrome sync settings and
  Google's privacy policy (https://policies.google.com/privacy)

## 4. Data Transmission and Third Parties

**Because the Developer never receives your data, there is nothing for us to sell, share,
or disclose to third parties.** We operate no servers to hold such data, and we use no
processors or subcontractors.

The Extension does, however, communicate directly from your device with the services below
in order to work. These requests are the same in nature as those your browser would make if
you used these services yourself, but each service does receive your IP address and similar
information.

| Destination | Purpose | Authentication |
| --- | --- | --- |
| `api.twitch.tv` | Retrieving the channels you follow and their live status | Uses your Twitch access token |
| `id.twitch.tv` | Twitch authorization; validating and revoking the token | Same as above |
| `www.youtube.com` | Retrieving your subscriptions and their live status (see §5) | Uses your browser's YouTube sign-in state (some requests are unauthenticated) |
| `i.ytimg.com`, `yt3.ggpht.com` | Displaying YouTube video thumbnails and channel icons | None |
| `static-cdn.jtvnw.net` | Displaying Twitch stream thumbnails and channel icons | None |
| `docs.google.com` (feedback form) | Where "Send feedback" in Settings > General takes you | None (only opens when you choose to click it) |

Images are not downloaded and stored by the Extension; they are loaded directly from each
service's content delivery network when they are displayed. As a result, opening the
Extension's window sends your IP address and browser information to those hosts.

In addition, if you have turned on desktop notifications (see §2), each time a notification
is shown the Extension fetches the channel icon and stream thumbnail in the background from
the same content delivery networks and embeds them in the notification (the images are not
stored). **These requests happen even when the Extension's window is not open**, and they
likewise send your IP address and similar information to those hosts. The destinations are
the ones listed in the table above; notifications add no new hosts.

Settings sync (see §3) goes through the sync feature built into Chrome, and synced data is
stored in your own Google Account. It adds no destination that the Extension connects to
directly, and the Developer never receives this data.

Choosing "Send feedback" opens a Google Form we created, in a new tab. This only happens
when you choose to click it; nothing is sent automatically. The form is pre-filled with the
Extension's version and your connection status (whether YouTube is enabled and whether
Twitch is connected), which are values already stored by the Extension — no access tokens,
channel lists, or other data are included. Whatever you enter and submit is stored on
Google's own service and governed by Google's privacy policy.

How these services handle that information is governed by their own privacy policies:

- Google (YouTube, the feedback form, and Chrome sync): https://policies.google.com/privacy
- Twitch: https://www.twitch.tv/p/legal/privacy-notice/

## 5. How We Obtain Information from YouTube

**The Extension does not connect to your Google Account via OAuth. Instead, it relies on
your browser already being signed in to YouTube: it fetches pages from youtube.com and
parses their contents.**

Specifically:

| Requested from | Contents | Authentication |
| --- | --- | --- |
| `youtube.com/feed/channels` | The list of channels you are subscribed to | Uses your browser's cookies (signed-in state) |
| `youtube.com/feed/subscriptions` | Recent uploads from those channels | Uses your browser's cookies (signed-in state) |
| `youtube.com/watch?v=...` and similar | Whether an individual video is live or scheduled | None (your signed-in state is not used) |

The retrieved pages are parsed on your device to extract channel names, video titles,
thumbnails, scheduled start times, and similar details. Neither the page contents nor the
parsed results ever leave your device.

What this approach means in practice:

- The Extension can only reach **what you yourself could see in your browser while signed
  in to YouTube.** It cannot access anything beyond that
- If your Chrome profile is not signed in to YouTube, the Extension cannot retrieve your
  subscriptions, and its YouTube features will not work
- Checks on individual videos are made without using your account

### Why we do not use the official API

The YouTube Data API imposes a daily usage quota per application. For a use case like ours,
where each user's subscriptions must be read individually, that quota is reached as the
number of users grows — and when it is, **every user loses the feature at once.** Using the
official API also requires connecting to your Google Account via OAuth, which would mean
asking you for a broader grant of access.

The approach described above works reliably regardless of how many people use the Extension,
without asking you to connect an additional account. To keep the load on YouTube reasonable,
the Extension keeps an internal record so it does not fetch the same information twice, and
caps the number of requests made in a single update cycle.

Note that this approach does not use an interface YouTube officially provides for this
purpose, so changes on YouTube's side may stop it from working. This is also documented in
the Extension's README.

## 6. Connecting to Twitch

For Twitch, the Extension uses Twitch's official authorization mechanism (OAuth). When you
start the connection from the settings screen, Twitch's authorization page opens, and an
access token is issued only if you approve it.

**The only permission the Extension requests is `user:read:follows` (read the channels you
follow).** This is shown on Twitch's authorization page, so you can verify it yourself.

The Extension does not request any of the following:

- Your email address
- Reading or sending chat messages
- Starting or stopping streams, or changing channel settings
- Acting on your behalf, such as following or unfollowing channels

The access token is stored only on your device and is used for nothing other than querying
Twitch's API. When you disconnect from the settings screen, the Extension **asks Twitch to
revoke the token** before deleting the local copy along with that platform's cached channel
list.

## 7. How to Delete Your Data

You can delete the data stored by the Extension in any of the following ways:

1. **Disconnect a platform** — Disconnecting from "アプリ連携" (Connections) in the settings
   screen deletes that platform's access token and cached channel list. For Twitch, the token
   is also revoked on Twitch's side
2. **Delete all stored data** — The settings screen lets you delete everything the Extension
   has stored, including your lists, hidden-item settings, notification settings, display
   settings, caches, and tokens. Afterwards the Extension returns to the state it was in when
   first installed. This also empties the Chrome sync storage area (see §3), so **the
   settings on your other synced devices are deleted as well**
3. **Uninstall** — Removing the Extension from Chrome causes Chrome to discard everything
   stored in `chrome.storage.local`. Settings synced to your Google Account (see §3) are
   handled by Chrome's sync mechanism. If you want to be sure the synced settings are
   removed, use option 2 above before uninstalling. You can also delete Chrome's sync data
   itself by resetting sync in your Google Account

You can also revoke the connection from Twitch's own settings, under
"Connections" (https://www.twitch.tv/settings/connections).

## 8. Compliance with the Limited Use Policy

The Extension complies with the Chrome Web Store's Limited Use requirements for user data.
We use data only to provide the features disclosed in this policy. Specifically, we do none
of the following:

- Use data for any purpose unrelated to what is disclosed here
- Transfer, sell, or share data with third parties
- Use data for advertising or any form of targeting
- Allow any human, including the Developer, to read the data

As described above, the Extension has no server operated by the Developer, and your data
never comes under the Developer's control (the Google Account used for settings sync is
your own, and the Developer has no access to it). These practices are therefore not merely prohibited by policy — they
**cannot occur by the design of the Extension.**

## 9. Children

The Extension is not directed to children under 13. Using it also requires a YouTube or
Twitch account, and both services set their own age requirements. Please use the Extension
in accordance with each service's terms of service.

## 10. Changes to This Policy

We may revise this policy as the Extension gains features or changes how it works. When we
do, we will update the "Last updated" date on this page and record the change in the
revision history below.

If we make a material change to the categories of data handled, where data is sent, or the
purposes for which it is used, we will also announce it in the Chrome Web Store update notes
and in the repository's README.

## 11. Contact

For questions about this policy or about how the Extension handles data, please get in touch:

- chkrym: chkrym.dev@gmail.com

## Revision History

| Date | Change |
| --- | --- |
| September 12, 2026 | Initial version |
| September 28, 2026 | Added disclosure of the feedback link (Google Forms) as an external destination |
| September 30, 2026 | Added desktop notifications (stored data, image fetching, and how notifications are handled), and settings sync via Chrome sync (where data is stored, transmission, and how to delete it) |
| October 4, 2026 | Added the hash that distinguishes your YouTube account to the stored data, for detecting account switches on YouTube |
| October 5, 2026 | Renamed the Extension from "Oshi Deck" to "Streamtheon" (no change to how data is handled) |
| October 6, 2026 | Added upcoming streams to notify you about to the notification settings, following the addition of per-stream notifications ("Notify for this stream") |
