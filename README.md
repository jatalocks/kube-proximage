# Kube Proximage

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/explorium-ai/kube-proximage)](https://img.shields.io/github/v/release/explorium-ai/kube-proximage)
[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/kube-proximage)](https://artifacthub.io/packages/search?repo=kube-proximage)

**kube-proximage** is a kubernetes chart that is an aggregation of *multiple open-source projects*. 

It allows for creating and managing a cache of container images directly on the worker nodes of a kubernetes cluster. It uses [kube-fledged](https://github.com/senthilrch/kube-fledged) as its controller, an [events-exporter](https://github.com/AliyunContainerService/kube-eventer) to get Pulled/Killed images and a [webhook-server](https://github.com/adnanh/webhook) to apply/purge/remove the ImageCache CRDs maintained by kube-fledged.

Where it differs from other similar projects is that it allows for *automatic discovery* of images based on regex. There is no need for manual input of images and repositories.
## Install using Helm chart

- Configure general values
    ```yaml
    global:
        # -- Defines the secrets which will be used to pull images into nodes and cache them
        imageCachePullSecrets: []

        # -- # List of images to exclude when creating image caches. works with Regex
        exclude:
          - ".*kube-proxy.*"

        # --  # List of images to include when creating image caches. works with Regex.
        include:
          - ".*"

        cacheAllOnDeploy: 
          # -- On Chart install, automatically create all caches for all images in the cluster (respecting excluded list)
          enabled: true
    ```
- Install latest version of kube-proximage helm chart

    ```
    $ helm repo add kube-proximage https://explorium-ai.github.io/kube-proximage/
    $ helm repo update
    $ helm install kube-proximage/kube-proximage -n kube-system -f values.yaml
    ```
## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on the process for submitting pull requests.

## Code of Conduct

Please read [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) for details on our code of conduct, and how to report violations.

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details
