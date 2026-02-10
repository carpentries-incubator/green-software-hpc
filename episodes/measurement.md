---
title: Measurement
teaching: 40
exercises: 20
---

::::::::::::::::::::::::::::::::::::::: objectives

- Understand how emissions are classified in the widely-used GHG protocol.
- Know which GHG protocol classifications are relevant to use of HPC systems.
- Learn a methodology to use GHG protocol to estimate the emissions associated with our use of HPC systems.
- Understand how emission rates from HPC can be calculated.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How are emissions measured and classified under the GHG protocol?
- How do I use the GHG protocol to estimate emissions from my use of HPC?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Introduction

The Greenhouse Gas (GHG) protocol is the most commonly-used method for organisations to measure their total carbon emissions. Understanding GHG scopes and how to measure your software against industry standards will help you see to what extent you are reducing carbon emissions and how that fits with wider activities to reduce emissions.

To complement the GHG protocol, and if you develop software that is used by others, you can also use the Software Carbon Intensity (SCI) specification. While the GHG is a more generic measurement suitable for all types of organisations, the SCI is specifically for measuring a rate of software emissions and designed to incentivise the elimination of those emissions.

## The GHG protocol

The [Greenhouse Gas protocol](https://ghgprotocol.org) is the most widely used and internationally recognized greenhouse gas accounting standard. [92%](https://ghgprotocol.org/about-us) of Fortune 500 companies use the GHG protocol when calculating and disclosing their carbon emissions and it provides the basis of emissions reporting for most countries (including the UK). Using the GHG protocol allows us to compare our emissions from use of HPC systems to other sources of emissions in a quantitative way.

The GHG protocol divides emissions into three scopes:

- **Scope 1**: Direct emissions from **operations** owned or controlled by the reporting organisation, such as on-site fuel combustion or fleet vehicles.
- **Scope 2**: Indirect emissions related to **emission generation of purchased energy**, such as heat and electricity.
- **Scope 3**: Other indirect emissions from all the other activities you are engaged in. Scope 3 emissions are typically split into two further categories: *upstream emissions* and *downstream emissions*:
   + **Upstream scope 3 emissions**: Includes all emissions from an organisation's supply chain, e.g. emissions from manufacturing and shipping a product
   + **Downstream scope 3 emissions**: Emissions resulting from the use of a product, e.g. the electricity customers may consume when using your product or waste output from the product

Scope 3, sometimes referred to as value chain emissions, is often the most significant source of emissions and the most complex to calculate for many organisations. These encompass the full range of activities needed to create a product or service, from conception to distribution. In the case of a laptop, for example, every raw material used in its production emits carbon when being extracted and processed (part of the upstream scope 3 emissions). Value chain emissions also include emissions from the use of the laptop, meaning the emissions from the energy used to power the laptop after it has been sold to a customer (part of downstream scope 3 emissions).

Through this approach, it's theoretically possible to sum up all the GHG emissions from every organisation and person in the world and reach a global total.

### What scope does my application fall into?

We have already seen how the GHG protocol asks us to bucket emissions from HPC system use according to scopes 1-3. But how do we actually do this?

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise: What scope for HPC emissions?

Throughout this lesson we have spoken about emissions from two different sources associated with our use of HPC: emissions from the electricity used to run our models/simulations on HPC systems and embodied emissions from the HPC system hardware. Given the definitions of scope 1-3 emissions given above, which scopes do you think these two different sources of HPC system use emissions fall into?

:::::::::::::::  solution

## Solution

- Emissions from electricity used: these would be classified as scope 2 emissions
- Embodied emissions from HPC system hardware: these would be classified as upstream scope 3 emissions

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::  callout

## HPC electricity: Scope 2 or Downstream Scope 3?

Whether the emissions from electricity use on HPC systems are downstream scope 3 or scope 2 really depends on who is computing the emissions and for what purpose. From the viewpoint of the hardware vendor who sells and manufactures the HPC system, the electricity use falls into downstream scope 3 emissions but for operators and users of the HPC system they would classified as scope 2 emissions. As we are approaching this subject as buyers, operators and users of HPC systems we will always classify the emissions from our electricity use on HPC systems as scope 2.

::::::::::::::::::::::::::::::::::::::::::::::::::


## How to calculate your HPC emissions


Quantifying the emissions from your work (and generating an emissions rate, as described below) are critical steps on the path to reducing and potentially eliminating emissions from your use of HPC systems. The formula for calculating your emissions from use of HPC systems (`HPC-E`) is straightforward:

```
HPC-E = (E * CI) + M
```

- `E` = Energy consumed by HPC use (in kWh)
- `CI` = Location-based carbon intensity (in kgCO<sub>2</sub>e/kWh)
- `M` = Embodied emissions (in kgCO<sub>2</sub>e)

You can calculate this on a per job basis or for a larger grouping of HPC use - even for a full lifetime of an HPC service.

:::::::::::::::::::::::::::::::::::::::: callout

## Include failed jobs and jobs that did not produce useful output

While it can be tempting to only include the use of HPC that produced useful output in our emissions calculations, this should be avoided. The true amount of emissions includes **all** of our HPC system use to get us to the results we use and so failed jobs (due to errors) or calculations that did not produce useful output must be included. On the positive side, one of the ways we can reduce our emissions from use of HPC systems is to be more careful and eliminate emissions arising from these types of non-productive jobs.

::::::::::::::::::::::::::::::::::::::::::::::::::

Instead of bucketing the carbon emissions of HPC use into scopes 1-3, this calculation buckets them into **operational emissions** (carbon emissions from the electricity required for your HPC use, represented by `E * CI`) and **embodied emissions** (carbon emissions from the physical HPC system components, represented by `M`).

Follow these steps to calculate your HPC emissions. 

1. Gather your energy use - this can be measured or estimated and is often a combination of measured and estimated data
2. Determine the carbon intensity at the location of the HPC system you are using
3. Determine the embodied emissions associated with your use of HPC
4. Compute your total HPC emissions

### 1. Gather energy use

Many HPC systems now provide energy use data for jobs run on the system. If this is the case, you can use these as the starting point for calculating your energy use of HPC resources. If this is not available, then you may need to estimate the energy use of your use of resources from component power draw. Even if you have energy use data available this may only cover energy use of compute nodes (or even processors on compute nodes) so you do typically have to do some estimation of power draw of other components to know how much extra energy to add on to include them in your calculation.

If you are really lucky, the HPC system staff will have done this calculation for you. This has been done for the UK National Supercomputing Service, ARCHER2: [Estimating emissions from ARCHER2](https://docs.archer2.ac.uk/user-guide/energy/#scope-2-emissions).

We will cover two different ways to estimate the power draw of HPC systems which can then be used to compute energy use.

a. Use the total power draw of the system
b. Use the per-component power draw of the system

:::::::::::::::::::::::::::::::::::::::: callout

## Heterogeneous systems

The methodologies outlined below all assume the compute nodes are homogeneous. What do you do if this is not the case and some nodes on the system have GPUs and others do not, for example? In this case, you should try, as much as possible, to treat each homogeneous partition as its own smaller HPC system to help calculate energy use.

::::::::::::::::::::::::::::::::::::::::::::::::::

#### a. Using total power draw

One of the simplest ways to estimate your energy use is to use the total power draw of the HPC system and divide it by the number of components to get a mean power draw per component that can be used to estimate energy use. For example, if the total power draw of the system is 250 kW and it contains 512 GPUs, then the mean power draw per GPU is `250 kW / 512 GPU = 0.488 kW/GPU`. This, in turn, means the energy used for 12 hours use of 2 GPUs is estimated by `12 hours * 2 GPU * 0.488 kW/GPU = 11.7 kWh`.

You should use the component that you measure resource use in to compute the mean power draw. For example, if your usage is measured in GPUh, then compute the power draw per GPU; if your usage is measured in nodeh, compute the power draw per node.

#### b. Using per-component power draws

This approach requires more detailed information being available on the power draw of different components through measurement or from information from the vendors of the components. If you are getting your energy use from counters on the compute nodes (as is sometimes possible on HPC systems) then this approach allows you to estimate additional energy overheads that need to be added on in addition to the measured power draw.

We illustrate this approach using the estimates for the ARCHER2 HPC system:

| Component | Count | Loaded power draw per unit (kW)| Loaded power draw (kW) | % Total | Notes |
|---|--:|--:|--:|--:|---|
| Compute nodes | 5,860 nodes | 0.41 | 2,400 | 85% | Measured by on system counters |
| Interconnect switches | 768 switches | 0.24 | 240 | 9% | Measured by on system counters |
| Lustre storage | 5 file systems | 8 | 40 | 1% | Estimate from vendor |
| NFS storage | 4 file systems | 8 | 32 | 1% | Estimate from vendor |
| Coolant distribution units | 6 CDU | 16 | 96 | 3% | Estimate from vendor |
| Total | | | 2,808 | 99% | |

In this case, we have a mix of data measured on the system (power draw of the compute nodes and power draw of the interconnect switches) and estimates from the vendor (storage systems and CDU). Here, the total power draw is estimated at 2,808 kW, there are 5,860 compute nodes and the unit of resource is nodeh so we can calculate the mean per node power draw (including all the components in the table) in the same way as we did for method (a) with `2,808 kW / 5,860 nodes = 0.480 kW/node` and use this to compute energy consumption based on how many nodeh we use.

However, on ARCHER2 we also have the total compute node energy use available per job to users from the Slurm scheduler. The table above shows that the compute nodes contribute around 85% of the total power draw of ARCHER2 (of the components included) so an alternative method to compute the energy use is to use the measurement from the scheduler and add an additional 18% to cover the energy used by other components. This is, in fact, the methodology used for computing per job energy use on ARCHER2.

#### Add in energy from plant overheads

As well as the energy used by the system itself, there is also the energy used by the plant that supplies power and cooling to the HPC system. Different data centres have different sizes of overheads and this is given by PUE (power use efficiency) which we met earlier in an earlier episode. For example, a PUE of 1.25 indicates that an additional 25% energy use is added on top of the system energy use to account for the plant. 

The PUE will vary with outside weather conditions at the data centre. For the ARCHER2 example, PUE is typically less than 10% so, as a conservative estimate, they add an additional 10% energy use to the total to account for plant overheads. 

So, for the ARCHER2 example, the process for computing your total energy use becomes:

- Measure total compute node energy use from all jobs run via node counters
- Add 15% extra energy to cover energy use from other components
- Add another 10% energy use on top of this new total to cover plant overheads

### 2. Determine local carbon intensity

Once you have your energy use then you need to convert this to emissions using the carbon intensity for the electricity supply for the HPC system. In most cases, HPC systems are powered by the energy grid and many energy grids provide details on the carbon intensity as a function of time.

As we saw earlier, for the UK, the carbon intensity is dependent on location and time. You can access the values through different web services but one that is commonly used is the [Carbon Intensity API](https://carbonintensity.org.uk). Carbon intensity is reported for every region every 30 minute interval. To estimate your emissions you can either use the fine-grained intensity matched to the run times of your HPC system use or use an aggregate value over a longer period. The aggregate value is a simpler choice for a first estimate. The table below shows the approximate average carbon intensities for the different regions of the UK national grid for 2024 ordered from lowest to highest.

| Type | Regions | Carbon Intensity (gCO<sub>2</sub>e/kWh) |
|--|------|------:|
| Low | N. Scotland, S. Scotland, N.E. England, N.W. England | 22 - 48 |
| Low Medium | N. Wales | 77 |
| Medium | E. England, London, W. Midlands, S.E. England, Yorkshire | 108 - 135 |
| High Medium | S. England, E. Midlands | 186 - 203 |
| High | S.W. England, S. Wales, | 242 - 255 |

### 3. Determine embodied emissions

:::::::::::::::::::::::::::::::::::::::: callout

## Upstream Scope 3 emissions

Remember that we are considering only *upstream* scope 3 emissions here. The emissions from electricity
use are captured in the scope 2 emissions estimates.

::::::::::::::::::::::::::::::::::::::::::::::::::

Calculating the embodied emissions can be more difficult than the operational emissions from energy 
consumption as it can be more difficult to get information on embodied emissions associated with HPC system hardware. You may, of course, be lucky and the HPC system you are using could already provide estimates of the 
embodied emissions which you can use!

If you need to estimate this yourself, the major contributors to embodied emissions are likely to be:

- Compute nodes
- Interconnect switches
- Storage

so these are the best place to start. Bear in mind that each HPC system is different so other components
may need to be taken into account. As a rule of thumb, you should look at the HPC system to see which
components there are lots of and use that as the starting place. Complex components (such as nodes, storage
and switches) are likely to have much higher embodied emissions than simpler components (pumps, fans, cables etc.).

As an example, here is how the embodied emissions for ARCHER2 have been estimated:

| Component | Count | Estimated kgCO<sub>2</sub>e per unit | Estimated kgCO<sub>2</sub>e | % Total Scope 3 | References |
|---|--:|--:|--:|--:|---|
| Compute nodes | 5,860 nodes | 1,100 | 6,400,000 | 84% | (1) |
| Interconnect switches | 768 switches | 280 | 150,000 | 2% | (2) |
| Lustre HDD | 19,759,200 GB | 0.02 | 400,000 | 6% | (3) |
| Lustre SSD | 1,900,800 GB | 0.16 | 300,000 | 4% | (3) |
| NFS HDD | 3,240,000 GB | 0.02 | 70,000 | 1% | (3) |
| Total | | | 7,320,000 | 100% | |

References:

1. [IRISCAST Final Report](https://doi.org/10.5281/zenodo.7692451)
2. Estimate taken from IBM z16(TM) multi frame 24-port Ethernet Switch Product Carbon Footprint
3. [Tannu and Nair, 2023](https://arxiv.org/abs/2207.10793)

Note that there is a large amount of uncertainty for scope 3 emissions due to lack of high quality embodied
emissions data. The number used for the compute node emissions is at the high end of estimated values for a
CPU-only compute node and the actual value could be as much as 15% lower at around 900 kgCO<sub>2</sub>e/node.
If the lower value is used, it reduces the overall estimated embodied emissions but does not significantly
change the fraction of emissions attributed to the compute nodes.

:::::::::::::::::::::::::::::::::::::::: callout

## Other embodied emissions sources

We have not included embodied emissions associated with the data centre buildings and plant in the
analysis above. [The IRISCAST report](https://doi.org/10.5281/zenodo.7692450) provides
an evaluation of these values. While the total embodied emissions can be high for these items, their
long lifespan means that their contribution to the embodied emissions during the lifespan of a particular
HPC system are generally much less significant than the embodied emissions from the HPC system hardware
itself.

::::::::::::::::::::::::::::::::::::::::::::::::::


### 4. Compute your total HPC emissions

Now we should have all the data we need to compute our total emissions from HPC system use:

- `E` = Energy consumed by HPC use (in kWh)
- `CI` = Location-based carbon intensity (in kgCO<sub>2</sub>e/kWh)
- `M` = Embodied emissions (in kgCO<sub>2</sub>e)

Remember the equation for computing total emissions from HPC system use (`HPC-E`):

```
HPC-E = (E * CI) + M
```

we can plug the numbers in and come up with a value for the total emissions arising from our
use of HPC.

:::::::::::::::::::::::::::::::::::::::: callout

## `E * CI` on a per job basis

Rather than computing total energy use and then using an aggregate value for the carbon intensity, it may
make more sense to compute `E * CI` on a per-job basis using the carbon intensity value at the job time. This is the approach used in the tools available on ARCHER2 for estimating emissions.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise: Computing total emissions from HPC system use

You are using (or running) a GPU-based HPC service and a particular project has used the
following amounts of resource over 3 months

- 1,100 GPUh
- 3,542,000 kWh

The total embodied emissions for the service are 6,500,000 kgCO<sub>2</sub>e, the service lifetime 
is 7 years and there are 1000 compute nodes each with 8 GPUs. The service is hosted in a
location with a carbon intensity of 40 gCO<sub>2</sub>e/kWh.

1. Compute the scope 2 emissions for the project use
2. Compute the scope 3 emissions rate in kgCO<sub>2</sub>e/GPUh
3. Compute the scope 3 emissions for the project use
4. Compute the total emissions for the project use
5. Do scope 2 or scope 3 emissions dominate or are they evenly matched?

:::::::::::::::  solution

## Solution

1. The scope 2 emissions from energy use by the project are given by `E * CI`, the energy used multiplied by the carbon intensity of the electricity supply. In this case, this is given by `3,542,000 kWh x 0.040 kgCO<sub>2</sub>e/kWh = 141,700 kgCO<sub>2</sub>e`.

2. The scope 3 emissions rate per GPUh is the total scope 3 emissions for the service divided by number of GPUh available over the lifetime of the service.
   1. The total GPUh over the service lifetime is estimated by `7 years x 365 days x 24 hours x 1000 nodes x 8 GPU per node = 490,560,000 GPUh`.
   2. The scope 3 emissions rate is given by `6,500,000 kgCO<sub>2</sub>e / 490,560,000 GPUh = 0.013 kgCO<sub>2</sub>e/GPUh`

3. The scope 3 emissions for the project use is the number of GPUh used multiplied by the scope 3 emissions per GPUh: `1,100 GPUh * 0.013 kgCO<sub>2</sub>e/GPUh = 14.3 kgCO<sub>2</sub>e`

4. Total emissions are scope 2 + scope 3 emissions: `141,700 kgCO<sub>2</sub>e + 14.3 kgCO<sub>2</sub>e = 141,714 kgCO<sub>2</sub>e`

5. Scope 2 emissions (from electricity use) heavily dominate the emissions in this example.

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::

## HPC Carbon Intensity (HPC-CI) specification

:::::::::::::::::::::::::::::::::::::::: callout

## Software Carbon Intensity (SCI)

The definition, application and calculation of the HPC-CI is heavily inspired
by the [Software Carbon Intensity (SCI)](https://sci.greensoftware.foundation/)
from the Green Software Foundation.

::::::::::::::::::::::::::::::::::::::::::::::::::

We now describe a methodology (the HPC Carbon Intensity specification, HPC-CI) to calculate your emissions from HPC system use and to encourage action towards eliminating emissions.

It is not a replacement for the GHG protocol, but an additional metric that helps you understand how your HPC system use can be measured in terms of carbon emissions so you can make more informed decisions. While the GHG protocol (or HPC-E) calculates the **total emissions**, the HPC-CI is about calculating the **rate of emissions**. In automotive terms, HPC-CI is more like a miles per gallon measurement and the GHG protocol/HPC-E is more like the total carbon footprint of a car manufacturer and all their cars they produce every year.

An important thing to note is that it is not possible to reduce your HPC-CI rate by purchasing offsets in the form of neutralisations, compensations, or by offsetting electricity in the form of renewable energy credits (we will cover this in more detail in the next section of the workshop). This means that HPC system use that makes no effort toward reducing emissions but spends money on carbon credits cannot reduce the associated HPC-CI rate.

Offsets are an essential component of any climate strategy; however, offsets are not eliminations and therefore are not included in the HPC-CI metric.

If you make your HPC use more **energy efficient**, **hardware efficient**, or **carbon aware**, your HPC-CI rate will decrease. The only way to reduce your rate is to invest time or resources into one of those three principles. As such, adopting the HPC-CI metric for your HPC use, will drive investment into one of the three pillars of green HPC use.

## The HPC-CI equation

The equation to calculate an HPC-CI rate is simple and very closely related to the calculation of total emissions (HPC-E) presented above:

```
HPC-CI = [(E * CI) + M] per R
```

- `E` = Energy consumed by HPC use (in kWh)
- `CI` = Location-based carbon intensity (in kgCO<sub>2</sub>e/kWh)
- `M` = Embodied emissions (in kgCO<sub>2</sub>e)
- `R` = Functional unit (e.g. iterations, simulated time, calculation cycles, research papers published, cost)

This yields an emissions rate in carbon emissions per functional unit (`HPC-E per R`), e.g. kgCO<sub>2</sub>e/iteration.

The steps to calculate your HPC-CI score are the same as calculating your total emissions (HPC-E) described above with additional steps to produce the rate. Steps 1-4 are identical to the HPC-E methodology described above:

1. Gather your energy use
2. Determine the carbon intensity at the location of the HPC system you are using
3. Determine the embodied emissions associated with your use of HPC
4. Compute your total HPC emissions
5. Select your functional unit (`R`)
6. Calculate your HPC-CI rate

### 5. Select your functional unit (`R`)

As we have seen, the HPC-CI is a rate rather than a total and measures the intensity of emissions
according to the chosen functional unit. The specification currently does not prescribe the
functional unit and you are free to pick whichever best describes the output from your use of HPC
systems. For example, this could be a metric from the software you use (ns simulated, number of
years simulated, iterations) or a metric tied to research progress (number of compounds modelled,
data points analysed, papers published). There may also be ideas in literature related to your
work area of what a good choice may be. You may want to trial different functional units to see
which one works best for your work.

As a concrete example, imagine that you are simulating the dynamics of a biomolecular system
(using software such as GROMACS, Amber, or NAMD) then you could well choose the number of ns 
simulated as your functional unit.

You can use multiple functional units simultaneously to have multiple HPC-CI values for
your use of HPC systems. Different HPC-CI units may be more or less useful in different
contexts.

### 6. Calculate HPC-CI rate

Now you have both the total emissions for your use of HPC systems and the number of functional 
units arising from the same use of HPC systems you can calculate the HPC-CI by dividing the 
total emissions by the total number of functional units.

To continue our example of biomolecular simulation that we mentioned above, we would take the
total emissions from our HPC system use - let us say this came out to be 1500 kgCO<sub>2</sub>e -
and the total number of functional units - say 950 ns simulated - and combine them:

```
HPC-CI  = 1500 kgCO<sub>2</sub>e / 950 ns = 1.58 kgCO<sub>2</sub>e/ns
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Exercise: HPC-CI rate 

In the previous exercise we computed the total HPC system emissions for 3 months of project
use to be 14,184 kgCO<sub>2</sub>e. The project was modelling the climate and managed to simulate
3,680 years of Earth's climate during that 3 month period using 1,100 GPUh of resource.

1. What is the HPC-CI in kgCO<sub>2</sub>e per simulated year?
2. What is the HPC-CI in kgCO<sub>2</sub>e per GPUh?

:::::::::::::::  solution

## Solution

1. Given by: `14,184 kgCO<sub>2</sub>e / 3,680 simulated years = 3.85 kgCO<sub>2</sub>e/simulated year`

2. Given by: `14,184 kgCO<sub>2</sub>e / 1,100 GPUh = 12.89 kgCO<sub>2</sub>e/GPUh`

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: callout

## Estimating emissions associated with future use of HPC systems

As well as using the HPC-CI metric as a tool to help quantify and reduce your emissions
from HPC system use it can also be used to project the emissions from HPC system use
from future or planned projects. Many funding bodies are starting to ask for emissions
estimates as part of the submission process. Calculating HPC-CI values can help you to 
provide these estimates.

::::::::::::::::::::::::::::::::::::::::::::::::::

Now we understand how to estimate our emissions (HPC-E) and how to define a useful
metric to understand our emissions rate linked to some concrete output from our use
of HPC systems (HPC-CI). The next section looks at how emissions can be reduced and,
ideally, eliminated.

:::::::::::::::::::::::::::::::::::::::: keypoints

- The GHG protocol is a metric for measuring an organisation's total carbon emissions and is used by organisations all over the world.
- The GHG protocol puts carbon emissions into three scopes. Scope 3, also known as value chain emissions, refers to the emissions from organisations that supply others in a chain. In this way, one organisation's scope 1 and 2 will sum up into another organization's scope 3.
- You can use the GHG protocol to estimate your emissions from HPC system use but it requires access to reasonable quality information from the HPC systems you are using.
- The HPC-CI is a metric designed specifically to calculate emissions from HPC systems and is a rate rather than a total. This can be used to measure improvements in emissions efficiency and drive reductions in emissions.

::::::::::::::::::::::::::::::::::::::::::::::::::
