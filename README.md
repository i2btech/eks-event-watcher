# Managing Amazon EKS control plane events


## Context

Currently EKS event TTL is set to 60m. Some customers have shown interest to increase the TTL. (https://github.com/aws/containers-roadmap/issues/785). It will be an additional burden if EKS control plane provided the option to increase TTL as this will add load to ETCD and storage. This solution here tries to bridge the gap to capture events beyond 60 minutes to cloudwatch, if the customers still achieve the same. That way control plane event TTL is not modified but at the sametime, if customer wanted to capture the events beyond 60m, they could achieve the same.


## TODO

- Improves documentation
    - add solution diagram
    - operation of helm chart
- Improves templates helm chart
    - edit/removes files: NOTES.txt, _helpers.tpl, test-connection.yaml
- Improves values.yaml helm chart
    - delete unused options
    - add option to pass arguments to container (`-list` to define events to watch)
- Improves Github actions
    - use `appVersion` in file Chart.yaml to set tag in docker hub image, we also need to keep the `latest` tag because it's used in the `Values.yaml` file
- Improves k8s templates
    - add option `resources` to control capacity used by pod
