---
title: Example Responsible Computing Plan
teaching: 0
exercises: 0
---

::::::::::::::::::::::::::::::::::::: objectives

- Provide a concrete example of an HPC responsible computing plan

::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::: questions

- What could a responsible computing plan for a research project using HPC look like

::::::::::::::::::::::::::::::::::::::::::::::::

# Project overview

This project uses DFT calculations to understand how physical properties
of a crystalline compound that is a candidate for novel solar panel
technology change with temperature and pressure. Many DFT (parallel)
calculations need run to sample the structure of the compound at
different temperatures and pressures to explore phase space.

# Responsible Computing Plan

## Positive environmental impact statement

This project will help develop new solar panel materials that require
less use of rare earth metals and use more sustainable materials
reducing the environmental impact of mining activities (both in terms of
resource use and in terms of clean water use). The resulting materials,
if viable, should be cheaper to produce and have a longer lifetime
accelerating the uptake of solar power. As described in the plan below,
we will run the research project in a sustainable way demonstrating how
such projects can be undertaken in a way that delivers the research
goals in a way that minimises GHG emissions. We will make sure that
discussion of this approach is highlighted in all research outputs from
the project demonstrating leadership and championing this approach in
our research community.

# Project approach

## Responsive plan

This plan will be reviewed at quarterly intervals throughout the project
to ensure it is being followed by project members and to update the
approach in light of project evolution.

## Preparation and resource selection

We will use a quick, lower-resolution methods to sketch out phase space
for the compound and then select the minimum number of points to run
high resolution calculations to capture the regions of interest with the
minimal resource use. Unfortunately, pre-existing datasets of
calculations on this compound do not exist but we will use known
experimental structures from crystallographic databases as starting
structures where possible to reduce the number of iterations required to
optimise structures.

## Running the calculations responsibly

All calculation methods will be benchmarked on a small number of
iterations to select the minimum number of cores/GPUs needed to run the
calculations and give results in a reasonable timeframe. The high
accuracy methods will be tested on a single point to ensure they produce
valid results before the full campaign of calculations are launched --
if problems are found, the method will be refined and re-benchmarked. We
will prioritise minimising the job size over time to solution to fit
within the wider research workflow so we are not computing quicker than
results can be analysed. Initial planning suggests that as long as
individual calculations complete within a 2 weeks of submission this
should be fine to complete the project aims.

## Measuring emissions from HPC use

The national HPC facility we plan to use publishes emissions data. We
will use this to calculate the emissions associated with our use of the
facility and convert it to a rate of bands simulated per kgCO2e. This
metric will be evaluated for all testing on this system throughout the
project and used to identify opportunities to become more emissions
efficient. The emissions data will be published as part of all the
research outputs to allow for better estimation of emissions (and
potential improvements) for future projects using similar methods.

## Data management

Each coarse-level calculation produces large (approx. 10 GB)
wavefunction files that can be used to restart calculations if needed in
addition to standard log output. From the initial coarse phase space
survey these wavefunction files will be compressed and kept for the
lifetime of the project to allow fine-grained calculations to be run
efficiently from these starting points. They will be deleted once the
research outputs from the project have been produced -- they will be
kept for this long to ensure reviewer comments can be addressed
efficiently with additional calculations if needed. The fine-grained
calculations produce larger wavefunction files (approx. 50 GB). We have
produced a list of all properties that need to be calculated from each
fine-grained calculation to try and ensure that calculations do not need
to be re-run. All the wavefunction files from the fine-grained
calculations will be compressed and stored in the same way as for the
lower-resolution calculations and deleted once they are no longer
possibly needed. All data will be stored in a single, shared location
with a clear labelling scheme so all project members can access them as
needed.

## Project finalisation

We will make the datasets (including calculation input and output files)
public via the Materials Cloud (materialscloud.org) using the ODC-by
licence to enable their re-use for follow-on research. Once research
output production has been finalised, we will delete the compressed
wavefunction files that are no longer needed. Repositories containing
analysis scripts and tools will be archived (e.g. to Zenodo) and made
public with an MIT licence. All outputs resulting from the work will
reference the public datasets and analysis repositories.

:::::::::::::::::::::::::::::::::::::: keypoints

- This demonstrates what a responsible computing plan could look like

::::::::::::::::::::::::::::::::::::::::::::::::