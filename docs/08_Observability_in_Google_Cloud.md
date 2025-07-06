# Observability in Google Cloud

## Configure

- Compute Engine --> Ops Agent

- App Engine, GKE, Cloud Run, Cloud functions --> in-built, can be extended by writing to stdout/stderr via client libs

- User-defined metrics
    - Compute Engine: OpenTelemetry --> OpsAgent
    - GKE: OpenTelemetry --> GMP

## Monitoring Network

- VPC Flow Logs
    - Samples of send/receive (~ one out of ten packets)
    - Records from "VM perspective"
        - egress is OK
        - if ingress is blocked by firewall, it won't be logged
    - Enabled at subnet level

- Firewall Rules Logs
    - Enabled per rule

- Loadbalancer Logs

- Packet mirroring

- Network Intelligence Center
    - Flow Analyzer
    - Connectivity Tests
    - Performance Dashboard
    - Firewall Insights
    - Network Analyzer
    - Network Topology

## Investigate Application Performance

- Error Reporting
    - `f(Cloud Monitoring + Cloud logging)` --> Error reporting
    - Analyzes
        - Cloud Logging buckets in "global" region
        - Have the same source and destination GCP projects (can route the logs, then the dest project should own the logging bucket)
        - Have the CMEK "disabled"

- Cloud Trace
    - Spans --> Sub-routines

- Cloud Profiler
    - Language specific
    - CPU time --> actively working CPU time
    - Wall time --> real-world CPU time
    - Heap --> dynamically used memory
    - Allocated Heap --> requested or allocated memory by the system
    - Contention --> Competition for resources between threads and processes
    - Threads --> Individual units of executions

## Optimizing the Costs

- Bill estimation
    - Billing by SKU
    - Metrics management --> analyze metrics usage
    - Log-based metrics --> analyze log data volume

- Best Practices
    - Logging
        - Exclude logs
        - Export logs
        - Reduce Ops Agent usage
    - Metrics
        - Optimize/reduce metrics and label usage (reduce high cardinality labels)
        - Reduce Ops Agent usage
        - Reduce custom metrics usage
        - GMP
            - Reduce number of time series
            - Reduce number of samples collection
            - Configure local agrregation
    - Tracing
        - Use OpenTelemetry sampling
        - Use Cloud Trace API span quotas
        - Optimize 3rd party callers
