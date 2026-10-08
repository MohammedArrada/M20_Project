M20 LINUX BASH SCRIPT REQUIREMENTS
==================================

Purpose
-------

Course 3 builds a small short-term Bash pipeline that reads the validated
12-record baseline and produces a report. It is separate from the text-
editing tasks in Course 2. Students should understand the interface before
scripting starts.

Script stages
-------------

One script checks required project paths and tools. A second validates data
fields, statuses, and date shape. Another counts status categories. A
reporting script prepares output after validation, and an orchestration
script runs stages in the correct order.

Each stage returns a useful success or failure code, describes errors in
plain language, and avoids publishing a report based on invalid input.
Scripts do not change received original data.

Input and output
----------------

Read source/linux/data/systems_status.dat or a documented input argument. The
file contains 12 rows with fields system_id|unit|status|last_checked.
Statuses are READY, MAINTENANCE, or NOT_READY; expected totals are 5, 3, 4,
and 12.

Write a current report with a generation date, source identifier, category
totals, and total. Preserve the prior report in reports/archive before
replacing it.

Verification cases
------------------

Test valid data, missing input file, unreadable file, wrong number of fields,
empty status, invalid status word, malformed date, duplicate ID, and
mismatched total. A failed test must produce a clear reason.

Document the command used and expected result for each check. Record the
ticket and commit in the course repository so another student can repeat the
demonstration.

Handoff boundaries
------------------

Course 2 provides corrected text files and a verified Git copy. Course 3
provides executable scripts and test evidence. Do not claim automation was
completed by a manual report or by editing the configuration.

FILE REVIEW GUIDE
=================

Locate and identify
-------------------

This reference applies to linux/SCRIPT_REQUIREMENTS.md. Verify your present
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

BASH IMPLEMENTATION REVIEW CASES
================================

Valid source with no hidden assumptions
---------------------------------------

The receiving student should locate a verified Git copy of the same approved
twelve-record baseline. The Bash work reads the repaired input from
source/linux and returns a failure code if a stage cannot validate, count,
archive, or publish correctly. A familiar filename alone is not enough; the
task record and path show which copy to use.

A test against the supplied baseline must produce 5 READY, 3 MAINTENANCE, 4
NOT_READY, and 12 TOTAL. The class can compare this result with the checked
manual report before trusting a new implementation.

Invalid or missing input
------------------------

An implementation must explain a missing file, an unreadable file, and a row
with an invalid status rather than silently producing an incomplete result.
In Bash, show the case, expected message, and whether publication is blocked.

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

The Bash team should describe what it received, what it built, how it checked
the result, and what remains unresolved. Do not claim a later deliverable
exists simply because its requirements file is present in this archive.

This reference is read-only during Simple Editing Basics. Students should not
alter it to make a local manual report pass its checks.
