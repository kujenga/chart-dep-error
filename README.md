# Helm Requirements Bug

This repository demonstrates a possible bug in the upgrade process for subcharts installed with Helm that use conditionals.

Steps to reproduce the issue:

```sh
helm install --name=example charts/test -f memcached-values.yaml
# the memcached deployment is available
helm get values example
# the values are set to the contents of memcached-values.yaml
helm upgrade example charts/test
# the redis deployment is now active
helm get values example
# the values are still set to the contents of memcached-values.yaml
helm upgrade example charts/test -f memcached-values.yaml
# the memcached chart is restored
```
