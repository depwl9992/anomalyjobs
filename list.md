# List #

> These commands help you sort through various +jobs.
```
  +jobs
  +jobs/all
  +jobs/list <bucket>
  +jobs/mine
  +jobs/pri
  +jobs/search <pattern>
  +jobs/new
```
> The first command displays a list of all +jobs for buckets that you have
> access to, not including any jobs in hidden buckets. The second command
> displays a list of all jobs in all buckets that you have access to,
> including hidden buckets. The /list switch gets a list of all jobs in
> `<bucket>`, provided that you have access to `<bucket>`. Using the /mine switch,
> you can get a list of all jobs assigned to you. Using the /pri switch, you
> can get a list of jobs by priority. You can /search through jobs for
> `<pattern>` and get a list of all jobs containing it. Using /new you can list
> all jobs that have new activity.
```
  +jobs/sort
  +jobs/date
  +jobs/stats
  +jobs/overdue
  +jobs/who <player>
```
> Using the /sort switch, you can get a list of jobs sorted by bucket. The
> list isn't very pretty, however. Using the /date switch, you can get a list
> of jobs sorted by when the job was last modified, with recent modifications
> at the bottom of the list. Using the /stats switch, you can get a list of
> basic statistics on the jobs system. With the /overdue switch, you can list
> all jobs that are in overdue status. The /who switch allows you to get a
> list of jobs that have been assigned to `<player>`.