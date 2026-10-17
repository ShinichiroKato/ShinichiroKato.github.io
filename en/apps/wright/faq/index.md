---
layout: default
lang: en
title: Wright FAQ
description: How to use Wright, and what to check when something doesn’t work as expected.
heading: Frequently Asked Questions
---

## Searching

### How do I search?

Type in the search bar, then tap the bookmark for the site or app you want to search. To search with Wright’s Settings > Search URL, tap the search button on the keyboard.

### How do I change the site or browser the keyboard’s search button opens?

In Wright’s Settings > Search URL, choose from Search Sites and Open With, or type a URL yourself. If you choose Default Browser, the browser you chose in the Settings app under Apps > Default Browser App opens. Tap Reset to Default to go back to the original URL.

### Why does searching with nothing typed search for my last search?

When the search bar is empty, your most recent search appears dimmed, and Wright searches for it. To fill it in, tap the search bar while the keyboard is showing.

### How do I hide the keyboard?

Swipe down on the search bar or the suggestions, or scroll your bookmarks.

### How do I move the cursor?

Swipe left or right on the search bar.

## Suggestions and Search History

### What appears in the suggestions?

Your search history, Google suggestions, and calculator results. When there’s text on your clipboard, a paste button also appears. You can turn each one off in Wright’s Settings > Suggestions. Tap a suggestion to put it in the search bar.

### How do I stop sending what I type to Google?

Turn off Google Suggestions in Wright’s Settings > Suggestions. While it’s on, Wright sends what you type even in Private Mode.

### How do I stop saving my search history?

Turn off Search History in Wright’s Settings > Suggestions. To stop saving it only in Private Mode, turn off Save History in Private Mode.

### How do I delete my search history?

To delete a single search, touch and hold a suggestion, then choose Delete. To delete all of it, choose Clear Search History in Wright’s Settings > Reset Wright.

### How do I keep a search at the front of the suggestions?

Touch and hold a suggestion, then choose Pin. Pinned searches always appear first and are never deleted automatically.

### What does “⊕” in a suggestion mean?

It stands for what you typed. For example, if you type “swift,” “swift playgrounds” appears as “⊕ playgrounds.”

### Can Wright do calculations?

Yes. Type an expression like “12*34,” and the answer appears in the suggestions.

## Bookmarks

### How do I add a bookmark?

Tap the “+” button at the top right, then enter a title and URL. When you have no bookmarks, tap Add Common Searches to add Google, YouTube, Wikipedia, and more at once.

### How do I make a bookmark that searches a site I like?

Put `{query}` where the search words go in the URL, for example `https://www.google.com/search?q={query}`. To choose from the keywords you can use, tap the “{}” button next to the URL field.

### Why is Japanese text garbled when I search?

Change `{query}` in the URL to `{query_sjis}` or `{query_eucjp}`. Some older sites expect Japanese text in these formats.

### How do I open a bookmark in an app?

Choose the app in Open With on the bookmark’s edit screen. The URL determines which app opens it.

### How do I rearrange my bookmarks?

Touch and hold a bookmark, then drag it where you want it.

### How do I change the size of my bookmarks?

Pinch your bookmarks, or choose a size in Wright’s Settings > Bookmark Size.

### Can I organize bookmarks into folders?

No. Wright doesn’t have folders or tabs.

### How do I give my bookmarks to another device or person?

In Wright’s Settings, tap Export Bookmarks to save them to a file you can share. To share a single bookmark, touch and hold it, then choose Share. Open the file you receive, or use Import Bookmarks, to add them.

## Private Mode

### What is Private Mode?

A mode that keeps a separate set of search history and bookmarks. Bookmarks and search history in Private Mode are stored only on this device and not synced.

### How do I turn Private Mode on or off?

Go to Wright’s Settings > Private Mode. You can also use the Toggle Private Mode action in the Shortcuts app.

### Can I protect Private Mode with Face ID?

Yes. Turn on Protect with Face ID on the Private Mode screen, and Wright verifies that it’s you when you turn Private Mode on. If you use Touch ID, the setting appears as Protect with Touch ID. If Face ID or Touch ID isn’t available, Wright uses your device passcode instead.

### Why does Private Mode turn off when I leave the app?

To stay in Private Mode, turn off Turn Off When Leaving the App on the Private Mode screen.

## Sync and Data

### What syncs with iCloud?

Your bookmarks and search history sync across your devices signed in to the same Apple Account, using iCloud. Bookmarks and search history in Private Mode, as well as your settings, are not synced. To check the sync status, go to Wright’s Settings > iCloud Sync.

### Why don’t my bookmarks appear after reinstalling Wright or on a new device?

It takes a little while for your bookmarks to come back from iCloud. If you tap Add Common Searches without waiting, those bookmarks appear alongside the ones that come back later, so delete the ones you don’t need.

### Does Wright keep my data from an earlier version?

Yes. The first time you open Wright after updating, it brings over your bookmarks, search history, and settings automatically. If version 2.2 or earlier was the last version you opened, your data can’t be brought over.

### Why do some bookmarks or searches appear twice?

This can happen after iCloud starts syncing, if you updated from an earlier version on two or more devices. In version 3.0.5 and later, bookmarks with the same title and URL are combined into one automatically. Searches with the same text are also combined into one automatically.

### Why does a keyword from an earlier version get searched as text?

Keywords for device information, such as `{device_name}` and `{os_version}`, are no longer available. Rewrite the bookmark’s URL.

### How do I delete all my bookmarks or search history?

Choose an option in Wright’s Settings > Reset Wright. Delete All Bookmarks and Clear Search History delete data in the mode you’re viewing (normal or Private). Erase All Content erases data in both modes. Data in normal mode is deleted from all of your devices using iCloud.

### Can I reset my settings?

There’s no way to reset all settings at once. To reset the search URL, tap Reset to Default in Wright’s Settings > Search URL.

## Using Wright From Outside the App

### Can I use Wright with the Shortcuts app or Siri?

Yes. You can use the Search with Wright, Open Wright, Toggle Private Mode, Scan Code, and Open Bookmark actions.

### Can I use Wright from Control Center?

Yes. You can add the Search with Wright and Scan Code controls. Wright doesn’t have a Home Screen widget.

### Where can I find Wright’s URL schemes?

They’re listed in Wright’s Settings > URL Schemes. You can use them in bookmark URLs or with the Open URLs action in the Shortcuts app.

### Why do I see “Open This Link?”

It appears when a URL opened from another app or web page uses the text in your search bar or on your clipboard. Tap Open only if you’re OK with sending that text to the link.

## Scanning Codes

### How do I scan a QR code or barcode?

When the search bar is empty, tap the button on its right. What Wright reads appears below the camera; tap it to open it. Wright searches for books on Amazon, opens URLs, and puts any other text in the search bar.

### Why can’t I use the camera?

Allow Wright to access the camera in the Settings app.

## Permissions

### What permissions does Wright use?

- **Camera:** Used to scan QR codes and book barcodes.
- **Media & Apple Music:** Used to search with the title of the song that is playing.
- **Biometrics:** Used to protect Private Mode with Face ID or Touch ID.

You can still use the rest of the app without allowing any of these. You can change these permissions at any time in the Settings app.

## Contact

### How do I report a problem?

Use Settings > About Wright > Send Feedback in Wright, or the contact form on the [Support](../support/) page. The developer does not reply to messages.
