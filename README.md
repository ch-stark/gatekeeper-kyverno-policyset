## gatekeeper-kyverno-policyset

## We will generate 3 PolicySets

* Security-Focused PolicySets for Gatekeeper and Kyverno as well as a 
* Multitenancy-Focused PolicySet for Kyverno

main.yaml:

* creates namespaces, installs GitopsOperator, installs PolicyGenerator with ArgoCD

policygenerator/openshift-gitops/

* .... installs 3 ArgoCD Applications

