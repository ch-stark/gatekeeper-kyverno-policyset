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
oc apply -f https://raw.githubusercontent.com/ch-stark/gatekeeper-kyverno-policyset/policies/managed-clustersetbinding.yaml 
oc apply -f https://raw.githubusercontent.com/stolostron/policy-collection/main/community/CM-Configuration-Management/policy-install-kyverno.yaml
until oc apply -f https://raw.githubusercontent.com/ch-stark/gatekeeper-kyverno-policyset/main/main.yaml; do sleep 15; done
```

* it created the namespaces
* configures ArgoCD to use with PolicyGenerator
* installs [Kyverno](https://github.com/stolostron/policy-collection/blob/main/community/CM-Configuration-Management/policy-install-kyverno.yaml) and/or Gatekeeper via ACM-Policies 
* used a [policy](https://raw.githubusercontent.com/ch-stark/gatekeeper-kyverno-policyset/main/policies/managed-clustersetbinding.yaml) that sets up ManagedClusterSetBindings to default ClusterSet for the namespaces where the PolicySets will be installed.


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

* any-warn-deprecated-api-versions
* container-deny-latest-tag
* container-deny-privileged-if-tenant
* pod-deny-host-ipc
* pod-deny-without-runasnonroot
* container-deny-added-caps
* container-deny-no-resource-constraints 
* pod-deny-host-network
* container-deny-escalation 
* container-deny-privileged
* pod-deny-host-alias
* pod-deny-host-pid

## Kyverno

# Kyverno Policies
Policies in this folder are based on [Kyverno - Kubernetes Native Policy Management](https://kyverno.io/docs/introduction/). The policies in this folder are based on security controls from the [OCP 4.x Platform &Infrastructure Security Best Practices](https://github.com/rhilconsultants/openshift/blob/master/featureReference/Red%20Hat%20Openshift%204.x%20Security%20Best%20Practices%20-%20Public%20Edition%20-%20Final%20v2%20(2).pdf) compliance document. Each security control will be represented by its own directory.

The solution presented in this directory is designed to provide compliance for  [Red Hat OpenShift](https://www.openshift.com/) clusters. Note that some policies can be applied _out of the box_, while other policies may require changes according to organization regulations.

## Security control catalog
- [authentication-user-management](./authentication-user-management)
- [authorization](./authorization)
- [etcd-security](./etcd-security)
- [infrastructure-general](./infrastructure-general)
- [monitoring-observability](./monitoring-observability)
- [networking](./networking)
- [resource-exhaustion](./resource-exhaustion)
- [storage](./storage)
- [trusted-image-sources](./trusted-image-sources)


### Authentication and User Management
Policy  | Description | Prerequisites
------- | ----------- | -------------

### Authorization
Policy  | Description | Prerequisites
------- | ----------- | -------------

### ETCD Security
Policy  | Description | Prerequisites
------- | ----------- | -------------

### Infrastructure General
Policy  | Description | Prerequisites
------- | ----------- | -------------
No policies yet       |  | 

### Monitoring and Observability
Policy  | Description | Prerequisites
------- | ----------- | -------------
No policies yet       |  |

### Networking
Policy  | Description | Prerequisites
------- | ----------- | -------------

### Resource Exhaustion
Policy  | Description | Prerequisites
------- | ----------- | -------------

### Storage
Policy  | Description | Prerequisites
------- | ----------- | -------------
No policies yet       |  |

### Trusted Image Sources
Policy  | Description | Prerequisites
------- | ----------- | -------------

* authentication-user-management
* networking
* restrict-clusterrole-nodesproxy
* restrict_ingress_host  
* restrict-secret-role-verbs  
* restrict_usergroup_fsgroup_id
* authorization 
* resource-exhaustion
* restrict_controlplane_scheduling
* restrict-ingress-wildcard
* restrict_secrets_by_label
* restrict-wildcard-resources
* etcd-security
* restrict_annotations
* restrict-escalation-verbs-roles
* restrict_loadbalancer 
* restrict_secrets_by_name 
* restrict-wildcard-verbs
* infrastructure-general
* restrict_automount_sa_token
* restrict_ingress_classes
* restrict_node_selection 
* restrict-service-account
* storage
* monitoring-observability 
* restrict-binding-clusteradmin
* restrict_ingress_defaultbackend
* restrict_pod_count_per_node
* restrict_service_port_range 
* trusted-image-sources



## Kyverno-Multitenancy

* addlabelstotenant
* generateManagedClusterSetBinding
* restrictions
* disallowplacementrules
* generatePlacementRules
* sharedresources
* generateall   
* other  
* validatens
* generateargocdpersmissions 
* preventupdatesappproject  
* validateplacement

# Testing



# related links





