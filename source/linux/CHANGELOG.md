M20 CHANGE HISTORY AND CONTROL NOTES
====================================

How to use this record
----------------------

This document records meaningful changes to controlled material. A
descriptive change entry explains what changed, who checked it, and which
approved task authorized it. A newer date or confident filename alone cannot
authorize a change.

During this course students should keep the received copy intact. A short
entry may be added only in the working copy after completing approved edits,
and the entry should identify the SEB task and the affected files.

Received package state 2026-10-05
---------------------------------

The received README gives an outdated data filename and says to email a final
report. The manual procedure still refers to commas, old statuses, an old
output path, and deletion of earlier reports. The configuration points to an
old data path and old report values.

The baseline data has 12 system IDs, SYS-101 through SYS-112. Some statuses
and one date need normalization. The supplied manual report is stale and must
not be treated as the evidence for the corrected counts.

Previous planning events
------------------------

Revision 1 identified an initial reporting problem and an early work
estimate. Revision 2 was approved for an earlier scope. Revision 3 later
became current following review of a change request and approval evidence.
The earlier approved document is historical evidence.

Received filenames and copied documents remain in the original-document
location in the Course 1 repository. The controlled copy of the current v3
plan governs edits and later implementation. Keep historical context
available for an audit or question from the team.

Change entry format
-------------------

Each entry records an ISO date, a Trello task ID, affected paths, an exact
description of the edit, the checker, and the verification result. Use
concrete language such as 'DATA_FILE changed from data/system_status.dat to
data/systems_status.dat'.

Do not write 'fixed everything', 'latest', or 'final'. Those phrases do not
help another team member identify a specific approved file or reproduce the
check.

Course handoff checks
---------------------

Before the Course 3 Bash work begins, confirm that the working data contains
exactly 12 valid records and reconciles to 5 READY, 3 MAINTENANCE, and 4
NOT_READY. Confirm the configuration paths and the handoff note agree with
the corrected procedure.

After scp, check the copy under M20_Project/source/linux on the Windows host,
inspect staged Git changes, commit them with SEB-08 in the message, push, and
record the commit ID in Trello.

FILE REVIEW GUIDE
=================

Locate and identify
-------------------

This reference applies to CHANGELOG.md. Verify your present working directory
before opening a file with a similar name. Incoming holds the original;
working holds the editable copy.

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

CHANGE ENTRY EXAMPLES AND REVIEW NOTES
======================================

An entry with enough detail
---------------------------

A useful example reads: '2026-10-05 | SEB-05 | config/report_settings.conf |
Corrected DATA_FILE to data/systems_status.dat and checked that the
referenced file exists | Checked by learner B.' The example identifies the
task, path, exact change, and check.

A reviewer can compare that entry against the Git diff. If the diff also
contains a change to PROJECT_NAME, the entry and authorized task do not
explain the additional change, so the reviewer asks for a correction before
approval.

An entry that cannot be verified
--------------------------------

'Updated the report and fixed the files' is too broad. It does not say which
report, which files, what values changed, or whether the source data passed
validation. Another student cannot repeat the check or discover whether an
unexpected path was introduced.

Improve a vague entry by identifying the relevant SEB card, exact path, the
old and new value where that helps, and the command or observation used to
check it. Keep the entry short enough to read but complete enough to support
a decision.

Difference between status and authority
---------------------------------------

A Trello card may say In Progress, Ready for Check, or Complete. Those labels
help the team organize work; they do not by themselves establish that a
proposed requirement was approved. The approved project plan and recorded
decision still govern which changes students make.

The Git commit proves what files were recorded and when. It does not prove
that every edit met the task. The peer review and validation evidence connect
the saved change back to its stated acceptance criteria.

What happens if a check fails
-----------------------------

Do not record a failed file as verified. State the failing check, the file
and row or line involved, and what must happen next. A failed check may be as
simple as one misspelled status, but the report should wait until the record
is corrected and the count is repeated.

A history entry can record a resolved failure without deleting that it
happened. This makes it possible to explain how the team reached a reliable
final state.
