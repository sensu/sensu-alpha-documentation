# Agent

## API
The Sensu agent api default host/port configuration is 127.0.0.1:3031.

### Healthz

The agent's /healthz endpoint serves as an indicator of the agent's liveness and
connectivity to a Sensu backend. A query to /healthz on a healthy agent will
return an 'OK' and a 200 status. If the agent is not able to communicate with
the backend, it will return a Service Unavailable status. The healthz endpoint
can be used to configure an http liveness probe in Kubernetes. 

