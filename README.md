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
# Project Exemplar

## Introduction 
TODO: Give a short introduction of our project. Let this section explain the objectives or the motivation behind this project. 

## Getting Started
TODO: Guide users through getting our code up and running on their own system. In this section we can talk about:
1.	Installation process
2.	Software dependencies
3.	Latest releases
4.	API references

## Build and Test
TODO: Describe and show how to build our code and run the tests. 

## Contribute
TODO: Explain how other users and developers can contribute to make our code better. 

If we want to learn more about creating good readme files then refer the following [guidelines](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-a-readme?view=azure-devops). We can also seek inspiration from the below readme files:
- [ASP.NET Core](https://github.com/aspnet/Home)
- [Visual Studio Code](https://github.com/Microsoft/vscode)
- [Chakra Core](https://github.com/Microsoft/ChakraCore)

