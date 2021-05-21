# zutil-unofficial-documentation
An unofficial documentation of $zu and $zutil function in IRIS/Ensemble/Caché

## Link to the official documentation

https://docs.intersystems.com/priordocexcerpts/rzut.pdf

## Official replacement

https://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=RCOS_replacements

## Table of commands


|Command|Description|Commentaire|
|----|----|----|
|$ZU(0)|  create CACHÉ.DAT
|$ZU(1)|  modify CACHÉ.DAT
|$ZU(2)|  delete CACHÉ.DAT
|$ZU(3)|  dismount CACHÉ.DAT
|$zu(4)|(4,pid) Terminate a process (^RESJOB)|API: SYS.Process.Terminate()|
|$zu(5)|Print current namespace||
|$zu(5, "namespace")|Switch to namespace|Can also be done with write $namespace or set $namespace="namespace"|
|$ZU(7)|Flush a block from buffer pool
|$ZU(8)|Manipulate DLM locks
|$zu(6)|Dead process clean up|
|$zu(9,device,message)|Print message to cconsole log (device = "" is the default device)|API for this: %SYS.System.WriteToConsoleLog()|
|$ZU(10)|Start network daemon
|$zu(12)|Print the full path of the mgr directory|
|$zu(12,dir,2)|Validate and check that dir exists. A null string return means not a valid directory.|API: %Library.File.ManagerDirectory and %Library.File.DirectoryExists()|
|$ZU(13) | old netalloc
|$ZU(14) | Job server
|$ZU(15) | Translate RMS filename to canonical form
|$ZU(16) | Returns device names of specified type
|$ZU(17) | mount database
|$ZU(18) | Set undefined variable handling
|$ZU(19) | duplicate of $ZU(18) – remove?
|$ZU(20) | Specify ns to contain routines
|$ZU(22) | Form feed/Backspace control sequence in this job.
|$ZU(23) | collation
|$ZU(27) | Create a database
|$ZU(29) | set up form feed control
|$ZU(31) | inlogor (for backup)
|$ZU(32) | dirpass
|$zu(33,lockitem,ownerjob,ownersys)|removes one item from the Lock Table. Use class calls for this if actually on a customer system.|API: SYS.Lock.DeleteOneLock()|
|$ZU(34)|Transactions
|$ZU(36)|Edit volume label
|$ZU(37)|
|$ZU(39)|Search path for % routines
|$ZU(40)|offsets for View command
|$ZU(41)|Symbol Table Management
|$ZU(42)|
|$ZU(43)|
|$ZU(44)|Manipulate path of namespaces
|$ZU(45)|
|$ZU(46)|
|$ZU(48)|ForceX for VMS
|$zu(49)|sfn info of mgr directory||
|$zu(49,"")|sfn info of current directory|
|$zu(49,"dir")|sfn info of database located in directory dir|
|$zu(49,"dir",0)|complete sfn info of db in dir|
|$ZU(50)|dpolabel for backup
|$zu(51)|Returns value of WDSTOP|
|$zu(51,1)|Start the Write Daemon if necessary|
|$ZU(52)|database restore
|$zu(53)|TCP Device name assigned by parent process|
|$zu(53,#)|Various TCP information|
|$zu(54,0)|See $zu(110)|
|$ZU(56)|Source file, code line of last COS error
|$zu(56,0)|return C module name that generated last Cache' error
|$zu(56,1)|return C line number that generated last Cache' error
|$zu(56,2)|return C mod name & line # that generated last Cache' err
|$zu(56,3)|return the error that caused the last job not to start
|$zu(56,4)|returns offset into routine buffer of current object code pointer
|$zu(56,5)|extended error information associatedwith the most recent error for which such information is maintained in perritem.
|$zu(56,6)|returns any OS error message associated with the COS error code, in the format "code text"
|$ZU(57) | devigclr (Management function for routine interlock devices).
|$ZU(59) | Clusters Support
|$ZU(60) | Manipulate priorities
|$ZU(61) | read/write process parms
|$ZU(62) | Syntax checker
|$ZU(63) | table of remote hosts
|$ZU(64) | table of incoming DDP volset  mappings
|$ZU(65) | cluster blocks and preallocated blocks.
|$ZU(66) | Create daemon jobs
|$zu(67,pid)|returns the job number of process "pid" if it is alive, else 0
|$ZU(67,0,pid)|returns 2 if pid is active, 0 if not there, 1 if job is dead but pidtab is still in pidtab.
|$ZU(67,1,pid)|same as $zu(67,0,pid) except it will clean up the pidtab if job is dead.
|$zu(67,15,$J)|IP Address of current job
|$zu(67,32,pid)|Return %SS name of pid|%SYS.ProcessQuery.Open() and .%OpenID() can also be used to check the state of a process.You can Open a %SYS.ProcessQuery object by job number or process ID, then look at the JobNumber or Pid propertyAlso, see the ClientIPAddress and StartupClientIPAddress properties of that class|
|$zu(68,x)|set config options for current process
|$zu(68,11)|set Read Line Recall (arrow keys in terminal)
|$zu(69,x)|set config options system-wide
|$ZU(70)|Subscript encoding
|$zu(71,date)|set $H >w $ZU(71,$H+2) would make $H always think it is the day-after-tomorrow 
|$zu(71,0)|set $H to default
|$ZU(72)| Internal Debug Features
|$ZU(73)| $List form of global reference
|$ZU(77)| initiate cluster recovery
|$ZU(78)|Journaling utilities
|$zu(78,3)|returns current journal file
|$zu(78,22)|returns whether journalling is enabled|API: %SYS.Journal.System.GetCurrentFileName() and .IsDisabled()
|$zu(78,21)|Oldest TSTART
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
|$ZU(94,pid,message)|sends message to process "pid".  Similar to $zu(9)
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
|$zu(112,0)|returns 1 if this process has a license, else 0
|$zu(112,3)|Returns # of license units available on this system.
|$zu(112,4)|Returns authorized license units in working memory
|$zu(112,15,0)|Maximum license units.
|$zu(112,15,1)|Currently available license units.|API:$system.License.LUAvailable()
|$zu(112,15,2)|Minumum available license units.|API:$system.License.LUMinAvailable()
|$zu(112,15,3)|$system.License.SetUserLimit maximum.
|$zu(112,15,10)|Maximum CSP active session count.
|$zu(112,15,11)|Current CSP active session count.
|$zu(112,15,20)|Maximum CSP grace period session count.
|$zu(112,15,21)|Current CSP grace period session count.
|$zu(112,15,30)|Maximum Non-CSP session count.
|$zu(112,15,31)|Current Non-CSP session count.
|$zu(112,19)|Return 1 if clustered, 0 otherwise.
|$ZU(114) | Returns Ethernet address
|$ZU(115) | pzuints
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
|$zu(132)|Make the current device the $principal device. 1 = success, else 0
|$ZU(133) | Maintain metric counters 
|$ZU(134) | NETCLOBBER
|$ZU(135) | class compiler support
|$zu(136,21)|return current lowtimeprecision flag.
|$zu(136,21,0)|switch to low time precision for $ZH and $zu(188). It clears lowtimeprecision.   Return original lowtimeprecision value.
|$zu(136,21,1)|switch to high time precision for $ZH  and $zu(188). It sets lowtimeprecision.  Return original lowtimeprecision value.
|$ZU(139)|suspend transaction
|$ZU(140)|VMS file/directory utilities
|$ZU(141)|number of actual params
|$zu(141)|return the number of actual parameters specified in the most recent entry to a function or subroutine.  Be careful!!  $ZU(141) is not for customer use. You must evaluate $ZU(141) at the beginning of the routine before any other functions are called if you want to argument count of the current routine.
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
|$zu(158,0)|On Windows, returns the number of printers defined on the system.  On other OS's this is a <<FUNCTION>> error.
|$zu(158,1,{#})|On Windows, returns the name of printer {#} as it needsto be referenced within Cache. On other OS's this is a <<FUNCTION>> error. Notes:       * f Idx=1:1:$ZU(158,0) w Idx,") ",$ZU(158,1,Idx),! will list all printers. * %Library.Device.InstalledPrinters() is the class wrapper and makes this functionality available to customers.
|$ZU(159) | obsolete printer wizard login support
|$ZU(160) | save/restore job state
|$ZU(161) | fastcloseobj
|$ZU(162) | seizespin stuff
|$ZU(163) | $ZS stuff
|$zu(163,n)|Change the value of $zs/$zstorage to n. $zs = max amount of job memory
|$zu(164) | rem_all_oid
|$zu(165,1,range)|Returns a random number from 1-range.  
|$zu(165,0)|Returns the last random number generated
|$zu(165,0,val)|sets seed value see also: $random, $system.Encryption.GenCryptRand()
|$ZU(166) | TCP B mode for Weblink et al
|$ZU(167) | used by REPAIR to analyze nodes
|$zu(168)|Returns current working directory
|$zu(168,"newdir")|Changes working directory to newdir
|$ZU(169) | returns info for a debugger
|$ZU(170) | crypt support
|$ZU(171,1)|returns CPU time (in milliseconds) on any OS, as a string in format SYS_time,USER_time
|$ZU(171,1,pid)|returns total CPU time (system + user) for process pid.
|$ZU(172,0)|Superserver port
|$zu(173,sfn)|Designates sfn as "cachetemp" database for this system
|$zu(178,ns,global,collation,protection,journaling,keep,pointer block, growth block)|Create a global with no data in the specified namespace with no data but with the specified characteristics. All parameters but ns and glo are optional. A value of -1 means use the defaults.|API: %Library.GlobalEdit.Create()
|$ZU(179) | audit setup
|$ZU(180) | Run prefetch background job
|$zu(181)|Returns current maxpid
|$zu(181,num)|Expand pidtab by num slots
|$zu(182,0)| return wdsuspd
|$zu(182,1)| return gbackupreq
|$zu(182,1,0)| Free a suspended Write Daemon
|$zu(182,1,n)| set gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to 0 and gbackupmaxtime to 0     
|$zu(182,1,n,m)|set gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to <m> and gbackupmaxtime to 0 gwdmaxsusptime is only changed when n>0
|$zu(182,1,n,m,t)| set gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to <m> and gbackupmaxtime to <t>   
|$zu(182,2,i)| return gbackupsfn[i] (i>=0)
|$zu(182,2,i,n)| set gbackupsfn[i] (i>=0) to sfn n
|$zu(182,3[,0/1])| get[,clear/set] bckjob to pjobnum.clear/set: return 1 on success or <=0
|$ZU(182) | wdsusp and gbackupreq
|$ZU(183) | ECPWork daemon
|$ZU(184) | Change ECP State
|$ZU(185) | compare/swap global node
|$ZU(186) | set process prompt
|$ZU(186,func1,func2,...)|build a terminal prompt by concatenating the n elements. values of func(n) are:1 - Host Name - $zu(110)             2 - NameSpace name - $zu(86)3 - Config name4 - Current time5 - pid6 - Username7 - Time executing last command (in seconds.milliseconds)
|$ZU(187) | removed, never used
|$zu(188)|Returns $h with milliseconds|see also: $now
|$zu(189)|Peek and see if TCP socket is disconnected
|$ZU(190)|SNMP support
|$zu(193)|Convert UTC date/time to local date/time
|$zu(194,1)|return 1 if emergency startup, otherwise 0.
|$zu(194,1,uname,pwd)|1 if uname,pwd good, otherwise 0.
|$zu(194,2)|return comma-sep list uid,gid,ownerid.
|$zu(194,3,uname,pwd)|Set username/pw into emergency space.
|$zu(194,4)|return 1 if private routine on stack
|$ZU(200) | Obsolete License support
|$ZU(201) | 5.0 License Support
