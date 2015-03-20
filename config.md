# Config #

## access ##
Access parameters to the Jobs system.

> Anomaly Jobs has a tiered access structure. By changing who has access to
> various commands, you can selectively allow players like builders into the
> system so they can work. The access locks are on the `Job Database <JD>`
> object. Bucket access locks are stored at the bucket level.
```
     HAS_ACCESS:      Returns 1 if a player can access the +jobs system.

     COMPLETE_ACCESS: Returns 1 if a player can /complete jobs.
     APPROVE_ACCESS:  Returns 1 if a player can /approve jobs.
     DENY_ACCESS:     Returns 1 if a player can /deny jobs.
     CREATE_ACCESS:   Returns 1 if a player can use the /create command.
     ADD_ACCESS:      Returns 1 if a player can use the /add command.
     GIVE_ACCESS:     Returns 1 if a player can use +bucket/access.
     EDIT_ACCCESS:    Returns 1 if a player can use the /edit command.
     STATS_ACCESS:    Returns 1 if a player can pull reports on the system.
     LOG_ACCESS:      Returns 1 if a player can /log a job.
     MAIL_ACCESS:     Returns 1 if a player can /query and /mail.
```
> A player must pass HAS\_ACCESS before the other locks are applied.

> Access to buckets are set at the bucket level (see [baccess](config#baccess.md)).

## advanced ##
Advanced configuration.

### aaccess ###

> Actions can be restricted by bucket. This allows you to customize the
> available actions to, for instance, prevent jobs from being tampered
> with in automated buckets. The format for this is:
```
  &<action code>_ACCESS <bucket>=<return 1 to access, 0 to deny>
```
> The `<action>`_ACCESS code allows for one argument: %%0 == PlayerDB#._

> Example: If you do not want a job to ever be transferred out
> of an automated XP bucket (not included) you can prevent
> this behavior if you know the three-letter action code (in this
> example, TRN):

> &TRN\_ACCESS XP=0

### hooks ###
How to set up action hooks.

> All actions have what are called ‘action hooks’, which are arbitrary commands
> that you can add to buckets to make the jobs process more automated and
> extensively expand the capabilities of the system. This is where the real
> power of Anomaly Jobs is located.

> These can be set either on the bucket or the bucket parent. If set on the
> bucket, an action hook will be for that local bucket only. If set on the
> parent, an action hook will be for all buckets. Setting them on a job is
> silly, but possible (the hook will be destroyed when the job is, and won't
> have any powers while it is there).

> The `HOOK_<action>` is passed three parameters:
```
      %0: Job DB#
      %1: DB# of action’s enactor.
      %2: DB# of the bucket.
```
> Examples:
```
    &HOOK_CRE <Job Parent Object>=&ASSIGNED_TO %0=%1
```
> > In the above example, the job is assigned to the creator. Since this is
> > set on the parent, this behavior is global.
```
    &HOOK_APR <Job Parent Object>=@trigger [v(VA)]/TRIG_LOG=%0,[v(VA)]
```
> > In the above example, the job will log to the server logfile when it is
> > +job/approved. Since it is set on the parent, it is global behavior.
```
    &HOOK_ADD <REQ bucket>=@pemit/list [u(%0/OPENED_BY)]=JOBS: Comments
      added to [name(%0)] by [name(%1)];@set %0/[dec(get(%0/NUM_COMMENT))]=
      no_inherit
```
> > In the above example, whenever anyone /adds to a job in the REQ bucket,
> > the player who opened it is sent a broadcast message, and then the
> > comment is published (no\_inherit set on a `COMMENT_*` determines if it is
> > published or not).

### letters ###
How to mail / bbpost / set automatic job comments.


> Anomaly Jobs supports four types of form letters:
|aletter     |Addition letters - formatting an added comment.   |
|:-----------|:-------------------------------------------------|
|bletter     |Broadcast letters - formatting broadcast messages.|
|mletter     |Mail letters - sent to the OPENED\_BY list.        |
|pletter     |Post letters - posting a letter to the BBS.       |


### codes ###
A list of default action codes.

| **CODE** | **Description** |
|:---------|:----------------|
|ADD|Player comment. Generated with +job/add                                 |
|APR|+job/approve closing action.                                            |
|ASN|Assignment to a user.                                                   |
|AUT|Automatic hook. If set, will run daily.                                 |
|CKI|Checked In.                                                             |
|CKO|Checked Out.                                                            |
|CLN|Clone action. Only appears on the newly created job.                    |
|COM|+job/complete generates this closing action.                            |
|CRE|Can only be first comment. Generated with +job/create.                  |
|DEL|+job/delete closing action.                                             |
|DNY|+job/deny closing action.                                               |
|DUE|Due date change.                                                        |
|EDT|Indicates when a comment has been edited.                               |
|LOK|Indicates when a job has been locked.                                   |
|MRG|Indicates a job that has been merged from two jobs.                     |
|NAM|Indicates a title change.                                               |
|OTH|A job created by any means other than /create triggers the OTH hook.    |
|PUB|Indicates a job/comment has been published.                             |
|SRC|Indicates when a job's OPENED\_BY (source) has changed.                  |
|STA|A +job/set status change.                                               |
|SUM|Indicates a change in the summary settings.                             |
|TAG|Indicates a job has been tagged or untagged.                            |
|TRN|Indicates a job has been transferred.                                   |
|UNL|Job unlocking action.                                                   |
|UNP|Indicates a job/comment has been unpublished.                           |

### summary ###
How to set up a Bucket Summary

> A Summary is a special type of sub-header that appears under the primary
> header. It can be used to display arbitrary information about the job,
> the poster, or types of jobs.

> Take a look at the summary from the TPS bucket:
```
  -----------------------------------------------------------------------------
   Approved: Yes
    Players: Laco, O'Rielly
   Schedule: Feb 2, 2006
        Arc: Groundhog Day
      Staff: Starfleet
   Synopsis: While celebrating Sid Vicious' birthday, Laco and O'Rielly are
     thrown into a short-term temporal loop.
  -----------------------------------------------------------------------------
```
> This information is independent of the comments added to the job and can be
> altered by the user using '+job/sumset'. If set on a bucket, it is local, and
> if set on the parent, the behavior is global.

> To set a summary:
```
       &SUMMARY <Bucket>=<text>
```
> It is passed two parameters:
```
       %0 = Job DB#
       %1 = Enactor's DB#.
```

### sumsetting ###
How to configure /sumset parameters.

> Summary settings should only be set on the bucket, and not the parent. If
> set on the parent, then it becomes a bucket setting and /sumset will not
> function on it (though +bucket/set will pick it up, as both formats are
> identical).

> A summary setting requires two attributes and has an optional third:
```
    ACCESS_<setting>  (required)
    PROCESS_<setting> (required)
    ERROR_<setting>
```
> If you need to see examples, refer to the TPS bucket's settings.
```
  ACCESS_<setting>:
```
> The `ACCESS_<setting>` determines who can use /sumset on the `<setting>`. It is
> passed one argument: %0, which is the Player DB# being tested. It returns 1
> if the player can access `<setting>` and 0 if not.
```
  PROCESS_<setting>:
```
> This is the most complicated attribute. It requires:
```
  [setq(3,<attribute>)][setq(1,<data>)][<test input, return 1 or 0>]
  
  Optional:
  
  [setq(2,<error>)]
```
> `<attribute>` is the attribute to set on the job object if the input is
> accepted. `<data>` is the data that is getting set (null will clear the attr).
> At the end of the two registers, you should test the input and return 1 if
> the input was acceptible, and 0 if it was not.

> Only if this returns 1 does `<attribute>` get set to `<data>`.
```
  ERROR_<setting>
```
> If `PROCESS_<setting>` has returned 0, then the code will generate an error
> message.

> If you set %q2 in `PROCESS_<setting>`, then error message attributes will be
> constructed like so:
```
       ERROR_<setting><%%q2>
```
> In this way, you can display 'complex' errors that make sense, such as the
> classic: 'That is not a player.', 'That player is not approved.', and 'That
> player is not of the Ninja class.'

### trig\_add ###
The 'add-to-job' trigger.

> Sometimes it is necessary to engage the TRIG\_ADD trigger from within your
> own code in order to add information to a job.
```
    @trigger <Job Database>/TRIG_ADD=<%0>,<%1>,<%2>,<%3>
```
> It accepts the following arguments:
```
       %0 = Job DB#
       %1 = Comments to add
       %2 = Player adding the comments
       %3 = Action code to run
```
> You can pass any action code (or any three-letter code) to the trigger that
> you wish. There is no 'master list' of actions. However, unless the action
> code is listed in Job Database's LIST\_VISCOMMENTS it will not be visible to
> someone looking at the job. So if you want your addition to be seen with
> the standard job-read view, you should either pass an ADD code or make sure
> that your unique action code is located in LIST\_VISCOMMENTS.
& trig\_broadcast

> You may need to trigger the broadcast within a command of your own.
```
  @trigger <Job Database>/TRIG_BROADCAST=<%0>,<%1>,<%2>,<%3>,<%4>
```
> > %0=Job DB# (or `<text>`)
> > %1=Enactor DB#
> > %2=Three letter Action Code
> > %3=Wild (handled via the BLETTER as necessary)
> > %4=Wild (as above)


> Only %0 is mandatory, and is a special case. If %0 is a DB#, it will go
> through the BLETTER process (see 'bletter'). If %0 is not a DB#, it will
> broadcast whatever you send to it.

## baccess ##
Setting bucket access parameters.

> Bucket access is set on the bucket itself, as the ACCESS attribute:
```
     &ACCESS <Bucket DB#>=[switch(get(%0/RACE),VAMPIRE,1,0)]
```
> It should return 1 for access and 0 for no access.

> You should make an effort to keep the access locks uncomplicated, as the
> broadcast code uses it to filter out non-receivers. Large locks can
> chew up that process on games with many people connected.

## bconfig ##
Basic bucket configuration.
```
  +bucket/info <bucket>
```
> Using the /info switch, you can get the configuration information on
> `<bucket>`.

> To change your basic configuration settings:
```
  +bucket/set <bucket>/<setting>=<value>
```
> Valid bucket `<settings>`:

> DESC: Change the bucket's description. These should be kept relatively
> > short.


> HELP: Text to display for +bucket/help to describe how to handle jobs
> > located there, plus any help for +job/sumset required.


> HIDDEN: Determines whether or not a bucket is visible when the player types
> > +jobs. Valid `<values>` are 'yes' and 'no'.


> LOCKED: If a bucket is locked, all jobs within cannot be modified. However,
> > jobs in locked buckets can be transferred out into non-locked
> > buckets.


> LOGFILE: Identifies the file to log to (if logging is enabled). Valid
> > `<value>` is a `<filename>` (with no directory or extension info -
> > all of that is handled automatically). See '[logging](config#logging.md)'.


> MYJOBS: Determines whether or not +myjobs can access the bucket. Valid
> > `<values>` are 'yes' and 'no'.


> POST\_APPROVE: Determines what BBS# a bucket will post to when a job is
> > completed with '+job/approve'.


> POST\_COMPLETE: Determines what BBS# a bucket will post to when a job is
> > completed with '+job/complete'.


> POST\_DENY: Determines what BBS# a bucket will post to when a job is
> > completed with '+job/deny'.


> TURNAROUND: Determines how many hours to add to the due date of a job
> > automatically upon creation.

## logging ##

> Jobs can be logged to files on the shell account. In TinyMUSH and PennMUSH,
> logs are stored in existing game logs. For MUX and RhostMUSH, a separate log
> file may be designated.  Lognames for supported servers are:
```
    TinyMUSH:  game/netmush.log
    PennMUSH:  game/log/command.log
    RhostMUSH: game/<logfile>_manual.log
    MUX:       game/logs/M-<logfile>.log   (Note: file must exist)
```
> The default `<logfile>` is 'reqlog' for the REQ bucket and 'joblog' for all
> other buckets.

> In MUX, logging cannot occur unless the log already exists on the server.
> You must have access to your shell account to create these files.  To create
> the logs, you can use touch, for example:

```
       > cd logs
       > touch M-joblog.log
```

## uconfig ##
How to configure your personal jobs experience.

> Your personal jobs list can be configured. By setting a list of fields on
> yourself, you can  get a customized display of the jobs listings.
```
  Field  Displays                         Field  Displays
  -------------------------------------------------------------------------
   T     Title                             B     Bucket
   D     Due On                            A     Assigned To
   S     Status                            M     Modified On
   C     Creation Date                     O     Opened By
   #     Job DB#                           F     Flags
```
> You can set these by typing, for example:
```
    > &JOBS me=TBDS (will display Title, Bucket, Due On, and Status)
```
> The default is: BTDAS

> Width of the individual job fields described above may also be customized by
> setting the JOBSWIDTH

&lt;field&gt;

 attribute.  For example:
```
    > &JOBSWIDTH_T me=25 (will reduce Title width to 25 characters)
```

> Anomaly Jobs will automatically detect your terminal width (if your client
> supports it), defaulting to 80 characters otherwise.  If your client does
> not report width, you may set it with the JOBSWIDTH attribute:
```
    > &JOBSWIDTH me=100 (will override autodetection and set width to 100)
```
> Anomaly Jobs also supports skins, which are display definitions that allow
> you to change the way that +jobs looks to the user. By default, Anomaly
> Jobs ships with three skins: DEFAULT (the classic skin), CHROME (an example
> skin), and WHITEBG (tamer color contrast than DEFAULT).

> To change your skin:
```
    > &JOBSKIN me=<skin name>
```

> There are two methods by which you can track new job activity. The new
> method is similar to Myrddin's BBS (i.e., once you read a job, it is no
> longer 'new' to you). The old method (new activity since your last log
> out is new until you log out again) is the default.

> To use the new method:
```
    > &JOBSN me=1
```
> You can filter out some mail generated by the system (such as +request
> receipts) by setting:
```
    > &JOBS_NOSPAM me=1
```
> This will filter out 'non-important' MLETTER