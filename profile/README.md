# PHPeek

A platform for observing, understanding and operating modern PHP and Laravel systems — from low-level system signals to high-level application behaviour.

## Scope
PHPeek provides an integrated stack of inspection and operational components.  
It spans host-level metrics, PHP runtime processes, Laravel queues, FastCGI communication paths and container orchestration patterns.  
Metrics are only the foundation. The roadmap includes runtime signals, deep introspection, behavioural analysis, workload optimisation and autoscaling logic.

---

## Laravel

**laravel-queue-metrics**  
Production-grade queue instrumentation with low overhead. Tracks job execution, worker behaviour, throughput and latency, with automatic Prometheus exporting.  
https://github.com/gophpeek/laravel-queue-metrics

**laravel-queue-autoscale** *(coming)*  
Autoscaling driven by real queue pressure and measured worker load.  
https://github.com/gophpeek/laravel-queue-autoscale

**laravel-queue-monitor** *(coming)*  
Job-level execution tracking with metadata, history and replay.  
*(Repo pending.)*

**laravel-queue-dashboard** *(coming)*  
Visual inspection of queue state, worker efficiency and processing trends.  
*(Repo pending.)*

---

## PHP Runtime and System

**system-metrics**  
Host-level CPU, memory, load, disk and network signals collected directly from PHP. Forms the foundation for system-aware PHP runtimes.  
https://github.com/gophpeek/system-metrics

**phpeek-pm**  
A process manager for containerised multi-service workloads. Implements PID 1 behaviour, signal handling, zombie reaping, a configuration system and structured JSON logging.  
https://github.com/gophpeek/phpeek-pm

**baseimages** *(coming)*  
Unified PHP base images for development and production: hardened entrypoints, health checks, graceful shutdown and integrated Prometheus metric exporters.  
https://github.com/gophpeek/baseimages

---

## Go

**fcgx**  
A minimal, robust FastCGI client library for Go. Enables Go services and agents to communicate efficiently with PHP-based runtimes.  
https://github.com/gophpeek/fcgx

---

## Direction
Reveal how applications and systems actually behave under real workloads.  
Build a coherent operational layer that spans metrics, processes, runtimes, queues and container environments — enabling deeper insight, better decisions and smarter automation.
