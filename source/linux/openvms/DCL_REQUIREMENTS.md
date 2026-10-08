M20 OPENVMS DCL EXPORT REQUIREMENTS
===================================

Purpose
-------

The legacy interface receives a controlled fixed-width export of the same
approved baseline. The DCL course implements this work after the Linux
course. A text file in this package is a requirements reference, not an
executable DCL procedure.

Input and version handling
--------------------------

Use the approved 12-record source and identify the exact version selected for
export. OpenVMS may retain several versions of one filename. The procedure
must report which one it read and must not silently take a stale version.

Reject a missing input file, malformed row, unsupported status, or failed
write. A failure result must be visible in the execution log and the
completion status.

Export format
-------------

The headerless transfer file is M20_STATUS_EXPORT.DAT. Use fixed widths 8,
12, 12, and 10 for system ID, unit, status, and date. Record layout and
padding must be documented so a receiving program can read the fields.

A separate control record reports source version, row count, and generated
timestamp. It must agree with the data file and must not claim success if any
row is excluded.

Expected reconciliation
-----------------------

Export all 12 records. The output must reconcile to 5 READY, 3 MAINTENANCE,
and 4 NOT_READY. The interface-control document describes how to verify the
row count and sample rows before transfer.

Retain prior output versions for review. Record verification and any
remaining departure under the correct Trello task and Git commit.

Course boundary
---------------

Simple Editing Basics repairs the input files; it does not implement this DCL
export. Read this reference for context and preserve it unchanged in incoming
and working unless an authorized later task changes it.

FILE REVIEW GUIDE
=================

Locate and identify
-------------------

This reference applies to openvms/DCL_REQUIREMENTS.md. Verify your present
working directory before opening a file with a similar name. Incoming holds
the original; working holds the editable copy.

Check authorization
-------------------

Find the matching SEB task and approved v3 requirement. When a task does not
authorize a change to this file, read it for context but do not save a
modified copy.

Protect relationships
---------------------

Check paths, status names, dates, counts, and report language against the
controlled references. A change that looks small can affect the next course
if it changes a file path or field format.

Collect evidence
----------------

If this file is edited, compare its working copy against incoming with diff.
Record the reason for each change, the task ID, the checker, and any
unresolved issue in Trello.

OPENVMS IMPLEMENTATION REVIEW CASES
===================================

Valid source with no hidden assumptions
---------------------------------------

The receiving student should locate a verified Git copy of the same approved
twelve-record baseline. The DCL export selects a specific file version and
produces fixed-width transfer rows with a separate control record. A familiar
filename alone is not enough; the task record and path show which copy to
use.

A test against the supplied baseline must produce 5 READY, 3 MAINTENANCE, 4
NOT_READY, and 12 TOTAL. The class can compare this result with the checked
manual report before trusting a new implementation.

Invalid or missing input
------------------------

An implementation must explain a missing file, an unreadable file, and a row
with an invalid status rather than silently producing an incomplete result.
In OpenVMS, show the case, expected message, and whether publication is
blocked.

A passing demonstration includes a successful valid case and at least one
deliberate failure case. A tool that only prints the expected number without
validating the source is not sufficient.

Changes that require traceability
---------------------------------

A new field name, different report path, new status word, or changed count
can affect more than one course. Record who requested the change, its scope,
a decision, and the baseline it replaces before implementing it.

The implementation commit and review evidence should point to the task. A
teammate must be able to see whether a changed program still reads the
approved input and produces the approved result.

Handoff review
--------------

The OpenVMS team should describe what it received, what it built, how it
checked the result, and what remains unresolved. Do not claim a later
deliverable exists simply because its requirements file is present in this
archive.

This reference is read-only during Simple Editing Basics. Students should not
alter it to make a local manual report pass its checks.
