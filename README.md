## gatekeeper-kyverno-policyset

## We will generate 3 PolicySets

* Security-Focused PolicySets for Gatekeeper and Kyverno as well as a 
* Multitenancy-Focused PolicySet for Kyverno

On the RHACM-Hub-Cluster please run

```
oc create -f main.yaml
```

* creates namespaces, installs GitopsOperator, installs PolicyGenerator with ArgoCD
```
policygenerator/openshift-gitops/
```

* .... installs 3 ArgoCD Applications


* every Policy-Set/Policy-Enforcement-Point has it's own input e.g. kyverno/input/ where the resources reside


## How to run it
```shell
until oc apply -f https://raw.githubusercontent.com/ch-stark/gatekeeper-kyverno-policyset/main/main.yaml; do sleep 15; done
```

* it created the namespaces
* configures ArgoCD to use with PolicyGenerator
* installs Kyverno and/or Gatekeeper via ACM-Policies 
* sets up ManagedClusterSetBindings to default ClusterSet for the namespaces where the PolicySets will be installed.


# Structure
```shell
|-- gatekeeper-kyverno-policyset
|   |-- gatekeeper
|   |   |-- input
|   |   |-- kustomization.yaml
        |-- placement.yaml
        |-- policyGenerator.yaml
|   |-- kyverno
|   |   |-- input
|   |   |-- kustomization.yaml
        |-- placement.yaml
        |-- policyGenerator.yaml
|   |-- kyverno-multitenancy
|   |   |-- input
|   |   |-- kustomization.yaml
        |-- placement.yaml
        |-- policyGenerator.yaml
|   |-- setup
|        |--  openshift-gitops
|-- README.md
```

|#|Directory Name|Description|
|---|----------------|-----------------|
| 1. | `gatekeeper` | This is where all configurations for the `gatekeeper-policyset` is stored. 
| 2. | `kyverno` | This is where all configurations for the `kyverno-policyset` is stored. <br /><br />|
| 3. | `kyverno-multitenancy` | This is where all configurations for the `kyverno-multitenancy-policyset` is stored.<br /><br />|
| 4. | `setup` | configuration files <br /><br /> 



# Documentaton of Policies 


## Gatekeeper
## Kyverno
## Gatekeeper-Multitenancy



# Testing









