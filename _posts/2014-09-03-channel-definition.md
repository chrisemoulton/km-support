---
layout: post
categories: tools
title: "Channel Definitions"
tags: []
summary: Channels is a Kissmetrics property that combines acquisition data from many sources.
---
* Table of Contents
{:toc}
* * *

Channels are your sources of traffic. The Channels property in Kissmetrics automatically reads incoming traffic data and organizes it into three different Kissmetrics Channel properties so you can analyze your acquisition data without any extra work. The three Channel properties are:

* `Channel` - what traffic source out of Direct/Organic/Referral/Email/Paid/Social
* `Channel: Origin` - traffic source + original referring URL/domain or Campaign Name
* `Origin` - referring URL/domain or Campaign Name

## Channel definitions

* `Direct` - Visits from direct referrers, typing your site into the browser, or bookmarks
* `Organic` - Visits from search engines
* `Referral` - Visits from 3rd party
* `Email` - Visits from emails
* `Paid` - Visits from Paid sources such as cpc, cpm, display, ppc, and more (details below)
* `Social` - Visits from social networks/sites

## How we calculate Channel

### 1. Google Campaign Medium UTMs

Before categorizing on any other criteria, the first thing Kissmetrics looks for is a [Google Campaign Medium UTM variable][Google UTM] on the referral URL (utm_medium). Here’s how we group different values into channels:

* `Paid` = utm_medium of "cpc", "cpm", "display", "cpv", "cpa", "cpp", or "ppc"
* `Email` = utm_medium of "email" or "e-mail"
* `Organic` = utm_medium of "organic" or "search"
* `Social` = utm_medium of “social", "social-network", "social-media", "sm", "social network", or "social media"

Any other values will be under their own channel.

When you drill down into Channel:Origin for these visitors, people will be also categorized under the Campaign Name UTM that was also defined at the same time. For example, a utm_medium of "email" with utm_campaign of "spring_promo" would read as a "Channel:Origin" property of "Email: Spring Promo.""

If the Campaign Name UTM is missing (usually shouldn't be as it's required along with Campaign Source and Campaign Medium), they will be labeled be as “Campaign Name Unknown”.


### 2. AdWords gclid parameter

If a campaign medium UTM parameter isn’t detected, the next thing Kissmetrics looks for is a [Google Adwords gclid parameter][Google gclid] on the referral URL.

Traffic with a gclid parameter is placed in the Paid channel and under AdWords in the Origin drilldown.

Google AdWords uses a gclid parameter when you set up auto-tagging in your Google AdWords account. The auto-tagging feature of Google AdWords is for the Google Analytics integration, but Kissmetrics and other analytics providers cannot read that parameter. Google restricts access to read the gclid parameter. We won't know which AdWords campaign/keyword was used but we do know that the traffic is from Google AdWords at least. Basically, any traffic with a gclid parameter will be added to an AdWords Origin within the Paid channel.

By putting AdWords after Campaign Medium UTM, the UTM acts as an override. Since we can’t get AdWords campaign values because Google blocks access to information like Campaign Name, Campaign Source, etc, we recommend that you add UTM variables to AdWords links even if you have Google AdWords auto-tagging/gclid enabled. So if you've added UTM parameters, we’ll use that data. If not, we’ll group them under the Paid channel as a generic AdWords Origin.

### 3. Organic

If the visit came from a search engine, people will be placed in the “Organic” channel. When you drill down into the Origin of the channel, you will see the search engine that drove the visit.

### 4. Social

We have a list of 276 social domains and subdomains including major social networks such as Facebook, Twitter, LinkedIn, Pinterest, Reddit, Quora, Tumblr, and more.

If the top-level domain of the referring URL matches one of these, peopel will be grouped into the Social channel. When you drill-down in the Social channel, you should be able to see the actual social network that drove the visit.

If you see a referring domain that should be grouped into the Social channel, please email feedback@kissmetrics.com and we'll add it to our list of domains to be considered for the Social channel.

### 5. Referral

This group will contain the top-level domains of any traffic that doesn't fit into any other category. When you drill-down into this channel Origin, you get a list of the referring domains.

### 6. Direct

Any people that have a site visit with a direct referrer. This will not have an Origin.

### 7. Unknown

If a visit doesn’t any of the above rules, we’ll place them into the Unknown channel. If you see traffic organized into Unknown, it may be from data that you imported from a database or CSV upload. This data usually doesn't contain acquisition/visit data unless you include it in the upload.

[Google UTM]: https://support.google.com/analytics/answer/1033863?hl=en&ref_topic=1032998
[Google gclid]: https://support.google.com/analytics/answer/1033981?hl=en
