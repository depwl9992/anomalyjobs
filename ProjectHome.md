Anomaly Jobs is a fully featured suite of tools for task tracking. It can install directly from a script without any editing at all - the script does all the work for you. If you want to keep your MUX or MUSH organized, this code is for you. Features include:

## New Features in Version 6 ##
  * Integrated install file for both new installs and upgrades from Jobs 5.
  * Fully Compatible with MUX 2.x, PennMUSH, RhostMUSH, and TinyMUSH 3.1.
  * Displays respect terminal width and allow users to set custom column widths.
  * +jobs/select command, allowing complex logical filtering of jobs lists with multiple criteria.
  * +jgroups, user groupings for job assignment, tagging, source and query.
  * New action locks to control CREATE and TRANS actions on buckets.
  * New +myjob summaries so users can use +myjob/sumset.
  * +jobs/checkout and /checkin support.
  * Better new job tracking; +jobs/catchup to clear new job indication flags.
  * +jobs/clean command and associated cron-capable &TRIG\_CLEAN to remove non-players from jobs data.
  * Added BLETTER support, to allow for broadcast customization.
  * Job posting BBoards are now stored by dbref to survive board renumbering.

## Standard Features ##
  * Tiered access control. Control who can see what, and who can use which commands.
  * +job/publish - Control the comments a player can see in jobs.
  * +job/mail - Staff-to-player communication on jobs is visible to all staff, improving coordination.
  * +myjobs - Players can contribute additional information on their own jobs.
  * Skins - Default, Chrome (greyscale), and WhiteBG skins, and the ability to create your own.
  * Jobs stored in organizational buckets, and gives you the ability to add or destroy buckets as needed.
  * Summaries - extend the functionality of buckets.
  * Add information to a job - without fear of hitting the 8k buffer limits.
  * View all actions performed on a job with a timestamp and owner of the action.
  * Reports - Advanced tracking and summary statistics for jobs, including bar and and pie charts.
  * Settable due dates.
  * Settable escalation codes - jobs are color-coded based on priority: Green/Yellow/Red.
  * Logging - Support for logging completed jobs to a server side log file.
  * Assign a job to someone.
  * Automatic escalation of priority if a job goes into overdue status.
  * Main job lists shows which jobs have new activity.
  * Simple, intuitive command structure.
  * Access locks on individual buckets. Control who can see which jobs.
  * Ability to hide buckets from the standard list, to keep the list from being too spammy.
  * Integration with Myrddin's BBS for archiving completed jobs and progress tracking.
  * Script installs the entire system with no user intervention, including BBS integration.
  * Security-conscious coding.
  * Help files included.
  * Query players with a paper trail.
  * Customizable bucket triggers.

Note: When uploading these to your game using your client, you should use at least a one second delay between the upload lines. Be sure to review the README document before you upload, as there may be settings that you wish to change. If you have renamed your Job Global Objects, this script may not work.