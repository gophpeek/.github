# PHPeek

Observability and operational tooling for PHP applications.
System metrics, queue monitoring, process management, and container infrastructure.

---

## Laravel Packages

| Package | Version | Description |
|---------|---------|-------------|
| [laravel-queue-metrics](https://github.com/gophpeek/laravel-queue-metrics) | v1.4 | Queue instrumentation with Prometheus export. Job duration, memory, CPU, throughput, health scores. ~1-2ms overhead per job. |
| [laravel-queue-autoscale](https://github.com/gophpeek/laravel-queue-autoscale) | v1.0 | SLA-based predictive autoscaling. Uses Little's Law + trend analysis. Respects CPU/memory limits. |
| [laravel-queue-monitor](https://github.com/gophpeek/laravel-queue-monitor) | v1.1 | Individual job tracking with payload storage. Retry chains, server identification, job replay. REST API included. |
| [system-metrics](https://github.com/gophpeek/system-metrics) | v1.6 | Pure PHP system metrics. CPU, memory, disk, network. No extensions required. Linux + macOS. |

All packages require PHP 8.3+ and Laravel 10+/11+.

---

## Go Tools

| Tool | Version | Description |
|------|---------|-------------|
| [phpeek-pm](https://github.com/gophpeek/phpeek-pm) | v1.2 | PID 1 process manager for Docker. Manages PHP-FPM, Nginx, Horizon, queue workers. Health checks, Prometheus metrics, TUI. |
| [phpeek-fpm-exporter](https://github.com/gophpeek/phpeek-fpm-exporter) | v2.0 | Prometheus exporter for PHP-FPM. Pool auto-discovery, opcache stats, Laravel queue sizes. |
| [fcgx](https://github.com/gophpeek/fcgx) | v1.0 | FastCGI client library. Context/timeout support, structured errors. Used by phpeek-fpm-exporter. |

---

## Docker Images

| Image | Description |
|-------|-------------|
| [baseimages](https://github.com/gophpeek/baseimages) | PHP Docker base images. Three tiers: Slim (~120MB), Standard (~250MB), Full (~700MB). Includes phpeek-pm. PHP 8.3/8.4 on Debian Bookworm. |

Images available at `ghcr.io/gophpeek/baseimages/`.

---

## How They Connect

```
┌─────────────────────────────────────────────────────────────────┐
│                     Docker Container                            │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ phpeek-pm (PID 1)                                        │   │
│  │   ├── php-fpm ←── phpeek-fpm-exporter (via fcgx)        │   │
│  │   ├── nginx                                              │   │
│  │   └── queue workers ←── laravel-queue-autoscale         │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                 │
│  Laravel Application                                            │
│    ├── laravel-queue-metrics (job instrumentation)             │
│    ├── laravel-queue-monitor (job tracking + replay)           │
│    └── system-metrics (CPU, memory, disk, network)             │
│                                                                 │
│  ──────────────────────────────────────────────────────────────│
│                         ↓ Prometheus ↓                          │
└─────────────────────────────────────────────────────────────────┘
```

---

## Quick Start

**Queue monitoring in 30 seconds:**

```bash
composer require gophpeek/laravel-queue-metrics
```

```php
use PHPeek\LaravelQueueMetrics\Facades\QueueMetrics;

$metrics = QueueMetrics::getJobMetrics(ProcessOrder::class);
echo "P95: {$metrics->duration->p95}ms, Health: {$metrics->health->score}/100";
```

**System metrics:**

```bash
composer require gophpeek/system-metrics
```

```php
use PHPeek\SystemMetrics\SystemMetrics;

$overview = SystemMetrics::overview()->getValue();
echo "CPU: {$overview->cpu->coreCount()} cores, Memory: {$overview->memory->usedPercentage()}%";
```

---

## Documentation

Full docs at [phpeek.com/docs](https://phpeek.com/docs)

---

## License

All packages are MIT licensed.
