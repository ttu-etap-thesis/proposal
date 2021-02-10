Proposal
========

The central question of this thesis is as follows: Could public DRT services meet mobility demands in in lieu of existing personal vehicle travel and existing fixed-route public transit systems?

Additionally, this thesis aims to understand non-mobility issues of a public DRT services such as:

- What fiscal impacts or pressures would a public DRT service create for local transportation budgets?
- How would such a system perform in rural or small population centers which have been historically under-served by public transit?

Methods and Approaches
----------------------

The proposed approach is to leverage an :abbr:`ABM (Agent Based Model)` :cite:`Evans2013` to simulate different DRT fleets and designs in a set of non metropolitan population centers.  The ABM will simulate many "possible realities" of how different population characteristics such as mode choice preferences and different geospatial distributions of travel demand origins and destinations would affect adoption and level of service.  Travel demand (defined as the set of tours each agent in a region requires in a 24 hour period, where each tour is composed of multiple trips each leg of which has a travel mode) will initially be characterized by public survey data such as the California Household Travel Survey :cite:`NREL2017`, and the national transit database :cite:`FederalTransitAdministration2020`.  An overview of this approach is shown in :numref:`system-architecture`.

.. figure:: figures/TTU-DRPT-Thesis.png
  :name: system-architecture

  Scenarios will be generated from combining characteristics of different modules as shown above.  The full result size will be the cross product of Regions x Populations x Strategies x Fleet Designs.  Aggregate results will be used to determine where a theoretical demand responsive public transit system could be used to effectively provide local mobility services.

Three critical components will make up the bulk majority of this thesis.

- Population Synthesis
- Transportation modeling & Scenario analysis
- Economic Analysis

Population Synthesis
::::::::::::::::::::

Population data is a critical input for an agent based model.  Travel decisions are modeled for every individual traveling within a Transportation Analysis Zone (TAZ).  Synthetic agents (persons) are typically modeled as follows for a single simulated day of trips:

- A sequential set of plans each describing an origin and destination trip with a start and end time and travel mode.
- Attributes of interest such as employment status, age, gender, income group, etc.  Person attributes may be inputs into a scoring function when evaluating mode choices for every individual agent.  

Three components are needed to create a synthetic population:

1.  Population characteristics
2.  Points of interest located within the network in the travel analysis zone
3.  Travel diaries describing trip behavior for individuals

Population characteristics such as household size, employment status, age, race and income will be post-stratified and distributed via proportions to synthetic populations at a census block level.

Points of interest (i.e. travel locations) will be generated from publicly available commercial mapping data and used as destinations and origins for travel tours.

Finally, travel diaries will be assigned based on travel survey data from the California Household Travel Survey.

These data will be compiled into a dimensional datawarehouse that can be used to generate inputs for the ABM software.

Trip Mode modeling & Scenario analysis
::::::::::::::::::::::::::::::::::::::

The central focus of this thesis is to evaluate a public transit fleet operating like a modern TNC.  TNC modeling in ABMs has been implemented in open source ABMs such as MatSim and ActivitySim.  The DRPT fleet in this thesis will strongly resemble a TNC with constraints based on real-world economic and implementation constraints.  Constraints that existing TNCs don't face such as fixed fleet size, higher operator costs, are examples of issues which might be modeled.  A critical part of this thesis will be to explore sensitivities from dimensions that drive mobility mode choice.  Multiple uncertainties present major challenges in this effort.

- One major limitation will be the need to evaluate how a DRPT option would be chosen between other trip modes.  To address this uncertainty, multiple "scoring" functions will be used drawn from existing literature.  This might be driven by total trip time, level of service/congestion, pricing, or subjective measures such as perceived convenience that could be modeled as ordinal numbers.
- Multiple fare collection strategies.  Fixed fare with limited transit zones, vs dynamic distance and demand driven pricing are both interesting deployment options or a mix of the two options should both be explored.
- Different types of fleets could be deployed with varying costs - a larger fleet of small microshuttles would operate differently from a small fleet of larger buses.
- Different routing and dispatch strategies should be evaluated.  Real world deployments such as RideWithVia's SMART ride program operate on a semi-fixed route which change based on time of day and demand, but TNCs like Uber and Lyft create completely dynamic stops and routes.


Economic Analysis
:::::::::::::::::

The ubiquitous presence of TNC operations has more than established the technical feasibility of a widespread responsive transit system.  The central concern is where could such a system produce cost savings, or cost effective expanded mobility access.  Two economic analyses are of concern:

1) What are the impacts on household travel spending?
2) What are the impacts on local agency budgets?

A census of public transit budgets will be compiled into a central source and used to evaluate plausible spending and economic viability at a transit-agency level of detail.  


Goals and Desired Outcomes
==========================

This thesis aims to produce the following artifacts:

- A model for evaluating DRT cost effectiveness in various contexts of geographical and population characteristics.
- A catalog of different DRT service architectures and designs (differing on vehicle size, fleet size, dispatch methods, payment schedules, and potential coverage goals.)
- Estimates of regionally specific travel demand profiles for non-metropolitan California communities based on household survey data, and determine required DRT fleet characteristics to meet said travel demand requirements
- An extensible Matsim or activitysim compatible framework for public consumption to evaluate potential of new demand responsive public transit systems.
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