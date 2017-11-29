# Upgrading

Upgrading the Sensu Alpha is usually a straightforward process. In
most cases, upgrading the Alpha only requires upgrading to the latest
package or Docker image. Certain versions of the Alpha may include
changes that are not backwards compatible and require additional steps
be taken when upgrading.

## Upgrading to 2.0.0~alpha8

There was a breaking change made to the Environmet type in Sensu
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
