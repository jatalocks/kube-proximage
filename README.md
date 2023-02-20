# Kube Proximage

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/explorium-ai/kube-proximage)](https://img.shields.io/github/v/release/explorium-ai/kube-proximage)
<!-- [![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/kube-proximage)](https://artifacthub.io/packages/search?repo=kube-proximage) -->

**kube-proximage** is a helm chart that defines a mutating webhook to proxy container images into custom registries

It uses [Next Trucking's Docker Proxy Operator](https://github.com/NextDeveloperTeam/kubernetes-webhooks/tree/main/docker-proxy-webhook) as its controller.

## Dependencies

- [Cert Manager](https://github.com/cert-manager/cert-manager)
## Install using Helm chart

- Configure
    ```yaml
    config:
      ignoreList:
      - "123456789012.dkr.ecr.us-east-1.amazonaws.com"
      domainMap:
        docker.io: org-name-docker-io.jfrog.io
        quay.io: org-name-quay-io.jfrog.io
        gcr.io: org-name-gcr-io.jfrog.io
        k8s.gcr.io: org-name-k8s-gcr-io.jfrog.io
        us.gcr.io: org-name
        docker.elastic.co: org-name-docker-elastic-co.jfrog.io
    ```
- Install latest version of kube-proximage helm chart

    ```
    $ helm repo add kube-proximage https://jatalocks.github.io/kube-proximage/
    $ helm repo update
    $ helm install kube-proximage/kube-proximage -n docker-proxy --create-namespace -f values.yaml
    ```    
## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on the process for submitting pull requests.

## Code of Conduct

Please read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) for details on our code of conduct, and how to report violations.

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details
