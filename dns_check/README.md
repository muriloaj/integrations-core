# DNS Integration

## Overview

Monitor the resolvability of and lookup times for any DNS records using nameservers of your choosing.

## Setup
### Installation

The DNS check is packaged with the Agent, so simply [install the Agent][1] on any host from which you want to probe your DNS servers. Though many metrics-oriented checks are best run on the same host(s) as the monitored service, you may want to run this status-oriented check from hosts that do not run the monitored DNS services.

### Configuration

Create a file `dns_check.yaml` in the Agent's `conf.d` directory. See the [sample dns_check.yaml][2] for all available configuration options:

```
init_config:

instances:
  - name: Example (com)
    # nameserver: 8.8.8.8   # The nameserver to query, this must be an IP address
    hostname: example.com # the record to fetch
    # record_type: AAAA   # default is A
  - name: Example (org)
    hostname: example.org
```

If you omit the `nameserver` option, the check will use whichever nameserver is configured in local network settings.

[Restart the Agent][3] to begin sending DNS service checks and response times to Datadog.

### Validation

[Run the Agent's `status` subcommand][4] and look for `dns_check` under the Checks section.

## Data Collected
### Metrics

See [metadata.csv][5] for a list of metrics provided by this integration.

### Events
The DNS check does not include any event at this time.

### Service Checks
This agent check tags all service checks it collects with:

  * `nameserver:<nameserver_in_yaml>`
  * `resolved_hostname:<hostname_in_yaml>`

`dns.can_resolve`:

Returns CRITICAL if the Agent fails to resolve the request, otherwise returns UP.

Tagged by `hostname` and `record_type`.

## Troubleshooting
Need help? Contact [Datadog Support][6].

## Further Reading
Learn more about infrastructure monitoring and all our integrations on [our blog][7]


[1]: https://app.datadoghq.com/account/settings#agent
[2]: https://github.com/DataDog/integrations-core/blob/master/dns_check/conf.yaml.example
[3]: https://docs.datadoghq.com/agent/faq/agent-commands/#start-stop-restart-the-agent
[4]: https://docs.datadoghq.com/agent/faq/agent-commands/#agent-status-and-information
[5]: https://github.com/DataDog/integrations-core/blob/master/dns_check/metadata.csv
[6]: http://docs.datadoghq.com/help/
[7]: https://www.datadoghq.com/blog/
