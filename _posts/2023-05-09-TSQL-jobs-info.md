---
layout: post
title:  TSQL Jobs info
categories: [Code, SQL]
---

This is a code snippet in TSQL which returns information on jobs scheduled on a particular server, ordered by their last run date. It can be used to monitor what is happening on the server.

```
SELECT
  j.job_id,
  j.name,
  h.last_run,
  description,
  enabled,
  p.name as owner,
  date_created,
  date_modified,
  FROM msdb.dbo.sysjobs j
  LEFT JOIN
    (SELECT job_id, MAX(run_requested_date) last_run FROM
      msdb.dbo.sysjobactivity
        GROUP BY  job_id)
  LEFT JOIN sys.server_principals p
    on p.sid = j.owner_sid
 ORDER BY h.last_run
```
