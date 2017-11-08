# Upgrading

Upgrading the Sensu Alpha is usually a straightforward process. In
most cases, upgrading the Alpha only requires upgrading to the latest
package or Docker image. Certain versions of the Alpha may include
changes that are not backwards compatible and require additional steps
be taken when upgrading.

## Upgrading to 2.0.0~alpha7

After upgrading to `2.0.0~alpha7-1`, users will have to
re-authenticate to the Sensu Backend API. To re-authenticate, users
must run `sensuctl configure` on their workstations.

## Help

During the Alpha, you can contact Sensu for support requests, to
report bugs, or to provide feedback by e-mailing sensualpha@sensu.io.
