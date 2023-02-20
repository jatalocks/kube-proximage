# Kube-proximage

![Version: 1.1.2](https://img.shields.io/badge/Version-1.1.2-informational?style=for-the-badge)

![AppVersion: 1.0](https://img.shields.io/badge/AppVersion-1.0-informational?style=for-the-badge)
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/kube-proximage)](https://artifacthub.io/packages/search?repo=kube-proximage)
## Description

A Kubernetes Image Puller and Cacher with Automatic Discovery

## Install

- Configure Registry Proxies
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

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| config | object | `{"domainMap":{"docker.elastic.co":"org-name-docker-elastic-co.jfrog.io","docker.io":"org-name-docker-io.jfrog.io","gcr.io":"org-name-gcr-io.jfrog.io","k8s.gcr.io":"org-name-k8s-gcr-io.jfrog.io","quay.io":"org-name-quay-io.jfrog.io","us.gcr.io":"org-name"},"ignoreList":["123456789012.dkr.ecr.us-east-1.amazonaws.com"]}` | Proxy Configuration |

**Homepage:** <https://github.com/explorium-ai/kube-proximage>

## Source Code

* <https://github.com/explorium-ai/kube-proximage>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| explorium-ai | <devops@explorium.ai> | <https://www.explorium.ai/> |
