---

copyright:
  years: 2018, 2019
lastupdated: "2020-07-06"

keywords: Use Page Rules, standard cache levels, Custom Caching Sets

subcollection: cis

---

{{site.data.keyword.attribute-definition-list}}

# Using page rules with caching
{: #use-page-rules-with-caching}

Page rules give you the ability to take various actions based on the page's URL, such as creating redirects, fine-tuning caching behavior, or enabling and disabling services.
{: shortdesc}

A page rule takes effect on a given URL pattern that matches the following format:

`<scheme>://<hostname><:port>/<path>`

For example:

`https://www.example.com:80/image.png`

The `scheme` and `port` components are optional. If the `scheme` component is omitted, the format accepts `http://` and `https://` protocols. If the `port` is not specified, the rule matches all ports. You can perform basic wildcard matches by using a `*` symbol in your rule pattern, allowing it to match a series of similar patterns.

**Important things to remember with page rules:**

* Only one page rule takes effect on any given request.
* Page rules are given priority in an order from top to bottom. After a URL matches a rule, only that rule is applied; that is, if a page rule has triggered already on a request, any subsequent rules that also match the URL pattern do not take effect.
* As a general rule, it is recommended to order from most-specific to least-specific rules.
* Page rules can be disabled, in which case they take no action. However, you can still see the rules in the list and edit them. Setting the **Enabled** toggle to **Off** creates a page rule that is disabled initially.

## Forwarding (URL redirection)
{: #forwarding-url-redirection}

Redirect one URL to another using an HTTP 301 or 302 redirect. The contents of any section of a URL that a wildcard matches can be referenced using `$X` syntax. The `X` indicates the index of a glob in the pattern: `$1` is replaced with the first wildcard match,  `$2` with the second wildcard match, and so on.

For example, suppose you set the following rule:

![image](images/url-redirection-example.png "Image describing forwarding rule"){: caption="Figure 1. Forwarding rule" caption-side="bottom}

Here, a request to `www.example.com/stuff/things` is redirected to `http://example.com/stuff/things`.

Be careful not to create a redirect in which the domain points to itself as a destination. This mistake can cause an infinite redirect error, and the affected URLs do not resolve.
{: note}

## Redirecting to HTTPS
{: #redirecting-to-https}

If you want to redirect your visitors to use HTTPS, use the **Always Use HTTPS** setting instead:

![image2](images/url-matching-patterns.png "Image describing Always Use HTTPS rule"){: caption="Figure 2. Always Use HTTPS" caption-side="bottom}

## Setting custom caching
{: #custom-caching}

Set caching behavior for any URL matching the page rule pattern, using any of our standard cache levels. Setting **Cache Level** to **Cache Everything** caches any content, even if it is not one of our default static file types. Setting **Cache Level** to the **Bypass** setting prevents caching on that URL.

When specifying cache level using page rules, you can set an **Edge Cache TTL**, which controls how long CIS retains files in the cache.

**Browser Cache TTL** controls how long resources cached by client browsers remain valid. If a browser requests a resource again and the TTL has not expired, the browser receives an `HTTP 304 (Not Modified)` response. You can set TTLs ranging from 30 minutes to 1 year.

Not all default caching behaviors are strictly RFC-compliant. Setting **Origin Cache Control** by means of page rules uses a newer set of caching rules that seeks to adhere more closely to RFCs, primarily with respect to revalidation. For example, our default behavior with `max-age=0` is to not cache at all, whereas setting **Origin Cache Control** caches, but it always revalidates.

The following example sets a page rule to cache everything found in the `/images` folder. Cached resources expire in 30 minutes in the user's browser, and they expire after one day in the IBM CIS data centers:

![image3](images/url-example.png "Image describing caching images folder"){: caption="Figure 3. Cache everything in /images" caption-side="bottom}

**Serve Stale Content** serves pages from our cache, even when your server goes down. Visitors see a limited version of your site, with a message that they are in offline browsing mode.

This feature returns an HTTP status 503. When servers are online again, CIS seamlessly takes visitors to regular browsing.

If the requested page is not in the cache, the visitor sees an error page that informs them the page they are requesting is offline. If a **Cache Everything** page rule is enabled with expiration times set lower than the caching frequency, the **Serve Stale Content** is purged in the corresponding interval.
{: note}
