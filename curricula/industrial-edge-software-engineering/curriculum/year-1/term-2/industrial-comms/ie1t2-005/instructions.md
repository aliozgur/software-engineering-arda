# MQTT QoS 1 telemetry with reconnect and backoff

**Task ID:** `ie1t2-005`
**Estimated effort:** 8 hours
**Module:** Industrial Comms

## Why this task exists

You built reliability over a fake datagram. The field talks MQTT. QoS 1 means "at least once" — which means duplicates, packet identifiers, and a session that survives a dropped TCP connection. You will run **Eclipse Mosquitto (or another local broker) on localhost**. Do not use a vendor IoT cloud for this task.

Host-side C is preferred (a minimal CONNECT/PUBLISH/PUBACK client, or a thin program over libmosquitto / Eclipse Paho C). A short Python subscriber only to *observe* is fine; the publisher you defend should be C unless your mentor agrees otherwise.

## Authoritative resources

- **MQTT Version 5.0 (OASIS Standard)** (primary): https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html — CONNECT (ClientId, Clean Start), PUBLISH QoS 1, PUBACK, packet identifiers, session expiry. You may implement MQTT 3.1.1 if your library forces it; say so and map the equivalent flags.

Use the official spec as the primary source. If you use broker man pages, record them.

## Work to complete

1. Install and run a local broker (Mosquitto is the default). Bind to localhost. Put the listen address/port in `broker.conf` or a captured `mosquitto -c` command. No TLS required for this task (Term 3 covers authentication).
2. Write `SESSION.md`: ClientId string; Clean Start true/false (or 3.1.1 clean session); one sentence why. Document backoff: at least two delays, for example 1s then 4s (capped).
3. Publisher: CONNECT, then PUBLISH at **QoS 1** on a documented topic with a documented payload. Keep the packet identifier. Wait for PUBACK (or the library equivalent you can log).
4. Subscriber (same host): subscribe to that topic and capture the payload.
5. Reconnect drill: after PUBLISH and before PUBACK (or by killing the broker for 2+ seconds), force a disconnect. Bring the broker back. Client reconnects using the backoff list. Show either a retry of the in-flight message or a duplicate delivery explained by the same packet identifier / session.
6. Incremental history: localhost CONNECT → QoS 1 happy path → reconnect/backoff.

## Required evidence

- Localhost broker config or run command; no cloud endpoint
- Client sources (or a documented library program plus your wrapper)
- A captured subscriber/broker log of the QoS 1 payload
- `SESSION.md` with ClientId, session choice, and backoff list
- A captured reconnect run matching that backoff list and explaining retry or duplicate
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of a GUI client.

## Acceptance criteria

- [ ] The broker listens on localhost (or a documented loopback address); the client config contains no public cloud IoT hostname.
- [ ] A QoS 1 PUBLISH is received by a subscriber; the captured log shows the topic and payload.
- [ ] `SESSION.md` states the ClientId string and whether Clean Start / clean session is true or false, with one sentence of reason.
- [ ] A forced disconnect mid-flight is followed by reconnect delays that match a list of at least two backoff values written in `SESSION.md`, and the in-flight payload is either retried or a duplicate is explained by a packet identifier in the log.

The mentor may ask what QoS 2 would add and why you did not use it on a constrained node. A QoS 0 publish is a fail.

## Reflection

Answer these in your own words after doing the work:

1. Under Clean Start = true, what in-flight state did you lose on reconnect, and how did you compensate?
2. Why is "at least once" the right default for a trip-value and a dangerous default for a toggle command — or the reverse?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Confirm the config file has no `*.amazonaws.com` / Azure / GCP IoT host.
- Ask the apprentice to point at the packet identifier in the reconnect log.
- Do not approve a client that busy-loops reconnect without the documented delays.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
