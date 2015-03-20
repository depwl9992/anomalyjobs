# Buckets #
```
  +buckets
```
> This command will display a list of information about all of the buckets that
> you have access to. For wizards, this information is very detailed. Here's
> the meaning of the more esoteric bucket info:
```
    Flags: VHPMLS (Viewing Hidden Published Myjobs Locked Summary)
    #Jobs: How many jobs are in the bucket.
    Pct: Percentage of jobs in the system in this bucket.
    A: Post to this BBS on /approve.
    C: Post to this BBS on /complete.
    D: Post to this BBS on /deny.
    Due: Auto-overdue in this many hours
    ARTS: Average resolution times.
```
```
  +bucket/help <buckets>
```
> This command displays the help file for `<bucket>`, which should outline how
> jobs within the bucket are worked, as well as any setting information for
> `+job/sumset`.
```
  +bucket/info <bucket>
```
> This command displays detailed information on `<bucket>`. Much of this reflects
> the +buckets command, only in an expanded form, except for the following:

> Provides: This lists special attributes that are passed down to the job. If a
> job has summary information, it will show up here.

> Settings: These are user-defined summary settings, settable with the command
> +job/sumset.

> Players: This is a list of connected players who presently have access to that
> bucket.
```
  +bucket/monitor <bucket>
```
> Invoking +bucket/monitor allows you to toggle whether or not you see a bucket
> when you type +jobs. Any jobs in those buckets still show up in other list
> views such as +jobs/new.
```
  +bucket/create <bucket>=<description>
```

> This command creates `<bucket>` with the `<description>` you provide. You must
> set a lock for the bucket on the `Job Database <JD>`, as it defaults to 1
> (anyone who can pass the main lock can access it). /create is Wizard-only.
> See '[baccess](config#baccess.md)' for help with configuring the bucket lock.
> You can also restrict actions by bucket (see '[aaccess](config#aaccess.md)').
```
  +bucket/access <player>=<bucket>
```

> This command toggles access to `<bucket>` to the named `<player>`. This allows
> them to bypass the default bucket locks. They must still pass the main
> lock to access. You can change who can alter access with the GIVE\_ACCESS
> on the `Job Database <JD>` object. It defaults to wizard only.
```
  +bucket/delete <bucket>
```

> This permanently removes `<bucket>`. The bucket must have no jobs inside of
> it for it to be successful. Wizard only.