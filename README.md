# Co-op Application Tracker - CSC 370 Sprint 1

Group 3: Amrinder Singh, Jaiman Singh, Aashna Sadeque. 
We worked together on the design, implementation, verification and documentation.

This MySQL database tracks students' co-op applications, job postings, resume selections, interview rounds and offers. Sprint 1 extends the kick-off implementation with a normalized resume-selection relationship, stronger integrity rules, complete diagrams and reproducible verification. All demonstration data is synthetic.

## Guide to the submission

Start with the [Sprint 1 report and Sprint 2 plan](SPRINT_PLAN.md). It compares the prior commitments with delivered results, addresses the kick-off feedback and sets measurable goals through Advanced SQL.

| Grading criterion | Evidence |
| --- | --- |
| Achievement of sprint goals | The report's prior-commitment and feedback tables link each result to its implementation or verification. [Saved results](evidence/README.md) include seven report outputs, valid workflows, rejected writes and migration checks. |
| Justification for missed goals | The report's technical-limits section distinguishes completed work, design assumptions and unverified submission actions. No subsequent TA meeting or approval is claimed. |
| Improvement in course-level competencies | The next-sprint matrix names the course competencies “Analyse data with SQL,” “Model the world as data,” and “Build robust back ends,” with current limitations, shared team responsibility, effort and objective success criteria. |
| Coverage of new module competencies | The [course mapping](docs/COURSE_ALIGNMENT.md) connects current work through Advanced Relational Design and planned work through Advanced SQL to evidence and checks. |

## Submission checklist

The assignment asks for a repository link plus the exact commit hash and one video; it does not ask for the course PDFs or a separate upload of every source file. The technical files to keep together in the Sprint 1 repository are:

- Core report/design: `README.md`, `SPRINT_PLAN.md`, `CONCEPTUAL_ERD.md`, `CONCEPTUAL_ERD.svg`, `ERD.md`, `ERD.svg`, `RELATIONAL_SCHEMA.md`, `NORMALIZATION.md`, and `SOURCES.md`.
- Video prep: `SPRINT1_VIDEO_SCRIPT.md` is optional planning support; the submitted artifact is the recorded video, not this script.
- Implementation/demo: `schema.sql`, `supporting-files/seed.sql`, and `supporting-files/demo_queries.sql`.
- Course/constraint justification: `docs/COURSE_ALIGNMENT.md`, `docs/CONSTRAINTS.md`, and `docs/CONCEPTUAL_DESIGN_REVIEW.md`.
- Evidence: `evidence/README.md` and all six supporting result files: `conceptual-erd-verification.txt`, `demo-output.tsv`, `design-verification.txt`, `migration-verification.txt`, `mysql-verification.txt`, and `theory-examples.txt`.

The `docs/archive/` kickoff plan/schema/seed are historical comparison material, not needed to run the current demo. They are useful for the documented migration and provenance, so **keep them in the repository**; do not attach them as separate submission files. Do not include `.DS_Store`, `.freebuff/`, lesson PDFs, the rubric, or unrelated kickoff-folder copies in the Sprint 1 repository. Do not include temporary preview wrappers or generated review artifacts. `SOURCES.md` should cite/acknowledge the assignment material and any AI assistance actually used. The supplied rubric and course PDFs are workspace reference materials, not part of the project submission; the course topics and assistance are documented by reference in SOURCES.md.

The required repository URL, exact commit hash and video are not stored in this folder and cannot be confirmed from this checkout. For this three-person team the maximum video length is **11 minutes** (5 + 2 × 3); the instructor may fail a video that exceeds the limit. Confirm repository access for the instructor and TA-client, then submit the link/hash and video through Brightspace.

The relational diagram (`ERD.svg`) is intentionally a logical, table-oriented view; the conceptual ERD (`CONCEPTUAL_ERD.svg`) is the Chen-notation model.

## Design and feedback corrections

| Topic | Files |
| --- | --- |
| Complete conceptual model and participation | [Chen ERD and explanation](CONCEPTUAL_ERD.md) |
| All nine tables and 59 columns | [Relational ERD](ERD.md), [schema reference](RELATIONAL_SCHEMA.md), [executable DDL](schema.sql) |
| Table-by-table BCNF, FDs, keys, minimal bases, projection, 3NF and 4NF | [Normalization report](NORMALIZATION.md) |
| SQL and relational-algebra constraints; weak entities and inheritance | [Integrity rules and design decisions](docs/CONSTRAINTS.md) |
| Eight conceptual-design quality criteria | [Design review](docs/CONCEPTUAL_DESIGN_REVIEW.md) |
| Preservation of the kick-off data | [Saved migration results](evidence/migration-verification.txt) |
| References and assistance acknowledgement | [Sources](SOURCES.md) |

The original kickoff plan, DDL and seed are retained in `docs/archive/` as the comparison baseline. They describe the earlier version; the files linked above describe Sprint 1.

## Run the database and reports

Requirement: MySQL 8.0.16 or later. Recorded database verification used MySQL 8.4.8. All nine tables explicitly use InnoDB.

Run these commands from the repository root with a MySQL account permitted to create databases, tables and triggers and execute SELECT, INSERT, UPDATE and DELETE:

```sh
mysql -u root -p < schema.sql
mysql -u root -p < supporting-files/seed.sql
mysql -u root -p < supporting-files/demo_queries.sql
```

This creates `coop_application_tracker_sprint1`. Existing tables cause the load to stop; the current schema does not drop a database. Use a fresh installation for these commands rather than loading the seed over existing data. The archived kickoff DDL is historical and includes a database reset; it is not the current setup command.

## Verification evidence

The [evidence index](evidence/README.md) describes the saved results: 56 database checks, 15 migration checks, 12 worked theory checks, 10 design checks and two conceptual-diagram coverage checks. The [seven report outputs](evidence/demo-output.tsv) can be compared with a fresh run of the supplied schema, seed and report SQL.

These are recorded verification results from the development version. The Python verification/generation tools and optional migration implementation are retained locally, outside this submission checkout. Their recorded results remain here as supporting evidence; the automated suites cannot be rerun from this checkout alone. The SQL demonstration and written design proofs can be checked using the files included here. Domain assumptions and 4NF reasoning are documented in the normalization report.
