![DK Hostmaster Logo](https://www.dk-hostmaster.dk/sites/default/files/dk-logo_0.png)

# DK Hostmaster Sandbox Environment Specification

![GitHub Workflow build status badge markdownlint](https://github.com/DK-Hostmaster/sandbox-environment-specification/workflows/Markdownlint%20Workflow/badge.svg)

2019-07-30 Revision 2.2

## Table of Contents

<!-- MarkdownTOC bracket=round levels="1,2,3,4,5" indent="  " autoanchor="true" autolink="true" -->

- [Introduction](#introduction)
  - [About this Document](#about-this-document)
  - [License](#license)
  - [Document History](#document-history)
- [The .dk Registry in Brief](#the-dk-registry-in-brief)
- [Sandbox Environment in Brief](#sandbox-environment-in-brief)
- [Sandbox Environment](#sandbox-environment)
  - [Available Services](#available-services)
    - [DAS](#das)
    - [DSU](#dsu)
    - [EPP](#epp)
    - [RP](#rp)
  - [Available Data](#available-data)
  - [Additional Facilities](#additional-facilities)
    - [Domain Application Processing](#domain-application-processing)
- [Implementation Requirements](#implementation-requirements)

<!-- /MarkdownTOC -->

<a id="introduction"></a>
## Introduction

This document describes the sandbox environment offered by DK Hostmaster.

The document is targeted at registrars as audience.

<a id="about-this-document"></a>
### About this Document

This specification describes the consolidated DK Hostmaster Sandbox environment.

Changes to the document are listed Document History and changes to the sandbox environment are described here.

Any future additions and changes to the implementation are not within the scope of this document and will not be discussed or mentioned throughout this document.

This document is owned and maintained by DK Hostmaster A/S and must not be distributed without this information.

<a id="license"></a>
### License

This document is copyright by DK Hostmaster A/S and is licensed under the MIT License, please see the separate LICENSE file for details.

<a id="document-history"></a>
### Document History

2.2 2019-07-30

- Added more test data
- Improved description on test data

2.1 2019-07-30

- Added section on test data

2.0 2018-11-29

- DSU Service added to consolidated sandbox environment

1.0 2018-11-28

- Initial revision

<a id="the-dk-registry-in-brief"></a>
## The .dk Registry in Brief

DK Hostmaster is the registry for the ccTLD for Denmark (dk). The current model used in Denmark is based on a sole registry, with DK Hostmaster maintaining the central DNS registry.

<a id="sandbox-environment-in-brief"></a>
## Sandbox Environment in Brief

The consolidated sandbox environment supports several of the services offered by DK Hostmaster and in addition some of the facilities required to support the services.

The sandbox environment is isolated from production and does not support all features and assets of the production environment. The environment is planned to be extended and information on these extensions will be described here as the modifications are scheduled.

Limitations and special circumstances are documented in the specifications for the separate services.

<a id="sandbox-environment"></a>
## Sandbox Environment

The services and components deployed to the sandbox environment are listed in [the Wiki](https://github.com/DK-Hostmaster/sandbox-environment-specification/wiki) with versions and other relevant information.

<a id="available-services"></a>
### Available Services

DK Hostmaster offers the following services on the sandbox environment:

<a id="das"></a>
#### DAS

- `https://das-sandbox.dk-hostmaster.dk/`

<a id="dsu"></a>
#### DSU

- `https://dsu-sandbox.dk-hostmaster.dk/`

<a id="epp"></a>
#### EPP

- `epp-sandbox.dk-hostmaster.dk` port `700`

<a id="rp"></a>
#### RP

- `https://rp-sandbox.dk-hostmaster.dk/`

<a id="available-data"></a>
### Available Data

The general test data available in the sandbox environment are currently:

- `dk-hostmaster.dk`
- `waiting-list.dk`
- `enqueued.dk`
- `æøåöäüé.dk`
- `domaeneklager.dk`
- `domæneklager.dk`
- `domaeneklagenaevnet.dk`
- `domæneklagenævnet.dk`
- `eksempel.dk`

The different services listed above might specify if the test data are put to special use, specific to the service in question and hence only documented per service in the relevant service specification.

<a id="additional-facilities"></a>
### Additional Facilities

<a id="domain-application-processing"></a>
#### Domain Application Processing

The sandbox environment also holds a back-end service component for domain processing, which processes domain applications.

<a id="implementation-requirements"></a>
## Implementation Requirements

Please see the specific service specification for details:

- [DK Hostmaster DAS Service Specification](https://github.com/DK-Hostmaster/das-service-specification)
- For details on the service version etc. please see [the DAS Service Wiki](https://github.com/DK-Hostmaster/das-service-specification/wiki)
- [DK Hostmaster DSU Service Specification](https://github.com/DK-Hostmaster/dsu-service-specification)
- For details on the service version etc. please see [the DSU Service Wiki](https://github.com/DK-Hostmaster/dsu-service-specification/wiki)
- [DK Hostmaster EPP Service Specification](https://github.com/DK-Hostmaster/epp-service-specification)
- For details on the service version etc. please see [the EPP Service Wiki](https://github.com/DK-Hostmaster/epp-service-specification/wiki)
- [DK Hostmaster RP Service Specification](https://github.com/DK-Hostmaster/rp-service-specification)
- For details on the service version etc. please see [the RP Service Wiki](https://github.com/DK-Hostmaster/rp-service-specification/wiki)
