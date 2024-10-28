# OpenLDAP

[OpenLDAP](https://openldap.org/) Software is an open source implementation of the Lightweight Directory Access Protocol.

The suite includes:

- lloadd - stand-alone LDAP Load Balancer Daemon (server or slapd module)
- slapd - stand-alone LDAP daemon (server)
- libraries implementing the LDAP protocol, and
- utilities, tools, and sample clients.

## Installation

We use the OpenLDAP Helm chart located here: [https://artifacthub.io/packages/helm/symas-openldap/openldap](https://artifacthub.io/packages/helm/symas-openldap/openldap). To install the chart, first add the repository:

```{.shell}
helm repo add helm-openldap https://symas.github.io/helm-openldap/
```

Next, create a `openldap` namespace:

```{.shell}
kubectl create namespace openldap
```

Next, create the administrative credentials for the LDAP server:

```{.shell}
kubectl apply -f secrets.yaml
```

Finally, install the chart with the `values.yaml` provided in this directory:

```{.shell}
helm install openldap -n openldap --version 1.1.7 -f values.yaml helm-openldap/openldap
```

## Add Ingresses

In addition to creating a OpenLDAP cluster, this chart installs the [phpLDAPAdmin](https://github.com/leenooks/phpLDAPadmin) administrative utility and the [ltb-password](https://ltb-project.org/documentation/self-service-password.html) self-service password change portal utility. Add the ingresses for both services:

```{.shell}
kubectl apply -f ingress.yaml
```

## Usage

LDAP (the user directory) is a fairly complex topic and as such, cannot be adequately covered in this simple README. If you need a good introduction, see the following guide: [https://www.brennan.id.au/20-Shared_Address_Book_LDAP.html](https://www.brennan.id.au/20-Shared_Address_Book_LDAP.html). Our intended use of LDAP is as a user directory for the [Keycloak](https://www.keycloak.org/) identity and access management service and for applications that do not support modern authentication services such as OAuth and OIDC. See the Keycloak operator configurations in this repository for more information.
