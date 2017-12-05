# Upgrading

Upgrading the Sensu Alpha is usually a straightforward process. In
most cases, upgrading the Alpha only requires upgrading to the latest
package or Docker image. Certain versions of the Alpha may include
changes that are not backwards compatible and require additional steps
be taken when upgrading.

Typically, all that is required is updating your operating system's
package cache (e.g. `sudo apt-get update`), and then following the
[installation instructions](02-installation.md). 

Note: you do not have to add the Sensu Alpha package repositories a 
second time.

## Upgrading to 2.0.0~alpha8

There was a breaking change made to the Environment type in Sensu
2.0.0~alpha8 that will require an offline database migration prior to
starting the upgraded binaries. Please follow these steps:

1. Stop the sensu-backend service

2. Upgrade Sensu

3. Run `sensu-backend start migration` (replace with the full path to
sensu-backend if necessary)

4. Start the sensu-backend service

## Upgrading to 2.0.0~alpha7

After upgrading to `2.0.0~alpha7-1`, users will have to
re-authenticate to the Sensu Backend API. To re-authenticate, users
must run `sensuctl configure` and follow the prompts on their
workstations.

## Help

During the Alpha, you can contact Sensu for support requests, to
report bugs, or to provide feedback by e-mailing sensualpha@sensu.io.
