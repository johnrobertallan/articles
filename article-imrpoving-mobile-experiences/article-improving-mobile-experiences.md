# Improving mobile experiences: OilSandsToday.ca

In my previous insight post [Light-responsive: Improving mobile experiences without breaking the bank](http://habaneroconsulting.com/insights/improving-mobile-experiences-without-breaking-the-bank) I described Habanero's 'light-responsive' approach and how it can be used to improve engagement and the user experience delivered on mobile devices. 

In this post, I'll examine how we applied these ideas to a specific client and what problems they helped us solve. 

## The client's problem: a high bounce rate

The Canadian Association of Petroleum Producers' (CAPP) site [oilsandstoday.ca](http://www.oilsandstoday.com), built on the SharePoint platform, worked well on a typical computer screen but had serious problems relaying information to its mobile users.

CAPP struggled to keep mobile users on the site; in fact, analytics indicated most left one second after landing on the homepage. It did not take long to discover there were two major issues affecting OilSandsToday.ca: visual design and performance.

## The first user problem: visual design.

As with many websites designed for large screens, oilsandstoday.ca was difficult to use on a hand-held device. 

When the page loaded it appeared in a zoomed out view. You could see the overall structure of the page but both the navigation and content were illegibly small. Before you could do anything useful, you had to zoom in and as you moved through the page you were forced to constantly scroll, pan and zoom in and out resulting in a disjointed and difficult reading experience.

These are exactly the issues our light-responsive approach addresses. 

After a meeting with the client to describe our approach we moved on to the design phase and began to examine how we could transform their existing layout for mobile visitors.

A mock-up tackled the two most common mobile design issues: page layout and navigation. 

To start, the page was collapsed down to a single column. This created enough space for properly sized text and easy-to-read line lengths. 

The secondary content, which normally appeared on the right, was moved below the main content.

The page header was cleaned up and elements such as the utility navigation and social icons (Facebook, Twitter, YouTube etc.) were moved to the footer while the logo remained in the top left. 

Finally all our navigation elements were compressed and hidden inside a 'menu' button represented by an image showing a stack of items, the commonly seen 'hamburger' icon.

[visual]

One major visual element you will notice is missing on a mobile device is the banner. In the desktop view each page has a large image at the top to introduce the content. During the design phase the client and our team agreed that for mobile devices, at least for the mean time, this could be removed. This would maintain the existing authoring experience and save CAPP from having to produce mobile versions of each banner. 

The above changes were achieved by adding just a few lines of JavaScript and some new CSS rules, all of which live inside a media query, meaning they only affect mobile screens. By doing this, we ensured the desktop version would remain the same and quality assurance testing would be kept to a minimum.

[visual with link]

## The second user problem: performance.

Aside from the layout issues, the site took a long time to load on a mobile device. In our tests the first page could take anywhere from 7 to 30 seconds to appear! That is a far cry from the common industry target of 1 second or less. These slow load times were probably the biggest reason people left the site so quickly. 

If a page doesn't load right away it feels broken and most users will abandon ship. In our experience and as seen in outside research, people have very little patience for slow websites—especially when using a mobile device.[1]

Unfortunately, performance problems are not as easy to solve as layout issues. There are many factors that can cause websites to run slowly, but after some analysis we identified two key culprits holding back oilsandstoday.ca: oversized banner images and unneeded resources.

To start, the banner images were not compressed properly, which meant file sizes were much bigger than they needed to be—even for a desktop view. Based on our recommendations, the client was able to fix this problem themselves, improving load times across the board.  

However, as we'd decided not to show the banner at all on mobile devices we didn't want just an improved file size; we wanted no file at all. Our new CSS hid the banner but that didn't stop the browser from downloading it. While it may be hidden initially as far as the browser knows it could be slated for an appearance at any time so it is still retrieved.

For various reasons each page also requested about 20 other CSS and JavaScript resources which were not required for our mobile view. Most of these files were quite small but for each one the browser has to send a new request to the server. All these requests add up, and the more there are, the larger affect they have on load times.[2]

## Solving our performance issues.

To solve these problems, we used a tool called [MobifyJS](http://www.mobify.com/mobifyjs/). MobifyJS enabled us to capture and manipulate the page on-the-fly before any of our problematic extra resources were downloaded. 

If you aren't familiar with the ins and outs web development you've probably never heard of the Document Object Model (DOM) but you can think of it as a table-of-contents and our web page as the book. Unfortunately, in our case the DOM lists a bunch of 'chapters' or resources that we don't need.

With CSS we can hide resources but this is the equivalent of whiting out the extra chapters. You can't see the words but the book is just as heavy. With MobifyJS we can rip those pages right out and give the browser a much lighter volume thereby reducing load times and bandwidth requirements.

[results graphic]

The result of all our changes is a new average load time of 1 second or less per page, a huge improvement over the 7-30 second times seen before!

If we were rebuilding the oilsandstoday.ca site from scratch, these problems could be solved with a new technical architecture. However, this project was not a rebuild and in keeping with the light-responsive approach, we only wanted to layer additions on top of what already existed. That is why MobifyJS was the perfect tool for us.

## Conclusion 

In many ways oilsandstoday.ca was a typical website in that when it was designed, there were few considerations for mobile users. With a relatively small budget and a limited time line, we managed to significantly improve the mobile user experience. 

Instead of the frustration caused by slow pages and challenging pinch'n'zoom interactions, users are now able to quickly and easily explore all of the site's content on a much broader range of devices.

## References

1. For some interesting statistics take a look at this article [Americans don't have time for slow websites](http://mashable.com/2012/03/14/slow-website-stats-infographic/).

2. For an in depth look at how requests and other issues affect performance check out this talk, [Six bottles of RUM](http://www.youtube.com/watch?v=GtebW-K2D-8) by Peter McLachlan of Mobify.

___________________________________



## Results

If those last few paragraphs were a bit too technical fear not. Here are some numbers which should make the outcome clear:

### 40 -> 20

We talked about reducing server requests. On average that number was dropped from 40 to 20 a 50% decrease. 

### 1.6MB -> 0.1MB

The total average page size was also dropped from a whopping 1.6MB to 0.1MB, a 94% decrease. 

### 7+ -> <1 seconds



## Sustainment 

Because we embarked on this work with limited resources there are still improvements to be made: 

- There is still room to increase performance. 
- Visually it would be nice to bring the banners back to the mobile view if it can be done without significantly impacting the performance gains or the authoring experience. 
- Navigation could still be improved to ease movement between different areas of the site and the deeper pages.
- We could update and improve the scripts and styles to support broader set of devices.
- We could fix minor visual issues which have appeared post-release due to new content.

Managing any site is an ongoing task but this is especially true in the case of mobile support where the landscape is constantly changing. It is important to ensure that the improvements continue to deliver an enhanced experience to mobile users and do not fall out of sync in any way with the desktop experience or users expectations.
