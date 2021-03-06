# Agent Check: SSH/SFTP

## Overview

This check lets you monitor SSH connectivity to remote hosts and SFTP response times.

## Setup
### Installation

The SSH/SFTP check is packaged with the Agent, so simply [install the Agent][1] anywhere from which you'd like to test SSH connectivity.

### Configuration

Create a file `ssh_check.yaml` in the Agent's `conf.d` directory. See the [sample ssh_check.yaml][2] for all available configuration options:

```
init_config:

instances:
  - host: <SOME_REMOTE_HOST>  # required
    username: <SOME_USERNAME> # required
    password: <SOME_PASSWORD> # or use private_key_file
#   private_key_file: <PATH_TO_PRIVATE_KEY>
#   private_key_type:         # rsa or ecdsa; default is rsa
#   port: 22                  # default is port 22
#   sftp_check: False         # set False to disable SFTP check; default is True
#   add_missing_keys: True    # default is False
```

[Restart the Agent][3] to start sending SSH/SFTP metrics and service checks to Datadog.

### Validation

[Run the Agent's `status` subcommand][4] and look for `ssh_check` under the Checks section.

## Data Collected
### Metrics

See [metadata.csv][5] for a list of metrics provided by this check.

### Events
The SSH Check check does not include any event at this time.

### Service Checks

**ssh.can_connect**:

Returns CRITICAL if the Agent cannot open an SSH session, otherwise OK.

**sftp.can_connect**:

Returns CRITICAL if the Agent cannot open an SFTP session, otherwise OK.

## Troubleshooting
Need help? Contact [Datadog Support][6].

## Further Reading
Learn more about infrastructure monitoring and all our integrations on [our blog][7]


[1]: https://app.datadoghq.com/account/settings#agent
[2]: https://github.com/DataDog/integrations-core/blob/master/ssh_check/conf.yaml.example
[3]: https://docs.datadoghq.com/agent/faq/agent-commands/#start-stop-restart-the-agent
[4]: https://docs.datadoghq.com/agent/faq/agent-commands/#agent-status-and-information
[5]: https://github.com/DataDog/integrations-core/blob/master/ssh_check/metadata.csv
[6]: http://docs.datadoghq.com/help/
[7]: https://www.datadoghq.com/blog/
