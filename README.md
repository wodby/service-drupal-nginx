# Drupal Nginx services for Wodby

Use Drupal Nginx as a reusable component in applications managed by Wodby. This
repository contains the service manifests and referenced files used by the
public Drupal Nginx service entries in the Wodby catalog.

- [Nginx (Drupal 11) service in the Wodby catalog](https://wodby.com/services/drupal11-nginx)
- [Nginx (Drupal 10) service in the Wodby catalog](https://wodby.com/services/drupal10-nginx)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

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

A service is a reusable component and does not deploy by itself. Add the public
catalog service to a stack, configure its required links and settings, publish
the stack, and then create or upgrade an app instance.

To maintain your own version of this service:

1. Fork this repository.
2. Edit the service manifest and any files it references.
3. Import the repository as a
   [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference `drupal11-nginx`, `drupal10-nginx` from your stack manifest.

Wodby imports the manifest and referenced files from the selected Git branch or
tag and creates a new service revision when the Git-backed service is updated.

## Customize the service

Common changes include adjusting versions, images, Helm chart settings, build
inputs, environment variables, links, storage, resources, and operational
workflows supported by the manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time. These names are part of the contract consumed by
downstream manifests.

Validate customized manifests with the Wodby CLI before importing them:

```bash
wodby service validate-manifest 11/service.yml --org <org-id>
wodby service validate-manifest 10/service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/)
for every supported field and the [managed services
index](https://github.com/wodby/services) for more service examples.
