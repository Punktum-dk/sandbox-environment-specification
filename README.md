![Punktum dk Logo][DKHMLOGO]

# Punktum dk Sandbox Environment Specification

![Markdownlint Action][GHAMKDBADGE]
![Spellcheck Action][GHASPLLBADGE]

2026-07-15
Revision: 3.0

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
    - [Limitations](#epp-limitations)
  - [RP](#rp)
    - [Sandbox Access](#rp-sandbox-access)
    - [What You Can Test](#rp-what-you-can-test)
    - [Limitations](#rp-limitations)
  - [DAS](#das)
  - [WHOIS](#whois)
  - [RESTful WHOIS](#restful-whois)

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
This allows registrars to test their integrations against upcoming changes before they take effect in
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

3.0 2026-07-15

- Complete rewrite of the document, restructured around the individual
  sandbox services and their capabilities
- Removed the DSU service, which has been discontinued
- Added the RESTful WHOIS service
- Restructured sandbox limitations: limitations are now documented per
  service, each with a recommended workaround where available
- Removed limitations related to registrant management scenarios
  (self-service portal, order confirmation, privilege grants, role
  acceptance flows, and passwords), which are no longer applicable
  following the transition to registrar management on 1 July 2026
- Added limitation on creation of registrant managed domains
- Added the General section describing access, data persistence, service
  releases, and support
- Updated test data: dk-hostmaster.dk replaced by punktum.dk
- Updated all references to point to the current Punktum dk repositories
  on GitHub

2.9 2021-09-08

- Added new sections to the chapter on sandbox limitations on:
  - [DNS]
  - [Email]
  - [Passwords]

2.8 2021-09-02

- Added information on [WHOIS](#whois) service

2.7 2021-08-23

- Updated information on simulation of 3rd. party interaction for [ID-control]

2.6 2021-05-26

- Added more information on the limitations on [ID-control]

2.5 2021-05-14

- Added two more limitations to the section on sandbox limitations
  - [ID-control]
  - [Role Acceptance For Role Invitations]

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
are described below.

The sandbox environment is isolated from production. Operations carried out
in the sandbox, such as domain registrations and name server changes, have
no effect on production data, making the environment safe for development,
testing, and experimentation.

The sandbox environment does not support all features of the production
environment. Known limitations and recommended workarounds are described 
per service in the Sandbox Environment chapter

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

The service versions currently deployed to the sandbox environment are
listed in the [sandbox environment wiki][SANDWIKI].

#### Operations and Support

The sandbox environment is operated as a production-grade service. Do note,
however, that resolution of errors in the sandbox environment may take
longer than for errors in production.

For questions or issues regarding the sandbox environment, please contact
Punktum dk at [registrar@punktum.dk](mailto:registrar@punktum.dk) or use
the [registrar contact form][CONTACT].

<a id="epp"></a>
### EPP

The EPP (Extensible Provisioning Protocol) service is the primary
integration point for registrars and supports provisioning and management
of domains, contacts, and host objects. The service is described in the
[Punktum dk EPP Service Specification][EPPSPEC].

<a id="epp-sandbox-access"></a>
#### Sandbox Access

| Parameter | Value                          |
| --------- | ------------------------------ |
| Hostname  | epp-sandbox.dk-hostmaster.dk   |
| Port      | 700                            |

Access to the EPP sandbox service requires IP whitelisting and an EPP
sandbox user, please see [General](#general) for details. The EPP sandbox
user is created by the registrar in the sandbox RP.

For further details on integrating with the EPP service, including
transport and connection requirements, please refer to the
[Punktum dk EPP Service Specification][EPPSPEC].

<a id="epp-what-you-can-test"></a>
#### What You Can Test

The EPP sandbox service is suited for testing your EPP client
implementation and most registrar workflows, including:

- **Domain registration**, including the complete application flow.
  Domain applications submitted in the sandbox are processed by a real
  back-end service, so status changes and poll messages occur as they
  would in production.
- **Domain lifecycle management**, such as renewal, deletion, and restore.
- **Domain transfers** between registrars.
- **Contact management**, such as creating and updating contact objects.
- **Name server administration**, such as creating and updating host
  objects.
- **DNSSEC management**, such as adding and updating DS records for a
  domain.
- **Poll message handling**, including retrieval and acknowledgement of
  poll messages.

For details on the individual EPP commands and their syntax, please refer
to the [Punktum dk EPP Service Specification][EPPSPEC].

<a id="epp-limitations"></a>
#### Limitations

Please note that the business rules of the production environment also
apply in the sandbox environment. The limitations listed below are
specific to the sandbox environment.

- **ID-control cannot be completed:** ID-control of registrants is not
  available in the sandbox environment. A domain registered to a contact
  with a Danish address will not be activated, as the system will await
  an ID-control that cannot be completed. Note that as a sandbox-specific
  rule, contacts with a non-Danish address are exempt from ID-control.
  **Workaround:** Use contacts with a non-Danish address for testing
  domain registration, or indicate that you, as the registrar, have
  verified the registrant, using the
  [`dkhm:contact_verification`][CONTACTVERIFICATION] extension.
- **Name servers cannot be changed on a domain:** When changing the name
  servers of a domain, the system validates that the name servers answer
  authoritatively for the domain. As sandbox domains do not exist in the
  public DNS, this validation will fail, and the name server change will
  be rejected. Note that this only applies to changing the name servers
  of an existing domain; creating host objects and registering domains
  on name servers registered in the sandbox both work.
- **No emails are sent:** The sandbox environment does not send emails,
  neither to registrants nor to registrars. Workflows that depend on
  email, such as email-based acceptance flows, can therefore not be
  tested end-to-end.
  **Workaround:** Contact Punktum dk at
  [registrar@punktum.dk](mailto:registrar@punktum.dk) to receive examples
  of the emails sent in a given workflow.
- **Registrant managed domains cannot be created:** As of 1 July 2026,
  new domains can only be created under registrar management, and this
  also applies in the sandbox environment. Workflows involving registrant
  managed domains can therefore not be tested on self-created domains.
  **Workaround:** Contact Punktum dk at
  [registrar@punktum.dk](mailto:registrar@punktum.dk) to have registrant
  managed test data made available.
- **Domain transfers require a counterpart:** Testing transfers requires
  a second registrar account as the receiving or losing party.
  **Workaround:** Coordinate transfer testing with Punktum dk by
  contacting [registrar@punktum.dk](mailto:registrar@punktum.dk), or test
  in cooperation with another registrar.

<a id="rp"></a>
### RP

The RP (registrar portal) is a web-based portal for registrars, offering
management of domains and related objects, as well as administration of
the registrar account. The RP operates on the same registry data as the
EPP service, so domains and other objects can be managed interchangeably
through either service. The service is described in the
[Punktum dk RP Service Specification][RPSPEC].

<a id="rp-sandbox-access"></a>
#### Sandbox Access

| Parameter | Value                                |
| --------- | ------------------------------------ |
| URL       | https://rp-sandbox.dk-hostmaster.dk/ |

Access to the RP sandbox service requires IP whitelisting and an RP
sandbox user, please see [General](#general) for details. RP sandbox
users can only be created by Punktum dk and are created automatically as
part of the onboarding of new registrars.

If you do not have access to the RP sandbox, please contact Punktum dk at
[registrar@punktum.dk](mailto:registrar@punktum.dk) or via the
[registrar contact form][CONTACT].

<a id="rp-what-you-can-test"></a>
#### What You Can Test

The RP sandbox service is suited for testing and exploring most registrar
workflows through the portal, including:

- **Domain registration**, including the complete application flow.
  Domain applications submitted in the sandbox are processed by a real
  back-end service, so status changes occur as they would in production.
- **Domain lifecycle management**, such as renewal, deletion, and restore.
- **Domain transfers** between registrars.
- **Contact management**, such as creating and updating contacts.
- **Name server administration**, such as creating and updating name
  servers.
- **DNSSEC management**, such as adding and updating DS records for a
  domain.
- **User administration**, such as creating additional RP users and
  Service API users for the EPP and DAS sandbox services.

<a id="rp-limitations"></a>
#### Limitations

Please note that the business rules of the production environment also
apply in the sandbox environment. The limitations listed below are
specific to the sandbox environment.

- **ID-control cannot be completed:** ID-control of registrants is not
  available in the sandbox environment. A domain registered to a contact
  with a Danish address will not be activated, as the system will await
  an ID-control that cannot be completed. Note that as a sandbox-specific
  rule, contacts with a non-Danish address are exempt from ID-control.
  **Workaround:** Use contacts with a non-Danish address for testing
  domain registration, or indicate in the domain creation flow that you,
  as the registrar, have verified the registrant.
- **Name servers cannot be changed on a domain:** When changing the name
  servers of a domain, the system validates that the name servers answer
  authoritatively for the domain. As sandbox domains do not exist in the
  public DNS, this validation will fail, and the name server change will
  be rejected. Note that this only applies to changing the name servers
  of an existing domain; creating name servers and registering domains
  on name servers registered in the sandbox both work.
- **No emails are sent:** The sandbox environment does not send emails,
  neither to registrants nor to registrars. Workflows that depend on
  email, such as email-based acceptance flows, can therefore not be
  tested end-to-end.
  **Workaround:** Contact Punktum dk at
  [registrar@punktum.dk](mailto:registrar@punktum.dk) to receive examples
  of the emails sent in a given workflow.
- **Registrant managed domains cannot be created:** As of 1 July 2026,
  new domains can only be created under registrar management, and this
  also applies in the sandbox environment. Workflows involving registrant
  managed domains can therefore not be tested on self-created domains.
  **Workaround:** Contact Punktum dk at
  [registrar@punktum.dk](mailto:registrar@punktum.dk) to have registrant
  managed test data made available.
- **Domain transfers require a counterpart:** Testing transfers requires
  a second registrar account as the receiving or losing party.
  **Workaround:** Coordinate transfer testing with Punktum dk by
  contacting [registrar@punktum.dk](mailto:registrar@punktum.dk), or test
  in cooperation with another registrar.

<a id="das"></a>
### DAS

The DAS (Domain Availability Service) is an HTTP-based service offering
lookup of the availability of a given domain name. The service is
described in the [Punktum dk DAS Service Specification][DASSPEC].

| Parameter | Value                                  |
| --------- | -------------------------------------- |
| URL       | https://das-sandbox.dk-hostmaster.dk/  |

Access to the DAS sandbox service requires IP whitelisting and a Service
API user created in the sandbox RP, please see [General](#general) for
details.

The DAS sandbox service can be used for testing your DAS client
implementation, including availability lookups for both available and
registered domain names. The service reflects all domains registered in
the sandbox environment, including domains you have registered yourself
via EPP or RP.

The following test domains are registered in the sandbox environment and
can be used for lookups of registered domain names:

- punktum.dk
- eksempel.dk
- æøåöäüé.dk

<a id="whois"></a>
### WHOIS

The WHOIS service offers lookup of information on domain names, such as
registration status, name servers, and registrant and registrar
information. The service is described in the
[Punktum dk WHOIS Service Specification][WHOISSPEC].

| Parameter | Value                            |
| --------- | -------------------------------- |
| Hostname  | whois-sandbox.dk-hostmaster.dk   |
| Port      | 43                               |

The WHOIS sandbox service is publicly available and requires neither IP
whitelisting nor a sandbox user.

The WHOIS sandbox service can be used for testing your WHOIS client
implementation and for looking up domains registered in the sandbox
environment, including domains you have registered yourself via EPP or
RP.

The following test domains are registered in the sandbox environment and
can be used for lookups:

- punktum.dk
- eksempel.dk
- æøåöäüé.dk

<a id="restful-whois"></a>
### RESTful WHOIS

The RESTful WHOIS service is an HTTP-based alternative to the WHOIS
service, optimized for structured querying and machine-readable
responses. It offers lookup of information on domain names, name servers,
and registrars. The service is described in the
[Punktum dk RESTful WHOIS Service Specification][RESTWHOISSPEC].

| Parameter | Value                                    |
| --------- | ---------------------------------------- |
| URL       | https://whois-api-sandbox.dk-hostmaster.dk/ |

Access to the RESTful WHOIS sandbox service requires IP whitelisting,
please see [General](#general) for details.

The RESTful WHOIS sandbox service can be used for testing your client
implementation and for looking up domains registered in the sandbox
environment, including domains you have registered yourself via EPP or
RP.

The following test domains are registered in the sandbox environment and
can be used for lookups:

- punktum.dk
- eksempel.dk
- æøåöäüé.dk

[DKHMLOGO]: https://punktum.dk/sites/default/files/logo/dk_logo_symbol_1.png
[GHAMKDBADGE]: https://github.com/Punktum-dk/sandbox-environment-specification/workflows/Markdownlint%20Action/badge.svg
[GHASPLLBADGE]: https://github.com/Punktum-dk/sandbox-environment-specification/workflows/Spellcheck%20Action/badge.svg
[SANDWIKI]: https://github.com/Punktum-dk/sandbox-environment-specification/wiki
[EPPSPEC]: https://github.com/Punktum-dk/epp-service-specification
[DASSPEC]: https://github.com/Punktum-dk/das-service-specification
[WHOISSPEC]: https://github.com/Punktum-dk/whois-service-specification
[RESTWHOISSPEC]: https://github.com/Punktum-dk/whois-rest-service-specification
[CONTACT]: https://punktum.dk/en/contact-customer-service?lvl1=Registrars&lvl2=CSRegistrarOther
[STATUSPAGE]: https://status.punktum.dk
[CONTACTVERIFICATION]: https://github.com/Punktum-dk/epp-service-specification#dkhmcontactverification
[RPSPEC]: https://github.com/Punktum-dk/rp-service-specification
