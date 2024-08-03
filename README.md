# Yaktt
Yet Another K8s Testing Tool

## Project's Purpose
This project aims to be a microservice integration testing development tool, easying the process of affirming end to end behaviour between various microservices living in a k8s environment.

As to how it aims to help the development of integration testing, is by providing tools for:
- Instantiating a temporary microservice system aimed to be tested "whole", manage said system, collect ouputs, and assert upon them.
- Delivering an Sdk for producing "behavioural triggers", assertions on outputs, and microservice system definition.

## Ephemeral System Instantiation Design

In order to fulfill the first purpose of Yaktt (Temporary Microservice System Instantiation), VCluster is used, setting already the interim scope of the system aimed to be tested.
After VCluster's instantation on a predetermined ns, there are several routes open in order to define the microservice system, via GitOps, Chart, plain K8s CR manifests, etc.

As main industry practices for declaring resources, revolve around the 3 methods stated above, support for a first version of Yaktt will only cover those same 3 options.

### GitOps

Support for Flux Kustomizations, and Argo Workflows is first priority, other GitOps tools should only receive support in latter versions.

### Charts

Support Helm Charts being applied inside ephemeral VCluster.

### Default Manifests

Simplest Solution, default Appliance of defined k8s resources.

## Testing SDK

For the testing SDK a simple solution consisting of a library with a weak opinated HTTP & GRPC client as the trigger mechanism, and a prometheus Logging server that is always added to any microservice system instantiation, serving as a log collector to run the assertion logic post trigger.
