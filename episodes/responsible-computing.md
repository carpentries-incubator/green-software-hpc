---
title: Responsible Computing Plans
teaching: 40
exercises: 35
---

::::::::::::::::::::::::::::::::::::: objectives

- Understand what a Responsible Computing Plan (RCP) is and why it is needed
- Know how to plan research projects to minimise environmental impact
- Learn how to develop a responsible computing plan for your own research
- Understand how to apply RCP principles throughout the project lifecycle

::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::: questions

- What is a Responsible Computing Plan?
- Why are RCPs needed for research projects?
- How can I develop and use an RCP for my research?

::::::::::::::::::::::::::::::::::::::::::::::::

## What is a Responsible Computing Plan?

A *Responsible Computing Plan (RCP)* is a document that ensures positive environmental impacts are captured and plans the project lifecycle to achieve project goals with minimal negative environmental impact. It is a living document that reacts to changes in the project rather than being prescriptive. 

:::::::::::::::::::::::::::::::::::::  callout

## Not just emissions

While this workshop has focussed on emissions, a responsible computing plan can cover all forms of environmental impact.

::::::::::::::::::::::::::::::::::::::::::::::::

There is often a disconnect between use and awareness of resources used in research computing. The default position is frequently to use more resources to achieve progress rather than think carefully about the most efficient way to achieve results. This is sometimes described as "reaching for the bigger hammer rather than the right tool."

RCPs help address this by:

- Providing the opportunity to think explicitly about the environmental impact of your computing choices
- Encouraging careful planning to minimise resource use and maximise resource efficiency
- Ensuring environmental considerations are built into the way the project is run throughout its lifetime 

We frame responsible computing plans in the context of research projects but, with some thought, they can be adapted for use more widely. 

While they are most impactful if used before a project or activity starts and throughout its lifetime by the whole project team; they can be used at any point in a project or activity lifecycle and by subsets of people or even individuals to bring environmental benefits. 

In this episode, we cover four main aspects of responsible computing plans to give you an idea of how to go about putting one together:

Evaluate positive environmental impacts 
: While we often focus on the negative environmental impacts of projects, it is important to try and evaluate any positive environmental impacts, both qualitative and quantitative.

Plan to minimise impact
: Looking at how we can plan projects and activities to minimise environmental impact, encourage good practice and behaviour and be as efficient as possible while still achieving the project goals.

Run the project responsibly
: While planning is important, following through on the plans and adapting to change as the project evolves is critical to working in an environmentally sustainable way.

Finish the project well
: One of the most challenging aspects of research projects is finishing them up in a way that makes the knowledge and outputs useable in a way that means future work can build on them without incurring unnecessary additional resource use. This is typically associated with ensuring project outputs and products conform to [FAIR principles](https://www.go-fair.org/fair-principles/).

## Evaluate positive environmental impacts

We will look at minimising the negative environmental impacts in the rest of this episode but the first step in developing responsible computing plan is taking some time to evaluate the positive environmental impacts of the work. Ideally, the impacts would be evaluated or estimated quantitatively but this may not always be possible and you may need to include more qualitative statements. You should consider direct, indirect and community/activism impacts.

The aim of the statement is to help justify the environmental cost of the computing resources used by highlighting the environmental benefits the project will deliver.

- Direct impacts: New approaches/technologies, efficiency improvements, understanding/quantifying polycrisis impacts
- Indirect impacts: Fundamental research to enable new approaches/technologies, model improvements
- Community/activism impacts: Adding awareness/skills in environmental issues, demonstrating leadership in environmental sustainability, normalising action

Some examples of direct, indirect and community/activism positive impacts can be found in the table below:

| Direct Impacts | Indirect Impacts | Community/activism impacts |
|:--|:--|:--|
| Developing a new, more efficient wind turbine | Research to understand possible new battery materials | Ensuring that environmental impact is publicly stated in all project outputs |
| Improving/evaluating biodiversity in a habitat | Developing improved climate modelling approaches | Developing training to raise awareness/understanding of environmental issues |
| Enabling reuse of water that would otherwise be wasted | Developing AI approaches that reduce the need for costly simulations | Organising events that normalise action to reduce environmental impacts in your research field |
| Running modelling to support IPCC reports and targets | Developing and using responsible computing plans for your projects | Gaining [GreenDiSC certification](https://www.software.ac.uk/GreenDiSC) for your research group |

:::::::::::::::::::::::::::::::::::::  challenge

## Positive environmental impacts

**Time: 10 minutes**

Choose a project/activity you are (or have been) involved in, or make up a plausible scenario.

1. Write up the project overview in 2-3 sentences
2. Produce 2-3 bullet points that describe how the project could have positive environmental impact. This would ideally include at least one point that could be evaluated quantitatively. Classify the points as *direct*, *indirect* or *community/activism*.

:::::::::::::  solution

## Solution

Your project overview should clearly state what the project/activity aims to achieve. Your positive environmental impacts might include:

- Quantitative measures (e.g., "This project will reduce energy consumption in X process by Y%")
- Qualitative measures (e.g., "This project will enable better understanding of climate patterns")
- Direct impacts (e.g., reduced emissions from the project itself)
- Indirect impacts (e.g., enabling others to reduce their environmental footprint)
- Community/activism impacts (e.g. enabling change and normalising action)

:::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Planning projects

Planning the project with environmental sustainability in mind is typically the time when you can have the largest impact. Planning to run the project in a responsible way almost always makes the project more impactful and robust from a non-environmental standpoint too.

We will look at both compute resource use and data resource use. Which of these is more important for your project/activity depends on the type of work you are doing. For most HPC work, compute resource use will dominate the emissions from the activity but if you use a relatively small amount of compute compared to data resources it could be a different story. You can use the measurement methodologies discussed earlier to try and estimate the relative contribution of compute and data resources to your work.

Finally, we will look at selecting appropriate HPC resources for the project.

### Responsible compute resource use

As we have already seen, *reduction of consumption* is the central tenet of reducing environmental impact. Planning to use minimal compute resources to achieve the project aims is critical. Some high level points to consider: 

- Look for existing datasets that you can use rather than repeating calculations
   - This is not all or nothing – existing data may help you make any use the most impactful use of resources
- Ensure that all planned use will contribute meaningful data points
   - If the project involves sampling, select a sampling distribution that maximises information per point
   - For example, a regular sampling grid at finest resolution is unlikely to be the most efficient use – minimise data points in regions of little change
- When running parallel calculations – using the smallest number of cores/nodes that take a reasonable time is usually the most efficient from an environmental standpoint

We now take a quick look in more detail at two aspects of planning compute resource use:

- The impact of testing before and during a project on environmental impact
- Making sure that environmental sustainability is considered when selecting the methods and approach to use

#### Testing before large-scale use

Test that the proposed methodologies will likely give viable results before embarking on large amounts of resource use:

- Review literature carefully
- Discuss the planned approach with experienced researchers
- Undertake pilot studies before committing to large resource use

You often do not need to run at full scale to test if the selected method is viable – shorter runs, reduced datasets or other reductions can give confidence in the proposed resource consumption estimates.

#### Selecting appropriate methods

Use methods proportionate to the project objectives rather than automatically choosing the most complex/advanced/higher resolution option:

- When planning a project, think carefully about the tools and methods you will use
- Some newer tools are more efficient than older ones, but not always
- Some computationally intensive approaches, including some machine learning methods, may not improve enough on simpler methods to justify their extra cost
- Think about redundancy – are you planning to compute too many datapoints or look at too many similar problems which will not provide substantial new information?
- Build smaller scale benchmarking and testing into the project plan to ensure the correct scale setup is chosen for each step (or when plans change)

:::::::::::::::::::::::::::::::::::::  challenge

## Compute resource planning

For the same project you worked on in the first challenge:

Write brief bullet points covering how you could, from an environmental sustainability viewpoint, plan the project to:

1. Minimise resource use
2. Build testing into the project approach
3. Select appropriate methods and scales

:::::::::::::  solution

## Solution

Your answers might include:

**Minimise resource use:**
- Search for and use existing datasets where possible
- Reduce sampling frequency in regions of little change
- Use the minimum number of compute nodes that give acceptable turnaround time
- Plan to delete intermediate files that are not needed

**Build testing into the project approach:**
- Run pilot studies with reduced datasets
- Test methodology on smaller problems before scaling up
- Schedule regular reviews to assess if resource use is justified
- Benchmark different approaches to find the most efficient

**Select appropriate methods and scales:**
- Choose simpler methods where they are sufficient for the objectives
- Avoid unnecessary high-resolution calculations
- Plan benchmarking to determine optimal resource allocation
- Consider whether machine learning approaches justify their computational cost

:::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

### Responsible data resource use

Many projects already produce data management plans, and these typically align well with responsible resource use. The questions that would be asked are similar to those for a data management plan. For example, questions such as:

- Do we really need to keep all intermediate files for a long period of time?
- Does each collaborator need their own copy of the dataset?
- Can rarely used data be compressed or moved to archival storage throughout the project?
- Have we planned time to review and tidy data during the project?

Additionally, build plans to publish data using a *FAIR approach* throughout the project (more on this in the "Finishing the project" section).

### Selecting HPC resources

Projects often have choices of HPC facility to use for different parts of the project. With environmental sustainability in mind, the choice depends on considerations of the principles we covered earlier in this course: hardware efficiency, energy efficiency and carbon awareness.

Some high level notes:

- Use existing resources where possible – making use of existing resources is usually the most sustainable approach
- Shared resources are often a more sustainable choice - they usually achieve higher utilisation over their lifetimes (though this is not always the case for specialist use cases)

Beyond these very high level considerations, you are looking for facilities that have the lowest emissions per unit of resource used. The following rules can help you do this:

First, select a facility to minimise operational emissions:
  - Use HPC facilities in locations that have the lowest emissions from electricity generation
  - This usually corresponds to them being sited in locations with lowest national grid carbon intensities
  - Can also be that they have direct connections to renewable energy sources
  - In the UK, if connected to the national grid, this typically means HPC resources located as far North as possible

Once you have done this, the next evaluation points depend on the facility providing estimates of where the emissions come from over the facility lifetime:

- If embodied emissions are a significant fraction of lifetime emissions, then you should assume you will use the facility in a way the maximises performance per unit of resource.

- If operational emissions are the dominant factor in the lifetime emissions, then you should assume you will use the facility in a way to maximise the energy efficiency of your use.

Looking at these points for the range of possible HPC facilities available to you should help you to make the most emissions-efficient decision on which HPC facility (or facilities) to use for the project.

:::::::::::::::::::::::::::::::::::::  challenge

## Data and resource planning

For the same project you worked on in previous exercises:

Write brief bullet points covering how you could, from an environmental sustainability viewpoint, plan the project to:

1. Use data resources responsibly (during the project – we will discuss finalising the project later)
2. Select the right (HPC) resource for the project

:::::::::::::  solution

## Solution

**Use data resources responsibly:**
- Plan which intermediate files need to be kept and which can be deleted
- Arrange for shared access to datasets rather than multiple copies
- Identify data that can be compressed or moved to archival storage
- Schedule regular data review points during the project
- Plan to follow FAIR data principles from the start

**Select the right HPC resource:**
- Choose an HPC facility in a location with low carbon intensity (e.g., northern UK)
- Consider whether existing resources can be used before requesting new allocations
- Evaluate whether shared resources would be more sustainable than dedicated resources
- Balance embodied vs operational emissions in facility selection
- Consider the energy efficiency of different hardware options

:::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Running the project

Re-planning is often needed during research projects as objectives might change, new methods may need to be employed, or new data may become available. Principles for responsible computing can be built into a research project throughout its execution.

### Run software carefully

Reducing waste of resources is key to using HPC in a sustainable way. The disconnect between using resources and visible consumption inherent in HPC use (where the resource you are using is remote and not visible to you in an immediate way) makes it easier to waste resources.

Points to consider include many things we have already discussed but must be kept in mind throughout the project:

- Plan testing of software and scripts on a smaller scale before running in ways that can consume large amounts of resource
- Plan to run appropriate benchmarking before committing to large usage to ensure you are using resources efficiently (cores, memory, IO, etc.)
- Smallest number of cores/nodes is almost always the most emissions efficient for parallel calculations – how fast do you really need results?
- Plan to revisit and replan if the research direction changes in terms of software, method, problem size, etc.
- Consider using carbon intensity forecasts to schedule work at a lower-carbon time (if that is possible on the facility you are using)
- Before running work, ensure you are recording enough information to avoid rerunning this work unnecessarily

### Optimise where it matters

Many projects waste time optimising workflows in areas that will make a negligible impact on reducing environmental impact (or even performance) or optimise inefficiently due to lack of specialist support.

- Find the locations where optimisation will likely have the largest impact
    + Remember, you may get a larger impact from running carefully without ever needing to get involved with programming
- Make sure you have some plan to measure the impact of any changes (e.g., using HPC-CI, covered in the Measurement episode)
- Enlist the support of specialists** to analyse and optimise your workflow
    + For example, many institutions have a local Research Software Engineering team who are well placed to help

## Finishing the project

In environmental sustainability terms, planning how a project will be finalised means:

- Ensuring that calculations do not need to be needlessly re-run for outcomes related to the project
- Ensuring that the right data is kept in a useful form
- Deleting data that is no longer needed
- Ensuring work can be re-used effectively in future work

For example, the following points could be considered:

- Which data genuinely need to be retained and what can be deleted?
- Could publishing this data or code reduce duplicated work elsewhere?
- Have I left enough documentation for others to reuse what has been done?

Finishing a project well typically corresponds to applying *FAIR principles**.

### FAIR data principles

The FAIR data principles provide a framework for ensuring data is:

1. **Findable** – Easy to find by both humans and computer systems and based on mandatory description of the metadata that allow the discovery of interesting datasets

2. **Accessible** – Stored for long term such that they can be easily accessed and/or downloaded with well-defined license and access conditions (Open Access when possible), whether at the level of metadata, or at the level of the actual data content

3. **Interoperable** – Ready to be combined with other datasets by humans as well as computer systems

4. **Re-usable** – Ready to be used for future research and to be processed further using computational methods

![FAIR data principles diagram](./fig/FAIR_data_principles.jpg "FAIR data principles: Findable, Accessible, Interoperable, Re-usable")

*Source: [https://www.go-fair.org/how-to-go-fair/](https://www.go-fair.org/how-to-go-fair/)*

By following FAIR principles, you ensure that:
- Your data can be found and used by others (and your future self)
- Work does not need to be duplicated
- The environmental cost of data generation is amortised over maximum reuse
- Research is more impactful and efficient overall

:::::::::::::::::::::::::::::::::::::  challenge

## Finishing the project well


For the same project you worked on in previous exercises:

Write brief bullet points covering how you could, from an environmental sustainability viewpoint, plan to end the project in as good a way as possible.

:::::::::::::  solution

## Solution

Your answers might include:

- Review all data and identify what genuinely needs to be retained vs what can be deleted
- Publish datasets in a recognised repository with appropriate metadata (making them FAIR)
- Publish code with documentation to enable others to build on your work
- Write clear documentation explaining methods and results
- Consider writing up negative results to prevent others repeating the same unsuccessful approaches
- Ensure data is in standard, interoperable formats
- Apply appropriate licenses to enable reuse
- Archive project materials in long-term storage
- Share lessons learned about efficient resource use with the community

:::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::

## Summary: Responsible Computing Plan

A Responsible Computing Plan with an HPC focus should cover:

### Before the project starts
- Write a positive environmental impact statement
- Plan to minimise resource consumption
- Build testing and benchmarking into the project plan
- Select appropriate methods and scales
- Plan responsible data management
- Choose HPC resources based on emissions efficiency

### During the project
- Test at small scale before large runs
- Benchmark to ensure efficient resource use
- Use the minimum resources needed
- Consider carbon intensity when scheduling
- Record enough information to avoid reruns
- Optimise where it will have the most impact
- Seek specialist support when needed

### At the end of the project
- Delete unnecessary data
- Publish data and code following FAIR principles
- Document work for future reuse
- Ensure calculations do not need to be rerun

Remember: an RCP is a living document that should evolve as your project develops, not a prescriptive checklist to be completed once and forgotten.

:::::::::::::::::::::::::::::::::::::: keypoints

- A Responsible Computing Plan (RCP) helps plan research projects to minimise environmental impact while achieving project goals
- RCPs are living documents that should be developed during project planning and updated throughout the project lifecycle
- Key planning considerations include: minimising resource use, building in testing, selecting appropriate methods, and choosing sustainable HPC resources
- During project execution: test at small scale, benchmark, use minimum resources, and consider carbon intensity
- Finishing a project well involves applying FAIR data principles to enable reuse and prevent duplication
- The four main sections of an RCP are: positive environmental impacts, planning, running, and finishing the project

::::::::::::::::::::::::::::::::::::::::::::::::
