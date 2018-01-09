# About Sensu Alpha Documentation

Welcome friends :wave:! This repository is intended primarily for
Sensu 2.0 Alpha users to guide them through their initial use. The
Alpha Program is a small, high-touch collaboration with Sensu Inc's
engineering team as they produce a Beta ready for wider use. We
appreciate everyone's patience in this early stage. For regular
updates, [join our Community Slack](http://slack.sensu.io) or [our
mailing
list](http://sensuapp.us6.list-manage.com/subscribe?u=576e632588&id=2e5efd43d8).

If you are not already a Sensu 2.0 Alpha Program participant, visit
[sensuapp.org/alpha](https://sensuapp.org/alpha#apply) to apply!

## Alpha Program Goals

Our hope is that Sensu 2.0 Alpha users will follow along with the documentation
and attempt to experiment with the functionality that we currently have available.
Beyond that, we would love further experimentation with those features you are
particularly interested in. For some examples:

If you have multiple environments, you may like to dig a little deeper into our
[RBAC](04-rbac-multitenancy.md) functionality. Or if you are interested in
distributed checks without configuration management, you might take a closer
look at [Checks and Assets](06-checks-and-assets.md).

We hope that throughout the alpha program we can:

- Test early Sensu 2.0 prereleases in diverse, real world situations.

- Collect feedback from existing and new Sensu users to help ensure we
  are taking Sensu in the right direction.

- Produce experienced Sensu 2.0 prerelease users before the Sensu 2.0
  beta (Q1 of 2018).

## Overview

Sensu 2.0 is a complete rewrite of Sensu in [Go](https://golang.org). It can be
installed via a binary distribution, packages, or used in Docker containers
(see the [installation](02-installation.md) instructions for further details).
There are three components to Sensu 2.0: the sensu-backend, sensu-agent, and
sensuctl programs.

### sensu-backend

The `sensu-backend` program replaces `sensu-server` and `sensu-api`. It will
also replace the `sensu-enterprise-dashboard` or `uchiwa` programs in the future.
It is responsible for the Sensu 2.0 API and Transport.

### sensu-agent

The `sensu-agent` program replaces `sensu-client`.

### sensuctl

The first UI we've implemented for Sensu 2.0 is the CLI `sensuctl`. See the
[CLI](03-sensuctl.md) section for more information.

## More Documentation

1. [What's different?](01-whats-new.md) - What's different in Sensu 2.0?
1. [Installation](02-installation.md) - Installing and Configuring Sensu 2.0
1. [CLI](03-sensuctl.md) An overview of the Sensu CLI utility - sensuctl
1. [RBAC](04-rbac-multitenancy.md) - An overview of Sensu RBAC and Multitenancy
1. [Users](05-users-and-roles.md) - Creating and managing users and roles
1. [Checks](06-checks-and-assets.md) - Creating and managing checks and assets
1. [Events](07-events.md) - An overview of events in Sensu
1. [Hooks](09-hooks.md) - Creating and managing hooks (with checks, mutators, and handlers)
1. [Silencing](10-silencing.md) - An overview of Silencing checks, subscriptions, and entities
1. [Getting Help](99-getting-help.md) - How to get help with Sensu 2.0
1. [Upgrading](98-upgrading.md) - How to upgrade the Sensu Alpha
1. [CHANGELOG](97-changelog.md) - What changed between Sensu Alpha releases
