# Heimdall Home Lab

Heimdall is my home lab project for building and documenting a real infrastructure environment. The project includes networking, security monitoring, virtualization, storage, media services, automation, environmental monitoring, and a planned hybrid AI system.

The purpose of this project is not just to have a lot of equipment running in one place. The purpose is to understand how the systems work together, keep the important parts separated, test what I build, and document the results so I can come back to them later or explain them to someone else.

This README is being prepared for a public repository. It only describes the lab at a general level. Private access information, credentials, internal addresses, API keys, and other proprietary information will not be placed here.

## What I am building

The Heimdall lab is built around several different functions. Some of these functions are already operating, while others are still being built or tested.

The main areas are:

- Network routing and firewall security
- Core switching and internal connectivity
- Virtual machines and infrastructure services
- Dedicated security monitoring
- A separate VPN and download system
- Storage and media services
- Rack management and environmental monitoring
- A planned local-AI worker system

Keeping these functions separate is important. For example, the system used for security monitoring should not have to depend on the same host that runs every household service. The download system should not be treated as the same thing as the administrative remote-access system. Storage should be able to be expanded or repaired without making the entire infrastructure host part of the same problem.

## Basic architecture

```text
Internet service
        |
Firewall and routing
        |
Core network switch
        |
        +-- Virtualization and infrastructure services
        +-- Dedicated security monitoring
        +-- Separate VPN/download system
        +-- Storage and media systems
        +-- Rack management and environmental monitoring
        +-- Planned local-AI worker systems
```

The lab uses a normal residential Internet connection and a faster internal network design. These are not the same thing. Internet speed controls how fast the lab can communicate outside the house. The internal network is important for moving files between systems, working with storage, moving virtual-machine data, handling backups, and supporting media services.

## Network and security

The firewall and routing system controls the connection between the Internet and the internal network. It is also responsible for the rules that determine which systems are allowed to communicate with each other.

The internal network is built around a core switch. Other systems connect through that core, including the virtualization host, security-monitoring system, storage, management equipment, and future access-layer devices.

Network segmentation is a planned part of the design. A network diagram or proposed VLAN is not the same thing as a deployed and tested security boundary. I will document a boundary as complete only after the configuration and the expected traffic have been verified.

## Virtualization and infrastructure services

The virtualization host provides a place for infrastructure services and other approved applications to run. Virtual machines and containers allow services to be separated by role without requiring a separate physical computer for every small service.

This does not mean that virtualization removes dependencies. If several services depend on one host, that host is still a shared point of failure. The purpose of documenting the services and their relationships is to make those dependencies visible instead of pretending they do not exist.

## Security monitoring

Security monitoring is kept separate from general application hosting. Its job is to collect approved security information, identify findings, and support investigation.

A monitoring system being installed does not automatically mean that every device is covered. Agent enrollment, log sources, alert behavior, retention, and current health all need to be checked. Historical evidence is useful, but it is not the same as a current test.

## VPN and download system

The VPN and download workload is kept separate from the main household services and administrative systems. This provides a clearer boundary and makes it easier to understand what happens if that system is unavailable or misconfigured.

The commercial VPN used for downloads should not be confused with the separate path used to administer the lab remotely. They serve different purposes and need different security decisions.

## Storage and media

Storage, media applications, and downloads are related, but they are not the same role. The media services can manage requests and playback, the download system can handle its own protected workload, and the storage system can provide the space used by those services.

Keeping those roles separate makes future changes easier. It also makes the recovery plan clearer because a storage outage, an application outage, and a VPN outage do not all have the same cause or the same repair.

## Rack management and environmental monitoring

The rack-management system is intended to provide the human administration surface for the lab. Environmental monitoring is intended to report conditions such as temperature and fan operation.

Safety-related actions should remain deterministic. The lab should not depend on an AI model to decide whether equipment needs to be protected from a heat or cooling problem. AI may help interpret information in the future, but the underlying safety controls must remain predictable.

## Hybrid AI direction

The AI part of Heimdall is being designed as a hybrid system. Cloud services will provide selected reasoning and research capabilities, while local workers will handle approved work that makes sense to run locally.

The planned orchestration layer will decide where a request should go, what tools are available, what information needs to be preserved, and when a result needs to be reviewed. The infrastructure systems themselves will continue to control their own configuration and execution.

The local worker fleet, final model choices, and production orchestration are still being evaluated. They should not be described as fully deployed until they have been installed, tested, and documented.

## Heimdall Command Center

The Command Center is a read-only view of the Heimdall environment. It is intended to make relationships between systems easier to understand and to display selected observations from existing services.

The Command Center should show real observations when they are available. If a source is unavailable, old, or stale, it should say so. It should not replace missing information with made-up sample data or turn a missing measurement into a healthy status.

The Command Center is not intended to replace the firewall, monitoring system, virtualization platform, storage system, or other service that owns the information. It is also not a production editing system, a hardware-control system, or an automatic remediation engine.

## How status is documented

One of the most important parts of this project is keeping completed work separate from planned work. The following terms are used for that reason:

| Status | Meaning |
|---|---|
| **Completed** | The work was performed and the stated result was verified. |
| **Recorded operating** | Earlier evidence showed that it worked, but it may not have been tested again recently. |
| **Purchased or received** | The item was acquired, but that does not prove it was installed. |
| **Confirmed direction** | The design choice was accepted, but the deployment is not necessarily complete. |
| **Planned** | The work is intended but has not been completed. |
| **Unresolved** | Something still needs to be confirmed, tested, or decided. |
| **Historical** | The information describes an older state or an option that may no longer be active. |

When I document a system or service, I want to answer five questions:

1. What is it supposed to do?
2. What evidence shows its current status?
3. When and how was it checked?
4. What is still unknown?
5. What is the next safe test or acceptance step?

## What will not be published

This repository is intended to be public, so the following information must stay out of it:

- Passwords and passphrases
- API keys, access tokens, private keys, certificates, and recovery codes
- Private remote-access instructions
- Sensitive internal addresses and management paths
- Personal information and private documents
- Raw service exports and unreviewed configuration backups
- Screenshots that show private interfaces or identifying information
- Proprietary material that I do not have permission to redistribute
- Claims that turn a plan, purchase, or historical record into a completed deployment

Files will be reviewed before they are committed. That review includes the text, code, comments, screenshots, filenames, links, metadata, logs, and example values. Removing sensitive information after it has already been published is not an adequate protection plan.

## Repository structure

```text
.
├── README.md
├── architecture/
│   └── README.md
├── projects/
│   ├── README.md
│   ├── command-center/
│   │   └── README.md
│   ├── environmental-monitoring/
│   │   └── README.md
│   ├── nextcloud-migration/
│   │   └── README.md
│   └── security-monitoring/
│       └── README.md
├── runbooks/
│   └── README.md
├── diagrams/
│   └── README.md
└── scripts/
    └── README.md
```

The directory READMEs are starting points. They will be filled in one document at a time after the material has been reviewed and approved for publication.

## Planned next steps

- Review this README and approve the overall wording
- Add a sanitized architecture diagram
- Document the Command Center without exposing private service details
- Add project pages based on verified evidence
- Add safe runbooks without private recovery information
- Add diagrams and scripts only after they have been reviewed
- Document recovery tests and lessons learned
- Continue evaluating the local-AI worker and orchestration design

## License

This project uses the MIT License for original code and scripts in this repository. Third-party software, vendor documentation, trademarks, and other materials remain subject to their respective licenses.
