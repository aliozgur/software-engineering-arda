# Threat-model an IIoT edge node before you write the updater

**Task ID:** `ie1t3-002`
**Estimated effort:** 6 hours
**Module:** OTA and Safety

## Why this task exists

The next task builds a dual-slot updater. If you write the updater first, you will invent threats that match your code. This task reverses that: RFC 9019 states why constrained devices need an authenticated, integrity-protected, preferably unattended firmware update. You will map that onto a node that looks like the one this curriculum has been simulating — sensors, a local map, an uplink, an update path.

No implementation required beyond the document and diagram. That is deliberate. Mentors approve the list, then you implement against it.

## Authoritative resources

- **RFC 9019 — A Firmware Update Architecture for Internet of Things** (primary): https://www.rfc-editor.org/rfc/rfc9019.html — architecture, threats against firmware update, manifests, authentication and integrity. Read the introduction and the architecture/threat discussion; cite a section in `THREAT.md`.

Use the official RFC as the primary source. If you use additional IETF SUIT material or a STRIDE cheat-sheet, record it. Do not use a vendor blog as the authority.

## Work to complete

1. Name the system: a host-simulated IIoT node with a sensor/producer, a register or telemetry map, an MQTT or Modbus uplink, and a firmware-update path. You may reuse your earlier repositories as the "as-built" surface.
2. Write `THREAT.md`:
   - **Assets** (≥ 6): examples — firmware slots, signing key, MQTT credentials, holding-register map, bootloader, device identity.
   - **Attacker positions** (≥ 4): local serial/debug, on-path uplink, malicious update host, physical swap of flash, compromised sensor, insider with plant network access — pick four you can describe.
   - **Mitigations**: one per asset, each a mechanism a later task could implement, not a slogan.
3. Draw a data-flow or trust-boundary diagram (Mermaid in the same file, or ASCII). Label at least two trust boundaries.
4. Firmware section: unsigned image **or** version downgrade / rollback to a vulnerable slot. Mitigation must name **signing** and **freshness or anti-rollback**. Quote or cite RFC 9019 (section number).
5. Commit `THREAT.md` in this task's repository (or a `threat-model/` folder). Do not start the updater implementation here; that is `ie1t3-003`.

## Required evidence

- `THREAT.md` with ≥ 6 assets, ≥ 4 attacker positions, one specific mitigation per asset
- A diagram naming at least two trust boundaries
- A firmware-image threat with signing + freshness/anti-rollback and an RFC 9019 citation
- Git history for this document (no requirement that the next task exist yet)
- Reflection notes answering the task questions

Submit the markdown file in a repository. Do not submit only a slide screenshot.

## Acceptance criteria

- [ ] `THREAT.md` lists at least six assets and at least four attacker positions.
- [ ] Each of the six assets has a mitigation that names a mechanism — not the phrase "use security" or "encrypt everything" alone.
- [ ] The diagram names at least two trust boundaries.
- [ ] One threat is an unsigned or version-downgraded firmware image; its mitigation names signing and a freshness or anti-rollback check and cites RFC 9019 (section number or a quoted sentence).

The mentor may pick one mitigation and ask which later artifact would prove it. A STRIDE table with empty cells is a fail.

## Reflection

Answer these in your own words after doing the work:

1. Which asset is the one you would spend the next engineering week on, and which attacker position makes it urgent?
2. RFC 9019 allows confidentiality of the image to be optional. For your node, would you encrypt the firmware in transit, and what measurement from Term 1 would that cost?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Strike any mitigation that is only "use TLS" with no key story.
- Ask where the signing public key lives and who can replace it — if that is not an asset, request revision.
- Do not approve a model that omits physical debug if the node is a plant device.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

A threat model that an AI generated and the apprentice cannot defend line-by-line is a revision, not a pass.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
