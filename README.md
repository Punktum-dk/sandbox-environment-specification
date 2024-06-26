![DK Hostmaster Logo][DKHMLOGO]

# DK Hostmaster Sandbox Environment Specification

![Markdownlint Action][GHAMKDBADGE]
![Spellcheck Action][GHASPLLBADGE]

2021-09-08
Revision 2.9

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
    - [WHOIS](#whois)
  - [Available Data](#available-data)
  - [Additional Facilities](#additional-facilities)
    - [Domain Application Processing](#domain-application-processing)
- [Implementation Requirements](#implementation-requirements)
- [Sandbox Limitations](#sandbox-limitations)
  - [Self-service Portal](#self-service-portal)
  - [Domain Creation and Order Confirmation](#domain-creation-and-order-confirmation)
  - [Privilege Grants](#privilege-grants)
  - [Role Acceptance For Domain Applications](#role-acceptance-for-domain-applications)
  - [Host and Role Acceptance For Name Server Applications](#host-and-role-acceptance-for-name-server-applications)
  - [ID-control](#id-control)
  - [Role Acceptance For Role Invitations](#role-acceptance-for-role-invitations)
  - [DNS](#dns)
  - [Email](#email)
  - [Passwords](#passwords)

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

DK Hostmaster is the registry for the ccTLD for Denmark (dk). The current model used in Denmark is based on a sole registry, with DK Hostmaster maintaining the central DNS registry.

<a id="sandbox-environment-in-brief"></a>
## Sandbox Environment in Brief

The consolidated sandbox environment supports several of the services offered by DK Hostmaster and in addition some of the facilities required to support the services.

The sandbox environment is isolated from production and does not support all features and assets of the production environment. The environment is planned to be extended and information on these extensions will be described here as the modifications are scheduled.

Limitations and special circumstances are documented in the specifications for the separate services.

<a id="sandbox-environment"></a>
## Sandbox Environment

The services and components deployed to the sandbox environment are listed in [the Wiki][DKHMSANDWIKI] with versions and other relevant information.

Updates are announced via our tech-announce mailing list.

Please see the [information page][DKHMMAIL] for details on subscribing etc.

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

<a id="whois"></a>
#### WHOIS

- `whois-sandbox.dk-hostmaster.dk` port `43`

<a id="available-data"></a>
### Available Data

The general test data available in the sandbox environment are currently:

#### Domains

| Domain           | Status |
| ---------------- | ------ |
| dk-hostmaster.dk | Active |
| eksempel.dk      | Active |
| æøåöäüé.dk       | Active |

The different services listed above might specify if the test data are put to special use, specific to the service in question and hence only documented per service in the relevant service specification.

<a id="additional-facilities"></a>
### Additional Facilities

<a id="domain-application-processing"></a>
#### Domain Application Processing

The sandbox environment also holds a back-end service component for domain processing, which processes domain applications.

<a id="implementation-requirements"></a>
## Implementation Requirements

Please see the specific service specification for details:

- [DK Hostmaster DAS Service Specification][DKHMDASSPEC]
- For details on the service version etc. please see [the DAS Service Wiki][DKHMDASWIKI]
- [DK Hostmaster DSU Service Specification][DKHMDSUSPEC]
- For details on the service version etc. please see [the DSU Service Wiki][DKHMDSUWIKI]
- [DK Hostmaster EPP Service Specification][DKHMEPPSPEC]
- For details on the service version etc. please see [the EPP Service Wiki][DKHMEPPWIKI]
- [DK Hostmaster RP Service Specification][DKHMRPSPEC]
- For details on the service version etc. please see [the RP Service Wiki][DKHMRPWIKI]
- [DK Hostmaster WHOIS Service Specification][DKHMWHOISSPEC]
- For details on the service version etc. please see [the WHOIS Service Wiki][DKHMWHOISWIKI]

<a id="sandbox-limitations"></a>
## Sandbox Limitations

<a id="self-service-portal"></a>
### Self-service Portal

As listed under the available services, a self-service portal aimed at end-users, meaning non-registrars is not available.

This mean that processes relying on registrant interaction are not possible, simulation can be implemented where this is possible, please see the list of specific limitations below.

<a id="domain-creation-and-order-confirmation"></a>
### Domain Creation and Order Confirmation

As described in the ["Implementation guide for registration of .dk"][IMPLGUIDE] there are two methods for registration of domain names.

1. Method 1: Requires that the accept of terms and conditions is done at the registrar and this is communicated via the application
1. Method 2: Requires that the accept of terms and conditions is done at the registry (with DK Hostmaster)

Method 2 can at this time not be simulated, as described in the section on the self-service portal.

The recommended way to a bypass this is by using method 1, even though this might not match you final implementation.

The bypass can be accomplished by adding a time stamp to the application, whether it is via: EPP or the registrar portal (RP)

Please see the below references for details:

- [DK Hostmaster EPP Service Specification: create domain](https://github.com/DK-Hostmaster/epp-service-specification#create-domain)
- [DK Hostmaster RP Service Specification: Domain Application](https://github.com/DK-Hostmaster/rp-service-specification#domain-application)

<a id="privilege-grants"></a>
### Privilege Grants

When operations are being completed in the sandbox services, privileges might change and privileges are granted and revoked based on business rules.

The privileges and business rules implemented in the sandbox environment are unchanged from the production environment and hence this can be quite strict.

We aim to implement simulated interactions with external components or user entities where possible to simulate a production like flow and to avoid any blocking process steps.

When an application is approved and a domain is created, it requires an acknowledgement from our finance system. A finance system is not available in our sandbox environment so this is simulated. This mean that the initial privileges granted to registrant, registrar etc. are activated.

<a id="role-acceptance-for-domain-applications"></a>
### Role Acceptance For Domain Applications

When an application is processed and the contacts assigned to the roles of:

- Proxy/admin
- Billing

Are pointing to user entities:

- not equal to the registrant
- not equal to the applicant (registrar)
- not a member of the registrar account group

An accept of the role is required.

In production this is accomplished using the self-service portal.

As stated in the section on the self-service portal, a instance of this portal is not available in the sandbox environment, so this accept cannot be collected.

Currently the acceptance is not simulated either.

The recommendation is to point to users associated with the registrar account group, so the collection is not required.

For details on registrar account groups, please see - [DK Hostmaster RP Service Specification: registrar account group](https://github.com/DK-Hostmaster/rp-service-specification#registrar-account-group)

<a id="host-and-role-acceptance-for-name-server-applications"></a>
### Host and Role Acceptance For Name Server Applications

When an application for creation of a name server is processed there are a number of possible scenarios depending on the data submitted with the application.

If the hostname of the name server is a subordinate to to a .dk domain name and the domain name is under registrant management the application require the approval of the registrant.

This approval has to be accomplished in our self-service platform. So this is currently not possible.

For domain names under registrar management, this approval is not necessary.

To bypass this step, it is recommended to create name servers for domain names under registrar management and in own portfolio.

See additional references:

- [DK Hostmaster EPP Service Specification: create host](https://github.com/DK-Hostmaster/epp-service-specification#create-domain)
- [DK Hostmaster RP Service Specification: Name Server Application](https://github.com/DK-Hostmaster/rp-service-specification#name-server-application)

Next up is the evaluation of the designated name server administrator (NSA).

1. If the designated user is the same as the requestor, approval of the role should not required (it is implicit)
1. If the requester and the designated user is in the same registrar account group the same rule apply
1. If the designated user is not the same as the requester and they are not related by group, the role has to be accepted by the designed name server administrator
    - If the user is not in a registrar group, the user has to accept the role via the self-service portal, which is currently not available in the sandbox environment
    - If the user is in another registrar group, this has to be accomplished in the registrar portal. Do note that this is a somewhat constructed  scenario, since it would mean that name server administrators are appointed across registrar groups, there is however no reason not to support this, since it comes with the implementation, which handles the above scenario

To bypass this step, it is recommended to appoint name server administrators in own registrar account group.

For details on registrar account groups, please see - [DK Hostmaster RP Service Specification: registrar account group](https://github.com/DK-Hostmaster/rp-service-specification#registrar-account-group)

See the same additional references for details on name server/host creation:

- [DK Hostmaster EPP Service Specification: create host](https://github.com/DK-Hostmaster/epp-service-specification#create-domain)
- [DK Hostmaster RP Service Specification: Name Server Application](https://github.com/DK-Hostmaster/rp-service-specification#name-server-application)

<a id="id-control"></a>
### ID-control

The requirement for ID-control cannot currently by bypassed.

We have implemented a sandbox feature, simulating the interaction with 3rd. parties, meaning designated registrants, which have been selected for manual ID-control all pass an ID-control check.

Over all the scenarios can be divided as follows:

- all users requiring ID-control using NemID, are kept in the state requiring this. The criteria is currently users with an address in Denmark
- users not requiring ID-control using NemID, are altered and pass the ID-control check. The criteria is currently users with an address outside Denmark

The capabilities and granularity of testing different use-cases and scenarios is expected to be extended in the future, but this first simulation, makes it it more predictable and makes it easier to test additional operations.

<a id="role-acceptance-for-role-invitations"></a>
### Role Acceptance For Role Invitations

Currently it is possible to change roles on domain names for the roles of billing contact and proxy, required that the initiating user holds the right privileges.

The accept of the role, concluding the process cannot be completed currently.

To bypass this, it is recommended to appoint from own registrar account group.

<a id="dns"></a>
### DNS

The sandbox environment is not shielded completely off from the live Internet for DNS and does currently not offer it's own DNS service, which influences some of the operations you can perform in the sandbox environment, even though these do not influence the production environment.

The most prominent example is that an attempt at changing name servers might fail, when the receiving name servers do not answer for the domain name in question.

A work around is to register a domain name on name servers, which do not respond for the domain name live (in production) and then update the domain name to the servers, which respond in production.

Currently name servers listed on a domain name application are not checked at the application processing stage, since by currently policy and process, domain name applications are not guaranteed to be fulfilled, so it is not required by the applicant (registrar) to have these settings in place until it makes sense. Having DNS working however is recommended for a better end-to-end user experience.

To test a name server change, one can turn the scenario around and register a domain name, which is also in production and has active DNS.

The application should point to name servers, which you already have access to (see: [Passwords](#passwords)). This is required if you need to generate the AuthInfo token.

The you request the change of name servers to the name servers already responding for the domain name and you can simulate the real operation.

<a id="email"></a>
### Email

The environment does not support sending out emails, the reason for this was to not confuse sandbox operations with production operations. Proper annotations or embedded warning or the like could open up for this, but for now no emails are sent.

<a id="passwords"></a>
### Passwords

When a user  is created it is not possible to obtain the password of the newly created user. Due to the lack of email communication it is not possible to obtain a password using the "forgotten password" feature. This applies to both regular users for domain and name server roles and portal users for the registrar portal.

If need be and you require the password of a given user in the sandbox environment, please contact DK Hostmaster

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
