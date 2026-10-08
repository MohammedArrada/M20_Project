# M20 Readiness Reporting Project
=================================

Purpose and approved starting point
-----------------------------------

The M20 team prepares a readiness report from a controlled status data file.
A commander needs to know how many systems are READY, MAINTENANCE, and
NOT_READY. The current work is a short-term manual repair. Later courses will
automate the work in Bash, export a controlled OpenVMS file, and build a
Python solution.

The current project plan is M20_Project_Plan_v3.docx. A file called FINAL or
v2_approved is not enough to establish the current instructions. The class
identified the current plan from approval and change evidence in Basic
Configuration Control. Use the SEB tasks from that plan and the class Trello
board.

Where to work
-------------

The incoming directory is the received source package and must remain
unchanged. The working directory contains a matching copy for editing. The
extensions directory holds optional practice. An editor may display files
from incoming for reading, but do not save changes there.

On the AlmaLinux VM use ~/simple_editing/working. At the end of the course,
copy the verified contents of working into source/linux inside your
M20_Project repository on Windows. Confirm the destination before staging
anything in Git.

Current manual process
----------------------

1. Open data/systems_status.dat.

2. Count each status value manually.

3. Update reports/current_status_report.txt.

4. Archive and publish the verified report.

How the report reaches the team
-------------------------------

The data file has four pipe-separated fields: system ID, unit, status, and
last-checked date. There are 12 approved baseline records. After correction,
the values must reconcile to 5 READY, 3 MAINTENANCE, 4 NOT_READY, and 12
TOTAL.

A count alone is not sufficient evidence. Check the structure and each
allowed status before trusting the totals. Preserve the earlier report when
updating the current report. Later automated work must stop if a record fails
validation.

Reading order and file map
--------------------------

Read docs/editing_tasks.txt for the approved editing scope and
docs/report_requirements.txt for the report rules. Consult
docs/data_dictionary.md for the four field meanings and
docs/maintenance_notes.txt for the approved decision about SYS-112.

The config directory holds settings that later scripts will read. The data
directory holds the baseline file. The reports directory holds the manual
current report. The linux, openvms, and python directories contain
requirements for the courses that follow. Do not implement code for those
later courses during Simple Editing Basics.

Review and handoff
------------------

For each edited file, compare the working copy against its incoming original
using diff. A difference is expected when it matches an approved correction.
A change to an unrelated sentence, field, or date requires investigation.

Before transferring the package, another student checks the corrected README,
procedure, configuration, data, handoff note, and report. Record the relevant
Trello task ID, the person who checked, the result, and any unresolved issue.
Git records the transferred files after verification.

SEB-01  Linux access
--------------------

Locate your AlmaLinux home folder, VM name, and editor commands.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

SEB-02  Package download
------------------------

Use the direct fixed ZIP URL supplied for class and check extraction.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

SEB-03  Inventory
-----------------

Identify original and working copies and count the baseline records.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

SEB-04  Documentation
---------------------

Correct the README, procedure, and handoff note using gedit.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

SEB-05  Configuration
---------------------

Repair settings using nano and check referenced paths.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

SEB-06  Data
------------

Correct specified rows using vim without changing other IDs or dates.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

SEB-07  Verification
--------------------

Validate 12 records, approved values, totals, and manual report.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

SEB-08  Transfer
----------------

Use scp, inspect Git changes, commit, push, and record evidence.

A task is complete when its expected output can be checked by someone else.
Record the result on the existing class Trello card; do not create a separate
printed worksheet.

PROJECT CONTEXT AND READING GUIDE
=================================

Why this package exists
-----------------------

The team had several project plans with close names and different scopes.
That experience showed why people need a controlled plan, a clear place for
source files, and a record of who approved a change. This package represents
the next part of the same mission: making the received Linux materials
accurate enough to support a trustworthy short-term readiness report.

The folder includes both original evidence and an editable work area. This
duplication is intentional. If a student is unsure what a line originally
said, the incoming copy supplies the answer. If a later team asks why a line
changed, a focused diff between incoming and working shows the specific edit
and its context.

How to read without getting lost
--------------------------------

Start with this README to understand the purpose of the project. Read
docs/editing_tasks.txt to find exactly which changes are authorized. Read
docs/report_requirements.txt to understand what the corrected report must
contain. Use the data dictionary for field meanings and the maintenance note
for the otherwise ambiguous SYS-112 record.

Do not read a future-course requirements file as permission to write Bash,
DCL, or Python code today. Those files are included so an editor can see how
a path or field name will be used later. The required work in this course is
reading, making targeted changes with Linux editors, and checking the result.

Two types of correct information
--------------------------------

Some content describes what the received package said, even though that
earlier statement was wrong. Historical descriptions can remain accurate
descriptions of the past. An operational instruction telling the next person
which file to open must reflect the approved current path.

When using search and replace, first ask which type of sentence you found.
For example, a sentence saying 'the older document used the singular
filename' is an explanation. A numbered step telling the operator to open
that singular filename is an instruction that needs correction. Avoid
changing both automatically.

Why preservation matters
------------------------

Incoming files and archived reports help the team explain how a wrong output
was corrected. Their presence does not make their contents the current
approved method. Current controlled instructions, reviewed working edits, and
an evidence record show what should guide the next action.

If a student edits an incoming file by mistake, stop and tell the instructor
before making more changes. Do not hide the mistake by changing another copy.
The original package can be extracted again for comparison while the editing
and verification are repeated in working.

How a new team member can check the handoff
-------------------------------------------

The new team member should locate the current v3 plan, identify the SEB task
card, see the corrected files in source/linux, and find the commit that
introduced them. They should be able to recompute the twelve-record counts
from the copied data without using the displayed report numbers as an answer
key.

When information is missing, the next team should record the gap, identify
who can resolve it, and continue only when the required input is trustworthy.
This is part of configuration control as well as careful editing.
