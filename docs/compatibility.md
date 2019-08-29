# Natively support Compose files on Kubernetes

These are the Compose file features supported on Kubernetes

| Feature                    | docker stack deploy | Compose on Kubernetes  | Amazon ECS |
|----------------------------|---------------------|------------------------|------------|
| build                      |                     |                        |  -         |
|  - context                 |                     |                        |  -         |
|  - dockerfile              |                     |                        |  -         |
|  - args                    |                     |                        |  -         |
|  - cache_from              |                     |                        |  -         |
|  - labels                  |                     |                        |  -         |
| cap_add                    |                     | Yes                    | Yes        |
| cap_drop                   |                     | Yes                    | Yes        |
| command                    | Yes                 | Yes                    | Yes        |
| configs                    | Yes                 | Yes                    | No (https://github.com/aws/containers-roadmap/issues/56)      |
| - external                 | Yes                 | Yes                    | -          |
| - file                     | Yes                 | Yes                    | -          |
| - mode                     | Yes                 | Yes                    | -          |
| cgroup_parent              |                     |                        |            |
| container_name             |                     |                        |            |
| credential_spec            | Yes                 |                        |            |
| deploy                     | Yes                 |                        | service    |
| - endpoint_mode: vip       | Yes                 | Yes                    | ELB        |
| - endpoint_mode: dnsrr     | Yes                 |                        | -          |
| - labels                   | Yes                 | Yes                    | ?          |
| - mode                     | Yes                 | Yes                    | Yes        |
| - placement                | Yes                 | Partial                | Expression |
| - replicas                 | Yes                 | Yes                    | Yes        |
| - resources                | Yes                 | Yes                    | Yes        |
|   -- limits                | Yes                 | Yes                    | Yes        |
|   -- reservations          | Yes                 | Yes                    | Yes        |
| - restart_policy           | Yes                 | Yes                    | No         |
|   -- condition: none       | Yes                 | Yes                    | -          |
|   -- condition: on-failure | Yes                 | Yes                    | -          |
|   -- condition: any        | Yes                 | Yes                    | -          |
|   -- delay                 | Yes                 |                        | -          |
|   -- max_attempts          | Yes                 |                        | -          |
|   -- window                | Yes                 |                        | -          |
| - update_config            | Yes                 |                        |            |
|   -- parallelism           | Yes                 | Yes                    | Yes        |
|   -- delay                 | Yes                 |                        | -          |
|   -- failure_action        | Yes                 |                        | -          |
|   -- monitor               | Yes                 |                        | -          |
|   -- max_failure_ratio     | Yes                 |                        | -          |
| - devices                  |                     |                        | Yes        |
| - depends_on               |                     |                        | Yes        |
| - dns                      |                     |                        | Yes        |
| - dns_search               |                     |                        | Yes        |
| - tmpfs                    |                     | Yes                    | Yes        |
| - entrypoint               | Yes                 | Yes                    | Yes        |
| - env_file                 | Yes                 | Yes                    | -          |
| - environment              | Yes                 | Yes                    | Yes        |
|   -- key=value             | Yes                 | Yes                    | Yes        |
|   -- key                   | Yes                 |                        | -          |
| - expose                   | Yes                 | Yes                    | Yes        |
| - external_links           |                     |                        | -          |
| - extra_hosts              | Yes                 | Yes                    | Yes        |
| - healthcheck              | Yes                 | Yes                    | Yes        |
|   -- test                  | Yes                 | Yes                    | Yes        |
|   -- test: NONE            | Yes                 | Yes                    | -          |
|   -- interval              | Yes                 | Yes                    | Yes        |
|   -- timeout               | Yes                 | Yes                    | Yes        |
|   -- retries               | Yes                 | Yes                    | Yes        |
|   -- disable               | Yes                 | Yes                    | -          |
| - image                    | Yes                 | Yes                    | Yes        |
| - isolation                | Yes                 |                        | -          |
| - labels                   | Yes                 | Yes                    | Yes        |
| - links                    |                     |                        | Yes        |
| - logging                  | Yes                 |                        | LogConfiguration |
|   -- driver                | Yes                 |                        | ~          |
|   -- options               | Yes                 |                        | ~          |
| - network_mode             |                     |                        | Yes        |
| - networks                 | Yes                 |                        | Yes        |
|   -- aliases               | Yes                 |                        | Yes        |
|   -- ipv4_address          | Yes                 |                        | -          |
|   -- ipv6_address          | Yes                 |                        | -          |
| - pid: host                | Yes                 | Yes                    | Yes        |
| - ports                    | Yes                 | Yes                    | Yes        |
|   -- target                | Yes                 | Yes                    | Yes        |
|   -- published             | Yes                 | Yes                    | Yes        |
|   -- protocol              | Yes                 | Yes                    | Yes        |
|   -- mode: host            | Yes                 | Not sure               | Yes        |
|   -- mode: ingress         | Yes                 | Not sure               | awsvpc     |
| - secrets                  | Yes                 | Yes                    | Env only (https://github.com/aws/containers-roadmap/issues/56) |
|   -- source                | Yes                 | Yes                    | -          |
|   -- target                | Yes                 | Yes                    | -          |
|   -- uid                   | Yes                 |                        | -          |
|   -- gid                   | Yes                 |                        | -          |
|   -- mode                  | Yes                 | Yes                    | -          |
| - security_opt             |                     |                        | Yes        |
| - stop_grace_period        | Yes                 | Yes                    | Yes        |
| - stop_signal              |                     |                        | -          |
| - sysctls                  |                     |                        | Yes        |
| - ulimits                  |                     |                        | Yes        |
| - userns_mode              |                     |                        | -          |
| - volumes                  | Yes                 | Yes                    | Yes        |
|   -- type: volume          | Yes                 | Yes                    | Yes        |
|   -- type: bind            | Yes                 | Yes                    | Yes        |
|   -- source                | Yes                 | Yes                    | Yes        |
|   -- target                | Yes                 | Yes                    | Yes        |
|   -- read_only             | Yes                 | Yes                    | Yes        |
|   -- bind/propagation      | Yes                 |                        | ?          |
|   -- volume/nocopy         | Yes                 |                        | -          |
| - restart                  |                     |                        | no         |
| - domainname               |                     |                        | -          |
| - hostname                 | Yes                 | Yes                    | Yes        |
| - ipc                      |                     | Yes                    | Yes        |
| - mac_address              |                     |                        | -          |
| - privileged               |                     | Yes                    | Yes        |
| - read_only                | Yes                 | Yes                    | Yes        |
| - shm_size                 |                     |                        | Yes        |
| - stdin_open               | Yes                 | Yes                    | Yes        |
| - tty                      | Yes                 | Yes                    | Yes        |
| - user: numerical          | Yes                 | Yes                    | Yes        |
| - user: name               | Yes                 |                        | Yes        |
| - working_dir              | Yes                 | Yes                    | Yes        |

# Not supported by k8s

+ mac_address (https://github.com/kubernetes/kubernetes/issues/2289)
+ shm_size (https://github.com/kubernetes/kubernetes/issues/28272)
+ ulimits (https://github.com/kubernetes/kubernetes/issues/3595)
+ non numerical user

# Placeholders interpolation

Before a yaml file is sent to Kubernenetes, its `${...}` placeholders
are replaced with actual values.
 + A first attempt is made at reading the variable from a `.env` file is
current working directory.
 + If no value is found, an environment variable are used.
