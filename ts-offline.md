---

copyright:
  years: 2021
lastupdated: "2021-02-05"

keywords: 

subcollection: cis

---

{{site.data.keyword.attribute-definition-list}}

# Why is my website offline?
{: #troubleshooting-cis-website-offline}

Here is what you might see: `IBM CIS cannot connect to the origin server (error 521, 522, 523)`.

**Website offline - no cached version**
{: tsSymptoms}


1. The server is online, but it is blocking the {{site.data.keyword.cis_short_notm}} request.
2. The origin server is offline and {{site.data.keyword.cis_short_notm}}S does not have a backup website image
{: tsCauses}


* Verify that the {{site.data.keyword.cis_short_notm}} IP addresses are allowlisted.
* Make sure that {{site.data.keyword.cis_short_notm}} IPs are not being rate-limited.
* Review the list of [IPs to allowlist](/docs/cis?topic=cis-cis-allowlisted-ip-addresses).
{: tsResolve}
