# Complete #
```
  +job/complete <#>=<comment>
  +job/approve <#>=<comment>
  +job/deny <#>=<comment>
  +job/delete <#>
```
> The first command allows you to complete job `<#>`. When `/complete` is used,
> the first comment of the job and your `<comment>` is posted on the public job
> bboard. No intermittent comments are posted to keep the buffer limit small
> (so that the BBS can handle it). It then deletes the job. `/approve` works in
> the same fashion, except the player who opened the job is sent an @mail, and
> a copy is posted to the staff-only job tracker. `/deny` works in the same
> fashion as `/approve`, only informs the job-opener that their request or job
> is denied.

> The `/delete` is only usable by a `WIZARD` character. The `/complete`, `/approve`
> and `/deny` commands can all be individually locked.

> Jobs will be permanently deleted 60 seconds after closing. To restore an
> inadvertently deleted job, use +job/trans to move it back to a bucket.