# psqlrc


Put this in your pipe and smoke it.

No wait, actually, put this in `~/.psqlrc`



```
-- Formatting for tables
\x auto

-- Print date on startup
\echo `date  +"%Y-%m-%d %H:%M:%S"`

-- Set client encoding to SQL_ASCII (to match what is on the server)
\encoding SQL_ASCII

-- Do NOT automatically commit after every statement!
\set AUTOCOMMIT off

-- Be verbose about feedback
\set VERBOSITY verbose

-- [user]@[host]:[port]/[db]['*' if we are in a transaction]['#' if we are root-like; '>' otherwise]
\set PROMPT1 '%n@%m:%>/%/%x%# '

-- Prevent Ctrl-D from exiting psql.
\set IGNOREEOF 5

-- Make history ignore all lines entered that were preceded by spaces, and ignore any entries that matched the previous line entered.
\set HISTCONTROL ignoreboth

-- Keep a different history file for each database name you log on to.
\set HISTFILE ~/.psql_history- :DBNAME

-- Keep a history of the last 2000 commands.
\set HISTSIZE 2000

-- Instead of displaying nulls as blank space, which look the same as empty strings (but are not the same!), show nulls as [NULL].
\pset null '[NULL]'

-- Show pretty unicode lines between rows and columns in select results.
\pset linestyle unicode

-- Show pretty lines around the outside of select results.
\pset border 2

-- Turn off the pager so that results just keep scrolling by, rather than stopping.
\pset pager off

-- Within columns, wrap long lines so that select results still fit on the display.
\pset format wrapped

-- Show how long it takes to run each query.
\timing

-- Show the application_name in pg_stat_activity.
-- Good database citizens set this field so we know who to blame when a query hogs resources,
-- or somebody stays idle in transaction for too long.
set application_name to manni_desktop; commit;

-- Set bytea output to show as many ASCII letters as possible.
-- (Handy if you are storing text whose encoding you do not know in bytea columns.)
set bytea_output to escape; commit;
```
