# sensualpha
Sensu 2.0 Alpha Documentation and Examples

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
2. [Installation](02-installation.md) - Installing and Configuring Sensu 2.0
3. [CLI](03-sensuctl.md) An overview of the Sensu CLI utility - sensuctl
4. [RBAC](04-rbac-multitenancy.md) - An overview of Sensu RBAC and Multitenancy
5. [Users](05-users-and-roles.md) - Creating and managing users and roles
6. [Checks](06-checks-and-assets.md) - Creating and managing checks and assets
7. [Getting Help](99-getting-help.md) - How to get help with Sensu 2.0
