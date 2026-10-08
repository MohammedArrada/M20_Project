M20 DATA DICTIONARY AND FIELD GUIDE
===================================

Purpose and record boundaries
-----------------------------

This file defines the field names and valid values of the approved status
baseline. Read it before changing the 12-row source file. Do not add
explanatory prose to systems_status.dat itself, because later programs expect
one record per line.

A line is one system observation. Four fields are separated by three literal
pipe characters. Empty fields, extra pipes, and spaces attached to a status
can change what the next program reads.

Field 1  system_id
------------------

A system ID identifies one specific monitored system. The baseline contains
SYS-101 through SYS-112 once each. Keep the ID stable when correcting another
field; changing an ID can lose the link to maintenance history.

The SYS prefix and three digits are part of the stored identifier. A report
count should be based on records that pass validation, not on the highest
numeric ID.

Field 2  unit
-------------

The unit names the group responsible for the system: ALPHA, BRAVO, CHARLIE,
or DELTA. The unit is separate from the status. Preserve the unit even if the
system is not ready.

Grouping by unit may be useful in a later report, but the required current
report counts statuses across the entire 12-record baseline.

Field 3  status
---------------

READY means available for the current mission. MAINTENANCE means work is
planned or underway. NOT_READY means unavailable for the reporting cutoff.
These three values must match spelling, case, and underscore exactly.

MAINT, NOT READY, ready, READY followed by a space, and an empty value do not
match the approved status strings. A blind text replacement can change
content outside the status field; inspect each affected row.

Field 4  last_checked
---------------------

The date records when the system was checked, in YYYY-MM-DD form. Use four
digits for year, two for month, and two for day. The classroom validation
checks its shape, not whether a calendar library accepts the date.

The source date may differ between valid records. Do not change a valid date
merely to make all rows match. SYS-108 is the specifically documented row
with the incorrect 10/05/2026 format.

Expected counts and verification
--------------------------------

The corrected 12-record baseline is 5 READY, 3 MAINTENANCE, and 4 NOT_READY.
The three category counts add to 12. If they do not, look for a missing row,
duplicate row, wrong status, or accidental edit.

A field-count check can identify a missing or extra pipe. A status check
identifies values outside the three-item list. A date-shape check identifies
other formats. All checks and counts must agree before updating the report.

READING EXAMPLES FOR THE DATA FILE
==================================

A complete row
--------------

SYS-101|ALPHA|READY|2026-10-05 has exactly three pipe separators and four
fields. SYS-101 identifies the system, ALPHA identifies its unit, READY
describes the status, and the last field records the check date.

The separator itself is not part of any field value. When an operator reports
that a row has four fields, they mean four values divided by three
delimiters.

A row with an empty status
--------------------------

SYS-112|DELTA||2026-10-05 still has four fields in a technical sense, but
field three contains no approved status. The field-count check alone cannot
prove that the row is valid.

Read the maintenance decision note before changing this field. After entering
NOT_READY, verify that the other three values remain unchanged.

A row with a formatting error
-----------------------------

SYS-108|CHARLIE|READY|10/05/2026 contains a status that is valid but a date
whose shape differs from YYYY-MM-DD. Correct only the date. Rewriting its
status or unit would introduce an unapproved change.

A regular-expression shape check cannot guarantee that a date exists on the
calendar. Explain the limit of the check when describing what was verified.

ADDITIONAL FIELD INTERPRETATION CASES
=====================================

The boundary between a delimiter and data
-----------------------------------------

A pipe separates fields, so the sequence of values matters. If a student
deletes a pipe while editing a status, a later program may read three fields
instead of four. A field-count check detects this structure error.

The same check cannot detect an empty third field if the two pipes remain
side by side. Always pair field-count validation with a status-value check.

Case and whitespace
-------------------

The approved values are exact strings. A lowercase character or a trailing
space can create an unexpected fourth category when sorting or counting. A
person may overlook that difference when scanning a printed report.

Inspect the field as data, not only as a word. A change in a narrative
example is different from a change in one of the 12 source rows. The latter
affects the counts the commander receives.

Date shape and meaning
----------------------

A YYYY-MM-DD shape is required because it avoids the two common month/day
interpretations of a slash date. The source includes valid rows checked on
dates other than October 5. Their date is still meaningful for the snapshot.

A shape check detects missing separators and swapped formats. It does not
independently verify that the day exists in a particular month. Describe
precisely what was checked when recording evidence.

System ID continuity
--------------------

After editing, the list should still contain SYS-101 through SYS-112 exactly
once each. A copied row can make the number of lines appear correct while
leaving one ID missing and another duplicated.

The approved editing task concerns specific status and date fields, not new
identities. If an ID appears to require changing, stop and request a separate
decision.

Relationship to later systems
-----------------------------

The Bash workflow uses the exact delimiter and status values for validation
and counting. The OpenVMS export converts the same records into fixed-width
fields. The Python solution normalizes approved formats to the same four
field names.

These later consumers make small text differences important today. A checked
data dictionary helps each course agree on what a record means without
relying on an ambiguous filename.
