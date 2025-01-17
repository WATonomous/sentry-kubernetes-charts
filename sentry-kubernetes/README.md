# sentry-kubernetes

[sentry-kubernetes](https://github.com/getsentry/sentry-kubernetes) is a utility that pushes Kubernetes events to [Sentry](https://sentry.io).

# Installation:

```console
$ helm install sentry/sentry-kubernetes --name my-release --set sentry.dsn=<your-dsn>
```

## Configuration

The following table lists the configurable parameters of the sentry-kubernetes chart and their default values.

| Parameter               | Description                                                                                                                 | Default                       |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------- |
| `sentry.dsn`            | Sentry dsn                                                                                                                  | Empty                         |
| `existingSecret`        | Existing secret to read DSN from                                                                                            | Empty                         |
| `sentry.environment`    | Sentry environment                                                                                                          | Empty                         |
| `sentry.release`        | Sentry release                                                                                                              | Empty                         |
| `sentry.logLevel`       | Sentry log level                                                                                                            | Empty                         |
| `image.repository`      | Container image name                                                                                                        | `getsentry/sentry-kubernetes` |
| `image.tag`             | Container image tag                                                                                                         | `latest`                      |
| `rbac.create`           | If `true`, create and use RBAC resources                                                                                    | `true`                        |
| `serviceAccount.name`   | Service account to be used. If not set and serviceAccount.create is `true`, a name is generated using the fullname template | ``                            |
| `serviceAccount.create` | If true, create a new service account                                                                                       | `true`                        |
| `priorityClassName`     | pod priorityClassName                                                                                                       | Empty                         |
| `extraEnv`              | Additional environment variables to be added to the deployment. Can be specified multiple times.                            | `[]`                          |

Each entry in the `extraEnv` array should be a key-value pair, for example:

```yaml
extraEnv:
  - name: LOG_LEVEL
    value: "info"
  - name: DEBUG
    value: "false"
```
