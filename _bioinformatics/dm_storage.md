---
title: Data Storage Best Practices
last_modified_at: 2018-06-20
---
Depending on the type of data used by a research group, different combinations of data storage options may be appropriate.  In general, the three categories of data storage common to Fred Hutch researchers are:
- Databases
- File-Based Storage, which includes:
  - POSIX Style, such as fh/fast or the "Z drive" often mapped directly to workstations)
  - Object Storage (AWS S3 and Swift, often accessed via a "client" or other software that facilitates the upload/download of items)
- Temporary File-Based Storage

Assessing the strengths, mode of access, and interactivity with computing resources of each of these types of data storage options alongside an assessment of the types of data a research group use and the type of interactions with those data is becoming more important for researchers.  This assessment also is becoming more important to repeat over time as data storage and connectivity infrastructure changes and as the particular data types and interactions of research groups evolve.  


## Database Storage Overview
Overview of what types of database storage systems are available for researcher use and generally how to get started/figure out which one to set up.  

## File-Based Data Storage

Most Fred Hutch based researchers using large scale biomedical data sets initially store their data using the *Fast File* service alongside their smaller scale laboratory data.  This provides direct, rapid access to files both manually (e.g., via mapping a drive to a workstation) and to local computing resources (via our HPC cluster, see below).  However, a strategy for where, when and for how long to store what size data is important to create to ensure that data access by researcher or compute resource, transfer and archiving are not unnecessarily complicated thus hindering the research process.  

### File-Based Storage PI Allocations
Each PI is provided with 5TB of storage space via the *Fast File* service which can be accessed by mapping the drive to their workstation (using "//center/fh/fast/lastname_f" on a Mac or "\\center\fh\fast\lastname_f" a PC). This storage space access point can provide members of research groups access to groups of datasets that can have different types of permissions.  Within a PI's *Fast File* directory, directories can exist for data shared to any Fred Hutch user (/pub), to any member of the PI's immediate research group (/grp), or private to each individual user in a PI's immediate research group (/user).  Additionally, links to other data sources can appear here, such as data from the Fred Hutch Genomics Shared Resource (/SR).  This can be customized for a given researcher in conjunction with Scientific Computing (see Available Resources).

### Object Storage PI Allocations
As the amount of research data grows, which can occur rapidly when new large scale data is generated, existing externally generated datasets are transferred into the *Fast File* system, OR if existing data is inadvertently duplicated.  When the space requirements become larger, it is recommended that researchers begin implementing a set of more active data management practices.

Currently it is recommended to use a combination of *Economy File*,
*Scratch* and *Fast File*.

*Economy File* is less expensive than *Fast File* and is suitable for large scale data sets that are not frequently accessed (i.e., ~monthly or less) but that require a relatively large amount of storage space.  For example, *Economy File* would be suitable for a set of large files such as fastq's or bam's that on a daily basis are not accessed, but when a new bioinformatic process is desired, a large "burst" of activity will be occurring that will need to interact with the data.  *Economy File* serves as an archive for these data, and typically compute processes do not directly access these files.

## Temporary File-Based Storage
*Scratch* serves as a temporary location for large data sets that ideally reside in an archive space like *Economy File*, to be transferred to when compute processes are applied to them.  Data in *Scratch* are typically then deleted automatically after certain timeframes when they are no longer needed. Intermediate data that is generated can be saved in *Scratch* as well, and then the final data resulting from the compute process can be written to the *Fast File* locations for the researcher.  This allows large data to be archived in *Economy File*, accessed by HPC when it is temporarily housed in *Scratch* and only the (typically smaller) resulting data are written to the more accessible, but more costly *Fast File* system.

## Overview of File-Based Storage Resources

Storage Resource | Costs per TB/month\* | Resource Admin\*\* | Backup Location/Duration | Desktop Access | HPC Access
--- | --- | --- | --- | --- | ---
Fast File | $30 | Center IT | On-site snapshots (7 days), Off-site tape (1 year) | Mapped Drive, (X:\fast\lastname_f on PC, smb://center/fh/fast/lastname_f on Mac) | Direct, path: /fh/fast/lastname_f
Economy Local | $3 | Center IT | On-site, multi-building replication (60 day) | Client Required (e.g., Cyberduck), download then use local copy | Via Swift command line tools, copy to Scratch for use
Economy Cloud | $3 | Scientific Computing | Off-site, multi-region (AWS) replication (60 day) | Client Required (e.g., Cyberduck), download then use local copy | Via AWS S3 command line tools, copy to Scratch for use
Scratch | Free, no max limit | Scientific Computing | No backup, data purged on regular basis (e.g., 10, 30, 90 days)  | Mapped Drive, (X:\scratch on PC, smb://center/fh/scratch on Mac) | Direct, path: /fh/scratch

\* Costs apply for stored data above 5TB per PI only.  
\*\* All admin contact can be initiated by emailing FH username `helpdesk`, but different system administrators are primary for different platforms.  Admin assistance can be requested for data transfers and validation, data import, as well as restoring data from backups for a given resource if available.

## Available Resources
- Contact Scientific Computing staff by emailing FH username `scicomp` for help with:
  - identifying current storage space usage
  - assistance with identification of possible duplicated data sets
  - setting up customized *Fast File* directory structures
  - guidance with implementing active data management practices
