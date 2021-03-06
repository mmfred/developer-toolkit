---
layout: page
title: "Roadmap"
permalink: /roadmap/
---

## Introduction

Welcome to the Developer Toolkit project! This is a community driven effort, sponsored by New Relic, to advance the practice of Observability as Code within our industry and developer community. This documentation will
define the initial problem space, identify who is impacted and provide a
roadmap for our success.

### Get Involved!
Whether you want to contribute code, have a great idea, or just notice a tpyo, we want to make it possible to share your thoughts and feedback. There are a number of ways we can work together. 
* [Roadmap RFC](https://discuss.newrelic.com/t/rfc-developer-toolkit-roadmap-2020/90528) -
  We have established a discussion board, as part of our
  [Request for Comments](https://en.wikipedia.org/wiki/Request_for_Comments) process
  for driving this roadmap.
* [Discussion Forum](https://discuss.newrelic.com/c/build-on-new-relic/developer-toolkit) -
  Ask questions about tools within the Developer Toolkit, or help answer
  questions from feloow community members.
* [Issues](https://github.com/newrelic/developer-toolkit/issues) - The
  easiest way to get involved is to identify a need, and report it as an issue
  on this GitHub repo.
* [Pull Requests](https://github.com/newrelic/developer-toolkit/pulls) - Want
  to directly contribute? Open a PR to add some documentation, fix a grammatical
  error, or add a feature to the backlog. Community review of PRs in-flight are
  also more than welcome!


## Overview

The Developer Toolkit is a set of tools that simplify New Relic configuration
and management, accelerating the ability for developers to implement DevOps best
practices. We've started by building around common open source tools and
frameworks such as Terraform and CloudFormation, to simplify integrating
observability into automation workflows. As a developer, you have complete
control through the New Relic Client.


## Personas

**Software Engineer** - A software engineer is someone who is writing,
deploying, and managing the lifecycle of any software stack that utilizes New
Relic. As the owner of the application, they are responsible for managing all
Alerts, Dashboards, Nerdpacks, and other New Relic resources specific to their
application.

**Site Reliability Engineer** - A Site Reliability Engineer (SRE) is an
individual who is responsible for the stability of the entire software stack.
They assist Software Engineers with proper New Relic configuration, and provide
overall guidance across teams.  Working with multiple teams becomes difficult
when they do not operate in a similar way, so SREs strive to develop easy to
follow standards.

**Security Engineer** - A Security Engineer is someone responsible for auditing
and verifying compliance of their software. In order to facilitate this, New Relic
has been made a requirement for all services, and as such needs specific tagging
and configuration across all assets. When faced with any reasonable sized
organization this becomes a daunting task.


## Job Stories

**Observability As Code Providers**

* When I deploy a service, I want to embed the New Relic configuration in code with the rest of the service definition
* When I audit our systems, I want an easy way to verify the New Relic configuration is defined as expected

**New Relic CLI**

* When I deploy an application, I want to record the deployment in New Relic without having to learn how their API works
* When service ownership changes, I want an easily automated way to change tags within New Relic

**New Relic Client**

* When I have custom tooling in place that I want to leverage New Relic, I want to be able to use a supported library
* When I build a deployment pipeline using serverless functions, I want to include New Relic



## Developer Toolkit v1

To solve for the above problems, the initial version of the Developer Toolkit
will contain the following resources.  All resources shall be built as Open
Source projects, and actively engage with the broader community.

* **[New Relic Terraform Provider](https://github.com/terraform-providers/terraform-provider-newrelic/)**
  - The New Relic Terraform Provider enables Observability as Code, reduces
  developer toil, and allows users to manage their entire ecosystem in a single
  place.

   * Built on the New Relic Client
   * Full implementation of APIs available through the New Relic Client
   <br/>

* **[New Relic Client](https://github.com/newrelic/newrelic-client-go)** - The New Relic Client provides the building blocks for
  many tools in the toolkit, enabling quick access to the suite of New Relic
  APIs.  As a library, it can also be leveraged within your own custom
  applications.

   * Full support for the following New Relic API endpoints:
     * GraphQL
     * APM REST v2 API
     * Infrastructure API
     * Synthetics API
   <br/>

* **[New Relic CLI](https://github.com/newrelic/newrelic-cli)** - The New Relic CLI enables integration of New Relic into
  your existing workflows. Be it fetching data from your laptop while
  troubleshooting an issue, or adding New Relic into your CI/CD pipeline.

   * Build on the New Relic Client
   * Initial implementation of
     * Deployment Markers
     * Tagging
   <br/>

* **[New Relic AWS CloudFormation Integration](https://github.com/newrelic/cloudformation-partner-integration)**
  - The AWS CloudFormation Integration enables developers using CloudFormation
  to easily provision a subset of New Relic resources.

   * Build on the NR Client
   * Initial implementation of
     * Basic NRQL Alert configuration
   <br/>


## Milestones

Ongoing work will be tracked in the [Developer Toolkit](https://github.com/orgs/newrelic/projects/6)
project, which contains overview and details status for each individual tool that is in flight.  Here is
the latest summary for planned work by the New Relic team:


### 2020 Apr-Jun

Following on the release of the Developer Toolkit v1, the focus is on
improving ease of adoption and increasing the depth of coverage for the tools.

| State | Tool | Milestone | Rationale |
| ----- | ---- | --------- | --------- |
| Completed | New Relic CLI | Streamlined Installation | Enabling easy installation and upgrades of the NR CLI in existing workflows provides a streamlined experience for the user.  This should include installation through well-known package managers for supported platforms, so maintenance of the CLI fits into existing user practices. |
| Completed | New Relic CLI | Plugin Architecture | The CLI is intended to provide a single entry point into automation and scripting of New Relic. Adding support for a plugin architecture allows for additional teams to easily work on adding new features to the CLI. This is most notable for managing the Nerdpack lifecycle. Transition plan for migration of users should also come out of this. |
| **Current** | New Relic Kubernetes Operator | Initial Support k8s | Kubernetes has become the defacto standard for containerized services. Custom operators allow configuration of third-party services within the the kubernetes so your monitoring definition is tightly coupled to the deployment, simplifying overall configuration. |
| Proposed | New Relic Terraform Provider | 2.0 Beta | In order to start migrating more usage from the legacy REST APIs to NerdGraph, there are a few breaking changes that need to happen.  This will lay all the groundwork for a 2.0.0-beta release that changes some basic requirements for the provider, and enables back-end migration to the new API platform. |
| Proposed | New Relic Client | Initial Code Gen | As the number of orchestration tools increases, and the depth of the API coverage expands through the migration to GraphQL, we must reduce the amount of manual work to stay up to date.  Following existing patterns, research creation of a code generation project to ensure consistency between tools, and decrease time to delivery of new features. |
| Proposed | New Relic CLI | New Relic Logs Support | Integration of New Relic Logs into the NR CLI extends the user experience of New Relic's logging solution into the terminal. |

### 2020 Jul-Sep

Work towards increasing effeciencies in how the team operates, and drive
consistency in the tools that are being delivered. This area is a bit more
ambiguous, and priorities / order is yet to be confirmed.

| State | Tool | Milestone | Rationale |
| ----- | ---- | --------- | --------- |
| Proposed | New Relic CLI | Plugin Service | In order to have a first-class plugin experience, we need to have a curated way to provide plugins to end-users in an automated way. Creating the pipeline for delivering plugins is a critical component in this initiative. |
| Proposed | New Relic CLI | NR1 Plugin | In the effort to consolidate command line interfaces into a consistent and easy user experience, we will initially adopt the current nr1 CLI as a plugin. |
| Proposed | Automated Actions | Initial work | Working with automation service providers, the New Relic Client should become a first class application that can be consumed by the community. |
| Proposed | New Relic CLI | Lambda Support | For community members already leveraging Serverless for their workflows, enabling the New Relic Client to be deployed in this way creates a quick path to embed New Relic along side their existing best practices. |

### Backlog

The following items are possible future work that has not yet been committed or
scheduled. This list is for the consideration of the community to assist in
prioritizing, adding to, or removing from scope.

| State | Tool | Milestone | Rationale |
| ----- | ---- | --------- | --------- |
| Proposed | CloudFormation | Feature Parity | As users adopt the CloudFormation partner integration, increase the API coverage to reach feature parity with the other orchestration tooling. |
| Proposed | Developer Toolkit | Initial IDE Plugin | Building a plugin for commonly used IDEs enables users to move faster, utilizing the environment that they are already accustomed to. Initial work is to-be-defined, but should include items such as syntax highlighting for the New Relic Terraform Provider and/or CloudFormation Integration |
| Proposed | New Relic Client | Insights | Migrate the [go-insights](https://github.com/newrelic/go-insights) package into the New Relic Client |

### Sustaining

The folowing items are ongoing, and while generally handled by our hero
rotation, can occasionally be pulled up into a Milestone the entire team
focuses on.

| State | Tool | Milestone | Rationale |
| ----- | ---- | --------- | --------- |
| Sustaining | Developer Toolkit Docs | Curate Community Docs / Examples | As a community focused project, it is important that we work with the extended community to provide documentation and example workflows. Engaging in this way will drive innovation and ease onboarding for those new to the space. |
