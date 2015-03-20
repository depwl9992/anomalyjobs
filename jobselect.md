
```
    +jobs/select all         (same as +jobs/all)
    +jobs/select new         (same as +jobs/new)
    +jobs/select mine        (same as +jobs/mine)
    +jobs/select overdue     (same as +jobs/overdue)
    +jobs/select who=none    (same as +jobs/who none)
```
> However, the +jobs/select command's power is in returning lists of jobs
> that meet multiple criteria.  For example, the command:
```
    +jobs/select new or mine
```
> would return a list of jobs that appeared in either the +jobs/new OR the
> +jobs/mine lists.  Similarly:
```
    +jobs/select new and mine
```
> would return a list of jobs that appeared in both +jobs/new AND +jobs/mine.

> The `<expression>` may be a single selection criterion or combination of
> several using the Boolean logic operators AND, OR, or NOT (&, |, or !),
> along with parentheses if needed, such as:
```
    +jobs/select (new | overdue) & ! who=none
```
> which would list jobs that are either new or overdue, and not unassigned.

> Job selection criteria include the following:
```
  all - all jobs
  new - new jobs (same criteria as +jobs/new)
  mine - jobs assigned to or tagged for you (same as +jobs/mine)
  overdue - jobs past their due date 
  due<=<date/time> - jobs due before the specified date/time
  due>=<date/time> - jobs due after the specified time or with no due date
  who=<player or none> - jobs assigned to <player> / unassigned
  source=<player> - jobs originated by <player> 
  pri=<color> (or esc=<color>) - jobs of green, yellow, or red priority
  status=<status> - jobs of hold, new, underway, 25, 50, 75, or 100 status
  bucket=<bucket> - jobs in <bucket> 
  search=<pattern> - jobs including <pattern> in their text
  viewing (or monitor) - jobs in buckets you have selected to monitor
  hidden - jobs in buckets designated as hidden
  public (or myjobs) - jobs in buckets designated public
  published - jobs which have been published
  summary - jobs containing summary attribute
```
> Logical operators are left-associative. The following are equivalent:
```
    +jobs/select new | overdue & mine
    +jobs/select (new | overdue) & mine
```
> Both would return new or overdue jobs that are assigned to/tagged for you.

> If a parameter requires spaces (such as dates, player names, or search
> terms) it must be enclosed in quotation marks.    Due dates may be
> specified as either:
> - time() format: "Dec 25 00:12:00 2009"
> - MM/DD/YY: 12/25/09
> - Time-from-now in days/hours/mins/secs:  "1d 12h" or 36h

> Examples:

```
    +jobs/select viewing 
```
> - would return output identical to +jobs.

```
    +jobs/select due<="1d 12h" & (pri=yellow | pri=red)
```
> - would return jobs of yellow or red priority due in the next 36 hours.

```
    +jobs/select (bucket=code | bucket=build) & due<=01/01/10
```
> - would return CODE or BUILD jobs due before the New Year

```
    +jobs/select bucket=TPS & (search=dragon & !search="dragon egg")
```
> - would return jobs in the TPS buckets which included the word dragon
> > but did NOT include the words "dragon egg".


> Similar to the way the &JOBS attribute specifies which columns display for
> +jobs, a player may use &JOBSELECT to redefine which jobs will be shown
> for the +jobs command.  For example:
```
    &JOBSELECT me=viewing | mine
```
> This would add jobs from "mine" to the existing list of monitored buckets
> for that player's +jobs command.

> Players may also store expressions using `&JOBSELECT_<name> me=<expression>`
> and then simply use `+jobs/select <name>`.  For example, if a player entered:
```
    &JOBSELECT_IMMINENT me=bucket=REQ & due<=36h & ! overdue
```
> They could then use the following command:
```
    +jobs/select imminent
```
> > - which would return REQ bucket jobs coming due in the next 36 hours.


> Players may override the default +jobs/all, +jobs/new, +jobs/mine, and
> +jobs/overdue lists by defining &JOBSELECT\_ALL, &JOBSELECT\_NEW,
> &JOBSELECT\_MINE, and &JOBSELECT\_OVERDUE.

> A game's code staff may add additional criteria by adding `&SEL_<criteria>`
> attributes to the Job Database `<JD>` object. These functions are called by
> filter() and take %0 (a job dbref) and %qa (the argument) and return 1
> if the job meets that selection criteria.