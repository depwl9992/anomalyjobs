# Player Commands #

## bug ##
How to submit a bug report.
```
  +bug <title>=<description>
```
> This command is used for bug reporting. In `<title>` put the command that is
> bugged, or something else appropriate. Please be as descriptive as possible
> in the `<description>` field. What were the results you were expecting? What
> happened in its place? By giving lots of detail here, it saves us the time of
> tracking you down to drag the information out of you. Thanks.

## myjobs ##
How players keep track of their issues.
```
  +myjobs
  +myjob <#>
  +myjob/add <#>=<comment>
```

> This suite of commands allows the submitter to view and modify jobs that they
> have submitted to the system. When viewing a job that you own, you can only
> see the comments that you have added, not comments added by others.

> Jobs can be tagged by staff for you to see. In those instances, you can see
> all comments added, not just those you have added.
```
  +myjob/help <#>
  +myjob/sumset <#>/<setting>=<value>
```
> If staff has set a MYHELP attribute on the bucket, +myjob/help will display
> it, as well as special summary settings, which may be set with
> +myjob/sumset.
```
  +myjob/help <#>
```
> This command displays the MYHELP attribute on the bucket that the job is in.
> If there are any special sumsettings (summary settings) for the job, the help
> for it will be located here.


## pitch ##
How players submit ideas to the game.
```
  +pitch <title>=<description>
```
> This command tosses an idea to staff. The idea can be story related or just
> an idea on how to make the game better. PITCH jobs are different from those
> created with +request. They are not issued due dates. Staff is under no
> obligation to even answer them. By procedure, they are either discarded
> with no fanfare, tucked away for future implementation or they are run with
> either in modified or unmodified form.

> For story pitches, it puts a story idea into the RP jobs bucket. Now, this
> is not a request for a TP, this is a method of giving story ideas, or theme
> ideas, to the staff for consideration. If you want to request a scene, use
> +request.

## request ##
How players submit a need to staff.
```
  +request <title>=<description>
```
> This command requests `<title>` and `<description>` from staff. The request is
> added to the jobs list and will be tended to as soon as possible. Please do
> not bug staff - it will be handled shortly. There is a standard three day
> turnaround time on +requests.

## typo ##
How to submit a typo report.
```
  +typo <typo description>
```
> This command reports a typo. Please be specific about where the typo is, what
> the typo is, and what you think it should be changed to.