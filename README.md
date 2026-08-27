# Rovia

Rovia is a learning project about logistics exceptions. It takes shipment data, rebuilds what happened, applies clear rules, and helps an operator decide what needs attention.

> **Project status:** early design. Rovia is not a production system, a validated commercial offer, or a replacement for a TMS.

## Planned first version

The first version will:

- import shipment and event data from CSV and XLSX files;
- validate required fields, dates, identifiers, and event types;
- report invalid, incomplete, and duplicate records;
- process imports through a background queue;
- make repeated imports safe, without duplicating shipments or events;
- preserve the shipment event history and derive the current state;
- detect exceptions with a small set of deterministic rules;
- show the rule, reason, and events behind each exception;
- let an operator resolve, reject, or correct an exception;
- keep decision history and a few operational metrics.

There is no working release yet. The repository starts with documentation so the system can be understood before implementation begins.

## Processing flow

```text
CSV or XLSX
    -> upload checks
    -> import job
    -> background worker
    -> validation report
    -> shipments and event history
    -> derived shipment state
    -> deterministic rules
    -> explainable exception
    -> operator decision
```

The queue is part of the first version because reliable file processing is one of the learning goals. It does not mean that Rovia will start as a distributed system. The initial direction is one application, one worker, one database, and one queue.

## AI comes later

The deterministic flow must work before AI is added.

AI may later classify a free-text occurrence, summarize recorded events, or suggest an action from an approved playbook. It will not create exceptions or make the final decision. An operator must review or correct its output.

## What Rovia is not

Rovia is not planned as:

- a complete TMS;
- a route optimization system;
- a live vehicle tracker;
- an autonomous decision maker;
- an invoicing or fiscal-document system;
- a collection of simultaneous TMS integrations.

Tracking, notifications, and dashboards already exist in common logistics systems. They may appear here as supporting interfaces, not as an original commercial advantage.

## Learning goals

Rovia is being built step by step to study:

- REST API design;
- relational data modeling and migrations;
- CSV and XLSX ingestion;
- validation, normalization, deduplication, and idempotency;
- queues, workers, retries, and failure states;
- deterministic decision rules;
- testing with synthetic datasets;
- Docker and basic cloud operation;
- limited AI assistance with human review.

Readable code and controlled dependencies matter more than the number of technologies used.

## Data safety

Only synthetic examples belong in this repository. Real company files, credentials, customer-specific rules, and production data must not be committed.

Before Rovia handles authorized real data, the project will need a defined purpose, access rules, retention period, deletion process, and review of any external AI service involved.

## Repository map

```text
.
├── BACKLOG.md
├── LICENSE
├── README.md
├── docs/
│   └── system-design.md
├── samples/
│   └── synthetic/
├── src/
└── tests/
```

The [backlog](BACKLOG.md) separates current work from later ideas. The [system design notes](docs/system-design.md) record the decisions that should be understood before implementation.

## License

Rovia is available under the [Apache License 2.0](LICENSE). The license allows use, modification, distribution, and commercial use under its terms.
