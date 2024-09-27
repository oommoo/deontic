# deontic

Define [Deontic Modality](https://en.wikipedia.org/wiki/Deontic_modality) as 

  "a linguistic modality that indicates how the world ought to be according to certain norms, expectations, ..."

# high availability

Define [High Availability](https://en.wikipedia.org/wiki/High_avalability) as 

  "a characteristic of a system that aims to ensure an agreed level of operational performance, usually uptime, for a higher than normal period."

or as 

  "a property of network resilience, the ability to provide and maintain an acceptable level of service in the face of faults and challenges to normal operation."

  ## cluster 

  Given that we have kubernetes to provide the cluster definitions, consider the following flowchart

```mermaid
flowchart TD 
K[kubernetes?] -->|define| V[volumes]
K[kubernetes?] -->|define| N[nodes]
K[kubernetes?] -->|define| P[pods]
K[kubernetes?] -->|define| S[services]
K[kubernetes?] -->|define| D[deployments]
P[pods] --> |on| N[nodes]
P[pods] --> |request| C[claims]
C[claims] --> |refer| V[volumes] 
S[services] --> |have| P[pods]
S[services] --> |have| I[ingress]
D[deployments] --> |specify| S[services]
```