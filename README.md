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

In the images


* every Policy-Set/Policy-Enforcement-Point has it's own input kyverno/input/


