# NeuronEX Operator Chart

Helm chart for NeuronEX Operator.

> Currently, the NeuronEX Operator is still under development, so this chart may change frequently.

## How the Operator Works

The NeuronEX Operator watches the `NeuronEX` custom resource, and creates, updates, or deletes NeuronEX instances according to the custom resource.

It aims to provide a simple way to manage NeuronEX instances on Kubernetes.

Below is a simplified workflow of the operator:

- Once the operator is deployed, it watches the `NeuronEX` custom resource.
- When a `NeuronEX` custom resource is created, the operator creates a NeuronEX instance.
- The operator will assistant users to create volumes, services, etc., according to the custom resource.

  For example, you don't need to create a volume manually, the operator will create a default volume for you and mount it to the NeuronEX instance. And you can also customize the volume by providing a custom volume claim template, or a storage class.

- If you want to update the NeuronEX instance, you can update the custom resource, and the operator will update the NeuronEX instance accordingly.

  For example, you want to update the environment variables of the NeuronEX instance, you can update the custom resource, and the operator will update the NeuronEX instance by restarting the pod.

- If you want to delete the NeuronEX instance, you can delete the custom resource, and the operator will delete the NeuronEX instance, and all owned resources.

  > Note: The operator will not delete the volumes. Due to its still under development, some of other resources may not be deleted.

## Values Explanation

Most of time, you don't need to change the default values, but you can customize the values according to your needs.

See the [values.yaml](values.yaml) for more information.

Nearly all the values are related to the container of manager, you can customize the container's resources, environment variables, etc.
