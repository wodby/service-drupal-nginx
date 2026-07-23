# Drupal Nginx service for Kubernetes on Wodby

Run Drupal Nginx as a reusable Kubernetes application service with Wodby.

This repository defines the Wodby service manifests and operational
configuration for Drupal Nginx.

- [Browse Wodby services](https://wodby.com/services)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Wodby stacks using this service

- [Drupal application stack](https://github.com/wodby/stack-drupal)

## Service entries

### Nginx (Drupal 11)

| Property | Manifest configuration |
| --- | --- |
| Service name | `drupal11-nginx` |
| Type | Application service |
| Inherits from | [`php-nginx`](https://github.com/wodby/service-php-nginx) with version constraint `^1.0.0` |
| Volumes | Files |
| Application build | Dockerfile: `Dockerfile` |
| Configuration | 2 settings, 1 configuration files |

Manifest: [`11/service.yml`](11/service.yml)

### Nginx (Drupal 10)

| Property | Manifest configuration |
| --- | --- |
| Service name | `drupal10-nginx` |
| Type | Application service |
| Inherits from | [`php-nginx`](https://github.com/wodby/service-php-nginx) with version constraint `^1.0.0` |
| Volumes | Files |
| Application build | Dockerfile: `Dockerfile` |
| Configuration | 2 settings, 1 configuration files |

Manifest: [`10/service.yml`](10/service.yml)

## Use this service

Use this service through [Drupal application stack](https://github.com/wodby/stack-drupal), or reference `drupal10-nginx`,
`drupal11-nginx` from a custom Wodby stack.

A service is a reusable component and does not deploy by itself. The stack
defines its links, settings, versions, resources, and relationship to the rest
of the application.

## Maintain a custom version

1. Fork this repository.
2. Edit the service manifest and referenced files.
3. Import the repository as a [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference the service from a stack manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time.

Validate the manifests with:

```bash
wodby service validate-manifest 11/service.yml --org <org-id>
wodby service validate-manifest 10/service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/) and the [managed services index](https://github.com/wodby/services).
