---
layout: default
lang: en
title: Yomu FAQ
description: How to use Yomu, and what to check when something doesn’t work as expected.
heading: Frequently Asked Questions
---

## Subscribing to Feeds

### How do I subscribe to a feed?

Tap + in the sidebar, choose Add Feed, and enter the URL of a website’s home page or of a feed. If you enter a website’s URL, Yomu looks for the site’s feed and subscribes to it. If it finds more than one feed, compare their latest articles and choose the one you want. If you’re not sure, choose Recommended.

You can also subscribe from a site you have open in your browser. Choose Yomu in the share menu, and the same screen opens with the URL already entered.

### Why can’t I subscribe?

Check the following.

- The site must serve its feed over https. Feeds available only over http can’t be added.
- If you see “No feed found on this page.”, the site may not offer a feed. If you know the feed’s URL, enter that instead.

### How do I move from another RSS reader?

Export an OPML file from your other RSS reader, then choose Import OPML in Yomu’s Settings > Import & Export OPML. Feeds you already subscribe to aren’t duplicated, and folders with the same name are merged.

You can’t import until the first sync from iCloud finishes, because importing before then can duplicate your feeds.

### My feeds aren’t updating.

Pull down on the article list, or use the Refresh button. These always fetch every feed, including ones that keep failing. To see why a feed failed, check Last Error in its Feed Info.

During automatic updates, feeds that keep failing are fetched less often. The interval grows with each failure, up to one day, and goes back to normal once the feed is fetched successfully.

## Reading Articles

### The article shows only the excerpt from the feed, not the full text.

Yomu couldn’t extract the text from the article’s page, or couldn’t fetch it because you’re offline. When you’re back online, tap Reload Article, or read the article with Open Original Page. Yomu doesn’t automatically retry an article it couldn’t extract for one hour.

If a feed includes the full text, set Content Source to Feed Content in the feed’s Feed Info > Article Settings to show the text from the feed without opening the article’s page. To change it for all feeds, choose it in Yomu’s Settings > Articles > Content Source.

### The article text looks broken.

Let us know with Report an Issue in the article’s … menu. The contact form opens with the article’s URL already filled in. Report an Issue appears when Yomu extracts the text from the article’s page (when Content Source is Full Text).

### Can I read articles offline?

Article titles and excerpts in the article list are available offline. Article text and images aren’t saved on your device, so they aren’t available offline.

### Articles take longer to load after I reopen the app.

Yomu keeps article text, images, translations, and summaries only while you’re using the app, and doesn’t save them on your device. After you quit the app, Yomu fetches the text again and creates translations and summaries again when you open an article.

## Translation and Summaries

### Why isn’t an article translated?

Check the following.

- Articles already in your device’s preferred language aren’t translated.
- Translation in Yomu’s Settings > Articles shouldn’t be Off. Translation of titles in the article list is set separately in Settings > List > Translation.
- The language must be downloaded for translation. If it isn’t, Yomu shows a message; follow it to download the language. Yomu never downloads languages automatically.
- If you see “Translation isn’t available for this language.”, that language can’t be translated.

### How do I change the language articles are translated into?

Yomu translates into your device’s preferred language. There’s no setting in Yomu to choose a different language.

### Why isn’t a summary created?

Summaries are created with Apple Intelligence. They can’t be created on devices that don’t support Apple Intelligence, when Apple Intelligence is turned off, or while its model isn’t ready yet. Follow the message that appears.

Short articles aren’t summarized. To summarize articles automatically when you open them, turn on Yomu’s Settings > Articles > Auto-Summarize Articles.

### Is article content sent anywhere?

No. Extracting article text, translating, and summarizing all happen on your device. When you open an article, Yomu fetches the article’s page and images from the site that publishes them.

## The Article List and Read Status

### Some articles disappeared.

Read articles are deleted automatically once the number of days in Keep Read Articles (30 Days by default) has passed since you read them. Unread articles are kept for one year, and starred articles are never deleted. Star any article you want to keep.

### Some articles don’t appear in the list.

Articles don’t appear in the article list in these cases.

- They match one of your Muted Words. They’re marked as read when they’re loaded and don’t appear in the list or in search results, whatever filter you use. Starred articles still appear.
- They’re in a locked folder. Even while the folder is unlocked, its articles don’t appear in All or in smart folders. Open the folder to read them.

### Can I search the full text of articles?

No. Search looks at article titles, feed excerpts, and translated titles.

## Notifications and Badges

### I don’t get notifications for new articles.

Notifications for new articles are turned on per feed. Turn on New Article Notifications in the feed’s Feed Info, and allow notifications. This setting is saved per device, so turn it on on each device where you want notifications. When an update finishes, Yomu sends one notification for each feed that has new articles, showing the feed name and a representative article title. Tapping it opens that feed.

Notifications arrive when Yomu updates your feeds, not as soon as a site publishes an article. When you aren’t using Yomu, the system decides when updates happen, so notifications may be delayed.

### The app icon doesn’t show the number of unread articles.

Turn on App Icon Badge in Yomu’s Settings, and allow notifications. Articles in locked folders and articles that match your Muted Words aren’t counted.

## Sync and Data

### Can I sync with my other devices?

Yes. Your subscriptions, folders, smart folders, muted words, and the read and starred status of articles sync across your devices signed in to the same Apple Account, using iCloud. You don’t need to create an account.

Article text, translations, and summaries don’t sync. Of the settings, only Keep Read Articles syncs. Other settings and whether notifications for new articles are on are stored only on this device and not synced.

### I unsubscribed from a feed, and it disappeared from my other devices too.

Unsubscribing, deleting a folder, and Delete All Feeds apply to all of your devices using iCloud, and starred articles are deleted too. If you might want to subscribe to the same feeds again later, export an OPML file first.

### How do I keep a folder private?

In the sidebar, touch and hold or Control-click the folder, then choose Lock Folder. A locked folder doesn’t show its contents until you authenticate with Face ID, Touch ID, Optic ID, or your passcode or password. It locks again when you leave Yomu.

## Contact

### How do I report a problem?

Use Settings > About Yomu > Send Feedback in Yomu, or the contact form on the [Support](../support/) page. The developer does not reply to messages.
