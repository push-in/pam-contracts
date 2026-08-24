<!-- pam:product-page:start -->
<div align="center">

# PAM Contracts

**Depend on the extension boundary—not an entire framework.**

Small, versioned interfaces for applications, middleware, providers, stability, and runtime compatibility.

[![Release](https://img.shields.io/github/v/release/push-in/pam-contracts?style=flat-square&label=stable)](https://github.com/push-in/pam-contracts/releases)
![PHP](https://img.shields.io/badge/PHP-8.5-777BB4?style=flat-square&logo=php&logoColor=white)
![License](https://img.shields.io/github/license/push-in/pam-contracts?style=flat-square)

**[Documentation](https://push-in.github.io/pam-docs/packages/overview/) · [Why this exists](#why-this-exists) · [What you can build](#what-you-can-build) · [Quick start](#quick-start) · [Issues](https://github.com/push-in/pam-contracts/issues)**

</div>

---

## Why this exists

Small, versioned interfaces for applications, middleware, providers, stability, and runtime compatibility.

| | |
| --- | --- |
| **Role** | Foundation contract |
| **Execution path** | Strict PHP 8.5 interfaces |
| **This repository owns** | Stable extension contracts shared across PAM packages |
| **Boundary** | No router, server, framework, or application implementation |

## What you can build

- Publishing framework-independent PAM extensions
- Testing runtime compatibility explicitly
- Sharing middleware and provider contracts without pulling a router

## Quick start

```bash
pam composer require pushinbr/pam-contracts
```

The **[PAM documentation](https://push-in.github.io/pam-docs/packages/overview/)** covers prerequisites, production setup, and the complete workflow. PAM projects keep normal manifests and lockfiles; product features stay in the package that owns them.
<!-- pam:product-page:end -->

Small, versioned contracts for packages that extend Pam. It contains the HTTP
application and middleware contracts, service providers, stability values and
native runtime compatibility checks. It does not contain a router or server.

## License

Free and open-source under the [Apache License 2.0](LICENSE). You may use,
modify, and distribute this package for any purpose, including commercially.


## Recommended PAM workflow

Most applications receive this contract package transitively. Extension authors can install it explicitly with `pam composer require pushinbr/pam-contracts`.

Run `pam doctor` after dependency changes and before creating a release. The project remains a normal Composer project with a standard manifest, lockfile, PSR-4 autoloading, and `vendor/autoload.php`.

## API guide

| Surface | Use it for |
| --- | --- |
| `ApplicationInterface` | Minimal route, middleware, error, and in-memory handling contract. |
| `MiddlewareInterface` | Process a request and delegate to the next handler. |
| `RequestHandlerInterface` | Handle PAM request/response values. |
| `ServiceProviderInterface` | Register and boot package integrations. |
| `RuntimeCompatibility` | Discover ABI/capabilities and assert required runtime features. |
| `Stability` | Represent the documented contract maturity. |

This package intentionally contains no router, server, or application implementation. Depend on it when publishing reusable PAM extensions that need stable contracts without forcing `pushinbr/pam-api` on consumers.

## Production checklist

- Keep request data and mutable state scoped to the current request.
- Test success, validation failure, exception, cancellation, and timeout paths.
- Configure explicit limits and avoid unbounded payloads, queues, or retained collections.
- Run `pam doctor`, `pam test`, and the relevant integration suite before release.
- Validate real dependencies and workload behavior; compatibility is not inferred from package installation alone.

## Troubleshooting

- **Class not found:** run `pam composer install`, verify PSR-4 configuration, and rerun `pam doctor`.
- **Behavior differs over the network:** reproduce with PAM's transport integration tests; in-memory execution does not model the socket boundary.
- **A dependency blocks a worker:** use PAM-native I/O, a compatible event loop, a process pool, or additional isolated workers.

## Documentation and support

- [PAM introduction](https://push-in.github.io/pam-docs/introduction/)
- [Package ecosystem](https://push-in.github.io/pam-docs/packages/overview/)
- [Runtime compatibility](https://push-in.github.io/pam-docs/runtime/compatibility/)
- [Report an issue](https://github.com/push-in/pam-contracts/issues)

Report security vulnerabilities through GitHub private vulnerability reporting or the PAM security policy, not a public issue.
