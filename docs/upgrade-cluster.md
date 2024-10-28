As part of our work as DevOps engineers, we will periodically be required to upgrade a cluster.

A cluster provides mechanisms or facilities to perform operations such as rolling deployments. 
Deployments occur in the context of a graph of dependencies. If we restrict our consideration to 
some subset of the overall cluster components, the number of considerations is reduced.

Consider an example, where *keycloak* is used to manage an *ldap* instance used by a *postgres* 
instance for authentication credentials.

## deployment dependency graph

For the purposes of this discussion, we would consider cluster components such as keycloak and 
ldap as atomic components, realizing that they can be further considered as composite entities.
Further elaboration of a component such as *ldap* will be considered in terms of its constituant 
components in a later section. 

```mermaid
flowchart TD 
A[argocd] -->|helm| HCLD[ldap chart]
A[argocd] -->|helm| HCAW[argo-workflows chart+]
A[argocd] -->|helm| HCPGO[Postgres Operator chart+]
A[argocd] -->|helm| HCKCO[Keycloak Operator chart+]
HCLD[ldap chart] -->|deploy| LD[ldap]
HCAW[argo-workflows chart+] -->|deploy| AW[argo-workflows+]
HCPGO[Postgres Operator chart] -->|provides| PGRD[Postgres Resource Definitions]
PGRD[Postgres Resource Definitions] -->|deploy| PGO[Postgres Operator]
HCKCO[Keycloak Operator chart] -->|deploy| KCO[Keycloak Operator]
KCO[Keycloak Operator] --> |deploy| KC[keycloak]
KC[keycloak] --> |manage| LD[ldap]
PGO[Postgres Operator] --> |deploy| P[postgres]
P[postgres] --> |auth| LD[ldap]
AW[argo-workflows+] --> |load| LD[ldap]
```
Note, items marked with `+` are recommended.