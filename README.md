# ZUtil-unofficial-documentation
An unofficial documentation of $ZU and $ZUtil function in IRIS/Ensemble/Caché

## Link to the official documentation

https://docs.intersystems.com/priordocexcerpts/rZUt.pdf

## Official replacement

https://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=RCOS_replacements

## Table of commands


|Command|Description|Commentaire|
|----|----|----|
|$ZU(0)|  create CACHÉ.DAT

|$ZU(1)|  modify CACHÉ.DAT

|$ZU(2)|  delete CACHÉ.DAT

|$ZU(3)|  dismount CACHÉ.DAT

|$ZU(4, pid)|Terminates a process (^RESJOB) |API: %SYSTEM.Process.Terminate()|
|$ZU(4, pid, flag) | flag = integer, if negative -> process termination operations (-65 when process is a systemdaemon / unresolved transaction state, other). If positive -> exit status code that Caché returns to the host operating system upon termination.

|$ZU(5)|Print current namespace| $NAMESPACE, not exactly replacement, but preferable |
|$ZU(5, "namespace")|Switch to namespace| $NAMESPACE="namespace"|

|$ZU(6)|Dead process clean up|

|$ZU(7)|Flush a block from buffer pool

|$ZU(8)|Manipulate DLM locks

|$ZU(9, device, message)|Print message to cconsole log (device = "" is the default device)|API: %SYS.System.WriteToConsoleLog() or %Library.Device.Broadcast()|
|$ZU(9, terminal, message, timeout) | timeout: integer specifying the number of secondes to wait before timeout (used with named terminals only) |
|$ZU(9, device, message, loglevel)|loglevel: numeric code indicating which logging level option to use (used with operator console only) |

|$ZU(10)|Start network daemon

|$ZU(11)|

|$ZU(12)|Returns the full path of the mgr directory|
|$ZU(12, name) | Returns the current namespace pathname |API: %Library.File.ManagerDirectory and %Library.File.DirectoryExists()|
|$ZU(12, name, canon=0) | Canonicalize name as a filename, does not check if valid | API: %Library.File.NormalizeDirectory() 
|$ZU(12, name, canon=1)| Canonicalize name as a directory name. Returns null if it is not a directory (existing or not) 
|$ZU(12, name, canon=2)| If name refers to an existing directory, canonicalize name and return the full pathname. Otherwise, return null.
|$ZU(12, name, canon=3)| If name refers to an existing directory or a special device that can contain a Caché database, canonicalize name and return the full pathname. Otherwise, return null
|$ZU(12, name, canon, case) | The default canonical form returned is entirely in lowercase letters, regardless of the case of name. To preserve uppercase letters on Windows systems, specify a caseflag with a value of 1. 

|$ZU(13) | old netalloc | Removed

|$ZU(14) | Job server | 

|$ZU(15, devname) | Translate RMS filename to canonical form | API: %Library.File.NormalizeFilename()

|$ZU(16) | Returns device names of specified type

|$ZU(17) | Mounts database

|$ZU(18, n) | Sets undefined variable handling for the current process. n is optional (0 by default), changes behavior of Caché when it encounters an undefined variable for local, process-private global, and global variables; it has no effect on special variables. | API: %SYSTEM.Process.Undefined()
|$ZU(18, 0) | Issues the <UNDEFINED> error for any undefined variable.
|$ZU(18, 1) | Returns a null string for a reference to an undefined variable with subscripts, and issues the<UNDEFINED> error for undefined variables without subscripts.
|$ZU(18, 2) | Returns a null string (instead of issuing an <UNDEFINED> error) for any undefined variable.
|$ZU(18, -1) | $ZU(18, 2)

|$ZU(19) | Duplicate of $ZU(18) |

|$ZU(20, new) | Specifies the namespace(s) that contains the routine dataset. | API: %SYSTEM.Process.UserRoutinePath() 
|$ZU(20, new, second, third) | If Caché does notfind a routine in new, Caché looks for the routine in second. If Caché does not find the routine in second, Caché looks for the routine in third, and so on. | Using routines in second is VERY slow!

|$ZU(21, 0) | Returns the location of process-private globals. | API: %SYSTEM.Process.PrivateGlobalLocation()
|$ZU(21, 1) | Deletes allprocess-private globals. It returns 1 upon successful completion, 0 upon error. Returns 1 even iuf no process-private globals defined. | API: %SYSTEM.Process.KillPrivateGlobals()

|$ZU(22, 0, ff, bs) | Form feed/Backspace control sequence in this job. ff and bs optional, new form feed control code sequence / new backspace control code sequence. | API: %Library.Device.SetFFBS()

|$ZU(23) | Collation

|$ZU(24) |

|$ZU(25) |

|$ZU(26) |

|$ZU(27) | Create a database

|$ZU(28, string, flag) | Performs collation conversion. It applies the collation type specified in flag to string | API: %SYSTEM.Util.Collation()
|$ZU(28, string, 0) | EXACT: Returns string unchanged. Does not convert NULLs. | Corresponds to the Caché SQL%EXACT function.
|$ZU(28, string, 1) | SPACE: Appends a blank to beginning of string
|$ZU(28, string, 2) | MVR: Returns string unchanged, except for NULLs, which are converted. Provided for MultiValue support. | Corresponds to the Caché SQL %MVR function.
|$ZU(28, string, 3) | PLUS: Converts numerics and numeric strings to canonical numbers. A nonnumeric string is returned as 0
|$ZU(28, string, 4) | MINUS: Converts numerics and numeric strings to canonical numbers and appends a minus sign. A nonnumeric string is returned as 0.
|$ZU(28, string, 5) | UPPER: Converts letters to uppercase. |Corresponds to the Caché SQL %UPPER function.
|$ZU(28, string, 6) | ALPHAUP: Removes leading, trailing, and embedded blanks. Removes all punctuation characters, except commas (,) and question marks (?). Converts letters to uppercase. | Corresponds to the Caché SQL %ALPHAUP function.
|$ZU(28, string, 7) | SQLUPPER: Removes trailing blanks. Converts letters to uppercase. Appends a blank to beginning of string. | Corresponds to the Caché SQL %SQLUPPER function.
|$ZU(28, string, 8) | SQLSTRING: Removes trailing blanks. Appends a blank to beginning of string. |Corresponds to the Caché SQL %SQLSTRING function.
|$ZU(28, string, 9) | STRING: Removes leading, trailing, and embedded blanks. Removes all punctuation characters, except commas (,). Converts letters to uppercase. Appends a blank to beginning of string. |Corresponds to the Caché SQL %STRING function.
|$ZU(28, string, flag, len) | len is the truncation length in characters, specified as an integer. Can be used with flag values of 7, 8 and 9.

|$ZU(29)| set up form feed control

|$ZU(30)

|$ZU(31)| inlogor (for backup)

|$ZU(32)| dirpass

|$ZU(33, lockitem, ownerjob, ownersys)|Removes one item from the Lock Table. Uses class calls for this if actually on a customer system.| API: SYS.Lock.DeleteOneLock()|

|$ZU(34)|Transactions

|$ZU(35)|

|$ZU(36)|Edit volume label

|$ZU(37)|

|$ZU(38)|

|$ZU(39, sys1)| Specifies a search path for percent (%) routines. sys1 corresponds to the namespace where we search (by default="" current namespace) | %SYSTEM.Process.SysRoutinePath()
|$ZU(39, sys1, sys2, sys3)|  If Caché does not find a routine in sys1, it will search for it in sys2. If Caché does not find a routine in sys2, it will search for it in sys3.

|$ZU(40)|Offsets for View command

|$ZU(41)|Symbol Table Management

|$ZU(42)|

|$ZU(43)|

|$ZU(44)|Manipulate path of namespaces

|$ZU(45)|

|$ZU(46)|

|$ZU(47)|

|$ZU(48)|ForceX for VMS

|$ZU(49)|Returns the header information for the manager’s directory. | API: SYS.Database.<various class properties>|
|$ZU(49, dir)| Returns information on the directory dir (if dir="", current directory). |
|$ZU(49, dir, 0)| Returns the database header information as a comma-separated string. This is the default if no flag parameter is specified.
|$ZU(49, dir, 1)| Returns cluster lock information as a comma-separated string. Do not use this flag value when specifying a system file number for dir.
|$ZU(49, dir, 2)| Returns the most recent database file expansion time (in $HOROLOG format). This value is returned as the second item in a comma-separated string.
|$ZU(49, dir, 3)| Returns the directory location as the string sys^dir, where sys is the remote system number (0 if local), and dir is the directory name. This flag value can only be used when specifying a system file number (sfn) for dir.


|$ZU(50)| dpolabel for backup

|$ZU(51)|Returns value of WDSTOP (wait for quiescence) |
|$ZU(51,1)|Start the Write Daemon if necessary|

|$ZU(52)|database restore

|$ZU(53)|TCP Device name assigned by parent process| API: %SYSTEM.INetInfo.<TCPName()/TPStats()>
|$ZU(53,2)| Returns the number of bytes that have been read from the current TCP device.
|$ZU(53,3)| Returns the number of bytes that have been read from the current TCP device and clears the counter.
|$ZU(53,4)| Returns the number of bytes that have been written to the current TCP device.
|$ZU(53,5)| returns the number of bytes that have been written to the current TCP device and clears the counter.

|$ZU(54,0)|Network db lookups (See $ZU(110)).|

|$ZU(55, n)| Returns or changes the current language mode | %SYSTEM.Process.LanguageMode()
|$ZU(55, 0)| Sets language mode to Caché and return the value for the previous state of the switch. Caché is the default mode for the switch.
|$ZU(55, 1)| Sets language mode to DSM-11 and return the value for the previous state of the switch.
|$ZU(55, 2)| Sets language mode to Open M [DTM] and return the previous state of the switch.
|$ZU(55, 5)| Sets language mode to DSM for OpenVMS an return the value for the previous state of the switch.
|$ZU(55, 6)| Sets language mode to DSM-J (Japanese) for OpenVMS and return the value for the previous stateof the switch.
|$ZU(55, 7)| Sets language mode to DTM-J (Japanese) for OpenVMS and return the value for the previous stateof the switch.
|$ZU(55, 8)| Sets language mode to MSM and return the value for the previous state of the switch. MSM modechanges the use of the $ZC ($ZCHILD) special variable.

|$ZU(56, 2)| Locates source file and line of code for last Caché ObjectScript error. 

|$ZU(56,0)|Returns C module name that generated last Caché error.
|$ZU(56,1)|Returns C line number that generated last Caché error.
|$ZU(56,2)|Returns C mod name & line # that generated last Caché error. | API: %SYSTEM.Process.ErrorLine()
|$ZU(56,3)|Returns the error that caused the last job not to start.
|$ZU(56,4)|Returns offset into routine buffer of current object code pointer.
|$ZU(56,5)|Extended error information associated with the most recent error for which such information is maintained in perritem.
|$ZU(56,6)|Returns any OS error message associated with the COS error code, in the format "code text"|%SYSTEM.Process.OSError()

|$ZU(57) | devigclr (Management function for routine interlock devices).

|$ZU(58) |

|$ZU(59) | Clusters Support

|$ZU(60) | Manipulates priorities

|$ZU(61) | Reads/Writes process parameters

|$ZU(62, 1) | This function can be used for general ObjectScript syntax checking, including XECUTE and $XECUTE command line arguments that do not use parameter passing. | %Library.Routine.CheckSyntax()
|$ZU(62, 2) | This function can be used for checking XECUTE and $XECUTE command line arguments that use parameter passing. It recognizes a formal parameter list at the beginning of the code string. $ZUTIL(62,2) also correctly performs syntax checking on a code string that does not include a formal parameter list.
|$ZU(62,n,code)| code: A string expression specifying a line of Caché ObjectScript code.

|$ZU(63) | Table of remote hosts

|$ZU(64) | Table of incoming DDP volset  mappings

|$ZU(65) | Cluster blocks and preallocated blocks.

|$ZU(66) | Creates daemon jobs

|$ZU(67,pid)|returns the job number of process "pid" if it is alive, else 0
|$ZU(67,0,pid)|returns 2 if pid is active, 0 if not there, 1 if job is dead but pidtab is still in pidtab.
|$ZU(67,1,pid)|same as $ZU(67,0,pid) except it will clean up the pidtab if job is dead.
|$ZU(67,15,$J)|IP Address of current job
|$ZU(67,32,pid)|Return %SS name of pid|%SYS.ProcessQuery.Open() and .%OpenID() can also be used to check the state of a process.You can Open a %SYS.ProcessQuery object by job number or process ID, then look at the JobNumber or Pid propertyAlso, see the ClientIPAddress and StartupClientIPAddress properties of that class|

|$ZU(68,x)|set config options for current process
|$ZU(68,11)|set Read Line Recall (arrow keys in terminal)
|$ZU(69,x)|set config options system-wide
|$ZU(70)|Subscript encoding
|$ZU(71,date)|set $H >w $ZU(71,$H+2) would make $H always think it is the day-after-tomorrow 
|$ZU(71,0)|set $H to default
|$ZU(72)| Internal Debug Features
|$ZU(73)| $List form of global reference
|$ZU(77)| initiate cluster recovery
|$ZU(78)|Journaling utilities
|$ZU(78,3)|returns current journal file
|$ZU(78,22)|returns whether journalling is enabled|API: %SYS.Journal.System.GetCurrentFileName() and .IsDisabled()
|$ZU(78,21)|Oldest TSTART
|$ZU(79) | WIJ reconfiguration
|$ZU(82) | I/O NLS and Glue Code support
|$ZU(83) | download NLS tables
|$ZU(84) | PERFMON support
|$ZU(85) | set/get default mnemonicspace
|$ZU(86) | Return config file pathname/config name, or set new config info
|$ZU(87) | Internal DCP support
|$ZU(88) | JOBEXAM/Debug support
|$ZU(88,2,j,n)|get value of local variable n for job j
|$ZU(89) |  OLD LOCKTAB support
|$ZU(90) | Namespace support. 
|$ZU(91) | user device table
|$ZU(93) | GIF/GOF support
|$ZU(94) | Broadcast message to process
|$ZU(94,pid,message)|sends message to process "pid".  Similar to $ZU(9)
|$ZU(95)|Cluster-wide switch set
|$ZU(96)|Glue Code support
|$ZU(97)|Legacy IJC device support
|$ZU(98)|gcompact
|$ZU(99)|date conversions
|$ZU(100)|Returns current Windows version
|$ZU(101)|Check license for validity
|$ZU(102)|set pcommport
|$ZU(105)|internal DTM socket stuff
|$ZU(106)|internal DTM memory stuff
|$ZU(107)|internal DTM packet stuff
|$ZU(108)|GetLogicalDrives
|$ZU(109)|TTYFREE support
|$ZU(110)|returns computer name You can also get the computer name from the $SYSTEM string - "write $SYSTEM" returns MachineName:InstanceName
|$ZU(111)|get tcp/ip client address
|$ZU(112,0)|returns 1 if this process has a license, else 0
|$ZU(112,3)|Returns # of license units available on this system.
|$ZU(112,4)|Returns authorized license units in working memory
|$ZU(112,15,0)|Maximum license units.
|$ZU(112,15,1)|Currently available license units.|API:$system.License.LUAvailable()
|$ZU(112,15,2)|Minumum available license units.|API:$system.License.LUMinAvailable()
|$ZU(112,15,3)|$system.License.SetUserLimit maximum.
|$ZU(112,15,10)|Maximum CSP active session count.
|$ZU(112,15,11)|Current CSP active session count.
|$ZU(112,15,20)|Maximum CSP grace period session count.
|$ZU(112,15,21)|Current CSP grace period session count.
|$ZU(112,15,30)|Maximum Non-CSP session count.
|$ZU(112,15,31)|Current Non-CSP session count.
|$ZU(112,19)|Return 1 if clustered, 0 otherwise.
|$ZU(114) | Returns Ethernet address
|$ZU(115) | pZUints
|$ZU(116) | revalidation
|$ZU(117) | ZOMSPACK
|$ZU(118) | reverse ZOMSPACK
|$ZU(119) | charwin support
|$ZU(120) | To set/get terminal capabilities
|$ZU(121) | set proc params (never used)
|$ZU(122) | localization support
|$ZU(123) | sliding window date support
|$ZU(124) | obsolete encode/decode
|$ZU(125) | FULLNLS support
|$ZU(126) | Load objects into shared memory
|$ZU(127) | lookup table setup
|$ZU(128) | Debugger/Trace support
|$ZU(129) | internal netnode support
|$ZU(130) | netwide domainspace
|$ZU(131) | Set/Return system identifiers
|$ZU(132) | Make last device principal device
|$ZU(132)|Make the current device the $principal device. 1 = success, else 0
|$ZU(133) | Maintain metric counters 
|$ZU(134) | NETCLOBBER
|$ZU(135) | class compiler support
|$ZU(136,21)|return current lowtimeprecision flag.
|$ZU(136,21,0)|switch to low time precision for $ZH and $ZU(188). It clears lowtimeprecision.   Return original lowtimeprecision value.
|$ZU(136,21,1)|switch to high time precision for $ZH  and $ZU(188). It sets lowtimeprecision.  Return original lowtimeprecision value.
|$ZU(139)|suspend transaction
|$ZU(140)|VMS file/directory utilities
|$ZU(141)|number of actual params
|$ZU(141)|return the number of actual parameters specified in the most recent entry to a function or subroutine.  Be careful!!  $ZU(141) is not for customer use. You must evaluate $ZU(141) at the beginning of the routine before any other functions are called if you want to argument count of the current routine.
|$ZU(142) | Check for valid literals
|$ZU(143) | Send suspend/resume to job
|$ZU(144) | quote string, add double quotes
|$ZU(145) | execute a string in remote job
|$ZU(146) | internal db locking support
|$ZU(147) | file name quoting
|$ZU(148) | VMS internal tape support
|$ZU(149) | Windows up/down checking
|$ZU(150) | DebugBreak (cause core dump)
|$ZU(151) | ODBC data packing
|$ZU(152) | ODBC data packing
|$ZU(153) | Compact Unicode Encode
|$ZU(154) | invalidate global vectors
|$ZU(155) | SuperToken compiler
|$ZU(156) | internal new lock support
|$ZU(157) | comm. Ports
|$ZU(158) | internal printer wizard support
|$ZU(158,0)|On Windows, returns the number of printers defined on the system.  On other OS's this is a <<FUNCTION>> error.
|$ZU(158,1,{#})|On Windows, returns the name of printer {#} as it needsto be referenced within Cache. On other OS's this is a <<FUNCTION>> error. Notes:       * f Idx=1:1:$ZU(158,0) w Idx,") ",$ZU(158,1,Idx),! will list all printers. * %Library.Device.InstalledPrinters() is the class wrapper and makes this functionality available to customers.
|$ZU(159) | obsolete printer wizard login support
|$ZU(160) | save/restore job state
|$ZU(161) | fastcloseobj
|$ZU(162) | seizespin stuff
|$ZU(163) | $ZS stuff
|$ZU(163,n)|Change the value of $zs/$zstorage to n. $zs = max amount of job memory
|$ZU(164) | rem_all_oid
|$ZU(165,1,range)|Returns a random number from 1-range.  
|$ZU(165,0)|Returns the last random number generated
|$ZU(165,0,val)|sets seed value see also: $random, $system.Encryption.GenCryptRand()
|$ZU(166) | TCP B mode for Weblink et al
|$ZU(167) | used by REPAIR to analyze nodes
|$ZU(168)|Returns current working directory
|$ZU(168,"newdir")|Changes working directory to newdir
|$ZU(169) | returns info for a debugger
|$ZU(170) | crypt support
|$ZU(171,1)|returns CPU time (in milliseconds) on any OS, as a string in format SYS_time,USER_time
|$ZU(171,1,pid)|returns total CPU time (system + user) for process pid.
|$ZU(172,0)|Superserver port
|$ZU(173,sfn)|Designates sfn as "cachetemp" database for this system
|$ZU(178,ns,global,collation,protection,journaling,keep,pointer block, growth block)|Create a global with no data in the specified namespace with no data but with the specified characteristics. All parameters but ns and glo are optional. A value of -1 means use the defaults.|API: %Library.GlobalEdit.Create()
|$ZU(179) | audit setup
|$ZU(180) | Run prefetch background job
|$ZU(181)|Returns current maxpid
|$ZU(181,num)|Expand pidtab by num slots
|$ZU(182,0)| return wdsuspd
|$ZU(182,1)| return gbackupreq
|$ZU(182,1,0)| Free a suspended Write Daemon
|$ZU(182,1,n)| set gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to 0 and gbackupmaxtime to 0     
|$ZU(182,1,n,m)|set gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to <m> and gbackupmaxtime to 0 gwdmaxsusptime is only changed when n>0
|$ZU(182,1,n,m,t)| set gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to <m> and gbackupmaxtime to <t>   
|$ZU(182,2,i)| return gbackupsfn[i] (i>=0)
|$ZU(182,2,i,n)| set gbackupsfn[i] (i>=0) to sfn n
|$ZU(182,3[,0/1])| get[,clear/set] bckjob to pjobnum.clear/set: return 1 on success or <=0
|$ZU(182) | wdsusp and gbackupreq
|$ZU(183) | ECPWork daemon
|$ZU(184) | Change ECP State
|$ZU(185) | compare/swap global node
|$ZU(186) | set process prompt
|$ZU(186,func1,func2,...)|build a terminal prompt by concatenating the n elements. values of func(n) are:1 - Host Name - $ZU(110)             2 - NameSpace name - $ZU(86)3 - Config name4 - Current time5 - pid6 - Username7 - Time executing last command (in seconds.milliseconds)
|$ZU(187) | removed, never used
|$ZU(188)|Returns $h with milliseconds|see also: $now
|$ZU(189)|Peek and see if TCP socket is disconnected
|$ZU(190)|SNMP support
|$ZU(193)|Convert UTC date/time to local date/time
|$ZU(194,1)|return 1 if emergency startup, otherwise 0.
|$ZU(194,1,uname,pwd)|1 if uname,pwd good, otherwise 0.
|$ZU(194,2)|return comma-sep list uid,gid,ownerid.
|$ZU(194,3,uname,pwd)|Set username/pw into emergency space.
|$ZU(194,4)|return 1 if private routine on stack
|$ZU(200) | Obsolete License support
|$ZU(201) | 5.0 License Support
