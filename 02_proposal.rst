Proposal
========

The goal of this thesis project is to evaluate the potential for real-time demand-responsive microtransit services to expand mobility access in rural geographies like Humboldt county. This thesis will focus on modeling microtransit services providing Mobility-on-Demand (MOD) services within Humboldt county to evaluate circumstances where public microtransit could improve or supplement existing fixed-route public transit services.  Though the proposed analysis focuses on Humboldt county, the hope is to gain some understanding of better approaches to address mobility challenges faced by rural and micropolitan communities.

Evaluation Framework
--------------------

This thesis aims to evaluate microtransit services based on the following factors.  This evaluation framework is aligned with that proposed in the Humboldt County Association of Governments (HCAOG) Mobility-on-Demand strategic plan. 

- Effectiveness with respect to the population and market served
  - Increasing system-wide ridership
  - Reducing travel times
  - Increasing riders per service-mile or service-hour
- Improving equity of access by providing reliable and cost accessible transit options for transportation disadvantaged populations
- Overall service costs 
  - Capital costs for fleets and infrastructure
  - Operating costs to run service
  - Costs for service operation through public-private partnerships
- System efficiency
  - $/trip
  - $/vehicle-hour
  - $/vehicle-mile
  - costs to end users and funding partners
- VMT reduction per capita or SOV
- Level of Service
  - Operating hours
  - Frequency
  - Trip purposes served
- Quality of Service
  - Convenience
  - Transfers
  - Trip times
  - Flexibility

Methods and Approaches
----------------------

One common approach in modeling transportation systems is to use :abbr:`ABM (Agent Based Models)` :cite:`Evans2013`. ABMs have historically been used to model and understand traveler behaviors :cite:`Kagho2020` and emerging/novel transportation services that would be expensive or impossible to deploy in the real world such as shared electric autonomous vehicles :cite:`Sheppard2019`.  ABMs are well suited to understand systems where many agents with a wide array of individual preferences operate independently under shared, collective constraints.  A transportation ABM typically works by encoding a population of travelers (i.e. "agents" which have a demand for transportation) and a supply of travel modes over a physical geography (a :abbr:`TAZ (Transportation Analysis Zone)` ) and simulating a series of trips (i.e. "schedules") for each individual agent in the TAZ over the course of some time where travelers decide on a set of available mode choices based on a configurable mode choice preference function.  Travelers must share the same physical space (roads), and in the case of public transit services or ride hailing services, the same pool of vehicles.  The collective behaviors and actions of individual agent interactions can be used to describe system level characteristics.  Some examples include traffic flow and congestion for some schedule of travel demand and transportation supply, average wait times for public transit modes, origin/destination distributions, and collective mode choice preferences.

This thesis proposes to build an ABM to study a transportation network in Humboldt County under different microtransit service models.  The goal of the ABM is to calculate performance metrics outlined in the evaluation framework section for several microtransit service models and service demand scenarios.

A single microtransit service model will consist of a fleet, operating hours, and an operating mode.  One example might describe a 100-vehicle fleet operating a fully flexible origin-to-destination service running on weekdays from 7AM to 7PM with no pooling for single riders as a full replacement for fixed-route services.  Another example might describe a 10 shuttle fleet providing flexible origin, fixed destination services as a supplemental service to existing fixed-route systems.  Both of these service models would be applied against a demand scenario (the former scenario would be deemed non-performant across most of the evaluation criteria)

Each demand scenario will be fed into the ABM as inputs, and evaluated against a fleet attempting to fulfill ride requests.  Using activitysim [#]_, activity schedules and population characteristics will be synthesized to create different demand scenarios.  For example, a single demand scenario might describe a population where by 20% of the population, uniformly distributed across the county intends to use the microtransit service for a single leg in their daily schedules.  A more realistic demand scenario might involve targeting populations that are transportation disadvantaged.  These data would be populated from commuter surveys and the American Community survey.

In order to model the Humboldt County transportation system, this thesis intends to leverage the BEAM model [#]_ :cite:`BEAM`.  The BEAM model will be used to actually execute trips and mode choice selections for our synthetic populations.  The resultant model will report on performance metrics outlined in the evaluation framework.  BEAM would be used to simulate intra-TAZ trips and schedules within the Humboldt County area to calculate ridership levels, wait times, travel times of the microtransit service, and other performance metrics needed to evaluate the a specific service model serving a single population demand scenario.  Different scenarios would be analyzed and compared to determine required service models and population demand scenarios where microtransit services could perform well.

Goals and Desired Outcomes
==========================

This thesis aims to produce the following artifacts:

- A catalog of different DRT service architectures and designs (differing on vehicle size, fleet size, dispatch methods, payment schedules, and potential coverage goals - i.e. how large can a service area get?)
- An extensible BEAM compatible framework for public consumption to evaluate potential of new demand responsive public transit systems.
  - An extensible tool for generating populations that could plug in publicly accessible data or more granular, localized, representative survey data.

Potential Expanded Scope of Work
--------------------------------
The approach above lends itself to future work, which may or may not be addressed over the course of the thesis.  By expanding understanding into new mobility service deployments, these issues may be addressed in the future.

- What grid services or burdens would a public DRT fleet present (both autonomous and non-autonomous fleets)?
  - What charging strategies should be deployed from medium and heavy duty commercial/public fleets?
  - Is it economical or does it make sense to use fleets as grid producer-consumers? or should they remain strictly consumers?
- What are the potential emissions benefits or harms in transportation deserts as a result of DRT services compared to traditional public transit systems and personal vehicle travel?
- What are social and cultural barriers to adopting and accepting new mobility systems over personal vehicle ownership? 
- What public safety implications are there from expanded deployments of shared fleets over a highly distributed personal fleet?

.. rubric:: Footnotes

.. [#] https://activitysim.github.io/
.. [#] https://beam.lbl.gov/