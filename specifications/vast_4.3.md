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
    - [Loading Verification Resources](#loadingresources)
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
  - [VideoClicks](#videoclicks)
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
  
# General Overview <a name="overview"></a>

VAST is used to send in-stream ad details to a media player. Historically, the player (client)
has received, executed, and tracked streaming video or audio ads. However, with the
increase in player devices, the player is often unable to execute anything more than a single
stream of content. Players might have compensated for this by using one player for content
and loading a secondary player for ad playback. After ad playback, the original player would
be reloaded for resuming content playback. This process caused a brief buffering period
between player loads.

The solution that has emerged for this challenge is a service that involves inserting ads into
a stream of content for the player. The result is a seamless experience for the viewer along
with the ability to select ads dynamically for insertion and more sophisticated tracking
options.

VAST 4.x includes support for high-quality video formats necessary for long-form video
content and server-side tracking for use when ad-stitching is leveraged to reach devices
that cannot use client-side tracking methods. Version 4.x also allows embedding optional
scripts for viewability and ad verification.

## VAST Ad Serving and Tracking <a name="adserving"></a>

Display advertising uses standardized browser technology to request and execute ads.
However, digital in-stream video and audio advertising operates on players, sometimes built
with proprietary code. As a template for ads served to a media player, VAST offers a set of
instructions for developers on how to program their players to process VAST-formatted ads.
Using VAST, ad servers can serve ads to any VAST-compliant player regardless of what
code the player uses.

### Client-Side Ad Serving <a name="clientside"></a>

VAST is a unidirectional means of sending ad details to a media player. Built as a layer on
top of browser technology, the VAST process that uses client-side execution looks
something like this:

1. <b>VAST Request:</b> At some point during content playback, either before (pre-roll), in
the middle of (mid-roll), or after (post-roll), the player reaches a cue to insert an ad
and uses HTTP to send the request for an ad. See section 1.1.1 on sending an ad
request. The request is sent to the primary ad server, which may be the publisher’s
ad server or a supply-side platform (SSP).
2. <b>* Wrapper Response:</b> The primary server responds with VAST. This response is
either an InLine response or a Wrapper response. If the server can fill the ad
request, it sends an InLine response (step 4). In many cases, the ad server redirects
the player to a secondary server using a Wrapper response.
3. <b>Secondary VAST Request:</b> If a Wrapper response is received, the player makes a
secondary request to another server. The secondary response may be an InLine
response or another VAST Wrapper.
4. <b>InLine Response:</b> Eventually, after a series of requests and responses, an ad
server provides an InLine response.
5. <b>InLine Execution:</b> The media player executes the VAST response.
6. <b>Tracking:</b> At key points during ad playback, tracking information is sent for both the
InLine and Wrapper responses that the player received. In traditional client-side ad
serving, cookies are used to track ads and the computers on which they play.

### Server-Side Ad Stitching <a name="serverside"></a>

The example just described the general process for serving an ad directly to a media player,
the client, and uses client-side tracking. With client-side tracking, the player sends tracking
information. However, in today’s wide array of streaming media players the player may not
be capable of executing dynamic ad responses or tracking impressions and interactions. In
these cases, an intermediary server is needed to insert ads dynamically into the video or
audio stream.
Called ad stitching (or stream stitching, ad insertion, etc.), the process looks something like
this:

1. <b>VAST Request:</b> The publisher sends an ad request to the ad-stitching service.
2. <b>Request VAST:</b> The ad-stitching service makes a request to the ad server for a
VAST tag.
3. <b>Send VAST:</b> The ad server sends a VAST tag with a mezzanine file and ready-toserve files. If the ad stitching service has already received the creative for a previous
request and has transcoded the mezzanine file, or the ready-to-serve files are
already in the format required to be stitched into the content stream, then it moves
on to step 5. If the VAST tag response is a Wrapper tag then the ad-stitching
service should extract the inner InLine response using the same precedence logic as
a client-side media player.
4. <b>*Extract Mezzanine and Transcode:</b> The ad-stitching service pulls the unique
creative identifier from the VAST tag. If the creative has never been used in the
system, the mezzanine file is extracted and transcoded. In this scenario, the ad is
skipped and the next available ad is played instead. VAST error code 407 is sent.
5. <b>Select Transcoded:</b> If the creative in the VAST tag from step 3 matches the unique
creative identifier for an ad that has already been transcoded, the ad-stitching
service selects the pre-transcoded file already in the system.
6. <b>Stitch Ad into Content Stream:</b> The ad-stitching service stitches the ad into the
content stream and serves the content and ad to the player in one continuous
stream.
Ad-stitching vendors rely on a unique creative identifier for managing the mezzanine source
file and its cache of transcoded files for stitching into a video or audio stream. If the ad
creative is changed in any way, it should be served with a new creative identifier. In VAST
4.x, the unique creative identifier is provided in the <UniversalAdId> element under
<Creative>. See section 3.7.1 for details.

### Headers in Server-to-Server Ad Requests and Ad Tracking <a name="headers"></a>

With client-side ad tracking described in section 1.1.2, the player (client) sends tracking
included in the VAST tag and uses cookies to determine which computers executed the ad.
However, in server-to-server and server-side ad-stitching, the player may not be able to
process ad tracking, and the ad-stitching service cannot access cookies used in traditional
client-side tracking. Instead, the ad-stitching service must identify devices where ads play
by a combination of other methods.
When an ad-stitching service is involved, the ad-stitching server may send tracking on the
player’s behalf. This server-to-server tracking process is problematic because all the
tracking is coming from one IP address. To an ad server that is receiving tracking
information, the reports look similar to invalid traffic. In addition, the server is initiating the
request on behalf of the client, so it is important to separate information describing the
server itself from information describing the client.

Note - For server-side VAST requests prior to version 4.1, namely VAST 2.0, 3.0 and 4.0,
the immediate goal is to standardize the ad requests and impression calls from the
publisher server (including SSAI platforms) which make the ad request to SSPs, ad
exchanges and DSPs. To this end, the publisher server or the SSAI platform may use
existing HTTP GET tag requests, on condition that they send the following additional HTTP
headers. The goal here is to provide SSAI technology providers the runway to make the
transition to the recommended macros-based request model (Section 1.5) which has
comprehensive support for this use case, while still allowing for adjustments for the
immediate term.
In the future, ad requests will move to a POST based model, which has performance and
scaling implications, so the working group recommends that platforms start working on
understanding architectural changes required to support POST messages at scale.
To avoid being mistaken as fraudulent traffic, ad stitching providers must include with their
ad tracking requests the following HTTP headers:
X-Device-IP set to the IP address of the device on whose behalf this request is being
made.
X-Device-User-Agent set to the User-Agent of the client on whose behalf the
request is being made.
The requester should also include the following headers, if available:
X-Device-Referer set to the Referer header value that the client would have used
when making a request itself.
X-Device-Accept-Language set to the Accept-Language header value that the
client would have used when making a request itself.
X-Device-Requested-With set to the X-Requested-With header value that the client
would have used when making a request itself.
The requester may also include the following headers:
X-Forwarded-For for backwards compatibility, although this is now deprecated.
X-Device-* Other HTTP headers that the client would have sent itself may be
forwarded as well by the requester using the X-Device- prefix.
The information included in these headers must match the information in the original ad
request payload, per section 1.1.1.
While these recommendations for tracking support server-side tracking, IAB Impression
Measurement Guidelines developed with the Media Rating Council (MRC) favor client-side
tracking. "The Measurement Guidelines require ad counting to use a client-initiated
approach; server-initiated ad counting methods (the configuration in which impressions are
counted at the same time the underlying page content is served) are not acceptable for
counting ad impressions because they are the furthest away from the user actually seeing
the ad. Measurement counting may happen at the server side as long as it is initiated based on client-side events and measurement assets. However, pass-through methods (where
client-initiated measurement is passed to server-side collection) of signaling interactions
detected on the client side from server infrastructure are acceptable." Source: MMTF Public
Comment Draft v2 Oct 2017.
In general, an ad-stitching service may have little or no control over ad play once the ad is
stitched into the content and streamed to the client. Impression reporting may vary by
implementation. For the ad stitching service in situations where the client cannot count
impressions, an impression could be reported as the ad is sent on the stitched stream and
therefore be as close as possible to the opportunity to play. Alternately, a session-oriented
ad-stitching service may report impressions from a given session at session completion.
However, any impression measurement beyond the ad-stitched stream is out of the adstitching services’ control and should be counted by the player whenever possible.
Auditing for compliance with IAB Viewable Ad Impression Measurement Guidelines should
focus on disclosing the process by which impressions are counted and any limitations with
reporting impressions in certain situations and environments.
See section 2.3.3 for more information on tracking.

## Ad Verification <a name="adverification"></a>

VPAID, the Video Player-Ad Interface Definition, was originally designed to support
interactive ads that controlled the entirety of creative execution. As this was, at the time, the
only way to execute code at impression time, ad verification services adopted VPAID in
order to run code that verifies and measures playback (including viewability).
An unfortunate side effect of this approach is that, rather than simply enabling monitoring of
player-controlled video playback, responsibility for creative rendering is placed on the
verification service. In many cases, multiple data-collection VPAID "wrappers" may be used,
leading to a fragile chain of intermediaries in the critical path which can significantly delay
page rendering and create a negative experience for the viewer.

### Loading Verification Resources <a name="loadingresources"></a>

In order to support verification with minimal impact to performance, VAST 4 separates
media resources from those intended for measurement.
The <AdVerifications> element provides a place for verification vendors to specify their
executable resources and related metadata, as described in section 3.16. The IAB Tech Lab
strongly recommends using code that supports the Open Measurement Interface Definition
(OMID) for this purpose, and strongly against using VPAID (which is being retired). OMID
has been designed from the ground up to support the needs of verification efficiently, while
providing a level of flexibility and transparency that was unavailable in previous VAST
generations.
See section 3.16 for details.

## Long-Form Video Support <a name="longform"></a>

Long-form video is the extension of traditional broadcast networks to digital mediums. To
enable video advertising across screens that include TV content, the response framework in
VAST needs to reduce the challenges faced in this digital video environment. Specifically,
VAST needs to support the following features:
● Server-to-server ad stitching
● Availability of the high-quality source (mezzanine) file for the ad
● A unique identifier that follows creative and related data from system to system

### High-Quality Video <a name="highquality"></a>

Previous versions of VAST have allowed for multiple media files so that the media player
can poll for the file best suited to the environment where the ad will play. However, the high
standards for quality in long-form video need more than a few options.
VAST 4.x includes a media container for the mezzanine file, which is the raw high-quality
video file that the publisher can use to produce the best quality file where needed. In
addition to the mezzanine file, VAST 4.x requires either an adaptive stream ready-to-serve
file or a minimum of three media files at different levels of quality: high, medium, and low.
Identifying the quality levels of three media files enables the media player to more quickly
find the appropriate file needed for a given environment. A separate document, the IAB
Digital Video Ad Format Guidelines, is provided for ad developers and outlines encoding
recommendations for each of these files.
See section 3.9 for details.
In order to support additional formats such as 3D, augmented reality (AR), virtual reality
(VR), 360-degree video, etc., more than one mezzanine file may be included, with a “type”
attribute to help identify the type of mezzanine file.

### Unique Creative Identification <a name="uniquecreativeID"></a>

As ad creatives move from system to system, they become more difficult to track and
impressions involving these creatives become difficult to reconcile in reports from different
systems. Historically, VAST has provided a placeholder for a creative id, but its purpose has
been unclear and its use varies under different vendors and use cases.
In VAST 4.x, the placeholder for a unique creative ID has been pulled out into a new
element to draw more attention to it and provide attributes that more clearly define the id.
The new <UniversalAdId> element is required for linear ads and consists of an attribute for
defining the idRegistry and the value of the ID specified in the content of the node.

Using a unique creative identifier enables all data associated with the creative to follow
across systems. Unifying data under a unique ID streamlines data collection operations,
reporting, and analysis.
See section 3.7.1 for details.

## Audio Ad Support <a name="audio"></a>   

DAAST, the Digital Audio Ad Serving Template was developed in 2014 as a spin-off of
VAST 3.0 to support Audio ads. DAAST is now being merged back into VAST4, though the
name of the standard will continue to be VAST for the moment.
The main changes are on the VAST “Ad” element (to include an “adType" attribute), some
minor additions (identified below), using the term “media player” instead of “video player”,
and instructions on handling various VAST elements/attributes when in an Audio Ad
scenario.

### Audio Player Use Cases <a name="audioplayer"></a>

Audio players may also support video and display ads but have the additional complexity of
being able to run in the background. This means that there are various modes in which ads
might be used and need to be well understood.
1. Audio only ads
2. Audio ads with Companion Ads
3. Audio ad provided through a video creative, expected to play as audio only mode
4. Video ad trafficked as audio first, but with the potential to be seen for additional
impact.

### "Audibility" / Viewability <a name="audibility"></a>

Discussions are still ongoing about the concept of “Audible Impression”, and will be added
later.

## VAST Ad Requests <a name="adrequests"></a>

VAST is a response protocol. Historically, the request mechanism was not discussed in the
VAST specs, even though the request is important since it contains the information needed
by the ad server to respond with a VAST response. The protocols used for ad requests vary
based on the type of inventory being served.
- For programmatic ad slots, OpenRTB is the standard typically used for ad requests,
and the OpenRTB response could include a VAST response.
- For non-programmatic scenarios, the ad requests are currently not based on any
standard and are proprietary agreements between the publishers and ad servers.
Typically this would consist of an HTTP GET request, with additional data passed in
the URL in the path or in query parameters in a key=value format. This is generally a
mix of platform-specific parameters, as well as information that is commonly required across the industry, such as device IDs, contextual information such as domain or
app ID, or details of the position of the video in video content.
In spite of many ad servers sharing requirements for this common data, passing this
information is extremely difficult, as ad servers often accept these values in different
formats. Additionally they are generally passed along VAST Wrapper chains using ad
server macros which populate at the time a VAST Wrapper document is generated. This
means if data must be passed from ad server A to ad server B to ad server C along a
wrapper chain, traffickers in both A and B must traffic proprietary tags properly and have
values align, otherwise data will be dropped.
Often necessary common data is missing by the time a final ad server is reached, causing
either loss of the opportunity or selection of a suboptimal ad. To mitigate this, some
standardization of request values, settable by the VAST client, is needed.
With VAST 4.1, a first step will be made towards a request protocol in VAST. To ensure
ease of adoption given the current industry setting of proprietary ad tag parameters on
HTTP GET requests, the request protocol will focus entirely on ensuring an agreed-upon
set of values that VAST clients can set, and which all ad servers should accept. Future
versions of VAST will go further, to define a full request protocol based on AdCOM
(reference OpenRTB 3.0) which will define request structure as well as values.
As a further note, this standard will also hold when requests are made for VMAP, as
requests for VMAP often result in VAST documents populated in the VMAP response. As
such, these values are equally needed at VMAP request time.
To allow VAST clients to set values in ad tags, the VAST macro concept will be expanded
to apply not just to tracking URIs, but to AdTagURIs in Wrapper creatives, as well as to
initial ad tags URIs passed to a VAST client for the ad initial request.
The list of macros (for both VAST Ad Requests as well as for tracking) has been
consolidated in Section 6.

## VAST Interactive Templates <a name="interactive"></a> 
## Flash Support <a name="flash"></a> 
## Handling MediaFile Nodes During the Transition from VPAID <a name="mediafile"></a> 
# VAST Compliance <a name="compliance"></a> 
## Ad Server Expectations <a name="adserver"></a> 
## Media Player Expectations <a name="mediaplayer"></a> 
## General Compliance <a name="generalcompliance"></a> 
### VAST Ad Types <a name="adtypes"></a> 
### XML Structure <a name="xml"></a> 
### Encoding URIs for VAST <a name="encodinguris"></a> 
### Tracking <a name="tracking"></a> 
### VAST Wrappers <a name="wrappers"></a> 
### Error Reporting <a name="errorreporting"></a> 
### Industry Icon Support <a name="industryicon"></a> 
## Viewability Verification and Interactive Linear Creative <a name="viewability"></a>
### Publisher Viewability <a name="publisherviewability"></a> 
### Viewability with Ad Verification Services <a name="adverificationservices"></a> 
### Interactive Linear Creative Files <a name="interactivelinear"></a> 
# VAST Implementation <a name="implementation"></a>    
## Declaring the VAST Response <a name="response"></a> 
## VAST <a name="spec"></a> 
### Error (VAST) <a name="error"></a>
## Ad <a name="ad"></a>
### Ad Pods and Stand-Alone Ads <a name="adpods"></a>
### The Ad Element <a name="adelement"></a>
## InLine <a name="inline"></a>
### AdSystem <a name="adsystem"></a>
### AdTitle <a name="adtitle"></a>
### AdServingId <a name="adservingid"></a>
### Impression <a name="impression"></a>
### Category <a name="category"></a>
### Description <a name="description"></a>
### Advertiser <a name="advertiser"></a>
### Pricing <a name="pricing"></a>
### Survey <a name="survey"></a>
### Expires <a name="expires"></a>
### Error (InLine and Wrapper) <a name="errorinline"></a>
## ViewableImpression <a name="viewableimpression"></a>
### Viewable <a name="viewable"></a>
### NotViewable <a name="notviewable"></a>
### ViewUndetermined <a name="viewundetermined"></a>
## Creatives <a name="creatives"></a>
## Creative <a name="creative"></a>
### UniversalAdId <a name="universaladid"></a>
### CreativeExtensions <a name="creativeextensions"></a>
### CreativeExtension <a name="creativeextension"></a>
## Linear <a name="linear"></a>
### Duration <a name="duration"></a>
### AdParameters <a name="adparameters"></a>
## MediaFiles <a name="mediafiles"></a>
### MediaFile <a name="mediafile"></a>
### Mezzanine <a name="mezzanine"></a>
### InteractiveCreativeFile <a name="interactivecreativefile"></a>
### ClosedCaptionFiles <a name="closedcaptionfiles"></a>
### ClosedCaptionFile <a name="closedcaptionfile"></a>
## VideoClicks <a name="videoclicks"></a>
### ClickThrough <a name="clickthrough"></a>
### ClickTracking <a name="clicktracking"></a>
### CustomClick <a name="customclick"></a>
## Icons <a name="icons"></a>
### Icon <a name="icon"></a>
### IconViewTracking <a name="iconviewtracking"></a>
### IconClicks <a name="iconclicks"></a>
### IconClickThrough <a name="iconclickthrough"></a>
### IconClickTracking <a name="iconclicktracking"></a>
### IconClickFallbackImages <a name="iconclickfallbackimages"></a>
#### IconClickFallbackImage <a name="iconclickfallbackimage"></a>
### NonLinearAds <a name="nonlinearads"></a>
#### NonLinear <a name="nonlinear"></a>
#### NonLinearClickThrough <a name="nonlinearclickthrough"></a>
#### NonLinearClickTracking <a name="nonlinearclicktracking"></a>
### CompanionAds <a name="companionads"></a>
#### Companion <a name="companion"></a>
#### AltText <a name="alttext"></a>
#### CompanionClickThrough <a name="companionclickthrough"></a>
#### CompanionClickTracking <a name="companionclicktracking"></a>
### Tracking Event Elements <a name="trackingeventelements"></a>
#### Tracking Event Descriptions <a name="trackingeventdesc"></a>
#### TrackingEvents <a name="trackingevents"></a>
#### Tracking <a name="tracking"></a>
### Creative Resource Files for Non-Video and Non-Audio Creative <a name="nonaudiononvideo"></a>
#### StaticResource <a name="staticresource"></a>
#### IFrameResource <a name="iframeresource"></a>
#### HTMLResource <a name="htmlresource"></a>
### AdVerifications <a name="adverifications"></a>
### Verification <a name="verification"></a>
#### JavaScript Resource <a name="javascriptresource"></a>
#### ExecutableResource <a name="executableresource"></a>
#### TrackingEvents <a name="trackingevents"></a>
#### Tracking <a name="tracking"></a>
#### VerificationParameters <a name="verificationparameters"></a>
### Extensions <a name="extensions"></a>
#### Extension <a name="extension"></a>
### Wrapper <a name="wrapper"></a>
#### VASTAdTagURI <a name="adtaguri"></a>
#### BlockedAdCategories <a name="blockedadcategories"></a>
# Migration to VAST 4.x <a name="migration"></a>
## Advertisers and Ad Technology Vendors <a name="advertisersandvendors"></a>
## Ad Servers and Networks <a name="adserversandnetworks"></a>
## Media Players <a name="mediaplayers"></a>
# Human Readable VAST XML Schema <a name="humanreadableschema"></a> 
# Macros <a name="macros"></a>
## Introduction <a name="intro"></a>
## List of Macros <a name="list"></a>
