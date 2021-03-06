# Install Instructions Windows

### Required Perl Modules - These will autoload on demand
~~~
Email::Send (If using email)              ->  command: ppm install Email::Send            - (Normaly installed by default)
Email::Send::SMTP (If using SMTP)         ->  command: ppm install Email::Send::SMTP      - (Normaly installed by default)
Email::Send::Sendmail (If using Sendmail) ->  command: ppm install Email::Send::Sendmail  - (Normaly installed by default)
Email::Send::Gmail (If using gmail)       ->  command: ppm install Email::Send::Gmail
* commands listed are for ActivePerl in elevated command prompt
~~~ 

##### This script does not write or manipulate any Array Data. It is a wrapper for snapraid http://www.snapraid.it/

##### Feel free to test. All data manipulation is done by snapraid http://www.snapraid.it/

##Windows: 

You need Perl installed on windows. Options are:
* ActivePerl       - http://www.activestate.com/activeperl - Version I have tested
* Strawberry Perl  - http://strawberryperl.com/
* DWIM Perl        - http://dwimperl.com/

~~~ Windows
1. Download latest snapPERL from https://github.com/Osjur/snapPERL/releases/
2. Extract to hard drive. Good place is under Snapraid folder eg. "C:\snapraid\snapPERL"
3. Edit and rename snapPERL.conf.example to snapPERL.conf
4. Rename custom-cmds.example custom-cmds
5. Edit snapPERL.conf taking great care to enable Windows paths to conf and snapraid binary with correct full paths
6. See notes about email before trying to enable sendmail
7. Use PPM with ActivePerl to install needed modules (Or other Perl Package Manager installed)
8. From elevated command prompt run snapPERL.pl
~~~
_(Always run first time on command line - Script will check your snapPERL conf file is valid)_

#### Automation using Task Scheduler

~~~
Automation:
I will create .bat file at some point which asks user how one wants to schedule the script to run with task scheduler. 


Manually:
Run Task Scheduler : Start Menu -> Search -> Task Scheduler
                     Start Menu -> All Programs -> Accessories -> System tools -> Task Scheduler
                     Start Menu -> Administrative Tools -> Task Scheduler
                     Start menu -> Run -> C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Administrative Tools\Task Scheduler.lnk

Click 'Create Basic Task'

Enter Name: snapPERL
Enter Description: Snapraid automation wrapper
Click 'Next'

Set to Daily 
Click 'Next'

Set date and Time (Tomorrow @ 02:00:00) - Should have 1 in the Recur box
Click 'Next'

Select 'Start a Program'
Click 'Next'

Enter loction of script -Example C:\snapraid\snapPERL\snapPERL.pl
Add any command line arguments (Normaly none)
Click 'Next'

Click on 'Open the Properties dialog for this task when I click Finish'

Click 'Finish'

Click 'Change User or Group'
Enter 'Local' in box and click 'Check Names'
Select 'LOCAL SERVICE'

Click on 'Run with highest privileges (Snapraid needs to be elevated but not sure if this is needed with LOCAL SERVICE)

Under 'Settings' tab change max run time to '1 day'

Click 'OK'

Done!
~~~

WOW and GUI's make things more easier? :P

---

#### Command Line Options - Good for testing after install
##### Only for overrides set all permanent options in snapPERL.conf

    snapPERL.pl [ -c  --conf CONFIG         { Full path to conf file        } ]
                [ -x  --custom-cmds FILE    { Full path to custom-cmds file } ]
                [ -m  --message-level 1-3   { Set message level             } ]
                [ -l  --log-level 1-5       { Set log level                 } ]
                [ --stdout    --nostdout    { Toggle log to stdout          } ]
                [ --check     --nocheck     { Toggle check option enable    } ]
                [ --scrub     --noscrub     { Toggle scrub option enable    } ]
                [ --email     --noemail     { Toggle email send             } ]
                [ --custom    --nocustom    { Toggle custom cmds            } ]
                [ --pushover  --nopushover  { Toggle Pushover send          } ]
                [ --smart     --nosmart     { Toggle smart logging          } ]
                [ --pool      --nopool      { Toggle snapraid pool          } ]
                [ --spindown  --nospindown  { Toggle spindown disks         } ]
                [ -h  --Help                { This Help                     } ]
                [ -v  --version             { Display Version               } ]

---
