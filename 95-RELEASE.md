# [2.0.0-alpha.9] - 2017-12-05

## Release Notes

We've received a lot of encouraging and positive feedback from Alpha participants, 
and we hope you'll continue to help us understand how we can make Sensu 2 better. 

It's clear that alpha participants miss some of their favorite Sensu 1.x features, 
so this release focuses on bringing you more what you know and love to Sensu 2.

### Silencing

Entities, subscriptions, and checks can now be silenced via the API or using sensuctl. 
When creating or updating silences, you can specify an optional TTL that indicates when 
the silence will expire. While silenced, handler execution will be prevented for at 
entity, subscription, or check.

Visit our documentation for [more information about silencing](https://github.com/sensu/sensu-alpha-documentation/blob/master/06-checks-and-assets.md#silencing).

### Agent /healthz endpoint

Ask and you shall receive. For those of you using Kubernetes, the sensu-agent process 
now has a /healthz endpoint that indicates that the agent has started and successfully 
authenticated to the backend.

### Event passing to Check STDIN

When creating or updating your checks with sensuctl, you can now pass the --stdin 
argument (or set stdin to yes/true during the interactive questionnaire). Doing so 
will cause the Sensu Agent to pass in the event via STDIN to your check at runtime.

### Manual event creation and resolution

Events can now be manually created and manually via the API or sensuctl. For more 
information on interacting with events in Sensu 2.x, see visit our events documentation.

### Proxy Entities

Proxy entities (formerly know as “proxy clients”) have been added to Sensu 2. Using 
`sensuctl check create`, you can create a check that specifies a `source`, which 
will dynamically create a new entity if it does not already exist while processing a check result.

For more details about this release, including a handful of the things we did 
behind the scenes for upcoming feature work and bug fixes, you can check out our [changelog](97-CHANGELOG.md).

# [2.0.0-alpha.8] - 2017-11-28

This release of Sensu 2.0 includes a number of bug fixes and changes
to support Sensu 1.x features.

## Release Notes

### Upgrading

There was a breaking change made to the Environmet type in Sensu
2.0.0~alpha8 that will require an offline database migration prior to
starting the upgraded binaries. Please follow these steps:

1. Stop the sensu-backend service

2. Upgrade Sensu

3. Run `sensu-backend start migration` (replace with the full path to
sensu-backend if necessary)

4. Start the sensu-backend service

### New Features

#### Agent Registration Events

Agent registration events have been added to Sensu 2.x. Using
`sensuctl`, you can create a handler named `registration` in your
environments that will be executed whenever a new Agent Entity is
registered in Sensu.

#### 1.x Feature Parity Progress

- The backend now has support for Silences via the /silenced API endpoint. We have a pull request open to add support to `sensuctl` that should be in the next release.
- We've implemented a mechanism for supporting Extended Attributes (arbitrary key/values in your Check config and Entity objects) and are in the process of adding support for configuring those via the API/CLI.
- Filters have been implemented, but are as of yet undocumented. We'll
- be "releasing" them next week along with documentation.
