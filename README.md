![DK Hostmaster Logo][DKHMLOGO]

# DK Hostmaster Sandbox Environment Specification

![Markdownlint Action][GHAMKDBADGE]
![Spellcheck Action][GHASPLLBADGE]

2026-07-14
Revision 3.0

## Table of Contents

<!-- MarkdownTOC bracket=round levels="1,2,3,4,5" indent="  " autoanchor="true" autolink="true" -->

- [Introduction](#introduction)
  - [About this Document](#about-this-document)
  - [License](#license)
  - [Document History](#document-history)
- [The .dk Registry in Brief](#the-dk-registry-in-brief)
- [Sandbox Environment in Brief](#sandbox-environment-in-brief)
- [Sandbox Environment](#sandbox-environment)
  - [General](#general)
  - [EPP](#epp)
    - [Sandbox Access](#epp-sandbox-access)
    - [What You Can Test](#epp-what-you-can-test)
    - [Test Data](#epp-test-data)
    - [Limitations](#epp-limitations)
  - [RP](#rp)
    - [Sandbox Access](#rp-sandbox-access)
    - [What You Can Test](#rp-what-you-can-test)
    - [Test Data](#rp-test-data)
    - [Limitations](#rp-limitations)
  - [DAS](#das)
    - [Sandbox Access](#das-sandbox-access)
    - [What You Can Test](#das-what-you-can-test)
  - [WHOIS](#whois)
    - [Sandbox Access](#whois-sandbox-access)
    - [What You Can Test](#whois-what-you-can-test)
  - [RESTful WHOIS](#restful-whois)
    - [Sandbox Access](#restful-whois-sandbox-access)
    - [What You Can Test](#restful-whois-what-you-can-test)

<!-- /MarkdownTOC -->

<a id="introduction"></a>
## Introduction

This document describes the sandbox environment offered by Punktum dk, the
registry for the .dk country code top-level domain (ccTLD).

The sandbox environment allows registrars to develop and test their
integrations with the .dk registry services in isolation from production.
Typical use cases include testing EPP client implementations, onboarding of
new registrars, and testing of domain registration, name server
administration, and poll message handling.

New service releases may be deployed to the sandbox environment prior to being released to production.
This allows registrars totest their integrations against upcoming changes before they take effect in
production.

The document is intended for a technical audience at registrars integrating
with the Punktum dk services.

<a id="about-this-document"></a>
### About this Document

This specification describes the Punktum dk sandbox environment.

Changes to this document and to the sandbox environment are listed in the
[Document History](#document-history) below.

This document is owned and maintained by Punktum dk A/S and must not be
distributed without this information.

<a id="license"></a>
### License

This document is copyright by Punktum dk A/S and is licensed under the MIT
License, please see the separate LICENSE file for details.

<a id="document-history"></a>
### Document History

2.9 2021-09-08

- Added new sections to the chapter on sandbox limitations on:
  - [DNS](#dns)
  - [Email](#email)
  - [Passwords](#passwords)

2.8 2021-09-02

- Added information on [WHOIS](#whois) service

2.7 2021-08-23

- Updated information on simulation of 3rd. party interaction for [ID-control](#id-control)

2.6 2021-05-26

- Added more information on the limitations on [ID-control](#id-control)

2.5 2021-05-14

- Added two more limitations to the section on sandbox limitations
  - [ID-control](#id-control)
  - [Role Acceptance For Role Invitations](#role-acceptance-for-role-invitations)

2.4 2021-05-13

- Added mention of tech-announce and linked to page in mailing list for subscription details

2.3 2021-05-07

- Added new section on sandbox limitations

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

Punktum dk is the registry for the Danish country-code top-level domain
(.dk) and maintains the central DNS registry.

Punktum dk offers a number of services for interacting with the registry,
such as [EPP][EPPSPEC], [DAS][DASSPEC], [WHOIS][WHOISSPEC], and
[RESTful WHOIS][RESTWHOISSPEC]. These services are described in separate
specifications.

The sandbox environment described in this document makes these services
available for test purposes.

<a id="sandbox-environment-in-brief"></a>
## Sandbox Environment in Brief

The sandbox environment offers the Punktum dk services relevant for
registrar integration: EPP, DAS, WHOIS, RESTful WHOIS, and the registrar
portal (RP). The individual services and how to access them in the sandbox
are described in [Available Services](#available-services).

The sandbox environment is isolated from production. Operations carried out
in the sandbox, such as domain registrations and name server changes, have
no effect on production data, making the environment safe for development,
testing, and experimentation.

The sandbox environment does not support all features of the production
environment. Known limitations and recommended workarounds are described in
[Sandbox Limitations](#sandbox-limitations).

<a id="sandbox-environment"></a>
## Sandbox Environment

<a id="general"></a>
### General

#### Access
Access to the sandbox services requires IP whitelisting, with the exception
of the WHOIS service, which is publicly available. In addition, the EPP,
DAS, and RP services require a sandbox user.

| Service       | IP whitelisting | Sandbox user |
| ------------- | --------------- | ------------ |
| EPP           | Required        | Required     |
| RP            | Required        | Required     |
| DAS           | Required        | Required     |
| WHOIS         | Not required    | Not required |
| RESTful WHOIS | Required        | Not required |

Sandbox access is set up as follows:

- **New registrars** automatically have a sandbox user created for the RP
  as part of the onboarding process.
- **Existing registrars** without sandbox access can request a sandbox
  user by contacting Punktum dk at
  [registrar@punktum.dk](mailto:registrar@punktum.dk) or via the
  [registrar contact form][CONTACT]. Sandbox users for the RP can only be
  created by Punktum dk.
- **IP whitelisting** for the sandbox services is managed by the registrar
  via the production RP.
- **Service API users** for the EPP and DAS sandbox services can be
  created by the registrar in the sandbox RP, once access to the sandbox
  RP has been established.

#### Data

Data created in the sandbox environment is persistent and is not reset. The
sandbox services share the same data set, so a domain registered via EPP or
RP is reflected across all sandbox services and can, for
example, be queried via DAS or looked up via WHOIS.

#### Service Releases

New XSD versions for the EPP service are deployed to the sandbox
environment three months prior to release to production. This allows
registrars to test and adapt their integrations before changes take effect
in production. Other changes and releases may be deployed to the sandbox
environment with shorter notice.

Releases are announced in the [Document History](#document-history) of
this document, on the [Punktum dk status page][STATUSPAGE], and via the
Punktum dk registrar newsletter. To subscribe to the newsletter, please
contact Punktum dk at [registrar@punktum.dk](mailto:registrar@punktum.dk).

#### Operations and Support

The sandbox environment is operated as a production-grade service. Do note,
however, that resolution of errors in the sandbox environment may take
longer than for errors in production.

For questions or issues regarding the sandbox environment, please contact
Punktum dk at [registrar@punktum.dk](mailto:registrar@punktum.dk) or use
the [registrar contact form][CONTACT].

[DKHMLOGO]: https://www.dk-hostmaster.dk/sites/default/files/dk-logo_0.png
[GHAMKDBADGE]: https://github.com/DK-Hostmaster/sandbox-environment-specification/workflows/Markdownlint%20Action/badge.svg
[GHASPLLBADGE]: https://github.com/DK-Hostmaster/sandbox-environment-specification/workflows/Spellcheck%20Action/badge.svg
[IMPLGUIDE]: https://www.dk-hostmaster.dk/en/implementation-guide-registration-dk
[DKHMMAIL]: https://www.dk-hostmaster.dk/en/mailing-lists
[DKHMEPPSPEC]: https://github.com/DK-Hostmaster/whois-service-specification
[DKHMRPSPEC]: https://github.com/DK-Hostmaster/whois-service-specification
[DKHMDASSPEC]: https://github.com/DK-Hostmaster/das-service-specification
[DKHMDSUSPEC]: https://github.com/DK-Hostmaster/dsu-service-specification
[DKHMWHOISSPEC]: https://github.com/DK-Hostmaster/whois-service-specification
[DKHMSANDWIKI]: https://github.com/DK-Hostmaster/sandbox-environment-specification/wiki
[DKHMEPPWIKI]: https://github.com/DK-Hostmaster/epp-service-specification/wiki
[DKHMRPWIKI]: https://github.com/DK-Hostmaster/rp-service-specification/wiki
[DKHMDASWIKI]: https://github.com/DK-Hostmaster/das-service-specification/wiki
[DKHMDSUWIKI]: https://github.com/DK-Hostmaster/dsu-service-specification/wiki
[DKHMWHOISWIKI]: https://github.com/DK-Hostmaster/whois-service-specification/wiki
[EPPSPEC]: https://github.com/Punktum-dk/epp-service-specification
[DASSPEC]: https://github.com/Punktum-dk/das-service-specification
[WHOISSPEC]: https://github.com/Punktum-dk/whois-service-specification
[RESTWHOISSPEC]: https://github.com/Punktum-dk/whois-rest-service-specification
[CONTACT]: https://punktum.dk/en/contact-customer-service?lvl1=Registrars&lvl2=CSRegistrarOther
[STATUSPAGE]: https://status.punktum.dk
