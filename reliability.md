# Reliability and limitations

## Inter-site link failure

The design uses redundant network paths and OSPF to detect changes in reachability and select an available alternate path. This addresses failures that may not cause the local CDN interface itself to go down.

## Gateway redundancy

A pair of remote gateways normally divides viewer-facing load balancing and upstream network forwarding duties. Each is designed to take over the other role if its peer becomes unavailable. The exact takeover mechanism, detection timers, route costs and recovery duration are not documented here.

## Storage and delivery

Persistent VOD storage is separated from short-lived live segments. Private cache and origin services serve on-demand content. A storage outage can still affect uncached VOD requests; caching and routing redundancy do not remove storage dependencies.

## Known limitations

- The central live delivery gateway remains a potential single point of failure in the described architecture.
- OSPF convergence is not a guarantee of seamless playback or survival of existing TCP sessions.
- No measured failover time, throughput, cache hit rate or availability target is asserted.
- This overview does not claim that every component is highly available.
- Failure simulations and reproducible verification belong in separate isolated labs, not in production.
