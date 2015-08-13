---
layout: post
title: Browser Detection
categories: how-tos
summary: Record information about your visitors' web browsers as Kissmetrics properties.
---
* Table of Contents
{:toc}
* * *

One of the more popular (yet optional) things to track is the web browser that your visitors are using when visiting your site. This information is readily available through a little use of JavaScript; you can parse `navigator.userAgent` and `navigator.appVersion`, among other variables. This [QuirksMode.org][1] article is a great reference and resource that you can use to fetch users' browser information.

If you choose to use their BrowserDetect plugin, you could then pass along the appropriate values to Kissmetrics as a property, perhaps like this:

{% highlight html %}
<script type="text/javascript">
_kmq.push(['set', {'Browser' : BrowserDetect.browser + " " +
  BrowserDetect.version }]);
</script>
{% endhighlight %}

For me, this would currently set the property "Browser" with the value "Chrome 15".

If you're familiar with this, then you can apply the same principles to filter out bot or spider traffic, or even detect the visitor's operating system.

## Mobile vs. Non-mobile

An extension of checking `navigator.userAgent` is to detect whether your visitors are on a mobile device or not. For example:

{% highlight js %}
var isMobile = function() {
    return (navigator.userAgent.match(/Android/i) ||
            navigator.userAgent.match(/BlackBerry/i) ||
            navigator.userAgent.match(/iPhone|iPod/i) ||
            navigator.userAgent.match(/iPad/i) ||
            navigator.userAgent.match(/Opera Mini/i) ||
            navigator.userAgent.match(/IEMobile/i) );
};

if (isMobile()) _kmq.push(['set', {'Mobile Session' : 'Yes' }]);
{% endhighlight %}

## Screen Resolution

Designers may be interested in knowing the screen resolution in which visitors are viewing their sites. This can inform them to optimize the site for the popular resolutions. The data is available in the JavaScript variables `screen.width` and `screen.height`:

{% highlight html %}
<script type="text/javascript">
_kmq.push(['set', {'Screen Resolution' : screen.width + " x " +
  screen.height }]);
</script>
{% endhighlight %}

[1]: http://www.quirksmode.org/js/detect.html
