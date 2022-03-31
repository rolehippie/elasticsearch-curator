# elasticsearch-curator

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/elasticsearch-curator) [![Testing Build](https://github.com/rolehippie/elasticsearch-curator/workflows/testing/badge.svg)](https://github.com/rolehippie/elasticsearch-curator/actions?query=workflow%3Atesting) [![Readme Build](https://github.com/rolehippie/elasticsearch-curator/workflows/readme/badge.svg)](https://github.com/rolehippie/elasticsearch-curator/actions?query=workflow%3Areadme) [![Galaxy Build](https://github.com/rolehippie/elasticsearch-curator/workflows/galaxy/badge.svg)](https://github.com/rolehippie/elasticsearch-curator/actions?query=workflow%3Agalaxy) [![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/elasticsearch-curator)](https://github.com/rolehippie/elasticsearch-curator/blob/master/LICENSE)

Ansible role to install and configure Elasticsearch curator and index lifecycle management.

## Sponsor

Building and improving this Ansible role have been sponsored by my current and previous employers like **[Cloudpunks GmbH](https://cloudpunks.de)** and **[Proact Deutschland GmbH](https://www.proact.eu)**.

## Table of content

- [Default Variables](#default-variables)
  - [elasticsearch_curator_actions](#elasticsearch_curator_actions)
  - [elasticsearch_curator_enabled](#elasticsearch_curator_enabled)
  - [elasticsearch_curator_hosts](#elasticsearch_curator_hosts)
  - [elasticsearch_curator_interval](#elasticsearch_curator_interval)
  - [elasticsearch_curator_library](#elasticsearch_curator_library)
  - [elasticsearch_curator_log_blacklist](#elasticsearch_curator_log_blacklist)
  - [elasticsearch_curator_log_format](#elasticsearch_curator_log_format)
  - [elasticsearch_curator_log_level](#elasticsearch_curator_log_level)
  - [elasticsearch_curator_restart_service](#elasticsearch_curator_restart_service)
  - [elasticsearch_curator_version](#elasticsearch_curator_version)
- [Discovered Tags](#discovered-tags)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Default Variables

### elasticsearch_curator_actions

Definition of curator actions

#### Default value

```YAML
elasticsearch_curator_actions:
```

#### Example usage

```YAML
elasticsearch_curator_actions:
  1:
    action: delete_indices
    description: >-
      Delete indices older than 45 days (based on index name), for logstash-
      prefixed indices. Ignore the error if the filter does not result in an
      actionable list of indices (ignore_empty_list) and exit cleanly.
    options:
      ignore_empty_list: True
      disable_action: True
    filters:
      - filtertype: pattern
        kind: prefix
        value: logstash-
      - filtertype: age
        source: name
        direction: older
        timestring: '%Y.%m.%d'
        unit: months
        unit_count: 1
```

### elasticsearch_curator_enabled

Enable installation and configuration

#### Default value

```YAML
elasticsearch_curator_enabled: true
```

### elasticsearch_curator_hosts

List of elasticsearch hosts

#### Default value

```YAML
elasticsearch_curator_hosts: []
```

#### Example usage

```YAML
elasticsearch_curator_hosts:
  - elastic1.example.com
  - elastic2.example.com
  - elastic3.example.com
```

### elasticsearch_curator_interval

Interval to execute service

#### Default value

```YAML
elasticsearch_curator_interval: daily
```

### elasticsearch_curator_library

Optionally use a downgraded version of elasticsearch library

#### Default value

```YAML
elasticsearch_curator_library:
```

### elasticsearch_curator_log_blacklist

#### Default value

```YAML
elasticsearch_curator_log_blacklist:
  - elasticsearch
  - urllib3
```

### elasticsearch_curator_log_format

Log blacklist

#### Default value

```YAML
elasticsearch_curator_log_format: default
```

### elasticsearch_curator_log_level

Log level

#### Default value

```YAML
elasticsearch_curator_log_level: INFO
```

### elasticsearch_curator_restart_service

Restart timer and service or only timer

#### Default value

```YAML
elasticsearch_curator_restart_service: true
```

### elasticsearch_curator_version

Version to install

#### Default value

```YAML
elasticsearch_curator_version: 5.8.4
```

## Discovered Tags

**_elasticsearch-curator_**


## Dependencies

- None

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
