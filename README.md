# DK Hostmaster Sandbox Environment Specification

2018-11-28 Revision 1.00

## Table of Contents

<!-- MarkdownTOC bracket=round levels="1,2,3,4,5" indent="  " -->

- [Introduction](#introduction)
  - [About this Document](#about-this-document)
  - [License](#license)
  - [Document History](#document-history)
- [The .dk Registry in Brief](#the-dk-registry-in-brief)
- [Sandbox Environment in Brief](#sandbox-environment-in-brief)
- [Sandbox Environment](#sandbox-environment)
  - [Available Services](#available-services)
    - [EPP](#epp)
    - [RP](#rp)
    - [DAS](#das)
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

1.00 2018-11-28

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

The services and components deployed to the sandbox environment are listed in the Wiki with versions and other relevant information.

<a id="available-services"></a>
### Available Services

DK Hostmaster offers the following services on the sandbox environment:

<a id="epp"></a>
#### EPP

- `epp-sandbox.dk-hostmaster.dk` port `700`

<a id="rp"></a>
#### RP

- `https://rp-sandbox.dk-hostmaster.dk/`

<a id="das"></a>
#### DAS

- `https://das-sandbox.dk-hostmaster.dk/`

<a id="additional-facilities"></a>
### Additional Facilities

<a id="domain-application-processing"></a>
#### Domain Application Processing

The sandbox environment also holds a back-end service component for domain processing, which processes domain applications.

<a id="implementation-requirements"></a>
## Implementation Requirements

Please see the specific service specification for details:

- [DK Hostmaster EPP Service Specification](https://github.com/DK-Hostmaster/epp-service-specification)
- For details on the service version etc. please see [the EPP Service Wiki](https://github.com/DK-Hostmaster/epp-service-specification/wiki)
- [DK Hostmaster DAS Service Specification](https://github.com/DK-Hostmaster/das-service-specification)
- For details on the service version etc. please see [the DAS Service Wiki](https://github.com/DK-Hostmaster/das-service-specification/wiki)
- [DK Hostmaster RP Service Specification](https://github.com/DK-Hostmaster/rp-service-specification)
- For details on the service version etc. please see [the RP Service Wiki](https://github.com/DK-Hostmaster/rp-service-specification/wiki)
