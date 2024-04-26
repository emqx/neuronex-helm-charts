# NeuronEX Helm Charts

Helm charts for NeuronEX Operator & NeuronEX.

## Overview

The main purpose of this repository is to provide a simple way to deploy NeuronEX on Kubernetes.
After deploying NeuronEX Operator, you can also use this chart to deploy NeuronEX instances.

For more information about values, please refer to the chart READMEs:

- [NeuronEX Operator README](charts/neuronex-operator/README.md)
- [NeuronEX README](charts/neuronex/README.md)

## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

```sh
helm repo add neuronex https://emqx.github.io/neuronex-helm-charts
```

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages. You can then run `helm search repo neuronex`
to see the charts.

### Installation

To install the NeuronEX Operator:

```sh
helm install neuronex-operator neuronex/neuronex-operator -n neuronex-op --create-namespace
```

To install the NeuronEX:

```sh
helm install neuronex neuronex/neuronex -n neuronex --create-namespace
```

To uninstall charts:

```sh
helm delete neuronex -n neuronex
helm delete neuronex-operator -n neuronex-op
```
