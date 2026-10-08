M20 PYTHON REPORTING REQUIREMENTS
=================================

Purpose
-------

The final course replaces the short-term manual and Bash steps with a
maintainable Python reporting solution. This file explains the later
interface needs so current editing decisions remain compatible.

Input and normalization
-----------------------

Read both approved input formats and normalize them into system_id, unit,
status, and last_checked fields. Keep source details so a reviewer can trace
a normalized record to its input.

Handle invalid input explicitly. A status outside READY, MAINTENANCE, or
NOT_READY cannot be silently counted, and an incomplete control record blocks
publication.

Separation of concerns
----------------------

Keep loading, validation, normalization, counting, report formatting,
archiving, and orchestration as understandable functions or modules. Document
a clear input and output contract for each stage.

Failure at one stage must prevent a later stage from claiming a complete
report. Protect previously published reports when preparing a replacement.

Testing and evidence
--------------------

Test the 12-record controlled baseline and compare 5 READY, 3 MAINTENANCE, 4
NOT_READY. Test invalid fields, unknown statuses, bad dates, duplicates,
missing files, and control-record mismatches.

Save relevant evidence with a traceable work item and Git commit. The release
manifest records the approved plan revision, code identity, tests, and known
issues.

Course boundary
---------------

Students read this reference during the editing course only to understand
what will consume the file later. Do not ask them to write Python code as
part of the gedit, nano, or vim labs.

FILE REVIEW GUIDE
=================

Locate and identify
-------------------

This reference applies to python/PYTHON_REQUIREMENTS.md. Verify your present
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

PYTHON IMPLEMENTATION REVIEW CASES
==================================

Valid source with no hidden assumptions
---------------------------------------

The receiving student should locate a verified Git copy of the same approved
twelve-record baseline. The Python system normalizes approved source formats,
validates rows, reconciles control counts, and records a release manifest. A
familiar filename alone is not enough; the task record and path show which
copy to use.

A test against the supplied baseline must produce 5 READY, 3 MAINTENANCE, 4
NOT_READY, and 12 TOTAL. The class can compare this result with the checked
manual report before trusting a new implementation.

Invalid or missing input
------------------------

An implementation must explain a missing file, an unreadable file, and a row
with an invalid status rather than silently producing an incomplete result.
In Python, show the case, expected message, and whether publication is
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

The Python team should describe what it received, what it built, how it
checked the result, and what remains unresolved. Do not claim a later
deliverable exists simply because its requirements file is present in this
archive.

This reference is read-only during Simple Editing Basics. Students should not
alter it to make a local manual report pass its checks.
