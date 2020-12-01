# SXO-workflows
Interesting workflows for Cisco SecureX Orchestration

## Handle MISP IOCs with filter
Playbook steps:

1.	Get Indicators - Make a generic http request to a web hosted IOC JSON file in MISP format (https://www.misp-standard.org/rfc/misp-standard-core.html), parse it and store the indicators.
2.	Parse IOCs - from raw text using SecureX Threat Response Inspect API
3.	Enrich Observables - with SecureX Threat Response Enrich API to find any global sightings (in integrated threat feeds) and more importantly local sightings/targets (in integrated security modules like Umbrella, AMP, etc.). Filter what is considered NOT malicious, and store these observables in a table. (Note: focusing on NON malicious IoCs here, because we are assuming that the malicious ones have already been blocked by the security products, and we want to investigate on unknown threats, instead.)
4.	Create Casebook - Format the observables in the right JSON, and use CTR to create a new casebook.
