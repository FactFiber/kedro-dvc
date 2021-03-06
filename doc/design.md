[toc]

# Kedro-dvc Design

Kedro-dvc integration to track and distribute experiments.

## Overview

Kedro creates and maintains machine-learning pipelines. DVC tracks
changes to data together with changes to code in the git repo, and
allows experiment tracking via git commits.

We would like to use dvc experiment tracking to track workflows
generated by kedro. As Kedro, unlike dvc, is not language neutral, we
can extend dvc's sensitivity to data changes to code changes as well.
Kedro-dvc traces what code is run during pipeline execution. When
rerunning an experiment we use this information to invalidate steps when
code changes.

Kedro is able to to generate distributed pipelines using templates, for
instance, to run on kubernetes via argo. Kedro-dvc will work well
together with experiments run in Kubernetes. It will pull together
artifacts run by distributed code into a dvc repo, allowing experiments whose runs are distributed to be tracked, compared, and rerun according
to changes in data, code and parameters.

## Goals:

* Generate .dvc files to track artifacts from kedro inputs & outputs
* Generate dvc pipelines from kedro workflows
* Use dvc experiment tracking on kedro workflows
* Invalidate steps based on both data and code change
* Distribute dvc experiments to kubernetes

## Resources

* [kedro discussion with some links](https://github.com/kedro-org/kedro/discussions/837)
* [dvc discussion](https://discord.com/channels/485586884165107732/938821298929430548/939175277228072970)

* kedro folks most interested in using dvc in conjunction with trace
  to decide what parts of pipeline to rerun.
* dvc @dberenbaum: notes no api yet, but "...the internals are fairly easy to interact with if you want to give it a try using dvc.repo.Repo"

## Design & Roadmap

The implementation roadmap consists of 4 stages. I have moved the details to the discussion boards. Please chime in!

### [Stage 1: setup correspondence between kedro and dvc](https://github.com/FactFiber/kedro-dvc/discussions/6)

### [Stage 2: Code-aware experiments](https://github.com/FactFiber/kedro-dvc/discussions/7)

### [Stage 3: Distributed experiments (Kubernetes)](https://github.com/FactFiber/kedro-dvc/discussions/7)

