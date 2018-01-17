# Agent

## API
The Sensu agent api default host/port configuration is 127.0.0.1:3031.

### Healthz

The agent's /healthz endpoint serves as an indicator of the agent's liveness and
connectivity to a Sensu backend. A query to /healthz on a healthy agent will
return an 'OK' and a 200 status. If the agent is not able to communicate with
the backend, it will return a Service Unavailable status. The healthz endpoint
can be used to configure an http liveness probe in Kubernetes. 

## Logging Redaction

Due to the possible sensitive nature of the agent attributes (e.g. API keys),
the agent automatically redact certain attributes values when logging and
sending entitity keepalives. By default, the following attributes are redacted:

`password`, `passwd`, `pass`, `api_key`, `api_token`, `access_key`,
`secret_key`, `private_key`, `secret`.

The default values can be overwritten using the `--redact` flag to
`sensu-agent`:

```
sensu-agent start --redact password,ec2_access_key,ec2_secret_key
```

**NOTE**: When using this flag, the default values will be overwritten,
requiring them to be re-added to your array.