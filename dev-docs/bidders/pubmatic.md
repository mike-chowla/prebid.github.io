---
layout: bidder
title: PubMatic
description: Prebid PubMatic Bidder Adaptor

top_nav_section: dev_docs
nav_section: reference

hide: true

biddercode: pubmatic

biddercode_longer_than_12: false

---

### Prebid Server Note:
Before configuring the PubMatic adapter as S2S, you must reach out to the PubMatic team for approval and setup steps.

### bid params

{: .table .table-bordered .table-striped }
| Name | Scope | Description | Example |
| :--- | :---- | :---------- | :------ |
| `publisherId` | required | Publisher ID | "32572" |
| `adSlot` | required | Ad Unit ID | "38519891@300x250" |
| `pmzoneid` | optional | Zone ID | "zone1,zone2" |
| `lat` | optional | Latitude | "40.712775" |
| `lon` | optional | Longitude | "-74.005973" |
| `yob` | optional | Year of Birth | "1982" |
| `gender` | optional | Gender | "M" |
| `kadpageurl` | optional | Overrides Page URL | "http://www.yahoo.com/" |
| `kadfloor` | optional | Bid Floor | "1.75" |

### Configuration

PubMatic recommends the UserSync configuration below.  Without it, the PubMatic adapter will not able to perform user syncs, which lowers match and reduces monetization.

```javascript
$$PREBID_GLOBAL$$.setConfig({
   userSync: {
    iframeEnabled: true,
    enabledBidders: ['pubmatic'],
    syncDelay: 6000
 }});
```
Note: Combine the above the configuration with any other UserSync configuration.  Multiple setConfig() overwrite each other and only last call for a given attribute will take effect.
