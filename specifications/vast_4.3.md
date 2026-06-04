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

While interactive video ads command a premium, they are not supported on all platforms or
by all publishers. While this is partly due to concerns around VPAID, which are being
addressed by VAST4 and the replacement for VPAID, the execution of unknown code may
never be allowed in many cases. To address this, VAST 4.1 introduces the concept of
“VAST Interactive Templates”. These are interactive experiences that only require some
visual assets (images, css, etc.) and some instructions/metadata in the VAST tag. The
publisher implements the interactive code and uses the metadata to run the interactive ad.

In VAST 4.1 we have included an “end-card” (Section 3.13) based on a use case that has
already been informally implemented in the industry. We expect to add more such
templates in the future.

Note - The IAB Tech Lab recommends the use of VAST extensions for the industry to
experiment with such experiences, and then bring in proposals to the Digital Video
Technical Working Group to formalize them as standard templates.


## Flash Support <a name="flash"></a> 

As indicated in the Flash to HTML5 transition guidance released by the IAB Tech Lab in
December 2016, all Flash references are considered deprecated as of January 2017.
VAST4 is now officially being updated to reflect that position by removing all Flash related
references.

## Handling MediaFile Nodes During the Transition from VPAID <a name="mediafile"></a> 

One of the goals of VAST4 is to eliminate the practice of using the MediaFile node to deliver
executable code (usually VPAID). To achieve this goal, the AdVerifications Node and the
InteractiveCreativeFile were added in VAST 4, so that executable code for measurement
and for interactivity could be delivered separately from the MediaFile. VPAID is being
replaced by OMID for verification/measurement and SIMID for interactivity. (Refer to
http://bit.ly/videoAdVision for more information).

However, adoption of new protocols require time and so there will be a transition period
where VPAID remains in use. With VAST 4.1, the working group has also deprecated the
“apiFramework” attribute on the MediaFile node, which enables the delivery of VPAID.
During the transition period, VAST 4.2 tags will likely have both the AdVerifications node for
Open Measurement, alongside a VPAID MediaFile element.

This section provides recommendations for both publishers and tag creators to help during
this transition period.

<b>For VAST tag creators (both direct as well as wrapped tags):</b>

VAST tag creators should plan to deliver the relevant VAST content based on information in
the ad requests (OpenRTB and via VAST ad request macros - refer section 1.5 and 5). Use
the APIFRAMEWORKS macro.

1. When OMID support is indicated in the request, include the AdVerifications node (or
extensions node with type AdVerifications for pre VAST 4.1) to include verification
scripts.
2. If VPAID support is indicated in the request and the tag creator requires VPAID
support (for interactivity or ad blocking), include the following in the VAST tag
a. The AdVerifications node (or extensions node with type AdVerifications for
pre VAST 4.1)
b. The VPAID file type MediaFile node (for Blocking or Interactivity)
3. If OMID/VPAID support status is not known and there is no hard requirement on
VPAID use from the buyer, ensure that the VAST tag contains all 3 of the following
so that the publisher has all resources available:
a. The AdVerifications node (or extensions node with type AdVerifications for
pre VAST 4.1)
b. The VPAID file type MediaFile node (for Blocking or Interactivity)
c. One or more non-VPAID (video creative) MediaFile nodes.

<b>For Publishers</b>

For best results, send information in the ad request (OpenRTB and VAST ad request
macros) about capabilities of the video player. Use the APIFRAMEWORKS macro.
Based on the standards supported, execute in this order for best results

1. If OMID is supported, run the AdVerifications node (for Open Measurement) - and
the video creative MediaFile
2. If OMID is not supported but VPAID is supported and VPAID MediaFile node is
available in VAST tag, run VPAID
3. If OMID and VPAID are supported, run both AdVerifications node and VPAID
4. If OMID and VPAID not supported, run one of the non-VPAID MediaFile nodes.

The above is only a recommendation and might not work in all cases. Publishers can decide
to run any MediaFile they deem appropriate for their use cases, so as always, please
ensure that your integrations are working as expected and per your business agreements.

Also, publishers and technology vendors are responsible for testing the various
combinations above and ensure that potential issues like double counting or namespace
clashes are correctly handled.

Once Open Measurement supports Brand Safety and once the interactivity replacement for
VPAID is defined (and is delivered via the InteractiveCreative Node) the use of “VPAIDMediaFile” will be eliminated.

# VAST Compliance <a name="compliance"></a> 

Compliance is a two-party effort that involves, at a minimum, the media player and the ad
server. Both must meet certain expectations so that VAST can be truly interoperable and
encourage growth in the marketplace.

General Implementation Note: Open Measurement, VPAID and VMAP specs are excluded from VAST compliance
because these specs are independent of each other and of VAST. Compliance with one
spec does not imply compliance with any of the other specs. Compliance for either spec
must be separately declared

## Ad Server Expectations <a name="adserver"></a> 

VAST-compliant ad servers must be able to serve ad responses that conform to the VAST
XML schema defined in this document. Ad servers must also be able to receive the
subsequent tracking and error requests that result from the media player’s execution of the
VAST ad response. Tables for each VAST XML element define which are required in a
VAST response.

## Media Player Expectations <a name="mediaplayer"></a> 

VAST-compliant media players and SSAI systems must be able to play the ad in a VAST
response according to the instructions provided by the VAST ad response and according
the media player’s declared format support, which includes:
● Rendering the ad asset(s) correctly
● Respecting ad server instructions in a VAST response including those of any
subsequent ad servers called in a chain of VAST Wrapper responses, providing the
responses are VAST-compliant
● Responding to supported user-interactions
● Sending appropriate tracking information back to the ad server
● Supporting XML conventions such as standard comment syntax (i.e. acknowledge
VAST comments in the standard XML syntax: <!--comment-->)
Details for proper ad display and VAST support are defined throughout this document,
including player support requirement notes for each XML element.

## General Compliance <a name="generalcompliance"></a> 

VAST specifies both the format of the ad response and how the media player should handle
the response. In order for VAST to be effective, both ad servers and media players must
adopt the guidelines outlined in this document.
In general, the video player need only accept ads that it requests and ad server responses
should be displayed in the ad format intended.
For example, VAST allows for compliance while only supporting a subset of ad types
(described in section 2.3.1). For example, if a standard Linear Ad is requested but a
Skippable Linear Ad is received, the media player is not expected to display the Skippable
Linear Ad nor should the media player play the Skippable Ad as a Linear Ad (without skip
controls).

The following features must be supported for general functionality:
● Declaration of ad types
● XML structure
● Tracking
● Wrappers
● Error reporting
● Macros
● Industry icons
● Verification
These features are described in the following sections.

### VAST Ad Types <a name="adtypes"></a> 

VAST covers several distinct ad types, but ad serving and publisher organizations may not
want to support all formats. For example, some vendors may choose to serve only linear
ads with companions.
VAST 3.0 introduced five ad types for compliance so that organizations may be compliant
with VAST while only supporting a selected subset of the ad types.
The VAST- compliant ad types are as follows:
1. Linear Ads
2. NonLinear Ads
3. Companion Ads
4. Skippable Linear Ads
5. Ad Pods
A company wishing to display IAB’s seal for VAST compliance must declare which of the
five ad types their technology supports.
Note – all ad types are relevant for “audio only” ads except NonLinear ads.

### XML Structure <a name="xml"></a> 

A VAST-compliant ad response is a well-formed XML document, compliant with XML 1.0 so
that standard XML requirements such as character entities and <!--XML comments-->
should be honored. It must also pass a schema check against the VAST 4.x XML Schema
Definition (XSD) that is distributed in conjunction with this document.
IAB Tech Lab Github URL for the XSD: https://github.com/InteractiveAdvertisingBureau/vast

Ad Server Implementation Note: All URIs or any other free text fields containing potentially dangerous characters
contained in the VAST document should be wrapped in CDATA blocks. The VAST
response should be carefully tested for appropriate treatment of URI characters that
require special handling.

### Encoding URIs for VAST <a name="encodinguris"></a> 

URIs provided in a VAST response must be CDATA-wrapped as in the following example:
<Impression id="myserver">
<![CDATA[
http://ad.server.com/impression/dot.gif
]]>
</Impression>
Wrapping the URI in a CDATA section enables most characters to be included as they are.
For example, without a CDATA section, the character & would need to be encoded as
&amp;. However, encoding this within a CDATA section double-encodes the URI.
Consider the CDATA wrapping needed for the following URI:
http://ad.server.com/impression/dot.gif?v=1&id=abc
<Impression id="myserver">
<![CDATA[
http://ad.server.com/impression/dot.gif?v=1&amp;id=abc
]]>
</Impression>
The encoding of & into &amp; is not necessary in this example because the URI is enclosed
in a CDATA section. Characters in the URI that are also used to section out the URI with
CDATA may need extra encoding.
Consider the CDATA wrapping needed for the following URI:
http://ad.server.com/impression/dot.gif?s=x]]>x
<Impression id="myserver">
<![CDATA[http://ad.server.com/impression/dot.gif?s=x]]
]]>
<![CDATA[>]]>
x
</Impression>
The ]]> characters are used to close the CDATA section; therefore, the > character must
be enclosed in a secondary CDATA section. Since the x is harmless character at the end, it
can be left outside the CDATA section and will be concatenated with the other two URI
components, each closed in their CDATA sections.
Since CDATA-wrapping URIs is a requirement in VAST, the author of the VAST response
should carefully edit and test all included URIs, especially when input values require special
handling. Incorrect treatment of these characters may cause ad playback to fail or enable
content injection attacks.
Some additional examples are offered in the following table.
 Impression URL: http://ad.server.com/impression/dot.gif
 <Impression id="myserver">
http://ad.server.com/impression/dot.gif
</Impression>
Not enclosed in a CDATA section
<Impression id="myserver">
<![CDATA[http://ad.server.com/impression/dot.gif]]>
</Impression>
Correct and backwards compatible
Impression URL: http://ad.server.com/impression/dot.gif?v=1&id=abc
<Impression id="myserver">
http://ad.server.com/impression/dot.gif?v=1&amp;id=abc
</Impression>
The & is xml-encoded, but the URI needs to be wrapped in a CDATA block
Invalid -
<Impression id="myserver">
http://ad.server.com/impression/dot.gif?v=1&id=abc
</Impression>
Not only is this URI not CDATA enclosed but the & is also not XML-encoded
<Impression id="myserver">
<![CDATA[http://ad.server.com/impression/dot.gif?v=1&amp;id=abc]]>
</Impression>
This URI is both CDATA-enclosed and the & is XML-encoded. The player will interpret the URI as:
http://ad.server.com/impression/dot.gif?v=1&amp;id=1234
<Impression id="myserver">
<![CDATA[http://ad.server.com/impression/dot.gif?v=1&id=abc]]>
</Impression>
This URI is properly wrapped in a CDATA block. The & doesn't need to be encoded.

Impression URL: http://ad.server.com/impression/dot.gif?s=x]]>x
<Impression id="myserver">
http://ad.server.com/impression/dot.gif?s=x]]&gt;x
</Impression>
Not enclosed in a CDATA section even though > is encoded
<Impression id="myserver">
http://ad.server.com/impression/dot.gif?s=x]]>x
</Impression>
Not enclosed in a CDATA section
<Impression id="myserver">
<![CDATA[http://ad.server.com/impression/dot.gif?s=x]]>x]]>
</Impression>
CDATA section used but appears to end early because of the ]]> characters before the x, potentially allowing
content injection attacks
<Impression id="myserver">
<![CDATA[http://ad.server.com/impression/dot.gif?s=x]]]]>
<![CDATA[>]]>x
</Impression>
Correct and backwards compatible

Finally, a VAST-compliant ad response must conform to certain additional dependencies
that cannot be expressed in the VAST 4 XSD. For example, one ad type of either <InLine>
or <Wrapper> is allowed but not both. Another example is the protocol for providing 3 readyto-serve media files, ideally separate from any interactive components (see section 3.9). The
XSD can only validate for whether you’ve provided a URI under <MediaFile>; it cannot
validate whether the appropriate files have been provided. Such dependencies are further
described throughout this document.

### Tracking <a name="tracking"></a> 

VAST tracking is implemented using a number of individual tracking elements that map to
video events, such as video start or video completion. Each of these elements contains a
reference to a server-side resource, which historically has been an 1x1 pixel image, but
may also be a script or document reference. Calls to these resources are counted by the
ad server or other measurement vendor to tally up the total for a specific video event.

Publisher Implementation Note: The publisher is responsible for making the server-side request associated with a
specific video event when that event occurs during video playback. These events
may originate from a client-side player, or (in some SSAI cases) from the publisher
server. In the event the request comes from the publisher server extra care must
be taken to make sure that the calls are made concurrently with the corresponding
playback events, and any missing client-side information (user agent, etc) should
be passed along via headers or other mechanism.

The media player is required to request the resource file for any included tracking elements
from the URI provided at the appropriate times, or “fire” the tracking element. Advertisers
and publishers depend on accurate tracking records for billing, campaign effectiveness,
market analysis, and other important business intelligence and accounting. Good tracking
practices throughout the industry are important to the success and growth of digital video
and audio advertising.

General Implementation Note: The publisher must send requests to the URIs provided in tracking elements;
however, the publisher is not required to do anything with the response that is
returned. The response is only to acknowledge an event and to comply with the
HTTP protocol. This response is typically a 200 with a 1x1 pixel image in the
response body (although the response could be of any other type).

The use of multiple impression URIs enables the ad server to share impression-tracking
information with other ad serving systems, such as a vendor or partner ad server employed
by the advertiser. When multiple impression elements are included in a VAST response, the media player is required to request all impressions at the same time or as close as possible
to the same time. Any significant delay between impression requests may result in count
discrepancies between ad serving systems.

Publisher Implementation Note: If multiple <Impression> elements are provided, they must be requested at the
same moment in time or as close in time as possible. In particular for a VAST
response containing a <Linear> element, compliance with the IAB Digital Video
Measurement Guidelines. If any of the requests are delayed significantly,
discrepancies may result in the counts of participating ad serving system.

### VAST Wrappers <a name="wrappers"></a> 

Wrappers provide a way for one ad server to redirect a media player to another, secondary
ad server to retrieve an ad, multiple ads, or yet another VAST Wrapper.
One ad server may redirect to another for a variety of reasons:
● The first ad server has selected a specific advertiser campaign to fill the inventory. In
this case the redirect instructs the secondary ad server to return specific ads from a
particular ad campaign.
● The first ad server is delegating a specific piece of inventory for either a single ad or
an entire Pod of ads to the secondary ad server to fill with any ads that are within an
established agreement between the two parties.
● An ad server may wish to delegate delivery of the specific ad creative file(s) to a
separate asset repository/host (ad cloud).
● An ad server may have no ad to return and may return a redirect to a backfill
provider.

Infinite Loops and Dead Ends
When serving an ad involves a chain of Wrappers, an infinite loop is possible where a chain
of Wrappers never results in a final InLine VAST response. Another case involves a finite
number of VAST Wrappers in which the resulting InLine response is used as a decisioning
mechanism to find an ad instead of delivering the ad as required. In these cases, the
decisioning mechanism may never return an ad or may take too long to return the ad.
In general, VAST Wrappers should be limited to five before resulting in an InLine response.
If the player detects more than five Wrappers, the player may reject any subsequent
responses in the chain, replace the [ERRORCODE] macro in the VAST/Ad/Wrapper/Error
URI if provided to indicate that the Wrapper limit was reached, and move on to the next
option for an ad. Error codes should be sent for all wrappers in the chain where provided.
When an InLine response fails to produce an ad within the timeframe identified in VPAID or
other ad framework, the player may reject the ad, send error code 304 to indicate that no ad
was produced in the given timeframe, and move on to the next option for an ad. Error codes
should also be sent to any wrappers preceding the InLine response.

Wrapper Conflict Management and Precedence
When creative elements, such as Companion creative or click-throughs, are included
directly in the Wrapper response, conflict may occur. In a VAST ad, whether served with
multiple Wrappers or in one Inline response, all creative offered is intended to be part of the
same creative concept, and the media player should attempt to display all creative
presented in the response (or in a chain of responses). However, when a conflict occurs,
the media player should favor creative elements offered closest to the InLine response.
For example, if a wrapper contains companion creative and the InLine response also
contains companion creative, the companion creative in the Inline response should be
selected (unless both creative can be displayed without conflict).
In another example, if the InLine response is absent of any companion creative but two or
more Wrappers contain companion creative, then creative for the Wrapper served closest to
the InLine response should be favored. However, if multiple creative can be served without
conflict, the media player should attempt to display whatever creative it can.
With respect to ClickThrough handling, if the InLine response doesn’t include a
ClickThrough element and one or more of the calling Wrappers includes a ClickThrough
element, then the ClickThrough element closest to the InLine response must be favored.
Similarly, if the inLine response includes a ClickThrough element then this must be favored
over ClickThrough element(s) specified in calling Wrappers.

### Error Reporting <a name="errorreporting"></a> 

The <Error> element enables the media player to provide feedback to ad servers when an
Ad cannot be served. In VAST 3.0, detailed error codes and specifications for format are
provided to enable detailed error logging for better ad serving diagnostics.
Providing more detailed error codes enables stronger diagnostics and enables better
technology development over time. If ad servers can collect more detailed information about
why their ads or specific creative couldn’t be served, they can improve their systems to
produce fewer errors.
The <Error> element is an optional element nested within the <InLine> or <Wrapper>
element. It is used to track errors for an Ad. An error for an Inline Ad that is part of a chain
of Wrappers will produce an error for each of the Wrappers used to serve the Inline Ad.
An <Error> element is also provided at the root VAST level and is primarily used to report a
“No Ad” response. See section 2.3.6.4) for more information.
2.3.6.1 Ad Server Details: <Error> Element
An <Error> element includes a URI that provides a tracking resource for the error. This
error-tracking resource is called when the media player is unable to display the Ad.
The following example is a sample VAST response that includes the <Error> element for
an Inline Ad.
<InLine>
…
<Error>
<![CDATA[http://adserver.com/error.gif]]>
</Error>
…
</InLine>
If the ad server wants to collect more specific details about the error from the media player
(as listed in section2.3.6.3), an [ERRORCODE] macro can be included in the URI.
2.3.6.2 Media Player Details
If an error occurs while trying to load an Ad and the <Error> element is provided, the media
player must:
● Request the error source file using the URI provided.
Replace the [ERRORCODE] macro, if provided, with the appropriate error code listed in the
table in section2.3.6.3. At a minimum, error code 900 (Unidentified error) can be used,
but a more specific error code benefits all parties involved.
If the Ad was served after a chain of Wrapper ad responses, the media player must also
return error details as listed above for each Wrapper response that also includes error
parameters. Macro responses must be correctly percent-encoded per RFC 3986.
The following table lists VAST error codes and their descriptions.

VAST Error Codes Table
| Code | Description |
| -------- | -------- |
| 100 | XML parsing error. |
| 101 | VAST schema validation error. |
| 102 | VAST version of response not supported. |
| 200 | Trafficking error. Media player received an Ad type that it was not expecting and/or cannot play. |
| 201 | Media player expecting different linearity. |
| 202 | Media player expecting different duration. |
| 203 | Media player expecting different size. |
| 204 | Ad category was required but not provided. |
| 205 | Inline Category violates Wrapper BlockedAdCategories (refer 3.19.2). |
| 206 | Ad Break shortened. Ad was not served. |
| 300 | General Wrapper error. |
| 301 | Timeout of VAST URI provided in Wrapper element, or of VAST URI provided in a subsequent Wrapper element. (URI was either unavailable or reached a timeout as defined by the media player.) |
| 302 | Wrapper limit reached, as defined by the media player. Too many Wrapper responses have been received with no InLine response. |
| 303 | No VAST response after one or more Wrappers. |
| 304 | InLine response returned ad unit that failed to result in ad display within defined time limit. |
| 400 | General Linear error. Media player is unable to display the Linear Ad. |
| 401 | File not found. Unable to find Linear/MediaFile from URI. |
| 402 | Timeout of MediaFile URI. |
| 403 | Couldn’t find MediaFile that is supported by this media player, based on the attributes of the MediaFile element. |
| 405 | Problem displaying MediaFile. Media player found a MediaFile with supported type but couldn’t display it. MediaFile may include: unsupported codecs, different MIME type than MediaFile@type, unsupported delivery method, etc. |
| 406 | Mezzanine was required but not provided. Ad not served. |
| 407 | Mezzanine is in the process of being downloaded for the first time. Download may take several hours. Ad will not be served until mezzanine is downloaded and transcoded. |
| 408 | Conditional ad rejected. (deprecated along with conditionalAd) |
| 409 | Interactive unit in the InteractiveCreativeFile node was not executed. |
| 410 | Verification unit in the Verification node was not executed. |
| 411 | Mezzanine was provided as required, but file did not meet required specification. Ad not served. |
| 500 | General NonLinearAds error. |
| 501 | Unable to display NonLinearAd because creative dimensions do not align with creative display area (i.e. creative dimension too large). |
| 502 | Unable to fetch NonLinearAds/NonLinear resource. |
| 503 | Couldn’t find NonLinear resource with supported type. |
| 600 | General CompanionAds error. |
| 601 | Unable to display Companion because creative dimensions do not fit within Companion display area (i.e., no available space). |
| 602 | Unable to display required Companion. |
| 603 | Unable to fetch CompanionAds/Companion resource. |
| 604 | Couldn’t find Companion resource with supported type. |
| 900 | Undefined Error. |
| 901 | General VPAID error. |
| 902 | General InteractiveCreativeFile error code. |

No Ad Response
When the ad server does not or cannot return an Ad, the VAST response should contain
only the root <VAST> element with optional <Error> element, as shown below:
<VAST version="4.1">
<Error>
<![CDATA[http://adserver.com/noad.gif]]>
</Error>
</VAST>
The VAST <Error> element is optional but if included, the media player must send a
request to the URI provided when the VAST response returns an empty InLine response
after a chain of one or more wrappers. If an [ERRORCODE] macro is included, the media
player should substitute with error code 303.
Besides the VAST level <Error> resource file, no other tracking resource requests are
required of the media player in a no-ad response in either the Inline Ad or any Wrappers.

### Industry Icon Support <a name="industryicon"></a>

Several initiatives in the advertising industry involve using an icon that overlays on top of an
Ad creative to provide some extended functionality such as to communicate with consumers
or otherwise fulfill requirements of a specific initiative. Often this icon and its functionality
may be provided by a vendor, and is not necessarily served by the ad server or included in
the creative itself.

One example of icon use is for compliance to certain Digital Advertising Alliance (DAA) selfregulatory principles for interest-based advertising (IBA). This section provides an overview
of how media players can support the use of icons in a general manner while using the
DAA’s AdChoices program, as a specific example.

Icons are optional for audio, and can be used in the context of a companion banner. But
since audio ad players are not required to have a rendering engine, icons are not a
requirement when the adType is “audio” or “hybrid”.

Icon Use Case: AdChoices for Interest-Based Advertising (IBA)
The Digital Advertising Alliance (DAA) sets forth principles that endeavor to give consumers
a better understanding of and greater control over ads that are customized based on the
consumer’s online behavior. This control is made available to the consumer in the form of
the AdChoices icon, which is displayed in a prominent location in or around the Ad creative.
When a consumer clicks the icon, they may be offered: information about the ad server and
data providers used to select the Ad, options to learn more about online behavioral
advertising (OBA), and the ability for consumers to opt out from receiving OBA ads in the
future.

The <Icons> Element
VAST 3.0 introduced the <Icons> element, which is offered under the <Linear> creative
element for both Inline and Wrapper ad elements.

The following diagram illustrates the general process for how the <Icons> element is
represented in a VAST response.

The Icon Provider Server represented in this diagram may be the same server that serves
the VAST response but more commonly, is a vendor that serves the icon from its own
systems.

When the <Icons> element is included in the VAST response, the media player must
display the object as an overlay on top of the Linear Ad with which the icon is served and
after the ad has started (i.e. first frame of video is displayed in the player).

## Viewability Verification and Interactive Linear Creative <a name="viewability"></a>

VAST 4 adds new sections in the Linear file for viewability, ad verification, and interactive
creative files. These new sections offer performance and measurement benefits but also
add a level of complexity.
Player compliance with VAST 4 requires appropriate execution of these files.
The player should execute the ad in the following order:
1. Start loading verification resources.
2. Start loading video assets and interactive resources.
3. Initialize interactive resources.
4. Start ad playback.
Player expectations on these added features are summarized here and further defined in
their corresponding sections.

### Publisher Viewability <a name="publisherviewability"></a> 

Publishers have the option to offer viewable impression tracking on the ad using the
<ViewableImpression> feature added in VAST 4. Three URIs may be provided to track
whether the ad was <Viewable>, <NotViewable>, or <ViewUndetermined> (see section
3.5).
Note that this feature is specific to (the likely uncommon) situation where the publisher is
the party monitoring ad geometry and making the viewability determination. As such, it will
very likely be limited to situations where the buyer and seller have some prior relationship
and agreement around measurement mechanics and the viewability standard used. It is not
a general replacement for, nor should it be confused with, measurement and reporting of
viewability by third-party verification services (as in section 2.4.2). These URIs are not
intended for reporting viewability determinations from such parties.
This feature is not applicable to audio ads.

### Viewability with Ad Verification Services <a name="adverificationservices"></a> 

Ad Verification services can be requested for measurement by adding a <Verification>
element under <AdVerifications> including their executable resources and associated
per-impression metadata. Multiple vendors may use this feature to measure the same ad
session. All verification resources listed in the VAST should be executed, including those
from any intermediary <Wrapper> VASTs, barring exceptions based on a whitelist or other
pre-defined rules as outlined below.
A VAST 4 player must check for these elements, however, players may optionally either:
refuse to execute unknown resources or declare it as not supported. The recommended
process is to consult an IAB TechLab-provided/certified list of known verification vendors
and domains, although the exact mechanism is left to the publisher/player. The player must
request each associated verificationNotExecuted tracking event URI (with the [REASON]
macro filled with reason code 1) in the case that it refuses to execute one or more
verification script (see section 3.17.4 for details).
Verification resources should be executed as required by the OMID specification. If the
code cannot be executed as provided, any included verificationNotExecuted tracking events
URIs must be sent with the appropriate reason code (e.g. not supported, error, etc.).

### Interactive Linear Creative Files <a name="interactivelinear"></a> 

In VAST 4, the <MediaFile> should only be used to include video or audio files. For Linear
files that require an API framework to be executed, the new <InteractiveCreativeFile>
should be used to include these files. Once the <AdVerifications> element has been
checked for verification code, the <InteractiveCreativeFile> element should be checked
for code in order to execute the ad. When the <InteractiveCreativeFile> cannot be
executed, the <Error> should be sent and the player may check the <MediaFiles> element
for any media files that are available to be played.
This script asset should only be used to enable interactive, dynamic or other creative
capabilities and not used for viewability, client-side arbitration, or other non-creative uses.

# VAST Implementation <a name="implementation"></a>

VAST is an XML schema for providing metadata about an ad for in-stream video or audio
that is parsed by a player or by a server on the player's behalf. This section provides the
details for forming the VAST.
Beginning with section 3.1, each element available in VAST is described and a table
summarizes information about hierarchy, requirements, and attributes. Each VAST element
that includes nested elements is defined under a second-level heading in this document.
Third-level headings represent nested elements that have no additional nested elements
under them.
Links to the table of contents (TOC) and the schema are provided under each heading to
aid in navigation. The human-readable schema in section summarizes VAST elements and
provides a link to the chapter that describes the element in more detail.

Before forming a VAST document, considerations for the XML namespace and browser
security for JavaScript or other scripting languages should be established as follows.
XML Namespace
Whenever VAST is used in conjunction with any other XML template, such as with VMAP or
VAST extensions, a namespace should be declared for each so that the elements of one
are not confused with the elements of another.
For more information, visit: http://www.w3.org/TR/REC-xml-names/
Browser Security
Modern browsers restrict Adobe Flash and JavaScript runtime environments from retrieving
data from other servers. Since typical VAST responses come from other servers, measures
must be taken for each.
Cross Origin Resource Sharing (CORS) for JavaScript
In order for JavaScript media players to accept a VAST response, ad servers must include
a CORS header in the http file that wraps the VAST response. The CORS header must be
formatted as follows:
Access-Control-Allow-Origin: <origin header value>
Access-Control-Allow-Credentials: true
These HTTP headers allow an ads player on any origin to read the VAST response from the
ad server origin. The value of Access-Control-Allow-Origin should be the value of the
Origin header sent with the ad request.
Setting the Access-Control-Allow-Credentials header to true will ensure that cookies
will be sent and received properly.
Note: For requests where the Origin header is null, ad servers should respond with only
Access-Control-Allow-Origin: * (and no Access-Control-Allow-Credentials header)
to prevent breaking on originless requests, such as those from iOS wkwebviews.
For more information, visit http://www.w3.org/TR/cors

## Declaring the VAST Response <a name="response"></a> 

All VAST responses share the same general structure. Each VAST response is declared
with <VAST> as its topmost element along with the version attribute indicating the official
version with which the response is compliant. For example, a VAST 4.1 response is
declared as follows:
<VAST version="4.1">
As with all XML documents, each element must be closed after details nested within the
element are provided. The following example is a VAST response with one nested <Ad>
element.
<VAST version="4.1">
<Ad>
<!--ad details go here-->
</Ad>

## VAST <a name="spec"></a> 
VAST is the root node for a VAST-compliant ad response and is used to declare the VAST
3.2 VAST response as described in section 3.1.

| Feature | Description |
| ------- | ------- |
| Player Support | Required |
| Required in Response | Yes |
| Parent | None (root) |
| Bounded | 1 |
| Sub-elements | Error* <br>Ad* |

| Attribute | Description |
| ------- | ------- |
| version | A float (number with decimal) to indicate the VAST version being used. |

*either <Error> or <Ad> may be provided but not both

### Error (VAST) <a name="error"></a>

Used to report a no-ad response. When the ad server does not or cannot return an Ad, the
VAST response should contain only the root <VAST> element with one or more <Error>
elements, as shown below:
<VAST version="4.1">
<Error>
<![CDATA[http://adserver.com/noad.gif]]>
</Error>
</VAST>
The VAST <Error> element is optional but if included, the media player must use the URI
provided to notify the server that no ad was returned. Multiple <Error> elements may be
provided to notify multiple parties of the no-ad response.

| Feature | Description |
| ------- | ------- |
| Player Support | Required |
| Required in Response | No, but if supplied no other elements are allowed |
| Parent | VAST |
| Bounded | 0+ |
| Contents | A URI supplied by the ad server and used to report the no ad response |

## Ad <a name="ad"></a>

The <Ad> element may contain an <InLine> ad or a <Wrapper>. The wrapper points to a
secondary server for another VAST response, which may be another wrapper or an InLine
response. An InLine response contains the ad creative necessary to execute ad playback.

### Ad Pods and Stand-Alone Ads <a name="adpods"></a>

While a single <Ad> element represents the most common VAST response, multiple ads
may be included as either stand-alone ads or a Pod of ads, or a mix of both. Ads in a Pod
are distinguished by using the sequence attribute for an <Ad>, denoting which ad plays first,
second, and so on. If the player supports Ad Pods, sequenced ads are played in numerical
order and all ads in the Pod should be played to the best of the player's ability. All sequence
values in a VAST response must be unique.
Non-sequenced ads, are stand-alone ads and considered part of an "ad buffet" from which
the player may select one or more ad to play in any order. Stand-alone ads may be included
in a VAST response with an Ad Pod and may be used to substitute an ad in the Pod when
an ad cannot be played.
The following diagram illustrates some options for how the <Ad> element may be
represented in a VAST response.

If the media player cannot display an entire Ad Pod or any stand-alone ads, it can decline
from loading the ad resources and use the error URI, if provided, to notify the server.
Playing a Pod of Ads
When electing to play a Pod of ads returned by the ad server, the media player must play
the ads in the Pod in the prescribed sequence and should play as many of the ads as
possible. The player may elect to truncate any ads at the end of an Ad Pod if either: the ads
cannot be played because they cannot physically fit into the ad break in the stream (such as
when time is limited in a live stream) or if the Pod violated any limits specified by the media
player request (for example: number of ads to return, or maximum pod duration).
When an Ad Pod is the result of following a VAST <Wrapper> the same impression and
tracking URIs in the VAST <Wrapper> are called as each ad in the Pod is played.
Should an ad in the Pod fail to play, the media player should substitute an un-played stand-
alone ad from the response. If stand-alone ads are unavailable, the player should move on
to the next ad in the Ad Pod.

If a Wrapper is used to provide an ad in the Ad Pod, the Wrapper can use attributes,
allowMultipleAds=false and followAdditionalWrappers=false to prevent performance
issues that result from an unmanaged string of Wrappers and multiple ads in an Ad Pod.

| Media Player Implementation Note | If multiple <Ad> elements are provided with sequence attributes and the player
supports Ad Pods, all ads in the Pod must be played to the best of the player's ability. If not supported or the Pod cannot be played, the media player should use the error-tracking URI, if provided, to notify the server. A special exemption exists when using VMAP. Please visit http://iab.com/vmap for information on VMAP. |

### The Ad Element <a name="adelement"></a>

Properties for the <Ad> element are listed in the following table.

| Feature | Description |
| ------- | ------- |
| Player Support | Required (Ad Pod support is optional) |
| Required in Response | Yes (unless there is no ad to return; in which case <Error> should be used to provide the error URI) |
| Parent | VAST |
| Bounded | 0+ |
| Sub-elements | InLine* <br>Wrapper* |

| Attributes | Description |
| ------- | ------- |
| id | An ad server-defined identifier string for the ad |
| sequence | A integer greater than zero (0) that identifies the sequence in which an ad should play; all <Ad> elements with sequence values are part of a pod and are intended to be played in sequence |
| conditionalAd | [Deprecated in VAST 4.1, along with apiFramework] A Boolean that identifies a conditional ad. In the case of programmatic ad serving, a VPAID ad unit or other mechanism might be used to decide whether there is an ad that matches the placement. When there is no match, an ad may not be served. Use of the conditionalAd attribute enables publishers to avoid accepting these ads in placements where an ad must be served. A value of true indicates that the ad is conditional and should be used in all cases where the InLine executable unit (such as VPAID) is not an ad but is instead a framework for finding an ad; a value of false is the default value and indicates that an ad is available. |
| adType | An optional string that identifies the type of ad. This allows VAST to support audio ad scenarios. <br>Possible values – video, audio, hybrid. <br>Default value – video (assumed to be video if attribute is not present) <br>More details on the use case in section 1.5 |

*The Ad element requires exactly one child, which can either be an <InLine> or <Wrapper>
element.

## InLine <a name="inline"></a>

Within the nested elements of an <InLine> ad are all the files and URIs necessary to play
and track the ad. In a chain of <Wrapper> VAST responses, an <InLine> response ends the
chain.

| Player Support | Required |
| Required in Response | One of <InLine> or <Wrapper> is required, but both are not allowed |
| Parent | Ad |
| Bounded | 0-1 |
| Sub-elements | AdSystem*, AdTitle*, Impression*, AdServingId*, Category, Description, Advertiser, Pricing, Survey, Error, Extensions, ViewableImpression, AdVerifications, Creatives*, Expires  |

*required

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
