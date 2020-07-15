
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v2.0.jpg)
-------

# Advanced Messaging Queuing Protocol (AMQP) Connection Info Property Version 1.0

## Committee Specification Draft 01 /<br>Public Review Draft 01

## 04 May 2020

#### Technical Committee:
[OASIS Advanced Message Queuing Protocol (AMQP) TC](https://www.oasis-open.org/committees/amqp/)

#### Chairs:
Rob Godfrey (rgodfrey@redhat.com), [Red Hat](http://www.redhat.com/) \
Clemens Vasters (clemensv@microsoft.com), [Microsoft](http://www.microsoft.com/)

#### Editor:
Keith Wall (kwall@redhat.com), [Red Hat](http://www.redhat.com/)

#### Additional artifacts:
This prose specification is one component of a Work Product that also includes:
* XML schemas: (list file names or directory name)
* Other parts (list titles and/or file names)
* `(Note: Any normative computer language definitions that are part of the Work Product, such as XML instances, schemas and Java(TM) code, including fragments of such, must be (a) well formed and valid, (b) provided in separate plain text files, (c) referenced from the Work Product; and (d) where any definition in these separate files disagrees with the definition found in the specification, the definition in the separate file prevails. Remove this note before submitting for publication.)`

#### Related work:

This specification is related to:
* _OASIS Advanced Message Queuing Protocol (AMQP) Version 1.0 Part 0: Overview_. Edited by Robert Godfrey, David Ingham, and Rafael Schloming. Latest version: http://docs.oasis-open.org/amqp/core/v1.0/amqp-core-overview-v1.0.html.
* Related specifications (include hyperlink, preferably to HTML format) \
`(remove "Related work" section or the "replaces" or "related" subsections if no entries)`

#### Abstract:

The Advanced Message Queuing Protocol (AMQP) is an open internet protocol for business messaging.
This document defines a mechanism by which an AMQP container can reveal product information about
itself and its operating environment to its partner.

#### Status:
This document was last revised or approved by the OASIS Advanced Message Queuing Protocol (AMQP) TC on the above date. The level of approval is also listed above. Check the "Latest version" location noted above for possible later revisions of this document. Any other numbered Versions and other technical work produced by the Technical Committee (TC) are listed at https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=amqp#technical.

TC members should send comments on this specification to the TC's email list. Others should send comments to the TC's public comment list, after subscribing to it by following the instructions at the "Send A Comment" button on the TC's web page at https://www.oasis-open.org/committees/amqp/.

This specification is provided under the [RF on RAND](https://www.oasis-open.org/policies-guidelines/ipr#RF-on-RAND-Mode) Mode of the [OASIS IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr), the mode chosen when the Technical Committee was established. For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the Intellectual Property Rights section of the TC's web page ([https://www.oasis-open.org/committees/amqp/ipr.php](https://www.oasis-open.org/committees/amqp/ipr.php)).

Note that any machine-readable content ([Computer Language Definitions](https://www.oasis-open.org/policies-guidelines/tc-process#wpComponentsCompLang)) declared Normative for this Work Product is provided in separate plain text files. In the event of a discrepancy between any such plain text file and display content in the Work Product's prose narrative document(s), the content in the separate plain text file prevails.

#### URI patterns:
Initial publication URI:  
https://docs.oasis-open.org/amqp/conninfo/v1.0/csprd01/conninfo-v1.0-csprd01.html

Permanent "Latest version" URI:  
https://docs.oasis-open.org/amqp/conninfo/v1.0/conninfo-v1.0.html

(Note: Publication URIs are managed by OASIS TC Administration; please don't modify.)

#### Citation format:
When referencing this specification the following citation format should be used:

**[Connection-Info-v1.0]**

_Advanced Messaging Queuing Protocol (AMQP) Connection Info Property Version 1.0_. Edited by Keith Wall. 04 May 2020. OASIS Committee Specification Draft 01 / Public Review Draft 01. https://docs.oasis-open.org/amqp/conninfo/v1.0/csprd01/conninfo-v1.0-csprd01.html. Latest version: https://docs.oasis-open.org/amqp/conninfo/v1.0/conninfo-v1.0.html.

-------

## Notices
Copyright © OASIS Open 2020. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full [Policy](https://www.oasis-open.org/policies-guidelines/ipr) may be found at the OASIS website.

This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Technical Committee (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.

OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Committee Specification or OASIS Standard, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this specification.

OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this specification by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this specification. OASIS may include such claims on its website, but disclaims any obligation to do so.

OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this document or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Technical Committee can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Committee Specification or OASIS Standard, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark for above guidance.

-------

# Table of Contents
[[TOC will be inserted here]]

-------

# 1 Introduction

## 1.1 IPR Policy
This specification is provided under the [RF on RAND](https://www.oasis-open.org/policies-guidelines/ipr#RF-on-RAND-Mode) Mode of the [OASIS IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr), the mode chosen when the Technical Committee was established. For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the Intellectual Property Rights section of the TC's web page ([https://www.oasis-open.org/committees/amqp/ipr.php](https://www.oasis-open.org/committees/amqp/ipr.php)).

## 1.2 Terminology
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [[RFC2119](#rfc2119)] and [[RFC8174](#rfc8174)] when, and only when, they appear in all capitals, as shown here.

## 1.3 Normative References

(Reference sources:
For references to IETF RFCs, use the approved citation formats at:  
http://docs.oasis-open.org/templates/ietf-rfc-list/ietf-rfc-list.html.  
For references to W3C Recommendations, use the approved citation formats at:  
http://docs.oasis-open.org/templates/w3c-recommendations-list/w3c-recommendations-list.html.  
Remove this note before submitting for publication.)

###### [AMQP-v1.0]
_OASIS Advanced Message Queuing Protocol (AMQP) Version 1.0 Part 0: Overview_. Edited by Robert Godfrey, David Ingham, and Rafael Schloming. Latest version: http://docs.oasis-open.org/amqp/core/v1.0/amqp-core-overview-v1.0.html.
###### [RFC2119]
Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997, http://www.rfc-editor.org/info/rfc2119.
###### [RFC2616]
Fielding, R., Gettys, J., Mogul, J., Frystyk, H., Masinter, L., Leach, P., and T. Berners-Lee, "Hypertext Transfer Protocol -- HTTP/1.1", RFC 2616, DOI 10.17487/RFC2616, June 1999, <https://www.rfc-editor.org/info/rfc2616>.
###### [RFC8174]
Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017, http://www.rfc-editor.org/info/rfc8174.

## 1.4 Non-Normative References

###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003, https://www.rfc-editor.org/info/rfc3552.

-------

# 2 Overview

This specification recommends a standard way for an AMQP container to reveal information about
itself and its operating environment to its partner.   This allows a container to expose information
that would be useful for problem diagnosis, such as process identifiers and software version
information.

This specification is equally appropriate for AMQP container fulfilling the role of clients or
servers, or containers supporting a peer-to-peer scenario.

-------

# 3 Definitions

An AMQP host that implements this specification MUST provide the following entry in the properties
field of the AMQP `open` performative [[AMQP-v1.0](#AMQP-v1.0)]. The key of the entry MUST be the symbol
`connection-info`. The value of the entry MUST be of type `fields`.

The following key values have defined meaning. An implementation MAY choose to omit a key from the map.
An implementation MAY also include keys of its own. If an implementation receives a key from its partner
that it does not recognise, it SHOULD ignore it.

# 3.1 connection-info

`<type name="connection-info" class="restricted" source="fields"/>`

The content of `connection-info` allows the container to provide information about itself and its operating
environment to its partner.

**Table 1-1. connection-info**

| Name | Description |
| :--- | :--- |
| `process-identifier` | The value of the process-identifier MUST be an AMQP string. The purpose of the value is to identify the process running this AMQP host. It is RECOMMENDED that this is an operating system PID. |
| `network-host` | The value of network-host MUST be an AMQP string. The purpose of the value is to identify the host running the AMQP container in a way that assists those fault finding within a system. This value MAY be a hostname, fully qualified hostname or IP address. The value MAY be network resolvable by the AMQP peer but the peer MUST NOT rely on this. |
| `amqp-product` | The value of amqp-product MUST be an AMQP string and is a `product-string`. It provides details of the software product(s) that provide the AMQP implementation. It MAY identify multiple products. By convention, the products are listed in order of their significance for identifying the product. |
| `product` | The value of product MUST be an AMQP string and is a product-string. It provides details of the software product(s) that is the end-user application. It MAY identify multiple products. By convention, the products are listed in order of their significance for identifying the application. |
| `platform` | The value of platform MUST be an AMQP string and is a product-string. It exists to expose details of a product’s runtime platform. This typically identify the operating system, Java/.NET runtimes etc. It MAY identify multiple products. By convention, the products are listed in order of their significance. |

# 3.2 product-string

`<type name="product-string" class="restricted" source="string"/>`

The content of the `product-string` MUST adopt the content structure of the `User-Agent` header (defined by 
[[RFC2616](#rfc2616)]) and commonly implemented by Web Browsing software. The field MAY contain multiple product tokens
and comments identifying the product and any sub-products which form a significant part of the system. By convention, 
the product tokens are listed in order of their significance

Formally, the content of `product-string` MUST conform to this ABNF production rule:
 
```
product-string = 1*( product | comment ) 
```

where symbols `product`, `comment`, and the ABNF grammar itself are as defined by [[RFC2616](#rfc2616)].

## Non normative examples:

```
ApacheQpidJMS/0.36
ApacheQpidJMS/0.36 ApacheQpidProton/0.45 (build 12345)
```

-------

# 4 Safety, Security, and Data Protection Considerations
(Note: OASIS strongly recommends that Technical Committees consider issues that might affect safety, security, privacy, and/or data protection in implementations of their specification and document them for implementers and adopters. For some purposes, you may find it required, e.g. if you apply for IANA registration.

While it may not be immediately obvious how your specification might make systems vulnerable to attack, most specifications, because they involve communications between systems, message formats, or system settings, open potential channels for exploit. For example, IETF [[RFC3552](#rfc3552)] lists “eavesdropping, replay, message insertion, deletion, modification, and man-in-the-middle” as well as potential denial of service attacks as threats that must be considered and, if appropriate, addressed in IETF RFCs.

In addition to considering and describing foreseeable risks, this section should include guidance on how implementers and adopters can protect against these risks.

We encourage editors and TC members concerned with this subject to read _Guidelines for Writing RFC Text on Security Considerations_, IETF [[RFC3552](#rfc3552)], for more information.

Remove this note before submitting for publication.)

-------

# 5 Conformance
(Note: The [OASIS TC Process](https://www.oasis-open.org/policies-guidelines/tc-process#wpComponentsConfClause) requires that a specification approved by the TC at the Committee Specification Public Review Draft, Committee Specification or OASIS Standard level must include a separate section, listing a set of numbered conformance clauses, to which any implementation of the specification must adhere in order to claim conformance to the specification (or any optional portion thereof). This is done by listing the conformance clauses here.
For the definition of "conformance clause," see [OASIS Defined Terms](https://www.oasis-open.org/policies-guidelines/oasis-defined-terms-2017-05-26#dConformanceClause).

See "Guidelines to Writing Conformance Clauses":  
http://docs.oasis-open.org/templates/TCHandbook/ConformanceGuidelines.html.

Remove this note before submitting for publication.)


-------

# Appendix A. Acknowledgments

(Note: A Work Product approved by the TC must include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list shall be initially compiled by the Chair, and any Member of the TC may add or remove their names from the list by request.  
Remove this note before submitting for publication.)

The following individuals have participated in the creation of this specification and are gratefully acknowledged:

**AMQP TC Members:**

| First Name | Last Name | Company |
| :--- | :--- | :--- |
Philippe | Alman | Something Networks
Alex | Amirnovman | Company B
Kris | Anderman | Mini Micro
Darren | Anstman | Big Networks

-------

# Appendix B. Revision History
| Revision | Date | Editor | Changes Made |
| :--- | :--- | :--- | :--- |
| conninfo-v1.0-wd01 | 2020-05-04 | Keith Wall | Initial working draft |

