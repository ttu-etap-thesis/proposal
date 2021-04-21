Proposal
========

This thesis will focus on modeling a microtransit service providing Mobility-on-Demand (MOD) services within Humboldt county to evaluate circumstances where public microtransit could reliably provide shorter trip times and lower costs to serve in comparison to existing fixed route transit services.  Though the proposed analysis focuses on Humboldt county, the hope is to gain some understanding of better approaches to address mobility challenges faced by rural and micropolitan communities. Additionally, this thesis aims to understand the economic and operational challenges in deploying a microtransit service from the perspective of public transit agencies.


Question : Where (and at what levels of ridership) would microtransit be more cost effective?

Evaluation:

- Existing data: https://cms7.fta.dot.gov/sites/fta.dot.gov/files/transit_agency_profile_doc/2019/9R02-91036.pdf
- Using an ABS, compare cost effectiveness metrics

Question : Where could microtransit supplement fixed-route services to serve more rides?

Evaluation:

- Simulate ridership demand profiles and compare fixed route + micro transit schedules to meet peak

Methods and Approaches
----------------------

One common approach in modeling transportation systems is to use :abbr:`ABM (Agent Based Models)` :cite:`Evans2013`. ABMs have historically been used to model and understand traveler behaviors :cite:`Kagho2020` and emerging/novel transportation services that would be expensive or impossible to deploy in the real world such as shared electric autonomous vehicles :cite:`Sheppard2019`.  ABMs are well suited to understand systems where many agents with a wide array of individual preferences operate independently under shared, collective constraints.  A transportation ABM typically works by encoding a population of travelers (i.e. "agents" which have a demand for transportation) and a supply of travel modes over a physical geography (a :abbr:`TAZ (Transportation Analysis Zone)` ) and simulating a series of trips (i.e. "schedules") for each individual agent in the TAZ over the course of some time where travelers decide on a set of available mode choices based on a configurable mode choice preference function.  Travelers must share the same physical space (roads), and in the case of public transit services or ride hailing services, the same pool of vehicles.  The collective behaviors and actions of individual agent interactions can be used to describe system level characteristics.  Some examples include traffic flow and congestion for some schedule of travel demand and transportation supply, average wait times for public transit modes, origin/destination distributions, and collective mode choice preferences.

This thesis proposes to build an ABM to study a transportation network in Humboldt County with a public microtransit service.  The goal of the ABM is to evaluate wait and trip times and system costs of a hypothetical microtransit fleet under different scenarios of fleet characteristics and ridership demand and mode-choice preferences.  Different demand and supply scenarios will be compared against existing performance metrics from publicly available transit agency audits [#]_.  

The proposed scope of work includes two major modeling activities:

- Creation of different mobility demand scenarios which capture varying levels of demand across different population characteristics and varying activity schedules (i.e. population synthesis)
- Trip modeling based on a microtransit fleet with scenarios varying across fleet size and individual vehicle specifications.

Each mobility demand scenarios will be fed into the ABM as inputs, and evaluated against a fleet attempting to fulfill ride requests.  Using activitysim [#]_, activity schedules and population characteristics will be synthesized to create different demand scenarios.  In order to model the Humboldt County transportation system, this thesis intends to leverage  the BEAM model [#]_ :cite:`BEAM`.  The BEAM model will be used to actually execute trips and mode choice selections for our synthetic populations.  The resultant model will report on the mode choice, wait times and travel times of microtransit modes, which will be used to estimate operating and long-term maintenance costs.

For example, a single demand scenario might describe a population where by 20% of a community intends to use the microtransit service for a single leg in their daily schedules.  A single fleet scenario might describe a fleet of 10 micro-shuttles capable of pooling up to 10 rides each.  BEAM would be used to simulate intra-TAZ trips and schedules within the Humboldt County area to calculate ridership levels, wait times, travel times of the microtransit service.  Using the modeled travel data, a bottom-up cost estimate would be used to build up annualized system costs associated with running the microtransit service.  Different scenarios would be analyzed and compared against existing costs and performance metrics of various HTA services.


----------------------------------------

Population Synthesis
::::::::::::::::::::

Population data is a critical input for an agent based model.  Travel decisions are modeled for every individual traveling within a Transportation Analysis Zone (TAZ).  Synthetic agents (persons) are typically modeled as follows for a single simulated day of trips:

- A sequential set of plans each describing an origin and destination trip with a start and end time and travel mode.
- Attributes of interest such as employment status, age, gender, income group, etc.  Person attributes may be inputs into a scoring function when evaluating mode choices for every individual agent.  

Three components are needed to create a synthetic population:

1.  Population characteristics
2.  Points of interest located within the network in the travel analysis zone
3.  Travel diaries describing trip behavior for individuals

Population characteristics such as household size, employment status, age, race and income will be post-stratified and distributed via proportions to synthetic populations at a census block level.  Points of interest (i.e. travel locations) will be generated from publicly available commercial mapping data and used as destinations and origins for travel tours.  Finally, travel diaries will be assigned based on travel survey data from sources such as the California Household Travel Survey :cite:`NREL2017`.  These data will be compiled into a dimensional datawarehouse that can be used to generate inputs for the ABM software representing different levels of demand for the DRPT service.

Trip Mode modeling & Scenario analysis
::::::::::::::::::::::::::::::::::::::

The central focus of this thesis is to evaluate a public transit fleet operating like a modern TNC.  TNC modeling in ABMs has been implemented in open source ABMs such as BEAM :cite:`BEAM`.  The microtransit fleet in this thesis will strongly resemble a TNC with constraints based on real-world economic and implementation constraints.  Constraints that existing TNCs don't face such as fixed fleet size, higher operator costs, are examples of issues which might be modeled. 

- Different types of fleets could be deployed with varying costs - a larger fleet of small microshuttles would operate differently from a small fleet of larger buses.
- Different routing and dispatch strategies should be evaluated.  Real world deployments such as RideWithVia's SMART ride program operate on a semi-fixed route which change based on time of day and demand, but TNCs like Uber and Lyft create completely dynamic stops and routes.


.. figure:: figures/TTU-DRPT-Thesis.png
  :name: system-architecture

  Scenarios will be generated from combining characteristics of different modules as shown above.  The full result size will be the cross product of Populations x Fleet Designs.  Aggregate results will be used to determine where a theoretical demand responsive public transit system could be used to effectively provide local mobility services.

Goals and Desired Outcomes
==========================

This thesis aims to produce the following artifacts

- A conceptual model for evaluating DRT cost effectiveness for different population characteristics that can be used by transit agencies to justify or consider pilot programs.
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

.. [#] https://hcaog.net/library?term_node_tid_depth=16
.. [#] https://activitysim.github.io/
.. [#] https://beam.lbl.gov/