### Overview

An important component of the SMARTA and Ataper projects is the eventual incorporation of user-generated feedback as an organic, discrete source of system events, behaviors, alerts, and foibles. This data source would service the needs of ostensibly ephemeral impact events for the system and ultimately feed a data warehouse for BI analysis. 

The conceit of the story is that primary sources of truth are fundamentally invalidated or otherwise eroded by one-off events that are unaccounted for in the existing API.

### Goals

Our exaxmple for the first iteration is a riff on the Waze-style user feedback system with the key characteristics:

* Pre-defined event categories.
* A confirm/deny system for each event to invalidate out-of-date/resolved incidents.
* Pre-emptive visual representation at impacted stations/lines.
* Traceability to individual rides and riders. 

Some stretch and open-ended goals and consequences of this initiative: 

* Rider login system (OpenID?)
* Tracked user preferences.
* Cached seaerches/previous trips.


<img src="https://i.imgur.com/l3VooIs.png" width="250" />

<img src="https://i.imgur.com/TmHonoS.png" width="250" />


### Scenarios

*Scenario 1*: Inclement weather has impacted the system as follows: 

  * A fallen tree forces Brookhaven station to single-track trains with all scheduled Gold line trains incurring a +3 minute delay to their overall trips. 
  * The bus bay capacity is reduced and bus departure/arrivals are shuffled from the posted locations.
  * The parking lot availability is reduced by 50% 
  * Adjacent traffic and crosswalk lights are non-functioning leading to considerable backed up traffic
  
|Actor|Goal(s)| 
|---|---|
|Rider (Reporter)| I wish to report discovered delays and station accessibility issues. If others have reported issues, I can confirm the on-going nature of those issues. |
|Rider (Viewer)| I wish to view relevant events that may impact my trip including parking, entrance closures, and schedule delays. |
|SMARTA (API)| I wish to collect, classify, and aggregate events on a chronological scale and supplement schedule requests with that feedback overlayed. |
|Ataper (UI)| I wish to display context-specific information for users requesting schedule details. |
|Analysis (Data science)| ??? |

*Scenario 2*: A major event downtown (concert, game, festival, etc...) has impacted the system as follows: 
  
  * Capacity at park-and-ride stations is limited and highly volatile, particularly at terminating stations (Doraville, North Springs, etc...)
  * Ticket kiosks are backed up as first-time riders purchase Breeze cards en masse.
  * Ridership is dense for all Five Points-bound trains with increasing delays as boarding and departures neccessarily lengthen in time to reflect the capacity.
  * Transfers at exits prior to arrival at Five Points become increasingly difficult as the volume of riders on trains and at the station prevent easy movement.
  
|Actor|Goal(s)| 
|---|---|
|Rider (Reporter)| I wish to document observed waits at the station (kiosks, boarding, transfers, etc...) and delays on the train itself. |
|Rider (Viewer)| I wish to see and/or be notified of trip-impacting events prior to immediate embarking. |
|SMARTA (API)| I wish to collect, classify, and aggregate events on a chronological scale and present warning/alternatives as supplemental station data. |
|Ataper (UI)| I wish to display inforation prominently and interactively to riders impacted at specific stations. |
|Analysis (Data science)| ??? |

*Scenario 3*: A gameday rider sets off a smoke bomb at Dome Stadium, impacting the system as follows:

  * The platforms area of Dome Station are engulfed in smoke.
  * Fire alarms are tripped as a consequence of the smoke.
  * Stairs and escalators become congested and slow-moving.
  * Trains in the immediate arrival schedule are stopped en route.
  * Trains in the distant arrival schedule are delayed.
  * Platforms for Dome-bound trains on the east/west line become congested as delays build.
   
|Actor|Goal(s)| 
|---|---|
|Rider (Reporter)| I wish to report the details and safety of the impact event and be made aware of emergency contact channels. |
|Rider (Viewer)| I wish to see and/or be notified of the delays and receive suggestions for alternative exits in proximity. |
|SMARTA (API)| I wish to collect and classify emergency-level events and triangulate/supplement the veracity with official MARTA notifications. |
|Ataper (UI)| I wish to prominently display information about the event, its emergency level, and alternative courses of actions. |
|Analysis (Data science)| ??? |


### Key Questions

To launch an MVP for this feature experiment we need answers to a handful of key questions:

* How do we determine consensus of the existence/non-existence for a given reported event? 
* What categories of events should we track by default?
* How should the events be represented in the UI?
* What's the lifespan of a reported event?


### Mock Ups

### Persistence and Identity

Wrapped up with this feature is the subtext of identity management. At the 6/26 discussion we arrived at consensus for the following items: 

* The user workflow can be transparently bisected between an "authenticated" experience and an anonymous experience
* Among other behaviors, the authenticated experience should persist certain preferences and interactions with the front-end. To what degree should we track and persist user feedback events?
* Concurrently, how do we prototype a feedback system that offers the same foundational experience (report events and view others) in an anonymous experience?
* To what degree is this intertwined with the authentication and authorization discussion?

### MVP

### Stretch Goals

* Push notifications for the Ataper UI
* Reporting history and trends linked with OpenID implementation
* Basic incentivization/gamification of reporting (a la Waze leaderboards)
* Incident heat maps
