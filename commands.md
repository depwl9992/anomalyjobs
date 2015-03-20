# Commands #

|`+jobs`                                    |List jobs.                           |
|:------------------------------------------|:------------------------------------|
|`+jobs/<all|mine|new>`                     |List in `<bucket>`/all/yours/new.      |
|`+jobs/catchup`                            |Clears new jobs.                     |
|`+jobs/clean`                              |Removes non-players from job data.   |
|`+jobs/compress`                           |Compresses job list. (Wiz)           |
|`+jobs/credits`                            |Display credit information.         |
|`+jobs/list <bucket>`                      |List all jobs in `<bucket>`.          |
|`+jobs/overdue`                            |List overdue jobs.                  |
|`+jobs/reports [<report>]`                 |Get a report.                      |
|`+jobs/search <pattern>`                   |Search jobs for `<pattern>`.          |
|`+jobs/select <expression>`                |List jobs matching `<expression>`.   |
|`+jobs/<sort|date|pri>`                    |Lists jobs by bucket/mod/priority.    |
|`+jobs/who <player>`                       |Lists jobs assigned to player.      |
|`+job <#>`                                 |View a job.                          |
|`+job/act <#>`                             |Display actions on a job.           |
|`+job/add <#>=<comments>`                  |Add comments to a job.              |
|`+job/all <#>`                             |Displays all comments in a job.     |
|`+job/approve <#>=<comment>`               |Approve a player request.           |
|`+job/assign <#>=<<player>|none>`          |Assign a job to player.              |
|`+job/checkin <#>`                         |Checks in a job                     |
|`+job/checkout <#>`                        |Checks out a job.                   |
|`+job/claim <#>`                           |Assign a job to yourself.           |
|`+job/clone <#>`                           |Clones a job.                       |
|`+job/complete <#>=<comment>`              |Complete a job.                     |
|`+job/create <bucket>/<title>=<comments>`  |Create a job manually.              |
|`+job/delete <#>`                          |Delete a job. (Wiz)                  |
|`+job/deny <#>=<comment>`                  |Deny a player request.              |
|`+job/due <#>=<<date>|none>`               |Set job due date.                   |
|`+job/edit <#>/<entry#>=<old>/<new>`       |Edits a job.                        |
|`+job/esc <#>=<green|yellow|red>`          |Escalate a job's priority.           |
|`+job/help <#>`                            |Display help for a job's bucket.     |
|`+job/last <#>=<X>`                        |List last `<X>` entries in `<#>`.       |
|`+job/lock <#>`                            |Locks a job and prevents changes.   |
|`+job/log <#>`                             |Logs a job.                          |
|`+job/mail <#>=<message>`                  |Mails opener with `<message>`.        |
|`+job/merge <source>=<destination>`        |Merge two jobs into `<destination>`.   |
|`+job/name <#>=<name>`                     |Rename a job.                       |
|`+job/publish <#>[=<comment>]`             |Publishes a job or `<comment>`.       |
|`+job/query <players>/<title>=<query>`     |Sends a query to `<players>`.         |
|`+job/set <#>=<status>`                    |Set progress status on a job.       |
|`+job/source <#>=<player list>`            |Changes opened-by to `<player list>`. |
|`+job/summary <#>`                         |Views a job's header & SUMMARY.     |
|`+job/sumset <#>/<set>=<value>`            |Changes a job SUMMARY setting.      |
|`+job/tag <#>`                             |Tags a job for you.                 |
|`+job/tag <#>=<player>`                    |Tags a job for `<player>`.            |
|`+job/trans <#>=<bucket>`                  |Transfer a job.                      |
|`+job/unlock <#>`                          |Unlocks a job.                      |
|`+job/untag <#>`                           |Untags a job.                       |
|`+job/untag <#>=<player list>`             |Untags a job for `<player list>`.     |
|`+buckets`                                |
|`+bucket/info <bucket>`                    |
|`+bucket/help <bucket>`                    |
|`+bucket/monitor <bucket>`                 |
|`+bucket/create <bucket>=<description>`    |
|`+bucket/delete <bucket>`                  |
|`+bucket/access <player>=<bucket>`         |
|`+bucket/check <player>`                   |
|`+bucket/set <bucket>/<setting>=<value>`   |
|`+jgroups                                  |
|`+jgroup/info `

&lt;jgroup&gt;

`                   |
|`+jgroup/create `

&lt;jgroup&gt;

`=`

&lt;description&gt;

` |
|`+jgroup/delete `

&lt;jgroup&gt;

`                 |
|`+jgroup/member `

&lt;player&gt;

`=`

&lt;jgroup&gt;

`      |



> <pre>+jobs</pre>

> This command will invoke the 'main' jobs list. It displays all jobs that
> you have access to and are presently monitoring. You can tailor this list
> in several ways: +bucket/monitor will toggle whether or not you are viewing
> a particular bucket, the list can be altered to display job information you
> want (see 'uconfig').

> <pre>+jobs/all</pre>

> This command behaves exactly like '+jobs' (and can be tailored to your own
> tastes, see 'uconfig'), except it does it for all buckets that you have
> access to.

> <pre>+jobs/mine</pre>

> This command lists just those jobs that have been assigned to you.

> <pre>+jobs/new</pre>

> This command will display a list of jobs that have new activity. You can
> alter how 'new activity' is presented to you - see 'uconfig'.

> <pre>+jobs/catchup</pre>

> This command will catch you up on the jobs system, clearing all unread
> jobs as being new. This works for both versions of new jobs.

> <pre>+jobs/clean</pre>

> This command will remove all non-players from job entries.

> A &TRIG\_CLEAN trigger is provided on the Jobs Database object which may be
> called from autonuke code or hooked to @nuke / @dest to execute this function
> automatically.

> <pre>+jobs/compress</pre>

> This command will rename all Job Objects, 1 to X, and then set the next
> job # to be X+1. This is useful if your jobs start running into less
> convenient numbers to type, and can be used to correct errors in the job
> numbering. It is wizard-only.

> <pre>+jobs/credits</pre>

> Roll the credits.

> <pre>+jobs/list <bucket></pre>

> This command will list all jobs in 

&lt;bucket&gt;

.

> <pre>+jobs/overdue</pre>

> This command works exactly like '+jobs', except that it only displays those
> jobs that are overdue.

> <pre>+jobs/reports [<report>]</pre>

> Without `<report>`, this command displays a list of available job reports. If
> `<report>` is supplied, then that report is displayed. Some reports take
> additional input, such as ACTBY, for example:

> `+jobs/reports actby=add`

> This will run a report on all ADD actions across all buckets.

> <pre>+jobs/search <pattern></pre>

> This will search all jobs for `<pattern>` and return a list of jobs that
> have that pattern. It will search the entire object, not necessarily comments
> that the player has access to.

> <pre>+jobs/sort</pre>

> This command will display a list of jobs, except the list is organized by
> bucket.

> <pre>+jobs/date</pre>

> This command will display a list of jobs, based on when they were last
> modified.

> <pre>+jobs/pri</pre>

> This sorts all jobs by escalation code, red at top, then yellow, then green.
> Note that any jobs that have gone into OVERDUE status are not sorted as 'red'
> to keep sorting sane.

> <pre>+jobs/who <player></pre>

> This command lists all jobs that have been assigned to 

&lt;player&gt;

.

> <pre>+job <#></pre>

> This command will display the contents of Job <#>. Only those comments posted
> in the job that are human-created (+job/add, +job/mail, etc) are displayed.

> The number in brackets before each comment is the number of that comment. A
> + or - after that number indicates publication status of the comment (a plus
> means the comment is published, a minus means the comment is not published).

> <pre>+job/act <#></pre>

> This command will list all comments in `Job <#>` in an abbreviated format that
> indicates what the action code was for that comment, who performed it, when,
> and any arbitrary comment information posted with it. In this way, you can
> track the action history of a particular job from the time it was opened.

> <pre>+job/add <#>=<comments></pre>

> This command adds a `<comment>` to `Job <#>`. This also triggers off the ADD
> hooks.

> <pre>+job/all <#></pre>

> This command will display all actions in detail for `Job <#>`. It is similar
> to an expanded +job/act.

> <pre>+job/create <bucket>/<title>=<first comment></pre>

> This command creates a new job in `<bucket>`. It triggers off the CRE hooks.
> Who can use the create command is governed by the CREATE\_ACCESS lock on the
> Job Database object.

> <pre>+job/approve <#>=<comments></pre>

> This command approves `Job <#>`. This will delete the job, post to the private
> BBS, and @mails the player that their job is approved. The `<comments>` are
> added to the job as an ADD action, and the system finishes up by running the
> APR action.

> This is a 'private' command, in that communication between staff and players
> is kept confidential.

> <pre>+job/deny <#>=<comments></pre>

> This command denies `Job <#>`. This will delete the job, post to the private
> BBS, and @mails the player that their job is denied. The `<comments>` are
> added to the job as an ADD action, and the system finishes up by running the
> DEL action.

> This is a 'private' command, in that communication between staff and players
> is kept confidential.

> <pre>+job/complete <#>=<comments></pre>

> This command publicly completes `Job <#>`. It will delete the job and post the
> `<comments>` to the public BBS board. The `<comments>` are also added to the job
> as an ADD action, and the system finishes up by running the COM hooks.

> This command should be used for game-wide information about the completion
> of a job, such as rules clarifications, or player notification of a new part
> of the grid. Anything posted to the job's first comment and your `<comments>`
> then become public, so be careful when using /complete lest any secret
> player information become public.

> <pre>+job/checkout <#></pre>

> This command allows you to check out `job <#>`. Checked out jobs can only be
> modified by you until it is checked back in.

> <pre>+job/checkin <#></pre>

> This command allows you to check in `job <#>`. Wizards and the person who
> checked out the job are allowed to check them back in.

> <pre>+job/assign <#>=<player></pre>

> This command assigns `<player>` as being responsible for `Job <#>`. It triggers
> the ASN hooks.

> <pre>+job/claim <#></pre>

> This command is an alias for `+job/assign <#>=<yourself>`. It triggers
> the ASN hooks.

> <pre>+job/clone <#></pre>

> Makes an identical copy of a job from `Job <#>`. The CLN hooks are run on the
> newly created job, not the old job.

> <pre>+job/delete <#></pre>

> This command removes `Job <#>` from the system. It behaves silently in that
> it does not issue a broadcast to the rest of the Jobs users. It is wizard-
> only.

> <pre>+job/due <#>=<<date>|none></pre>

> This sets the due date for a job to `<date>`. Use the word 'none' if you want
> to clear the date. The `<date>` string can be in one of two formats:

> Jan 13 10:00:00 2006
> 01/13/06

> This command also runs the DUE hooks.

> <pre>+job/edit <#>/<comment#>=<old>/<new></pre>

> This edits the contents of `Job <#>`'s `<comment#>`, replacing `<old>` text with
> `<new>` text. You can only edit the ADD and CRE comments. You can only edit
> comments that belong to you, except in the case of wizards, who can edit
> anyone's comments. This command triggers the EDT hooks.

> <pre>+job/esc <#>=<green|yellow|red></pre>

> This command changes the job's escalation color (aka priority color). A green
> color indicates a low priority. A yellow color indicates that the priority is
> elevated. A red color indicates a high priority.

> A job that has gone into overdue status will display as red in priority.
> However, this does not actually change anything on the job itself. If you
> set a yellow priority on a job and it goes overdue, you can remove the due
> date and it will revert to a yellow priority.

> This command triggers the ESC hooks.

> <pre>+job/help <#></pre>

> This command displays the HELP attribute on the bucket that the job is in. If
> any MYHELP exists, it will be displayed as well.

> <pre>+job/last <#>=<X></pre>

> This command will list the last `<X>` normally viewable entries in `Job <#>`.

> <pre>+job/lock <#></pre>

> This command will lock a job from further modifications. The only changes
> that can be made to a locked job is a transfer to a new bucket (this is to
> support locking a bucket, but you may want to move jobs in and out of a
> locked bucket). This command also runs the LOK hooks.

> <pre>+job/log <#></pre>

> This command dumps `Job <#>` into its bucket's LOGFILE setting. It also runs
> the LOG hooks.

> <pre>+job/mail <#>=<message></pre>

> This command will send mail to the players listed as the job's source (or
> Opened By field). It triggers the MAI hooks when enacted.

> <pre>+job/merge <source>=<destination></pre>

> Sometimes it becomes necessary to combine jobs, and this command does just
> that. It merges `<source>` into the `<destination>` job. The MRG hooks are run on
> the destination, not the source.

> <pre>+job/name <#>=<title></pre>

> This command changes the `<title>` of `Job <#>`. It runs the NAM hooks when
> enacted.

> <pre>+job/publish <#>[=<comment>]</pre>

> If `<comment>` is provided, then this command publishes (or unpublishes) a
> comment. Without `<comment>`, this publishes the whole job. For a breakdown of
> publication rules, please see 'publication'. It runs the PUB and UNP action
> hooks when activated, depending on whether or not the comment is being
> published or unpublished.

> <pre>+job/query <player list>/<title>=<comments></pre>

> This command will create a job in the QUERY bucket. It will set the source
> of the job to `<player list>`. It then sends an @mail to `<player list>` that
> informs them of the query and how to access it via +myjobs. It also runs the
> OTH hooks.

> Once there, the job follows standard myjobs rules: each player can only see
> their own comments and the initial comment in the job.

> <pre>+job/set <#>=<hold|new|underway|25|50|75|100></pre>

> This command changes the completion/progression status of a job.

> The available settings are:
```
    hold       The job is currently awaiting something and cannot proceed.
    new        Newly created jobs default to this status.
    underway   The job is currently being processed.
    25         The job is 1/4 complete.
    50         The job is 1/2 complete.
    75         The job is 3/4 complete.
    100        The job is complete.
```
> Job status should be periodically updated with the progression of the work.

> <pre>+job/source <#>=<player list></pre>

> This command changes the Opened By list on `Job <#>` to `<player list>`.

> <pre>+job/summary <#></pre>

> This command displays the header of the job, the summary of the job, and
> a staff-only view of settings, readers and statistical information.

> <pre>+job/sumset <#>/<setting>=<parameter></pre>

> This command changes `Job <#>`'s summary `<setting>` to `<parameter>`. You can get
> a list of available `<settings>` using `'+bucket/info <bucket>'`, where `<bucket>`
> is the bucket that the job is presently in.

> By default, only two buckets come with settings that can be altered: TPS and
> RP. These buckets use identical SUMMARY information to assist in the
> management of plots. It also runs the SUM hooks.

> <pre>+job/tag <#>[=<player list>]</pre>

> This command tags a job for a player, letting them see the job in +myjobs.
> The player will see all of `Job <#>` as if they had access to the bucket that
> it was in. Even if the job is not in a +myjobs-accessible bucket, the player
> will still be able to read all of it.

> If used without `<player list>`, the tagging is accomplished for yourself. It
> runs the TAG hooks.

> <pre>+job/trans <#>=<bucket></pre>

> This command will move `Job <#>` from its current bucket to a new `<bucket>`.
> It also runs the TRN hooks.

> <pre>+job/unlock <#></pre>

> This command unlocks `Job <#>`, allowing modifications to be made to the job
> once again. This command runs the UNL hooks.

> <pre>+job/untag <#>[=<player list>]</pre>

> This is the opposite of +job/tag, and will remove `<player list>` from the
> list of people that `Job <#>` is tagged for. If used without `<player list>`,
> then the untagging is done for yourself. It runs the TAG hooks.

> <pre>+bucket/info <bucket></pre>

> This command allows you to see detailed configuration information about a
> `<bucket>`, including its DB#, most of which can be altered using +bucket/set.

> <pre>+bucket/monitor <bucket></pre>

> This command toggles whether or not you are viewing a bucket in your normal
> +jobs list. If a bucket is not monitored, then jobs in it will not appear
> on the normal list, but will still appear in places like '+jobs/mine',
> '+jobs/new', etc.

> <pre>+bucket/create <bucket>=<description></pre>

> This command creates a new `<bucket>`, assigning it a `<description>`. The locks
> for the bucket will be set to '1', so you will probably want to change those.
> This is a wizard-only command.

> <pre>+bucket/delete <bucket></pre>

> This command destroys `<bucket>`. The bucket must be empty. This will destroy
> the bucket instantly. Wizard only.

> <pre>+bucket/access <player>=<bucket></pre>

> This gives `<player>` access to `<bucket>`, even if the player does not pass the
> default bucket locks. They must still pass the system's HAS\_ACCESS lock,
> however.

> <pre>+bucket/check <player></pre>

> Checks all buckets and lists whether the player has access or not.

> <pre>+bucket/set <bucket>/<setting>=<parameter></pre>

> This command sets `<bucket>`'s `<setting>` to `<parameter>`.

> See 'bconfig' for information on how to configure your buckets.

> <pre>+bucket/help <bucket></pre>

> This command displays help for `<bucket>`, showing information on how jobs
> in the bucket should be handled and any setting information. The bucket's
> HELP file can be set with +bucket/set.