---
layout: bidder
title: PubMatic
description: Prebid PubMatic Bidder Adaptor
top_nav_section: dev_docs
nav_section: reference
hide: true
biddercode: pubmatic
biddercode_longer_than_12: false
prebid_1_0_supported : true
gdpr_supported: true
media_types: video
---

### Prebid Server Note:
Before configuring the PubMatic adapter as S2S, you must reach out to the PubMatic team for approval and setup steps.

### Prebid 1.0 Upgrade Note:
If you upgrading from a Prebid version prior to 1.0, please reach out to your PubMatic Customer Success Manager prior to your upgrade.  Publisher accounts need new settings to function correctly with the PubMatic Prebid 1.0 adapter and your Customer Success Manager will ensure your account is setup correctly.

### bid params

{: .table .table-bordered .table-striped }
| Name | Scope | Description | Example |
| :--- | :---- | :---------- | :------ |
| `publisherId` | required | Publisher ID | `"32572"` |
| `adSlot` | required | Ad Unit ID | `"38519891@300x250"` |
| `pmzoneid` | optional | Zone ID | `"zone1,zone2"` |
| `lat` | optional | Latitude | `"40.712775"` |
| `lon` | optional | Longitude | `"-74.005973"` |
| `yob` | optional | Year of Birth | `"1982"` |
| `gender` | optional | Gender | `"M"` |
| `kadpageurl` | optional | Overrides Page URL | `"http://www.yahoo.com/"` |
| `kadfloor` | optional | Bid Floor | `"1.75"` |

### video parameters

The PubMatic adapter supports video as of Prebid 1.17.0

{: .table .table-bordered .table-striped }
| Name | Scope | Description | Example |
| :--- | :---- | :---------- | :------ |
| `mimes` | required | Video MIME types | `['video/mp4','video/x-flv']` |
| `skippable` | optional | If 'true', user can skip ad | `true` |
| `minduration` | optional | Minimum ad duration in seconds| `5` |
| `maxduration` | optional | Maximum ad duration in seconds | `30` |
| `startdelay` | optional | Start delay in seconds for pre-roll, mid-roll, or post-roll ad placements | `5` |
| `playbackmethod` | optional | Defines whether inventory is user-initiated or autoplay sound on/off<br/>Values:<br/>`1`: Auto-play, sound on<br/>`2`: Auto-play, sound off<br/>`3`: Click-to-play<br/>`4`: mouse-over| `1` |
| `api` | optional | API frameworks supported<br/>Values:<br/>`1`: VPAID 1.0<br/>`2`: VPAID 2.0<br/>`3`: MRAID-1<br/>`4`: ORMMA<br/>`5`: MRAID-2 | [1, 2] |
| `protocols` | optional |  Supported video bid response protocols<br/>Values<br/>`1`: VAST 1.0<br/>`2`: VAST 2.0<br/>`3`: VAST 3.0<br/> `4`: VAST 1.0 Wrapper<br/>`5`: VAST 2.0 Wrapper<br/>`6`: VAST 3.0 Wrapper| `[5, 6]` |
| `w` | optional | Video player width in pixels | `640` |
| `h` | optional | Video play height in pixels | `480` |
| `battr` | optional | Blocked creative attributes, See [OpenRTB 2.5 specification](https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf), List 5.3 for values | `[3, 9]` |
| `linearity` | optional | Indicates if the impression is linear or nonlinear<br/>Values:<br/>`1`: Linear/In-Stream<br/>`2`: Non-Linear/Overlay. | `1` |
| `placement` | optional | Video placement type.  See [OpenRTB 2.5 specification](https://www.iab.com/wp-content/uploads/2016/03/OpenRTB-API-Specification-Version-2-5-FINAL.pdf), List 5.9 for values| `1` |

### Configuration

PubMatic recommends the UserSync configuration below.  Without it, the PubMatic adapter will not able to perform user syncs, which lowers match rate and reduces monetization.

```javascript
pbjs.setConfig({
   userSync: {
    iframeEnabled: true,
    enabledBidders: ['pubmatic'],
    syncDelay: 6000
 }});
```
Note: Combine the above the configuration with any other UserSync configuration.  Multiple setConfig() calls overwrite each other and only last call for a given attribute will take effect.
