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

## CHANGELOG

### Added
- New "event delete" subcommand in sensuctl
- The "Store" interface is now properly documented
- The incoming request body size is now limited to 512 KB
- Silenced entries in the store now have a TTL so they automatically expire
- Initial support for custom attributes in various Sensu objects
- Add "Error" type for capturing pipeline errors
- Add registration events for new agents
- Add a migration tool for the store directly within sensu-backend

### Changed
- Refactoring of the sensu-backend API
- Modified the description for the API URL when configuring sensuctl
- A docker image with the master tag is built for every commit on master branch
- The "latest" docker tag is only pushed once a new release is created

### Fixed
- Fix the "asset update" subcommand in sensuctl
- Fix Go linting in build script
- Fix querying across organizations and environments with sensuctl
- Set a standard redirect policy to sensuctl HTTP client

### Removed
- Removed extraneous GetEnv & GetOrg getter methods
