# Signed OTA with dual-slot rollback you can fail on purpose

**Task ID:** `ie1t3-003`
**Estimated effort:** 10 hours
**Module:** OTA and Safety

## Why this task exists

`ie1t3-002` named the unsigned image and the missing rollback. This task implements those two mitigations as a **host-side** dual-slot bootloader: two files (or directories) are the slots, a small C program is the bootloader, HMAC or a public-key signature is the authenticator. You will fail the update on purpose three ways — bad signature, downgrade, failed health — and keep the node bootable.

No production secure-element, no vendor OTA cloud, no board required. A well-documented MCU you already own is optional and must not be the only way to run the tests.

## Authoritative resources

- **RFC 9019 — A Firmware Update Architecture for Internet of Things** (primary): https://www.rfc-editor.org/rfc/rfc9019.html — image authentication, integrity, unattended update, and the role of a manifest / metadata. You are not required to implement SUIT manifests; you are required to implement the properties your threat model and this RFC treat as mandatory: authenticate the image, do not apply an unknown image, keep a way back.

Use the official RFC as the primary source. If you use Mbed TLS or a host HMAC API for the signature, record that library.

## Work to complete

1. Represent two slots as files (`slot-a.bin`, `slot-b.bin`) plus a metadata file per slot (`version`, `sha256`, `sig_ok`). A `current` pointer names the active slot.
2. **Sign** images with a key that lives in a file the bootloader can read (HMAC-SHA256 is enough; Ed25519 is welcome). Document the algorithm in `UPDATE.md`.
3. `apply <image>`:
   - verify signature; on failure, do not change `current` or the active slot bytes;
   - if anti-rollback is on and `image.version < current.version`, reject;
   - otherwise write the inactive slot, flip `current` only after a successful verify.
4. `boot`:
   - run a health check hook (a script or a function you can force to fail);
   - on failure, flip `current` back to the previous slot and log both versions.
5. Three captured runs: bad signature; signed downgrade with anti-rollback on; good apply + forced health fail + rollback. Dump metadata after each.
6. Incremental history: slots + metadata → verify/reject → anti-rollback → health rollback.

## Required evidence

- Bootloader and slot sources with incremental Git history
- Captured invalid-signature run (active slot unchanged)
- Captured anti-rollback reject (version < current)
- Captured health-fail rollback with both versions printed
- Slot-metadata dump (version, hash, signature-valid)
- Reflection notes answering the task questions

Submit a repository URL plus a commit reference. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] Applying an image whose signature does not verify leaves the active slot's version unchanged; before and after versions are in the captured log.
- [ ] Applying a correctly signed image whose version is less than the current active version is rejected when anti-rollback is enabled; the log states the rejected version and the current version.
- [ ] After a correctly signed apply, a simulated failed health check causes the next boot to select the previous slot; the log prints both slot versions and which one is active.
- [ ] Slot metadata for each slot includes version, content hash, and a signature-valid bit or equivalent, inspectable in a file or dump.

The mentor may hand you a fourth image (wrong key, same version) and ask you to predict the log. A bootloader that always boots the newest file on disk is a fail.

## Reflection

Answer these in your own words after doing the work:

1. Which RFC 9019 requirement did you implement most faithfully, and which did you stub (confidentiality, manifest, unattended scheduling)?
2. If health check passes but the new image livelocks the uplink, what extra signal would you add before declaring the slot good?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Confirm the bad-signature path does not leave a half-written slot marked valid.
- Ask who can replace the HMAC key file — map the answer back to `THREAT.md`.
- Do not approve anti-rollback that compares strings ("v2" > "v10") without a documented numeric version.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
