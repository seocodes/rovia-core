# Backlog

This backlog is intentionally small. Items move when the previous behavior is understood and tested.

## Now: system design

- Trace one late delivery from an input file to an operator decision.
- Define the minimum CSV and XLSX columns.
- Define shipment and event identities.
- Define how repeated files and repeated rows are detected.
- Define import job states, retry rules, and terminal failure states.
- Define the first deterministic rules and the evidence each one shows.
- Choose the application, database, and queue technologies after these boundaries are clear.

## Next: deterministic version

- Create the application skeleton and database migrations.
- Import and validate CSV and XLSX files.
- Add the queue, worker, retries, and import status.
- Store shipments and historical events without duplicate imports.
- Build shipment timelines and derive the current state.
- Detect a small set of explainable exceptions.
- Add the exception inbox and operator decisions.
- Add unit and integration tests using synthetic files.
- Run tests in continuous integration.
- Run the application locally with Docker.

## Later

- Add simple exception and resolution metrics.
- Add one AI-assisted task with structured output and human correction.
- Create an evaluation dataset from reviewed AI outputs.
- Deploy a small private or synthetic-data environment in the cloud.
- Add authentication when there are multiple users or a reachable deployment.
- Revisit organization boundaries only when more than one organization is a real requirement.
- Consider configurable rule thresholds after real operational differences are observed.
- Create a connector only when a concrete data source requires one.

## Not planned for the initial project

- complete TMS features;
- route optimization;
- live vehicle tracking;
- autonomous operational decisions;
- invoicing or fiscal-document issuance;
- multiple simultaneous TMS integrations;
- microservices or Kubernetes without a measured need.
