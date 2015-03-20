# JGroups #
```
  +jgroups
```

> This command will display a list of jgroups that have been defined.  Jgroups
> are convenient ways to add a list of players to some jobs commands, and may
> be used in place of player names in the +job/assign, /query, /source, /tag,
> and /untag commands.

```
  +jgroup/create <jgroup>=<description>
```
> This command creates `<jgroup>` with the `<description>` you provide. Jgroup
> names must begin with +, e.g., +TPStaff, +Coders, etc.  The ISMEMBER
> attribute is used to determine membership in the group and defaults
> to checking the MEMBERLIST attribute. The ISMEMBER attribute may be changed
> to reference other tests of group membership.

```
  +jgroup/member <player>=<jgroup>
```
> This command toggles membership in `<jgroup>` to the named `<player>`.  This has
> no effect if the ISMEMBER attribute does not reference MEMBERLIST.

```
  +jgroup/info <jgroup>
```
> This command displays the description and membership of `<jgroup>`.

```
  +jgroup/delete <jgroup>
```
> This permanently removes `<jgroup>`.