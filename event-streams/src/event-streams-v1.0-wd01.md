
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v2.0.jpg)
-------

# Event Stream Extensions for AMQP Version 1.0

## Committee Specification Draft 01 /<br>Public Review Draft 01

## 03 June 2020

#### Technical Committee:
[OASIS Advanced Message Queuing Protocol (AMQP)
TC](https://www.oasis-open.org/committees/amqp/)

#### Chairs:
Rob Godfrey (rgodfrey@redhat.com), [Red Hat](http://www.redhat.com/) \
Clemens Vasters (clemensv@microsoft.com), [Microsoft](http://www.microsoft.com/)

#### Editor:
Clemens Vasters (clemensv@microsoft.com), [Microsoft](http://www.microsoft.com/)

#### Related work:

This specification is related to:
* _OASIS Advanced Message Queuing Protocol (AMQP) Version 1.0 Part 0: Overview_.
  Edited by Robert Godfrey, David Ingham, and Rafael Schloming. Latest version:
  http://docs.oasis-open.org/amqp/core/v1.0/amqp-core-overview-v1.0.html.

#### Abstract:
This specification defines a set of AMQP extensions for interaction with event
stream engines, including annotations for partition selection and filter
definitions for indicating offsets into an extension stream to which a link
shall be attached.

#### Status:
This document was last revised or approved by the OASIS Advanced Message Queuing
Protocol (AMQP) TC on the above date. The level of approval is also listed
above. Check the "Latest version" location noted above for possible later
revisions of this document. Any other numbered Versions and other technical work
produced by the Technical Committee (TC) are listed at
https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=amqp#technical.

TC members should send comments on this specification to the TC's email list.
Others should send comments to the TC's public comment list, after subscribing
to it by following the instructions at the "Send A Comment" button on the TC's
web page at https://www.oasis-open.org/committees/amqp/.

This specification is provided under the [RF on
RAND](https://www.oasis-open.org/policies-guidelines/ipr#RF-on-RAND-Mode) Mode
of the [OASIS IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr),
the mode chosen when the Technical Committee was established. For information on
whether any patents have been disclosed that may be essential to implementing
this specification, and any offers of patent licensing terms, please refer to
the Intellectual Property Rights section of the TC's web page
([https://www.oasis-open.org/committees/amqp/ipr.php](https://www.oasis-open.org/committees/amqp/ipr.php)).

Note that any machine-readable content ([Computer Language
Definitions](https://www.oasis-open.org/policies-guidelines/tc-process#wpComponentsCompLang))
declared Normative for this Work Product is provided in separate plain text
files. In the event of a discrepancy between any such plain text file and
display content in the Work Product's prose narrative document(s), the content
in the separate plain text file prevails.

#### URI patterns:
Initial publication URI:  
https://docs.oasis-open.org/amqp/event-streams/v1.0/csprd01/event-streams-v1.0-csprd01.html

Permanent "Latest version" URI:  
https://docs.oasis-open.org/amqp/event-streams/v1.0/event-streams-v1.0.html

(Note: Publication URIs are managed by OASIS TC Administration; please don't
modify.)

#### Citation format:
When referencing this specification the following citation format should be
used:

**[Event-Streams-v1.0]**

_Event Stream Extensions for AMQP Version 1.0_. Edited by Clemens Vasters. 03
June 2020. Working Draft 1.
https://docs.oasis-open.org/amqp/event-streams/v1.0/csprd01/event-streams-v1.0-wd01.html.
Latest version:
https://docs.oasis-open.org/amqp/event-streams/v1.0/event-streams-v1.0.html.

-------

## Notices
Copyright © OASIS Open 2020. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them
in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The
full [Policy](https://www.oasis-open.org/policies-guidelines/ipr) may be found
at the OASIS website.

This document and translations of it may be copied and furnished to others, and
derivative works that comment on or otherwise explain it or assist in its
implementation may be prepared, copied, published, and distributed, in whole or
in part, without restriction of any kind, provided that the above copyright
notice and this section are included on all such copies and derivative works.
However, this document itself may not be modified in any way, including by
removing the copyright notice or references to OASIS, except as needed for the
purpose of developing any document or deliverable produced by an OASIS Technical
Committee (in which case the rules applicable to copyrights, as set forth in the
OASIS IPR Policy, must be followed) or as required to translate it into
languages other than English.

The limited permissions granted above are perpetual and will not be revoked by
OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS"
basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT
LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE
ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR
A PARTICULAR PURPOSE.

OASIS requests that any OASIS Party or any other party that believes it has
patent claims that would necessarily be infringed by implementations of this
OASIS Committee Specification or OASIS Standard, to notify OASIS TC
Administrator and provide an indication of its willingness to grant patent
licenses to such patent claims in a manner consistent with the IPR Mode of the
OASIS Technical Committee that produced this specification.

OASIS invites any party to contact the OASIS TC Administrator if it is aware of
a claim of ownership of any patent claims that would necessarily be infringed by
implementations of this specification by a patent holder that is not willing to
provide a license to such patent claims in a manner consistent with the IPR Mode
of the OASIS Technical Committee that produced this specification. OASIS may
include such claims on its website, but disclaims any obligation to do so.

OASIS takes no position regarding the validity or scope of any intellectual
property or other rights that might be claimed to pertain to the implementation
or use of the technology described in this document or the extent to which any
license under such rights might or might not be available; neither does it
represent that it has made any effort to identify any such rights. Information
on OASIS' procedures with respect to rights in any document or deliverable
produced by an OASIS Technical Committee can be found on the OASIS website.
Copies of claims of rights made available for publication and any assurances of
licenses to be made available, or the result of an attempt made to obtain a
general license or permission for the use of such proprietary rights by
implementers or users of this OASIS Committee Specification or OASIS Standard,
can be obtained from the OASIS TC Administrator. OASIS makes no representation
that any information or list of intellectual property rights will at any time be
complete, or that any claims in such list are, in fact, Essential Claims.

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the
owner and developer of this specification, and should be used only to refer to
the organization and its official outputs. OASIS welcomes reference to, and
implementation and use of, specifications, while reserving the right to enforce
its marks against misleading uses. Please see
https://www.oasis-open.org/policies-guidelines/trademark for above guidance.

-------

# Table of Contents
[[TOC will be inserted here]]

-------

# 1 Introduction

This specification defines a set of AMQP extensions for interaction with event
stream engines, including annotations for partition selection and filter
definitions for indicating offsets into an extension stream to which a link
shall be attached.

In the context of this specification, the term "event stream engine" describes a
particular archetype of AMQP node that manages sequences of events (messages) in
an ordered log structure.

Event logs differ from queue-like structures in that they do not track message
delivery state across competing receivers. The message delivery state is instead
tracked for each link at its terminus. When attaching a `receive` AMQP link, the
receiver MAY indicate an initial offset into the retained event log. The
delivery of events then progresses in log order from that initial offset to more
recently added events. Omitting the offset results in delivery of events added
after attaching the link.

Event stream engines conforming to this specification MAY implement any of the
capabilities defined here and they MUST implement the default behaviors defined
here when those capabilities are not explicitly used.

## 1.1 IPR Policy
This specification is provided under the [RF on
RAND](https://www.oasis-open.org/policies-guidelines/ipr#RF-on-RAND-Mode) Mode
of the [OASIS IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr),
the mode chosen when the Technical Committee was established. For information on
whether any patents have been disclosed that may be essential to implementing
this specification, and any offers of patent licensing terms, please refer to
the Intellectual Property Rights section of the TC's web page
([https://www.oasis-open.org/committees/amqp/ipr.php](https://www.oasis-open.org/committees/amqp/ipr.php)).

## 1.2 Terminology
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 [[RFC2119](#rfc2119)] and
[[RFC8174](#rfc8174)] when, and only when, they appear in all capitals, as shown
here.

## 1.3 Normative References

###### [AMQP-v1.0]
_OASIS Advanced Message Queuing Protocol (AMQP) Version 1.0 Part 0: Overview_.
Edited by Robert Godfrey, David Ingham, and Rafael Schloming. Latest version:
http://docs.oasis-open.org/amqp/core/v1.0/amqp-core-overview-v1.0.html.

###### [FILTEX-v1.0]
_AMQP Filter Expressions Version 1.0_.
Edited by Clemens Vasters. Latest version:
http://docs.oasis-open.org/amqp/filtex/v1.0/filtex-v1.0.docx
###### [RFC2119]
Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14,
RFC 2119, DOI 10.17487/RFC2119, March 1997,
http://www.rfc-editor.org/info/rfc2119.
###### [RFC8174]
Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14,
RFC 8174, DOI 10.17487/RFC8174, May 2017,
http://www.rfc-editor.org/info/rfc8174.

## 1.4 Non-Normative References

###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security
Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003,
https://www.rfc-editor.org/info/rfc3552.

# 2 Concepts and default behaviors

The following terminology is used in this specification to clarify roles. These
definitions are narrower than their use in the core AMQP specification.

- `producer` is the sender of events into the event log.
- `consumer` is the receiver of events from the event log.
- `event log node` is where AMQP links of senders and receivers attach.


## 2.1 Partition support

An event log managed by the event stream node MAY be split into multiple
parallel partitions that are reachable under the same network address. A single
event log might also be shared by multiple AMQP containers/nodes that each have
a separate network address and are each responsible for one or more partitions.

The association between a producer/consumer and a partition MAY be chosen using
link properties when the link is being attached. The bi-directional negotiation
capabilities of AMQP apply here: A consumer MAY request being associated with a
particular partition, but the responding event log node MAY also assign a
partition if none has been requested.

A producer's `send` link being attached to an event log node MAY request
association with a specific partition using the [`event-streams-partition` link
property](#211-event-streams-partition-link-property). If the requested
partition does not exist, attaching the link MUST be rejected by the event log
node. The event log node MAY assign a partition when none has been requested. It
MUST NOT assign a partition other than the one that has been requested.

If no partition is assigned, the default behavior MUST be for a `send` link to
be partition agnostic and for any partition-related hints to flow via delivery
annotations, which are defined further below in this section.

A consumer's `receive` link being attached to an event log node MAY request
association with a specific partition using the the [`event-streams-partition`
link property](#211-event-streams-partition-link-property). If the requested
partition does not exist, attaching the link MUST fail. If the event log is
partitioned and no association has been requested, the event log node MUST
associate a partition with the link.

For both `send` and `receive` links, the effective associated partition MUST be
expressed with the [`event-streams-partition` link
property](#211-event-streams-partition-link-property) set by the event log node.

### 2.1.1 event-streams-partition link property

The `event-streams-partition` link property is a `symbol` value and describes
the partition with which the link is associated. When set by the producer or
consumer, the property value is a request for association with the given
partition. When set by the event log node, the value is the effective
association.

When not set for a producer 'send' link, the link is partition-agnostic.

### 2.1.2 event-streams-partition delivery annotation

The `event-streams-partition` delivery annotation is a `symbol` value and
describes the partition to which the message carrying it MUST be routed or from
which partition is has been retrieved.

If the link over which a message is routed is not partition agnostic with or if
the link is not associated with the exact same partition, the transfer MUST be
rejected.

If the event log is partitioned, the delivery annotation MUST be added by the
event log node before delivery to consumers. A consumer SHOULD strip the
annotation before forwarding it.

### 2.1.3 event-streams-group-key message annotation

The `event-streams-key` message annotation is a `string` value and
is a grouping key that identifies events that are related and SHOULD therefore
be treated as a group for partitioning purposes.

This is an annotation and therefore differs from the core message property
`group-id` by allowing overrides as messages get routed through multiple
partitioned intermediaries where partitioning concerns might vary.

When set by the producer and used over a partition agnostic link, the value of
the annotation MAY be used by the event log to associate the message with a
partition. If the key is used in this way, the event log SHOULD associate the
same partition with the same key at all times until the number of partitions
changes.

# 2.2 Stream delivery offsets and filters 

As stated in the introduction, event logs differ from queue-like structures in
that they only track message delivery state at the AMQP link level. While
attaching a `receive` AMQP link, the consumer MAY indicate a desired initial
offset into the retained log or some other condition based on which events
become eligible for delivery. The desired offset is expressed using an AMQP
filter expression.

# 2.2.1 Delivery annotations

The delivery filter expressions refer to a set of delivery annotations defined
in the following. These delivery annotations MUST be added by the event log to
all messages delivered to consumers.

# 2.2.1.1 event-streams-offset

The `event-streams-offset` delivery annotation property is a `symbol` expression
whose internal syntax is opaque to the receiver. Receivers MUST NOT interpret or
construct offset values. The offset value represents the relative position of
the event to the beginning of the log.

Even though the syntax is opaque, the chosen syntax MUST ensure that the
lexicographical rank of the `event-streams-offset` of any event in the log MUST
be greater than the lexicographical rank of any other event preceding it in the
order of the log.

Receivers learn about offset values either by obtaining the runtime information
of a partition, which contains the offset of the most recently added event, or
by retaining the value of the last `event-streams-offset` delivery annotation
property they read from the partition.

For use with [delivery filter expressions](#222-delivery-filters), the reserved
values MAY be used as constants for comparand values:

- "@earliest" is smaller than all existing offsets in the log.
- "@latest" is greater than all existing offsets in the log.

# 2.2.1.2 event-streams-timestamp

The `event-streams-timestamp` delivery annotation property is a timestamp
expression and reflects the absolute UTC instant when the event has been added
to the event log. This is different from the `creation-time` message property
that is set by the sender.

Multiple events added to the log around the same instant MAY have identical
timestamps due to the UTC clock resolution concerns. The timestamp only serves
as a filter criterion to determine a desired offset into the stream, but MUST
NOT be used to determine the order of events.

A distributed event log implementation where the ownership of a log changes
between different hosts and where clocks might not be fully synchronized MAY
record `event-streams-timestamp` values that reflect the existing clock skew,
meaning that some events that appear later in the log than a given event might
yet carry earlier UTC timestamps.

# 2.2.2 Delivery filters

A delivery filter specifies which events are eligible for delivery from the
event log. The delivery filter is provided as a source filter during link
attach.

Delivery filters MAY be expressed using any AMQP filter expression that is
supported by the source (the event log node). This specification defines two
simplified filters that allow for a conforming implementation without having to
implement the full [AMQP filter expressions](#filtex-v10) specification in a
conforming fashion.

The source filter MUST be evaluated against the retained events in the log from
earliest to latest. Events matching the source expression are eligible for
delivery.

# 2.2.2.1 event-streams-delivery-annotations filter

The `event-streams-delivery-annotations` filter type applies to AMQP
delivery annotations section (AMQP 3.2.2). The filter evaluates to true if all
annotations enclosed in the filter expression match the respective
delivery annotation map entries in the message.

Only the [`event-streams-offset`](#2211-event-streams-offset) and/or
[`event-streams-timestamp`](#2212-event-streams-timestamp) delivery annotation
properties are eligible to be used with this filter.

The property values match the given values in the filter expression, if the value
of the property is greater or equal to the value given in the filter expression.

``` XML
<type name="event-streams-delivery-annotations-filter" class="restricted" source="amqp:map" provides="filter">
<descriptor name="amqp:event-streams-delivery-annotations-filter" code="0x00000000:0x00000200"/>
</type> 
```

The filter-type is “amqp:event-streams-delivery-annotations-filter”, with
type-code 0x00000000:0x00000200

# 2.2.2.2 event-streams-sql filter 

The event streams SQL filter expression is a constrained subset of the SQL filter
expression defined in [AMQP filter expressions [FILTEX, 6]](#filtex-v10).

The grammar builds on the grammar defined for those SQL filters, but is
constrained as follows:

```
predicate ::=  <boolean_constant> |
              | <expression> <comparison-operator> <expression>
              | <predicate> <binary-logical-operator> <predicate>
expression ::= <constant> | <field_value>  
constant   ::= <string_constant> | <integer_constant>
field_value := <field>
field ::= <section> ’.’<field_name>
section ::= { ‘message_annotations’ | ‘m’ }
```

This grammar subset allows for a minimal implementation that is limited to
evaluating the delivery annotation properties defined here while being
interoperable with the full SQL filter syntax.

Examples:

- Start from event at offset "a4c5" exclusively: `m.event-streams-offset > '100'`
- Start from event at offset "a4c5" inclusively: `m.event-streams-offset >= '100'`
- Start from event received after the timestamp: `m.event-streams-timestamp > 1585672841`


``` XML
 <type name="event-streams-sql-filter" class="restricted" source="sql-filter" provides="filter">
<descriptor name="amqp:event-streams-sql-filter" code="0x00000000:0x00000201"/> 
</type>
```

The filter-type is “amqp:event-streams-sql-filter”, with type-code 0x00000000:0x00000201


## 2.3 Link ownership

An implementation MAY constrain the number of concurrent receivers that can
receive from a log or its partitions.

In scenarios where a group of multiple concurrent event processors want to
receive events from a partitioned event log and where they use an external
consensus mechanism to agree on which event processor owns which partition, it
is desireable to restrict each partition to one (the owning) receiver from the
group and for event processors to "steal" ownership of the partition as
assignments amongst the group change.

This specification does not prescribe any algorithm or strategy for reaching
such consensus, but only a mechanism for realizing its outcome:

For an event log that is partitioned, a link MAY be associated with a partition
and a consumer group when the respective link properties are provided during
`attach`. For the combination of partition and consumer group, the node
maintains a `long`-valued `epoch` counter, which is seeded with zero and
returned in the `event-streams-epoch` link property to the receiver during a
successful attempt to attach.

Any subsequent attempt to attach a link with the same combination of partition
and consumer group link property values will be rejected while there is an
active link and unless the newly attaching receiver provides an epoch counter
greater than the current epoch counter value using the `event-streams-epoch`
link property. If that condition is true, the new epoch counter value is
recorded, any existing link for the given partition and consumer group is closed
by the node, and the new link is attached.

Whenever the link for a partition within a group is closed by the receiver and
therefore no links remain, the respective epoch counter is reset to zero.  

### 2.2.1 event-streams-consumer-group link property

The `event-streams-consumer-group` link property is a `string` value that
identifies a group of consumers and provides a scope for the epoch counter.

An implementation MAY require for the group identifier to correspond to a
configured item on the event stream engine and otherwise refuse to attach the
link.

### 2.2.1 event-streams-epoch link property

The `event-streams-epoch` link property is a `long` integer value and describes
the ownership epoch for the link relative to the consumer group and while at
least one link is attached to the partition within the given consumer group.

If no link is attached to node for the given partition and group, the epoch
counter SHOULD be reset to zero.

-------

# 3 Runtime Information

TBD.

>This section will describe a request/response operation to acquire information
>about the available partitions and offsets. 

-------

# 4 Safety, Security, and Data Protection Considerations

[[TBD]]

-------

# 5 Conformance

[[TBD]]

-------

# Appendix A. Acknowledgments

(Note: A Work Product approved by the TC must include a list of people who
participated in the development of the Work Product. This is generally done by
collecting the list of names in this appendix. This list shall be initially
compiled by the Chair, and any Member of the TC may add or remove their names
from the list by request.  
Remove this note before submitting for publication.)

The following individuals have participated in the creation of this
specification and are gratefully acknowledged:

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
| specname-v1.0-wd01 | yyyy-mm-dd | Editor Name | Initial working draft |

