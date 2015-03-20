# Manage #

```
  +job <#>
  +job/new <#>
  +job/add <#>=<comments>
  +job/trans <#>=<bucket>
  +job/esc <#>=<green|yellow|red>
  +job/assign <#>=<player>
  +job/merge <source>=<destination>
```
> The first command allows you to view an individual job. You can only see
> added comments with this command. The /new switch allows you to see just
> the comments that have been added to `<#>` since your last log out. The /add
> switch adds `<comments>` to job `<#>`. The /trans switch transfers job `<#>` to
> `<bucket>`. The next command alters job `<#>`'s escalation code to `<green>`
> or `<yellow>` or `<red>`. The next command assigns job `<#>` to `<player>`. The
> next command merges two jobs together. Job `<source>` is copied into Job
> `<destination>`.
```
  +job/mail <#>=<message>
```
> The /mail switch sends the list of players in Opened-By a `<message>`
> via @mail and gives instructions to the player on how to respond.
```
  +job/set <#>=<hold|new|underway|25|50|75|100>
  +job/due <#>=<<date>|none>
  +job/act <#>
  +job/all <#>
  +job/name <#>=<title>
```
> The first command changes job `<#>`'s status to the given value. The second
> command allows you to set a due date for job `<#>`. The `<date>` string can be
> in one of two formats: 'Jan 13 10:00:00 2003' or '01/13/03'. Using /act
> will allow you to view all job actions performed on a job - escalations,
> sets, merges, all information will be displayed, with when the action was
> performed and by whom. +job/all reads an entire job, like an expanded /act
> command. Using /name allows you to change the `<title>` of Job `<#>`.

> The /set value codes are: hold=ON HOLD, new=NEW, underway=UNDERWAY,
> 25=1/4 COMPLETE, 50=1/2 COMPLETE, 75=3/4 COMPLETE, 100=COMPLETE.
```
  +job/lock <#>
  +job/unlock <#>
  +job/checkout <#>
  +job/checkin <#>
```
> When a job is locked, it cannot be modified in any way until unlocked. It
> can, however, be transferred to another bucket. This behavior is allowed in
> case administrators wish to impose a lockdown on a whole bucket. If someone
> has checked out a job, it cannot be modified until it is checked back in.
```
  +job/edit <#>/<Entry #>=<Old>/<New>
```
> This command edits `<Entry #>` on Job `<#>`, replacing `<Old>` with `<New>`.
```
  +jobs/compress
```
> This is a wizard-only command. When job ID numbers become too large (say,
> in the thousands), it is prudent to compress your job list to make the
> numbers more manageable. When you compress the jobs, it renumbers all
> open jobs, one through X, and resets the next available job number.