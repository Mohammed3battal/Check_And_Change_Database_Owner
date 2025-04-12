## Script: Check and Change SQL Server Database Owner

**Description**:
This script is designed to:
1. Check the current owner (`SUSER_SNAME(owner_sid)`) of all databases on the instance.
2. Generate dynamic SQL statements to change the owner of any database to the `sa` login (or another account).

**Use Case**:
- Useful during SQL Server migrations, audits, or standardizing ownership across databases.
- Helps detect non-standard or orphaned owners.
- Allows you to safely generate the `sp_changedbowner` commands for manual review.

**⚠️ Warning**:
Changing the owner may revoke permissions from an application service account if that account is the current owner. Always validate with application teams before proceeding.

**Instructions**:
- Step 1: Run the query to check all current owners.
- Step 2: Set the value of `sp.name` in the second query to the login you wish to replace.
- Step 3: Review and optionally execute the generated `sp_changedbowner` statements.

**Requirements**:
- SQL Server 2005 or later.
- Permissions to run `sp_changedbowner` (typically `db_owner` role or `sysadmin`).
