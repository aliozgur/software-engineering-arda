# Networking I: Packets, IP, DNS and Routing

**Task ID:** `y2t1-005`  
**Estimated effort:** 18 hours  
**Module:** Networking

## Why this task exists

Build a packet-level model of how data reaches another host.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Stanford CS144 - Introduction to Computer Networking** (primary): https://cs144.github.io/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Study Ethernet/IP/routing/DNS fundamentals.
2. Use ip/ifconfig, route, ping, traceroute and DNS tools.
3. Capture DNS and ICMP traffic with Wireshark/tcpdump.
4. Calculate IPv4 subnets manually for several examples.
5. Draw the path from browser hostname to routed IP packet.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Packet captures are annotated.
- [ ] Subnet calculations are correct.
- [ ] Apprentice distinguishes MAC, IP, port and hostname.
- [ ] Routing explanation includes default gateway and longest-prefix intuition.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Where does DNS end and HTTP begin?
2. Why does a router not need the destination MAC of a remote Internet host?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Give a fresh subnet/routing problem live.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
