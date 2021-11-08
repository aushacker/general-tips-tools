# OpenShift Examples

These examples have been tested in OCP 4.9.

## Basic Tekton Build Pipeline

First use the OCP console to install the OpenShift Pipelines operator.
This installs the Tekton resource definitions.

Then:
```
oc create -f maven-settings.yaml
oc create -f basic-maven-pipeline.yaml
oc create -f basic-maven-pipeline-run.yaml
```
