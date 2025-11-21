# PHPeek

You don’t need to be a geek to peek.

## Scope
PHPeek is the base layer for inspecting how your systems and Laravel applications actually behave. Metrics are the first step. The roadmap includes deeper introspection, runtime signals, analysis tools and autoscaling logic.

## Projects
- **laravel-queue-metrics**  
  Measures queue pressure, throughput, latency and worker behaviour.
  https://github.com/gophpeek/laravel-queue-metrics

- **system-metrics**  
  Collects CPU, memory, load, disk and network signals. Released.  
  https://github.com/gophpeek/system-metrics

- **laravel-queue-autoscale** *(coming)*  
  Scaling driven by measurable pressure.  
  https://github.com/gophpeek/laravel-queue-autoscale

- **laravel-queue-monitor** *(coming)*  
  Tracks each job’s execution details with full processing metadata and supports job replay.  
  *(Repo will be added when published.)*

- **laravel-queue-dashboard** *(coming)*  
  Visual inspection of queue state and worker efficiency.  
  *(Repo will be added when published.)*

- **phpeek-pm**
  A process manager for multi-service workloads in containers. PID 1 signal handling with zombie reaping and configuration system. Structured JSON logging.  
  https://github.com/gophpeek/phpeek-pm
  
- **baseimages** *(coming)*  
  Streamlined PHP images for dev and production with hardened entrypoints, integrated health checks, clean shutdown logic and built-in Prometheus metric exporters.  
  https://github.com/gophpeek/baseimages
  
- **fcgx**  
  A minimal, robust, and modern FastCGI client library for Go.  
  https://github.com/gophpeek/fcgx
  

## Direction
Expose real behaviour instead of assumptions. Build a unified operational layer for Laravel and system environments.
