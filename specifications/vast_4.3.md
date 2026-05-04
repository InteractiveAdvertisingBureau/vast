![](https://drive.google.com/uc?id=1MStOYYaZDqrvuOwlmecX0iayL0Jt_eAN)

# VAST 4.3

**December 2022**

**About the IAB Technology Lab**

The IAB Technology Laboratory is a nonprofit research and development consortium charged
with producing and helping companies implement global industry technical standards and
solutions. The goal of the Tech Lab is to reduce friction associated with the digital advertising
and marketing supply chain while contributing to the safe growth of an industry.
The IAB Tech Lab spearheads the development of technical standards, creates and maintains a
code library to assist in rapid, cost-effective implementation of IAB standards, and establishes a
test platform for companies to evaluate the compatibility of their technology solutions with IAB
standards, which for 18 years have been the foundation for interoperability and profitable growth
in the digital advertising supply chain.

Learn more about IAB Tech Lab at [www.iabtechlab.com](https://www.iabtechlab.com).

**License**

VAST Specification the IAB Tech Lab is licensed under a Creative Commons Attribution 3.0 License. To view a copy of this license, visit[ creativecommons.org/licenses/by/3.0/](http://creativecommons.org/licenses/by/3.0/) or write to Creative Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA.

![](https://drive.google.com/uc?id=1cbwEGlb8S69SndIDoHnvc5_3TfmkGM7R)

**TABLE OF CONTENTS**

- [Executive Summary](#execsummary)
  - [VAST 4.0 Updates](#vast40)
  - [VAST 4.1 Updates](#vast41)
  - [VAST 4.2 Updates](#vast42)
  - [VAST 4.3 Updates](#vast43)
- [Intended Audience](#audience)
- [Resources for Digital In-Stream Video and Audio](#resources)
- [General Overview](#overview)
  - [VAST Ad Serving and Tracking](#adserving)
    - [Client-Side Ad Serving](#clientside)
    - [Server-Side Ad Stitching](#serverside)
    - [Headers in Server-to-Server Ad Requests and Ad Tracking](#headers)
  - [Ad Verification](#verification)
  - [Long-Form Video Support](#longform)
    - [High-Quality Video](#highquality)
    - [Unique Creative Identification](#uniquecreativeID)
  - [Audio Ad Support](#audio)
    - [Audio Player Use Cases](#audioplayer)
    - ["Audibility" / Viewability](#audibility)
  - [VAST Ad Requests](#adrequests)
  - [VAST Interactive Templates](#interactive)
  - [Flash Support](#flash)
  - [Handling MediaFile Nodes During the Transition from VPAID](#mediafile)
- [VAST Compliance](#compliance)
  - [Ad Server Expectations](#adserver)
  - [Media Player Expectations](#mediaplayer)
  - [General Compliance](#generalcompliance)
    - [VAST Ad Types](#adtypes)
    - [XML Structure](#xml)
    - [Encoding URIs for VAST](#encodinguris)
    - [Tracking](#tracking)
    - [VAST Wrappers](#wrappers)
    - [Error Reporting](#errorreporting)
    - [Industry Icon Support](#industryicon)
  - [Viewability Verification and Interactive Linear Creative](#viewability)
    - [Publisher Viewability](#publisherviewability)
    - [Viewability with Ad Verification Services](#adverificationservices)
    - [Interactive Linear Creative Files](#interactivelinear)
- [VAST Implementation](#implementation)
  - [Declaring the VAST Response](#response)
  - [VAST](#spec)
    - [Error (VAST)](#error)
  - [Ad](#ad) 
    - [Ad Pods and Stand-Alone Ads](#adpods)
    - [The Ad Element](#adelement)
  - [InLine](#inline)  
    - [AdSystem](#adsystem)
    - [AdTitle](#adtitle)
    - [AdServingId](#adservingid)
    - [Impression](#impression)
    - [Category](#category)
    - [Description](#description)
    - [Advertiser](#advertiser)
    - [Pricing](#pricing)
    - [Survey](#survey)
    - [Expires](#expires)
    - [Error (InLine and Wrapper)](#errorinline)
  - [ViewableImpression](#viewableimpression)  
    - [Viewable](#viewable)
    - [NotViewable](#notviewable)
    - [ViewUndetermined](#viewundetermined)
  - [Creatives](#creatives)
  - [Creative](#creative) 
    - [UniversalAdId](#universaladid)
    - [CreativeExtensions](#creativeextensions)
    - [CreativeExtension](#creativeextension)
  - [Linear](#linear) 
    - [Duration](#duration)
    - [AdParameters](#adparameters)
  - [MediaFiles](#mediafiles)
    - [MediaFile](#mediafile)
    - [Mezzanine](#mezzanine)
    - [InteractiveCreativeFile](#interactivecreativefile)
    - [ClosedCaptionFiles](#closedcaptionfiles)
    - [ClosedCaptionFile](#closedcaptionfile) 
  - [VideoClicks](#mediafiles)
    - [ClickThrough](#clickthrough)
    - [ClickTracking](#clicktracking)
    - [CustomClick](#customclick)
  - [Icons](#icons)
    - [Icon](#icon)
    - [IconViewTracking](#iconviewtracking)
    - [IconClicks](#iconclicks)
    - [IconClickThrough](#iconclickthrough)
    - [IconClickTracking](#iconclicktracking)
    - [IconClickFallbackImages](#iconclickfallbackimages)
      - [IconClickFallbackImage](#iconclickfallbackimage)  
  - [NonLinearAds](#nonlinearads)
    - [NonLinear](#nonlinear)
    - [NonLinearClickThrough](#nonlinearclickthrough)
    - [NonLinearClickTracking](#nonlinearclicktracking)
  - [CompanionAds](#companionads)
    - [Companion](#companion)
    - [AltText](#alttext)
    - [CompanionClickThrough](#companionclickthrough)
    - [CompanionClickTracking](#companionclicktracking)
  - [Tracking Event Elements](#trackingeventelements)
    - [Tracking Event Descriptions](#trackingeventdesc)
    - [TrackingEvents](#trackingevents)
    - [Tracking](#tracking)
  - [Creative Resource Files for Non-Video and Non-Audio Creative](#nonaudiononvideo)
    - [StaticResource](#staticresource)
    - [IFrameResource](#iframeresource)
    - [HTMLResource](#htmlresource)
  - [AdVerifications](#adverifications)
  - [Verification](#verification)
    - [JavaScript Resource](#javascriptresource)
    - [ExecutableResource](#executableresource)
    - [TrackingEvents](#trackingevents)
    - [Tracking](#tracking)
    - [VerificationParameters](#verificationparameters)
  - [Extensions](#extensions) 
    - [Extension](#extension)
  - [Wrapper](#wrapper) 
    - [VASTAdTagURI](#adtaguri)
    - [BlockedAdCategories](#blockedadcategories)
- [Migration to VAST 4.x](#migration)
  - [Advertisers and Ad Technology Vendors](#advertisersandvendors)
  - [Ad Servers and Networks](#adserversandnetworks)
  - [Media Players](#mediaplayers)
- [Human Readable VAST XML Schema](#humanreadableschema)
- [Macros](#macros)
  - [Introduction](#intro)
  - [List of Macros](#list)
 

# Executive Summary <a name="execsummary"></a>

The Video Ad Serving Template or VAST is a template for structuring ad tags that serve
video and audio ads to media players. Using an XML schema, VAST transfers important
metadata about an ad from the ad server to a media player. Initially launched in 2008,
VAST has since played an important role in the growth of the digital video and audio
marketplace.

The early days of video consisted mostly of shared videos and other user-generated
content. Success in monetizing this content with ads has produced the resources to
improve the digital video marketplace. However, digital video has met a number of
challenges along the way.

One challenge, and a key reason some video publishers avoid using VAST, is a lack of
quality control. Along with the IAB Video Player-Ad Interface Definition (VPAID), VAST can
deliver ads programmatically or include ads with complex interactions. If a player isn't
programmed to accept VPAID ads, the ad cannot be executed. Even when the player does
accept VPAID ads, performance may be slow and cause latency in load times. In the
meantime, the audience experiences a delay or a malfunction in their viewing experience.

Publishers and ad vendors need a way to separate the video file from its interactive
components to ensure that ads play in systems that cannot execute the interactive
components. These ads should also execute more efficiently in players that are equipped to
handle the interactions.

Another challenge, especially for broadcasters who are moving their content online, is the
lack of a consistent identifier for creative that is maintained across systems. VAST offers a
creative identifier, but it has been used inconsistently and one creative may use different
identifiers for every system it passes through. A system-wide identifier is a requirement for
broadcasters trying to maintain control over the ads they play.

VAST 4 has addressed these challenges along with a few others. As players begin to adopt
the updates in VAST 4.x, digital video and audio can expect to see smoother operation and
the continued growth that results.

## VAST 4.0 Updates <a name="vast40"></a>

The updates made in VAST 4.0 and the challenges they address are summarized here:

- <b>Separate Video File and Interactive File:</b> The complexity of digital video has given
rise to the need to separate the linear video file from any creative interactive API
files. While the VAST media file has accepted a variety of media files in the past,
interactive APIs cannot always be executed. A VAST tag that provides the video file
separate from APIs can display more successfully across platforms and devices.
The Interactive File standard is expected to be Secure Interactive Media Interface
Definition (SIMID) - which is a replacement for VPAID focused on interactivity.

- <b>Server-Side Ad Insertion Support:</b> While client-side ad execution and tracking has
been the recommended way to track ad impressions and other metrics, digital instream video and audio ads are often served to devices (clients) that cannot execute and track ads using traditional display methods. VAST 4 supports the increasingly common “ad-stitching” method for stitching linear ads into a video or audio content stream and sending it to players with limited capabilities.

- <b>Mezzanine File:</b> To support advertising across video platforms that include longform content and high-resolution screens, VAST 4 features include support for the
raw, high-quality mezzanine file. The mezzanine file is very large and cannot be
used for ad display, but ad-stitching services and other ad vendor use it to generate
files at appropriate quality levels for the environment in which they play.

- <b>Ready-to-Serve Files:</b> Along with support for including the mezzanine file, VAST 4
provides guidance on providing three ready-to-serve media files, each at different
quality levels, to ensure that a linear video/audio ad can always play. The IAB Digital
Video Ad Format Guidelines offers guidance on video/audio file specifications for
linear ads.

- <b>Universal Ad ID:</b> While VAST has offered a creative identifier in the past, it has
been used inconsistently. The new Universal Ad ID feature is used specifically for
including a creative identifier that is maintained across systems. The existing adId
attribute for creative can still be used to log creative IDs specific to the server.

- <b>Ad Verification and Viewability Execution:</b> Verification vendors have been using
VPAID for measurement verification instead of using it for ad interaction as VPAID
was intended. VAST 4 offers a designated space (<AdVerifications>) for inserting
ad verification APIs, enabling a more streamlined process for executing files strictly
intended for ad verification. Open Measurement (OM) is expected to be used for this
purpose. In addition, a secondary impression element, the <ViewableImpression>
element, has been added to allow publishers the option to track viewability on their
inventory.

- <b>Support for Categories:</b> Ad categories help publishers separate competing ad
creative and improve brand safety. VAST 4 ad categories support these efforts.

- <b>Conditional Ad Declaration:</b> In programmatic environments, a VPAID unit is
sometimes used to decide whether or not to place an ad. If this “conditional ad”
never results in an ad to display, the publisher may have to forfeit any revenue from
the resulting lost inventory. A declaration in VAST for a conditional ad helps
publishers prevent and reclaim any potentially lost inventory revenue in
programmatic ad delivery. Note - VPAID & this element are being deprecated as of
VAST 4.1 since VPAID is being replaced by SIMID (Secure Interactive Media
Interface Definition) and OMID (Open Measurement Interface Definition.

- <b>New Error Codes:</b> Along with support for the mezzanine file and other new features,
added error codes provide additional troubleshooting support.

- <b>Standardized Timestamp:</b> Trackers used in VAST often include timestamp macros,
but its use has not been consistent. In VAST 4, the [TIMESTAMP] macro and the
format for time has been standardized to enable more consistent time-sensitive
tracking.

## VAST 4.1 Updates <a name="vast41"></a>

The updates made in VAST 4.1 are summarized here:

- <b>Verification:</b> Changes that enable verification to be supported in a non-VPAID
architecture (separated from media file). Also includes changes required to work with
Open Measurement.

- <b>Digital Audio Ad Serving Template (DAAST):</b> With VAST 4.1, DAAST has been
merged into VAST. This mostly involves providing direction in places where audio
ads might need to be treated differently. The main change is an optional “adType”
added to the “Ad” element to support the various audio use cases.

- <b>Ad Requests:</b> VAST is a response protocol. 4.1 now includes a basic Ad Request
specification, based on macros.

- <b>Updates to Macros:</b> With the new Ad Requests proposal, the Macros section has
been completely revamped and updated.

- <b>Server Side Ad Insertion (SSAI) related changes:</b> VAST 4.1 includes minor
changes to how headers should be handled. The “Ad Request” section is also
relevant to SSAI use cases.

- <b>Deprecating Video Player Ad-Serving Interface Definition (VPAID):</b> While VPAID
will likely be in use for some more time, with VAST 4.1 we are taking the first steps
to officially deprecate the use of VPAID. The apiFramework attribute on MediaFile,
and the conditionalAd attribute on the Ad element are being deprecated.

- <b>Updates to Tracking Events:</b> Added “loaded”, “closeLinear” (back from VAST 3.0).
Removed acceptInvitationLinear and timeSpentViewing.

- <b>AdServingId:</b> A required field has been added to simplify comparing data about a
video impression across the various systems involved with the delivery and tracking
of the impression.

- <b>VAST Interactive Templates:</b> Recognizing the need for standardizing interactive
ads without ad delivered executable code, VAST 4.1 introduces the concept of
interactive templates, with End-Cards as an example template.

- <b>Closed Captioning:</b> VAST 4.1 enables Closed Captioning by standardizing the
delivery of Closed Captioning files.

- <b>Flash:</b> Following up on the white paper to transition video ads from flash to HTML5
(https://iabtechlab.com/html5videotransition/) with VAST 4.1, all references to Flash
and Flash resources are being removed.

- <b>Survey:</b> The survey node is being deprecated as of VAST 4.1.

- <b>Other Updates:</b>
  - MediaFile fixes - fixes to UniversalAdId, added support for more types, changed bounding of Mezzanine files, added support for fileSize etc.
  - Added id attribute to "Advertisers" element
  - Added "Expires" element
  - Added variableDuration to InteractiveCreativeFile

<b>Note:</b> based on feedback received during public comment, the group decided not to
deprecate nonlinear ads in VAST 4.1. However, we will continue to explore this format
further to determine if the use cases are better handled with other options.

## VAST 4.2 Updates <a name="vast42"></a>

The updates included in VAST 4.2 are summarized here:
  - Support for Secure Interactive Media Interface Definition (SIMID). SIMID is the
replacement for VPAID to support interactive use cases. More information available
at this blog post by the IAB Tech Lab. This includes a new tracking event and an
error code 902.
  - Allow ClickThrough element to be specified in a wrapper to better enable the use
case defined in 2.3.5 (managing assets with an ad cloud)
  - Added error code 206 to support use cases where the player might decide not to
play an ad (for example during live broadcasts where the break needed to be
shortened at the last moment).
  - Allow multiple UniversalAdID nodes to be provided
  - Updates to Icon and Icon ClickFallbackImages
  - New macros for better adbreak info.

## VAST 4.3 Updates <a name="vast43"></a>

The updates included in VAST 4.3 are summarized here:
  - Macros moved to Github for management independent of VAST updates (Section
6.2)
  - Macro value added for [PLAYBACKMETHODS] to indicate continuous play, where
content episodes are being played back to back without any user interaction. A
value of 7 indicates “continuous play”
  - For interactive creative files, an inline data URI may be included such as when you
want to place HTML directly instead of a URL for retrieving the file. (section 3.9.3)

# Intended Audience <a name="audience"></a>

This document was designed for digital video and audio technologists who either develop
players that accept digital in-stream ads or for vendors who develop ads to be sent to digital
in-stream players.
For engineers, section 3 defines all the VAST XML elements. Section 5 includes a “humanreadable” schema for quick reference with links to more details in the document if needed.
Section 2 defines VAST compliance and section 4 provides technical tips for migrating to
VAST 4.x.
For executives, the executive summary and section 1 provide high-level explanation of how
VAST can be used to streamline digital video or audio ad operations.

# Resources for Digital In-Stream Video and Audio <a name="resources"></a>

In order to improve the interconnectivity of the digital video and audio marketplaces, the IAB
has published technical specifications, metric definitions, and best practices developed by
members with industry experience. Descriptions for each of these publications are listed
below.
  - <b>VAST:</b> The Video Ad Serving Template is an XML response framework that enables
a consistent delivery format for ad across streaming video and audio platforms.
  - <b>VPAID:</b> The Video Player-Ad Interface Definition specifies the protocol between the
ad and the media player required to enable ad interactivity and other advanced video
advertising functionality. Deprecated - VPAID is being phased out, to be replaced by
OMID (for Verification) and SIMID for interactivity.(http://bit.ly/videoAdVision)
  - <b>SIMID:</b> The Secure Interactive Media Interface Definition, the API made available to
build an interactive experience with the video ad media. A replacement for VPAID for
interactivity in the VAST 4 model of separated media & executable files.
  - <b>OMID:</b> The Open Measurement Interface Definition, the API made available to
verification code by OMSDK or equivalent service. A replacement for VPAID for
verification in the VAST 4 model of separated media & executable files.
  - <b>VMAP:</b> The Video Multi-Ad Playlist is an XML response framework that defines
where to place ads within the video content.
  - <b>Digital Video Ad Metric Definitions:</b> An industry-defined list of metrics used in
digital video ads.
a consistent delivery format for ad across streaming video and audio platforms.
  - <b>Digital Video Ad Format Guidelines:</b> An industry-defined list of streaming video
creative submission specifications. https://iabtechlab.com/standards/iab-digitalvideo-in-stream-ad-format-guidelines/ 
a consistent delivery format for ad across streaming video and audio platforms.
  - <b>Digital Advertising Alliance (DAA) Interest-Based Advertising (IBA) Notice for Digital Video:</b> Guidelines for implementing the AdChoices program within in-stream
ads that are placed using interest-based criteria.
   - <b>Open Measurement SDK (OM SDK):</b> An IAB-led project developing a common
library to collect and expose measurements of ad creatives, including video, at view
time, for verification purposes.
  
