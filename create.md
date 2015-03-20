# Create #

> Jobs can be created in a variety of ways. Players can use +pitch to put up
> a PITCH job, +request to put up a REQ job, +bug to put up a CODE job, and
> +typo to put up a BUILD job.
```
  +job/create <bucket>/<title>=<text of job>
```
> This command allows those with access to the system to create a new job.
> This job is placed into `<bucket>`, provided the enactor has access to that
> bucket. Jobs created with the suite of player commands are assigned
> priorities, buckets, and due dates automatically. The `/create` command
> creates a job with none of this information - it is a clean slate.
```
  +job/query <player list>/<title>=<query>
```
> This command opens a job in the QUERY bucket, and mails `<player list>` with
> the query. Players can then access the job with +myjobs. Players have 7 days
> to respond to queries.

## TRIG\_CREATE ##

> Sometimes it is necessary to engage the TRIG\_CREATE trigger from within
> your own code in order to create a new job.
```
    @trigger <Job Database>/TRIG_CREATE=<%0>,<%1>,<%2>,<%3>,<%4>,[%5],[%6],[%7]
```
> It accepts the following arguments:

> %0=Person who opened the job
> %1=Bucket DB#
> %2=Priority
> %3=Title (truncated to 30 characters)
> %4=Opening Comment (truncate to 8000 for MUX and 4000 for MUSH3)
> %5=Player List for Opened\_By (if different from %0)
> %6=Assigned\_To (null if you don't want to assign anyone)
> %7=Hook to run

> Only 0-4 are required, and the others are optional.

> You should not have to worry about passing %7. If it is '1', then that
> means the job will run HOOK\_CRE (+job/create), and any other value
> indicates that HOOK\_OTH is to be run. Since you are using code other than
> +job/create to create the job, you should leave it blank.