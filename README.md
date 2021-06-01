# ZU-unofficial-documentation
An unofficial documentation of $ZU and $ZU function in IRIS/Ensemble/Caché

## Link to the official documentation

https://docs.intersystems.com/priordocexcerpts/rZUt.pdf

## Official replacement

https://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=RCOS_replacements

## Table of commands


| Command | Description | Commentaire | 
| ---- | ---- | ---- | 
| $ZU(0) | create CACHÉ.DAT
| $ZU(1) | modify CACHÉ.DAT
| $ZU(2) | delete CACHÉ.DAT
| $ZU(3) | dismount CACHÉ.DAT
| $ZU(4,pid) | Terminates a process (^RESJOB) | API: %SYSTEM.Process.Terminate() | 
| $ZU(4,pid,flag) | flag = integer, if negative -> process termination operations (-65 when process is a systemdaemon / unresolved transaction state,other). If positive -> exit status code that Caché returns to the host operating system upon termination.
| $ZU(5) | Print current namespace | $NAMESPACE, not exactly replacement, but preferable | 
| $ZU(5,"namespace") | Switch to namespace | $NAMESPACE="namespace" | 
| $ZU(6) | Dead process clean up | 
| $ZU(7) | Flush a block from buffer pool
| $ZU(8) | Manipulate DLM locks
| $ZU(9,device,message) | Print message to cconsole log (device = "" is the default device) | API: %SYS.System.WriteToConsoleLog() or %Library.Device.Broadcast() | 
| $ZU(9,terminal,message,timeout) | timeout: integer specifying the number of secondes to wait before timeout (used with named terminals only) | 
| $ZU(9,device,message,loglevel) | loglevel: numeric code indicating which logging level option to use (used with operator console only) | 
| $ZU(10) | Start network daemon
| $ZU(11) | 
| $ZU(12) | Returns the full path of the mgr directory | 
| $ZU(12,name) | Returns the current namespace pathname | API: %Library.File.ManagerDirectory and %Library.File.DirectoryExists() | 
| $ZU(12,name,canon=0) | Canonicalize name as a filename, does not check if valid | API: %Library.File.NormalizeDirectory() 
| $ZU(12,name,canon=1) | Canonicalize name as a directory name. Returns null if it is not a directory (existing or not) 
| $ZU(12,name,canon=2) | If name refers to an existing directory, canonicalize name and return the full pathname. Otherwise, returns null.
| $ZU(12,name,canon=3) | If name refers to an existing directory or a special device that can contain a Caché database, canonicalize name and return the full pathname. Otherwise, returns null
| $ZU(12,name,canon,case) | The default canonical form returned is entirely in lowercase letters, regardless of the case of name. To preserve uppercase letters on Windows systems, specify a caseflag with a value of 1. 
| $ZU(13) | old netalloc | Removed
| $ZU(14) | Job server | 
| $ZU(15,devname) | Translate RMS filename to canonical form | API: %Library.File.NormalizeFilename()
| $ZU(16) | Returns device names of specified type
| $ZU(17) | Mounts database
| $ZU(18,n) | Sets undefined variable handling for the current process. n is optional (0 by default), changes behavior of Caché when it encounters an undefined variable for local, process-private global, and global variables; it has no effect on special variables. | API: %SYSTEM.Process.Undefined()
| $ZU(18,0) | Issues the <UNDEFINED> error for any undefined variable.
| $ZU(18,1) | Returns a null string for a reference to an undefined variable with subscripts,and issues the<UNDEFINED> error for undefined variables without subscripts.
| $ZU(18,2) | Returns a null string (instead of issuing an <UNDEFINED> error) for any undefined variable.
| $ZU(18,-1) | $ZU(18,2)
| $ZU(19) | Duplicate of $ZU(18) | 
| $ZU(20,new) | Specifies the namespace(s) that contains the routine dataset. | API: %SYSTEM.Process.UserRoutinePath() 
| $ZU(20,new,second,third) | If Caché does notfind a routine in new,Caché looks for the routine in second. If Caché does not find the routine in second,Caché looks for the routine in third,and so on. | Using routines in second is VERY slow!
| $ZU(21,0) | Returns the location of process-private globals. | API: %SYSTEM.Process.PrivateGlobalLocation()
| $ZU(21,1) | Deletes allprocess-private globals. It returns 1 upon successful completion,0 upon error. Returns 1 even iuf no process-private globals defined. | API: %SYSTEM.Process.KillPrivateGlobals()
| $ZU(22,0,ff,bs) | Form feed/Backspace control sequence in this job. ff and bs optional,new form feed control code sequence / new backspace control code sequence. | API: %Library.Device.SetFFBS()
| $ZU(23) | Collation
| $ZU(24) | 
| $ZU(25) | 
| $ZU(26) | 
| $ZU(27) | Create a database
| $ZU(28,string,flag) | Performs collation conversion. It applies the collation type specified in flag to string | API: %SYSTEM.Util.Collation()
| $ZU(28,string,0) | EXACT: Returns string unchanged. Does not convert NULLs. | Corresponds to the Caché SQL%EXACT function.
| $ZU(28,string,1) | SPACE: Appends a blank to beginning of string
| $ZU(28,string,2) | MVR: Returns string unchanged,except for NULLs,which are converted. Provided for MultiValue support. | Corresponds to the Caché SQL %MVR function.
| $ZU(28,string,3) | PLUS: Converts numerics and numeric strings to canonical numbers. A nonnumeric string is returned as 0
| $ZU(28,string,4) | MINUS: Converts numerics and numeric strings to canonical numbers and appends a minus sign. A nonnumeric string is returned as 0.
| $ZU(28,string,5) | UPPER: Converts letters to uppercase. | Corresponds to the Caché SQL %UPPER function.
| $ZU(28,string,6) | ALPHAUP: Removes leading,trailing,and embedded blanks. Removes all punctuation characters,except commas (,) and question marks (?). Converts letters to uppercase. | Corresponds to the Caché SQL %ALPHAUP function.
| $ZU(28,string,7) | SQLUPPER: Removes trailing blanks. Converts letters to uppercase. Appends a blank to beginning of string. | Corresponds to the Caché SQL %SQLUPPER function.
| $ZU(28,string,8) | SQLSTRING: Removes trailing blanks. Appends a blank to beginning of string. | Corresponds to the Caché SQL %SQLSTRING function.
| $ZU(28,string,9) | STRING: Removes leading,trailing,and embedded blanks. Removes all punctuation characters,except commas (,). Converts letters to uppercase. Appends a blank to beginning of string. | Corresponds to the Caché SQL %STRING function.
| $ZU(28,string,flag,len) | len is the truncation length in characters,specified as an integer. Can be used with flag values of 7,8 and 9.
| $ZU(29) | set up form feed control
| $ZU(30)
| $ZU(31) | inlogor (for backup)
| $ZU(32) | dirpass
| $ZU(33,lockitem,ownerjob,ownersys) | Removes one item from the Lock Table. Uses class calls for this if actually on a customer system. | API: SYS.Lock.DeleteOneLock() | 
| $ZU(34) | Transactions
| $ZU(35) | 
| $ZU(36) | Edit volume label
| $ZU(37) | 
| $ZU(38) | 
| $ZU(39,sys1) | Specifies a search path for percent (%) routines. sys1 corresponds to the namespace where we search (by default="" current namespace) | %SYSTEM.Process.SysRoutinePath()
| $ZU(39,sys1,sys2,sys3) | If Caché does not find a routine in sys1,it will search for it in sys2. If Caché does not find a routine in sys2,it will search for it in sys3.
| $ZU(40) | Offsets for View command
| $ZU(41) | Symbol Table Management
| $ZU(42) | 
| $ZU(43) | 
| $ZU(44) | Manipulate path of namespaces
| $ZU(45) | 
| $ZU(46) | 
| $ZU(47) | 
| $ZU(48) | ForceX for VMS
| $ZU(49) | Returns the header information for the manager’s directory. | API: SYS.Database.<various class properties> | 
| $ZU(49,dir) | Returns information on the directory dir (if dir="",current directory). | 
| $ZU(49,dir,0) | Returns the database header information as a comma-separated string. This is the default if no flag parameter is specified.
| $ZU(49,dir,1) | Returns cluster lock information as a comma-separated string. Do not use this flag value when specifying a system file number for dir.
| $ZU(49,dir,2) | Returns the most recent database file expansion time (in $HOROLOG format). This value is returned as the second item in a comma-separated string.
| $ZU(49,dir,3) | Returns the directory location as the string sys^dir,where sys is the remote system number (0 if local),and dir is the directory name. This flag value can only be used when specifying a system file number (sfn) for dir.
| $ZU(50) | dpolabel for backup
| $ZU(51) | Returns value of WDSTOP (wait for quiescence) | 
| $ZU(51,1) | Start the Write Daemon if necessary | 
| $ZU(52) | database restore
| $ZU(53) | TCP Device name assigned by parent process | API: %SYSTEM.INetInfo.<TCPName()/TPStats()>
| $ZU(53,2) | Returns the number of bytes that have been read from the current TCP device.
| $ZU(53,3) | Returns the number of bytes that have been read from the current TCP device and clears the counter.
| $ZU(53,4) | Returns the number of bytes that have been written to the current TCP device.
| $ZU(53,5) | returns the number of bytes that have been written to the current TCP device and clears the counter.
| $ZU(54,0) | Network db lookups (See $ZU(110)). | 
| $ZU(55,n) | Returns or changes the current language mode | %SYSTEM.Process.LanguageMode()
| $ZU(55,0) | Sets language mode to Caché and return the value for the previous state of the switch. Caché is the default mode for the switch.
| $ZU(55,1) | Sets language mode to DSM-11 and return the value for the previous state of the switch.
| $ZU(55,2) | Sets language mode to Open M [DTM] and return the previous state of the switch.
| $ZU(55,5) | Sets language mode to DSM for OpenVMS an return the value for the previous state of the switch.
| $ZU(55,6) | Sets language mode to DSM-J (Japanese) for OpenVMS and return the value for the previous stateof the switch.
| $ZU(55,7) | Sets language mode to DTM-J (Japanese) for OpenVMS and return the value for the previous stateof the switch.
| $ZU(55,8) | Sets language mode to MSM and return the value for the previous state of the switch. MSM modechanges the use of the $ZC ($ZCHILD) special variable.
| $ZU(56,2) | Locates source file and line of code for last Caché ObjectScript error. 
| $ZU(56,0) | Returns C module name that generated last Caché error.
| $ZU(56,1) | Returns C line number that generated last Caché error.
| $ZU(56,2) | Returns C mod name & line # that generated last Caché error. | API: %SYSTEM.Process.ErrorLine()
| $ZU(56,3) | Returns the error that caused the last job not to start.
| $ZU(56,4) | Returns offset into routine buffer of current object code pointer.
| $ZU(56,5) | Extended error information associated with the most recent error for which such information is maintained in perritem.
| $ZU(56,6) | Returns any OS error message associated with the COS error code,in the format "code text" | %SYSTEM.Process.OSError()
| $ZU(57) | devigclr (Management function for routine interlock devices).
| $ZU(58) | 
| $ZU(59) | Clusters Support
| $ZU(60) | Manipulates priorities
| $ZU(61) | Reads/Writes process parameters
| $ZU(62,1) | This function can be used for general ObjectScript syntax checking,including XECUTE and $XECUTE command line arguments that do not use parameter passing. | %Library.Routine.CheckSyntax()
| $ZU(62,2) | This function can be used for checking XECUTE and $XECUTE command line arguments that use parameter passing. It recognizes a formal parameter list at the beginning of the code string. $ZU(62,2) also correctly performs syntax checking on a code string that does not include a formal parameter list.
| $ZU(62,n,code) | code: A string expression specifying a line of Caché ObjectScript code.
| $ZU(63) | Table of remote hosts
| $ZU(64) | Table of incoming DDP volset mappings
| $ZU(65) | Cluster blocks and preallocated blocks.
| $ZU(66) | Creates daemon jobs
| $ZU(67,pid) | Returns the job number of process "pid" if it is alive,else 0
| $ZU(67,0,pid) | Returns 2 if pid is active,0 if not there,1 if job is dead but pidtab is still in pidtab. | API: %SYS.ProcessQuery.IsGhost / %SYSTEM.Process.IsGhost()
| $ZU(67,1,pid) | Same as $ZU(67,0,pid) except it will clean up the pidtab if job is dead. 
| $ZU(67,4) | Returns Process State of a Specified Process | API: %SYS.ProcessQuery.State / %SYSTEM.Process.State()
| $ZU(67,5) | Returns Routine Name of a Specified Process | API: %SYS.ProcessQuery.Routine / %SYSTEM.Process.Routine()
| $ZU(67,6) | Returns Namespace Name of a Specified Process | API: %SYS.ProcessQuery.NameSpace / %SYSTEM.Process.NameSpace()
| $ZU(67,7) | Returns Current Device Name of a Specified Process | API: %SYS.ProcessQuery.CurrentDevice / %SYSTEM.Process.CurrentDevice()
| $ZU(67,8) | Returns Number of Lines Executed for a Specified Process | API: %SYS.ProcessQuery.LinesExecuted / %SYSTEM.Process.LinesExecuted()
| $ZU(67,9) | Returns Number of Global References for a Specified Process | API: %SYS.ProcessQuery.GlobalReferences / %SYSTEM.Process.GlobalReferences()
| $ZU(67,10) | Returns Job Type of a Specified Process | API: %SYS.ProcessQuery.JobType / %SYSTEM.Process.JobType()
| $ZU(67,11) | Returns Username that Invoked a Specified Process | API: %SYS.ProcessQuery.UserName / %SYSTEM.Process.UserName()
| $ZU(67,12) | Returns System Name Running a Client Process | API: %SYS.ProcessQuery.ClientNodeName / %SYSTEM.Process.ClientNodeName()
| $ZU(67,13) | Returns Executable Filename of a Client Process | API: %SYS.ProcessQuery.ClientExecutableName / %SYSTEM.Process.ClientExecutableName()
| $ZU(67,14) | Returns Operating System Running a Client Process | API: %SYS.ProcessQuery.CSPSessionID / %SYSTEM.Process.CSPSessionID()
| $ZU(67,15) | Returns IP Address of a Client Process | API: %SYS.ProcessQuery.ClientIPAddress / %SYSTEM.Process.ClientIPAddress()
| $ZU(67,32,pid) | Returns %SS name of pid | %SYS.ProcessQuery.Open() and .%OpenID() can also be used to check the state of a process. You can Open a %SYS.ProcessQuery object by job number or process ID,then look at the JobNumber or Pid property. Also, see the ClientIPAddress and StartupClientIPAddress properties of that class | 
| $ZU(68,1,n) | Null Subscript Mode Process Switch. n=0, Disables setting/referencing null subscripted globals (the default). n=1, Enables setting/referencing null subscripted globals.
| $ZU(68,2,n) | Default OPEN Mode for Sequential Files. n the boolean value that specifies the process-specific default mode for sequential files on OPEN.
| $ZU(68,3,n) | Automatic Sequential File Creation Mode Process Default. n the boolean value that specifies whether a sequential file is automatically created on OPEN.
| $ZU(68,5,n) | Argumentless BREAK Process Switch. n The boolean value that specifies whether or not argumentless BREAK commands are enabled for the current process.
| $ZU(68,6,n) | Reliable SET Networking Mode Process Switch. n The boolean value that specifies whether or not Reliable SET Networking mode is enabled for the current process.
| $ZU(68,7,n) | External Reference Mode Process Switch. n The boolean value that specifies whether or not extended global references are retained for the current process.
| $ZU(68,11,n) | Read Line Recall Mode Process Switch. n The boolean value that specifies whether read line recall mode is enabled for the current process. 1=enabled. 0=disabled.
| $ZU(68,15,n) | Modem Disconnect Detection. n The boolean value that specifies whether Caché detects I/O disconnection.
| $ZU(68,21,n) | Synchronous Transaction Commit Mode. n A boolean value that specifies whether or not synchronous transaction commit mode is enabled for the current process.
| $ZU(68,22,n) | $X Update Mode for Escape Sequences. n The numeric code that specifies the $X update mode for the current process. This mode should correspond to your computer platform and Intersystems software.
| $ZU(68,25,n) | Dynamically Set or Remove Batch Status. n The boolean value that specifies whether batch or interactive status is active for the current process.
| $ZU(68,26,n) | Default Display of Current Namespace. n The boolean value that specifies whether Caché includes the current namespace name in the terminal prompt for the current process.
| $ZU(68,27,n) | Network Hardening for the Current Process. n The boolean value that specifies whether Caché enables or disables network hardening for the current process.
| $ZU(68,28,n) | Control Root (Unsubscripted) Node Kills. n An integer code value that specifies whether Caché allows the current process to kill root-level (unsubscripted) global nodes. Supported values are 0, 1, and 2.
| $ZU(68,30,n) | Error-Handling Behavior (to allow use of DSM language-mode error-handling). n The boolean value that specifies whether or not a process uses Caché-style error handling. 0 specifies Caché-style behavior. 1 specifies DSM-style behavior. The system default setting is 0.
| $ZU(68,32,n) | Date Range and Invalid Date Behavior. n The boolean value that specifies whether or not a process uses Caché-style date behavior.
| $ZU(68,34,n) | Process Interruptible by Asynchronous Errors. n The boolean value that specifies whether or not the current process should receive asynchronous errors.
| $ZU(68,39,n) | Disable or Enable Caching. n The boolean value that specifies whether or not a process has caching enabled. Note that settings are: 0 = caching enabled. 1 = caching disabled.
| $ZU(68,40,n) | End-of-File Handling for Sequential Files (to support porting of MSMroutines). n The boolean value that sets end-of-file handling for the current process. 0=Caché default format. 1=end-of-file flagging format.
| $ZU(68,42,n) | $JOB Format for Process. n The boolean value that specifies whether or not a process uses the standard $JOB return string.
| $ZU(68,43,n) | Clearing of Global Vectors (when calling $ZU(5).). n The boolean value that specifies whether or not $ZU(5) clears global vectors for the current process.
| $ZU(68,45,n) | Truncate Numbers During String-to-Number Conversion (to supportporting of MSM routines). n The boolean value that specifies whether or not the current process truncates numbers.
| $ZU(68,51,n) | Namespace Default Directory Assignment. n The boolean value that specifies whether or not changing the namespace also changes the default directory for the current process.
| $ZU(68,55,n) | $X/$Y Behavior for TCP Devices. n A boolean value that specifies the behavior for $X and $Y for TCP devices for the current process: 0 = Caché sets $X and $Y to conventional values (terminal emulation). 1 = Caché sets $X and $Y to specialized TCP values used for TCP data transfer output. The default is 0.
| $ZU(68,60,n) | Asynchronous Telnet Disconnect Errors. n A boolean value that specifies whether or not the current process should receive Telnet disconnect errors asynchronously
| $ZU(68,63,n) | Lowercase “e” as a Scientific Notation Exponent Symbol. n The boolean value that specifies whether or not a process should treat lowercase “e” as a scientific notation base-10 exponent symbol. 1 = evaluate “e” as an exponent symbol. 0 = do not evaluate “e” as an exponent symbol. The default is 1.
| $ZU(68,66,n) | Suppress Telnet NUL at End-of-Line32. n The boolean value that specifies whether or not Caché should suppress NUL following a CR atend-of-line. 1 = suppress NUL. 0 = do not suppress NUL. The default is 0.
| $ZU(68,67,n) | Stack and Register Usage Message Box Display. n The boolean value that specifies whether or not Caché should display or suppress the Windows stackand register usage box for a cache.exe process when it encounters an exception. 1 = enable display of the message box. 0 = suppress display of the message box. The default is 0.
| $ZU(68,70,n) | $DOUBLE INF and NAN Behavior. n A boolean that specifies whether to generate Caché error messages or return INF, –INF, and NAN values for unresolvable IEEE floating point conversions.
| $ZU(68,71,n) | Sets IP address format for the current process. n A boolean value to set IP address format. 0=IPv6 format disabled (IPv4 only). 1=IPv6 format enabled (both IPv4 and IPv6 supported).
| $ZU(68,72,n) | Sets MVBasic handling of undefined variables. n The boolean value that specifies whether or not Caché should issue an error when the current MVBasic routine references an undefined variable. 1 = substitute the empty string for an undefined variable. 0 = issue an <UNDEFINED> error for an undefined variable. The default is 0.
| $ZU(69,0,n) | Default $ZU(18) Values. n A numeric code specifying how to handle undefined variables system-wide. Permitted values are 0, 1, and 2.
| $ZU(69,1,n) | Null Subscript Mode System Default. n The boolean value that specifies whether or not to enable the setting and referencing of null subscripted globals.
| $ZU(69,2,n) | Default Mode for Sequential Files. n The boolean value that specifies the system-wide default mode for sequential files on OPEN. The options are: 0=Read-only, 1=Read/Write
| $ZU(69,3,n) | Automatic File Creation Mode SystemDefault. n A boolean value that specifies whether or not an OPEN command should create a new sequential file if the specified sequential file does not exist.
| $ZU(69,5,n) | Argumentless BREAK System Default. n The switch that determines the system-wide default behavior of argumentless BREAK: 0 = Caché treats an argumentless BREAK as a no-op. 1 = Caché executes BREAK on argumentless BREAK (the default).
| $ZU(69,6,n) | Reliable SET Networking Mode SystemDefault. n The boolean value that specifies whether or not Reliable SET Networking mode is enabled system-wide.
| $ZU(69,7,n) | Reference-in-Kind Mode System Default. n The boolean switch to set the default for handling extended global references system-wide.
| $ZU(69,8,n) | ZA and ZD Modes. n The boolean value to set the system-wide default locking behavior when ZA and ZD are called.
| $ZU(69,10,n) | Freeze System if Journal Full SystemDefault. n The boolean value that specifies which system behavior applies when a journal is full.
| $ZU(69,11,n) | Read Line Recall Mode System Default. n The boolean value to enable or disable Read Line Recall mode system-wide.
| $ZU(69,13,n) | Asynchronous SET/KILL Errors to mneterr.log File. n The boolean value that specifies whether to log asynchronous SET/KILL errors in MNETERR.LOG.
| $ZU(69,14,n) | Asynchronous SET/KILL Errors to Operator Console. n The boolean value that specifies whether to send asynchronous SET/KILL errors to the operator console.
| $ZU(69,15,n) | Modem Disconnect Detection SystemDefault. n The boolean value that specifies whether Caché detects I/O device disconnection.
| $ZU(69,19,n) | DDP Password Security. n A boolean value that specifies whether to enable or disable password protection for DDP connections.
| $ZU(69,20,n) | Transfer Nodes with Null Subscripts withDSM-DDPYe. n The boolean value that specifies whether the network allows null subscripts.
| $ZU(69,21,n) | Synchronous Transaction Commit Mode. n A boolean value that specifies whether or not synchronous transaction commit mode is enabled system-wide.
| $ZU(69,22,n) | $X Update Mode for Escape Sequences. n A numeric code that specifies the $X update mode. Select the value that corresponds to your systemplatform.
| $ZU(69,24,n) | $ZF Process Deletion by STOP/ ID(OpenVMS)Ye. n The switch that controls whether Caché can delete a process that is executing a user-written $ZF function. 0 = Enable deletion of Caché processes with STOP/ID. 1 = Disable deletion of Caché processes with STOP/ID.
| $ZU(69,26,n) | System Namespace Display Defaul. n The boolean value that specifies whether to display the namespace name at the terminal prompt.
| $ZU(69,27,n) | Network Hardening. n The boolean value that specifies whether to enable network hardening system-wide.
| $ZU(69,28,n) | Control Root (Unsubscripted) Node Kills. n An integer code value that specifies whether Caché allows the processes to kill root-level global nodes system-wide. Supported values are 0, 1, and 2.
| $ZU(69,30,n) | Error Handling Behavior. n The boolean value that specifies the system-wide default mode for error handling behavior.
| $ZU(69,31,n) | Network Locks Handling Following a DCPOutage. n A boolean value that specifies whether or not to reinstate network locks when the network returns after a DCP outage.
| $ZU(69,32,n) | Date Range and Invalid Date Behavior. n The boolean value that specifies whether or not to use Caché-style date behavior system-wide.
| $ZU(69,34,n) | Processes Interruptible by AsynchronousError. n The boolean value that specifies whether or not processes should be interrupted by receiving asynchronous errors system-wide.
| $ZU(69,35,n) | Silent Retry for domainspace ConnectionAttemptsYe. n A boolean value that specifies whether or not to perform a silent retry for domainspace connection attempts.
| $ZU(69,37,n) | Physical Cursor Positioning Mode. n A boolean value that specifies whether or not physical cursor positioning mode is enabled system-wide.
| $ZU(69,39,n) | Caching for Future Processes. n The boolean value that specifies whether or not a process has caching enabled. Note that settings are: 0 = caching enabled. 1 = caching disabled.
| $ZU(69,40,n) | End-of-File Handling for Sequential File. n The boolean value that sets end-of-file handling system-wide. 0=Caché format. 1=end-of-file flagging format.
| $ZU(69,42,n) | $JOB Format System Default. n The boolean value that specifies whether or not to use the standard $JOB return string system-wide.
| $ZU(69,43,n) | Clearing of Global VectorsYe. n The boolean value that specifies whether or not
| $ZU(5) clears | global vectors for the current process.
| $ZU(69,44,n) | Nagle Algorithm for Telnet Transmissions. n A boolean value that specifies whether or not the Nagle algorithm is enabled.
| $ZU(69,45,n) | Truncate Numbers During String-to-Number Conversion. n The boolean value that specifies whether or not to truncate numbers system-wide.
| $ZU(69,49,n) | Logging of Transaction Rollb. n A boolean value that specifies whether or not to log transaction rollbacks.
| $ZU(69,51,n) | Namespace Default Directory Assignment. n The boolean value that specifies whether or not changing the namespace also changes the default directory.
| $ZU(69,55,n) | $X/$Y Behavior for TCP Devices. n A boolean value that specifies the system-wide default behavior for $X and $Y for TCP devices: 0 = Caché sets $X and $Y to conventional device values (terminal emulation). 1 = Caché sets $X and $Y to specialized TCP values used for TCP data transfer output. The default is 0.
| $ZU(69,60,n) | Asynchronous Telnet Disconnect Errors. n A boolean value that specifies whether or not processes receive Telnet disconnect errors asynchronously.
| $ZU(69,63,n) | Lowercase “e” as Scientific NotationSymbol. n The boolean value that specifies whether or not Caché should treat lowercase “e” as a scientific notation base-10 exponent symbol. 1 = evaluate “e” as an exponent symbol. 0 = do not evaluate “e” as an exponent symbol. The default is 1.
| $ZU(69,66,n) | Suppress Telnet NUL at End-of-Line. n The boolean value that specifies whether or not Caché should suppress NUL following a CR at end-of-line. 1 = suppress NUL. 0 = do not suppress NUL.The default is 0.
| $ZU(69,67,n) | Stack and Register Usage Message BoxDisplay. n The boolean value that specifies whether or not Caché should display or suppress the Windows stack and register usage box for a cache.exe process when it encounters an exception. 1 = enable display of the message box. 0 = suppress display of the message box. The default is 0.
| $ZU(69,68,n) | Encryption of Journal Files. n The boolean value that specifies whether or not Caché should establish encryption for future journal files. 1 = encrypt journal files. 0 = do not encrypt journal files. The default is 0.
| $ZU(69,69,n) | Long String Support. n The boolean value that specifies whether or not Caché should allocate stack space to support strings over 32K characters in length. 1 = allocate long string stack space. 0 = do not allocate long string stack space. The default is 0.
| $ZU(69,70,n) | $DOUBLE INF and NAN Behavior. n A boolean that specifies whether to generate Caché error messages or return INF, –INF, and NAN values for unresolvable IEEE floating point conversions.
| $ZU(69,71) | Sets IP address format system-wide. n A boolean value to set IP address format system-wide. 0=IPv6 format disabled (IPv4 only). 1=IPv6 format enabled (both IPv4 and IPv6 supported).
| $ZU(69,72) | Sets MVBasic handling of undefined variables system-wide. n The boolean value that specifies whether or not Caché should issue an error when an MVBasic routine references an undefined variable. 1 = substitute the empty string for an undefined variable. 0 = issue an <UNDEFINED> error for an undefined variable. The default is 0.
| $ZU(70) | Subscript encoding
| $ZU(71,date) | Sets date to a fixed value for the current process. $HOROLOG format. | API: %SYSTEM.Process.FixedDate()
| $ZU(71,0) | Sets date to default.
| $ZU(72) | Internal Debug Features.
| $ZU(73) | $List form of global reference.
| $ZU(77) | Initiates cluster recovery.
| $ZU(78) | Journaling utilities
| $ZU(78,3) | Returns current journal file
| $ZU(78,21) | Searches journal file for open transactions | API: %SYS.Journal.System.GetImageJournalInfo()
| $ZU(78,22,filename,key) | Returns journaling information. filename (optional) The full pathname of a journal file, specified as a quoted string. The default is the current active journal. key (optional) A numeric code for the type of journal information to return. | API: %SYS.Journal.System.GetCurrentFileName() / .IsDisabled()
| $ZU(78,23,filename) | Deletes a journal file. | %SYS.Journal.PurgeOne()
| $ZU(78,28) | Returns journal directory block information.
| $ZU(78,28) | Flushes journal buffer. | API: %SYS.Journal.System.Sync() 
| $ZU(79) | WIJ reconfiguration
| $ZU(80) | 
| $ZU(81) | 
| $ZU(82, 12, n) | Redirects I/O operations. n The boolean value that specifies whether or not to perform I/O redirection. | API: %Library.Device.ReDirectIO()
| $ZU(83) | Download NLS tables
| $ZU(84) | PERFMON support
| $ZU(85) | Sets/gets default mnemonicspace
| $ZU(86) | Returns configuration file pathname and config name | API: %SYS.System.GetCPFFileName()
| $ZU(87) | Internal DCP support
| $ZU(88) | JOBEXAM/Debug support
| $ZU(88,2,j,n) | Gets value of local variable n for job j
| $ZU(89) | OLD LOCKTAB support
| $ZU(90,4,namespace) | Starts up in a specified namespace (UNIX®/OpenVMS). 
| $ZU(90,10,namespace) | Tests whether a namespace is defined. | API: %SYS.Namespace.Exists()
| $ZU(91) | user device table
| $ZU(92) | 
| $ZU(93) | GIF/GOF support
| $ZU(94,pid,message,timeout,noxy) | Broadcasts a message to a specified process. timeout (optional) An integer specifying the number of seconds to wait before timeout. If omitted, no timeout occurs. noxy (optional) A boolean value specifying whether the $X and $Y values are to be modified in the terminal process receiving the message. If 0, $X and $Y are updated. If 1, $X and $Y are not updated.The default is 0. This parameter does not apply to OpenVMS systems, which do not update $X and $Y following a broadcast message. | API: %SYSTEM.Process.Broadcast()
| $ZU(95) | Cluster-wide switch set
| $ZU(96) | Returns or sets Caché information
| $ZU(96,3,n) | Return error number for user-defined command. n A user-defined error number to return, specified as an expression that resolves to a positive integer. | API: %SYSTEM.Process.ThrowError()
| $ZU(96,4,n) | Sets $TEST to Reflect Redirection Operations. n The boolean value used to set the $TEST special variable upon return from I/O redirection code. 0 = Clears $TEST (sets to 0) on return from the redirected READ. 1 = Sets $TEST (sets to 1) on return from the redirected READ. | API: %SYSTEM.Process.IODollarTest()
| $ZU(96,5,string) | Sets $DEVICE | API: <special variable>.$DEVICE
| $ZU(96,9) | Returns the Calling Routine Name | API: %SYSTEM.Process.CallingRoutine()
| $ZU(96,10) | Returns the Calling Routine Namespace |  API: %SYSTEM.Process.CallingDatabase()
| $ZU(96,14) | Returns the Current Device Type. | API: %Library.Device.GetType()
| $ZU(97) | Legacy IJC device support
| $ZU(98) | Gcompact
| $ZU(99) | Date conversions
| $ZU(100) | Returns current Windows version
| $ZU(101) | Checks license for validity
| $ZU(102) | Sets pcommport
| $ZU(103) | 
| $ZU(104) | 
| $ZU(105) | Internal DTM socket stuff
| $ZU(106) | Internal DTM memory stuff
| $ZU(107) | Internal DTM packet stuff
| $ZU(108) | GetLogicalDrives
| $ZU(109) | TTYFREE support
| $ZU(110) | Returns the name of the system that is running. | API: %SYS.System.GetNodeName()
| $ZU(111) | Gets tcp/ip client address
| $ZU(112,0) | Returns 1 if this process has a license,else 0
| $ZU(112,3) | Returns the number of license units available on this system.
| $ZU(112,4) | Returns authorized license units in working memory
| $ZU(112,15,0) | Maximum license units.
| $ZU(112,15,1) | Currently available license units. | API:$system.License.LUAvailable()
| $ZU(112,15,2) | Minumum available license units. | API:$system.License.LUMinAvailable()
| $ZU(112,15,3) | $system.License.SetUserLimit maximum.
| $ZU(112,15,10) | Maximum CSP active session count.
| $ZU(112,15,11) | Current CSP active session count.
| $ZU(112,15,20) | Maximum CSP grace period session count.
| $ZU(112,15,21) | Current CSP grace period session count.
| $ZU(112,15,30) | Maximum Non-CSP session count.
| $ZU(112,15,31) | Current Non-CSP session count.
| $ZU(112,19) | Returns 1 if clustered,0 otherwise.
| $ZU(113) | 
| $ZU(114,0) | Returns the address of the primary ethernet device. This primary ethernet device is the first ethernet device found on the device names list with a valid ethernet address. Any ethernet device can be designated the primary ethernetdevice. | API: %SYSTEM.INetIngo.EthernetAddress()
| $ZU(114,0,name) | Returns the address of any attached ethernet device specified by name. On OpenVMS systems, this is the physical port address of the ethernet device, not the hardware address.The ethernet address is returned as a string of 12 characters that represent the 48-bit ethernet address. The name is not case sensitive. The maximum length of a device names list is platform-dependent, but the name of anindividual device cannot be more than 15 characters in length. An invalid name value results in a <FUNCTION> error.
| $ZU(114,0) | Returns a null string, rather than an ethernet address, if problems.
| $ZU(114,1) | Returns the current list of attached ethernet device names, delimited by $CHAR(1). The first name in this list is the primary ethernet device.
| $ZU(114,2) | Returns the current list of ethernet device names, delimited by commas.
| $ZU(114,2,name) | Replaces the current ethernet device names list with the list specified in name; it then returns the ethernet device names list prior to the replacement.
| $ZU(115) | pZUints
| $ZU(115,11,flag) | Specifies whether a value can be inserted into an identity column. flag The switch that specifies whether a value may be inserted to an IDENTITY column. Valid values are 1 (can insert a value) and 0 (cannot insert a value). The default is 0. | API: %SYSTEM.SQL.GetIdentityInsert() / SetIdentityInsert()
| $ZU(116) | Revalidation
| $ZU(117) | ZOMSPACK
| $ZU(118) | Reverse ZOMSPACK
| $ZU(119) | Charwin support
| $ZU(120) | Sets/gets terminal capabilities
| $ZU(121) | Sets proc params (never used)
| $ZU(122) | Localization support
| $ZU(123) | Sliding window date support
| $ZU(124) | Obsolete encode/decode
| $ZU(125) | FULLNLS support
| $ZU(126) | Load objects into shared memory
| $ZU(127) | Lookup table setup
| $ZU(128) | Debugger/Trace support
| $ZU(128,1) | Returns location of last single step during debugging. | API: %SYSTEM.Process.StepInfo()
| $ZU(129) | Internal netnode support
| $ZU(130,flag,0,value) | Sets or returns the domain ID or index. flag Specifies which value to set or return. value (optional) The value to set.
| $ZU(131) | Set/Return system identifiers
| $ZU(132) | Makes the last device in use the principal I/O device. | API: %Library.Device.ChangePrincipal()
| $ZU(133) | Maintain metric counters 
| $ZU(134) | NETCLOBBER
| $ZU(135) | Class compiler support
| $ZU(136,21) | Returns current lowtimeprecision flag.
| $ZU(136,21,0) | Switches to low time precision for $ZH and $ZU(188). It clears lowtimeprecision. Returns original lowtimeprecision value.
| $ZU(136,21,1) | Switches to high time precision for $ZH and $ZU(188). It sets lowtimeprecision. Returns original lowtimeprecision value.
| $ZU(137) | 
| $ZU(138) | 
| $ZU(139) | Suspends transaction
| $ZU(140) | VMS file/directory utilities | API: %Library.File.<various class methods> 
| $ZU(140,1,name) | Returns file size in bytes.
| $ZU(140,2,name,timeflag) | Returns modification date/time in $HOROLOG format. Returns -2 if the specified file or directory does not exist. On Windows systems, -2 is also returned if a trailing slash is specified. Using the optional timeflag, you can specify whether to return the modification time value in local timezonetime or Universal time (UTC). Universal time is (for most purposes) equivalent to Greenwich Mean Time (GMT).
| $ZU(140,3,name,timeflag) | Returns creation date/time in $HOROLOG format. Returns -2 if the specified file or directory does not exist. On Windows systems, -2 is also returned if a trailing slash is specified. Using the optional timeflag, you can specify whether to return the creation time value in local timezone time or Universal time (UTC). Universal time is (for most purposes) equivalent to Greenwich Mean Time (GMT).
| $ZU(140,4,name) | Tests whether the named item exists. Returns 0 if the specified pathname exists, for either a fileor a directory. Returns -2 if the specified item does not exist. On Windows systems, a directory can be specified with or without a trailing slash. On Windows systems, returns -123 if a valid filename is followed by a trailing slash.
| $ZU(140,5,name) | Deletes the named file. Can delete a read-only file if user has privileges to modify the directory inwhich the file resides. Returns 0 when successful. Returns -2 if name does not exist. Returns -5 if name is a directory.
| $ZU(140,6,name,newname) | Renames the file specified in name with the name specified in newname. May move the file to a different location, if the host operating system supports it. Returns -2 if name does not exist. Returns -32 if name is a directory.
| $ZU(140,7,name) | Returns file attributes as a bit map. Returns -2 if the specified file does not exist. On Windows systems, a directory can be specified with or without a trailing slash. On Windows systems, returns -123 if a valid filename is followed by a trailing slash. | | API: %Library.File.Attributes() 
| $ZU(140,9,name) | Creates the directory specified in name. Returns 0 when successful, or a negative integer indicating an error. Error return values are supplied by the operating system, and are thus platform dependent. On Windows, returns -183 if the specified directory already exists or could not be created. On UNIX®, returns -17 if the specified directory already exists or could not be created. On OpenVMS, returns a negative integer error code if the specified directory could not be created; returns 0 if the specified directory already exists.
| $ZU(140,10,name) | Deletes the directory specified in name. Returns 0 when successful; returns -2 if the specified directory does not exist.
| $ZU(140,11,source,destination) | Copies a file or directory from source to destination. This operation overwrites any prior contents of destination.$ZUTIL(140,14) is similar, but it does not overwrite destination. The source must exist. If a destination file does not exist, it will be created. If source is a file, destination may be a file or an existing directory. If source is a directory, destination must be an existing directory. In this case, all files in the source directory are copied to the destination directory, but subdirectories in source are not copied. Returns 0 when successful; returns a negative integer upon failure.
| $ZU(140,12,name,mode) | Check a file’s access permissions:$ZUTIL(140,12,name,mode). The mode bit mask has the following values: 0=file exists, 1=execute permission, 2=write permission, 4=read permission; values 3, 5, 6, and 7 represent combinations of these values. Returns 0 when successful (bit mask matches file’s permissions); returns -2 if the file does not exist, -13 if not all specified modes are permitted. $ZUTIL(140,12)does not change a file’s modification date/time.
| $ZU(140,13,dir) | Returns the amount of disk space available on the dir disk as four numeric values separated by commas: Free disk space available to the caller. Windows: space available to the caller in bytes (limited ifthere is a quota for the user). UNIX®: space available to non-privileged users in blocks. OpenVMS: space available to the caller in blocks. Total free disk space. Windows: in bytes. UNIX® or OpenVMS: in blocks. Total disk space. Windows: in bytes. UNIX® or OpenVMS: in blocks. Size of a block. Windows: defaults to 1. UNIX® or OpenVMS: in bytes.
| $ZU(140,14,source,destination) | Appends the contents of the source file to the destination file, or copies files from the source directory to the destination directory. This operation retains any prior contents of destination. $ZUTIL(140,11) is similar, but it overwrites the prior contents of destination. The source must exist. If a destination file does not exist, it will be created. If source is a file, destination may be a file or an existing directory. If source is a directory, destination must be an existing directory. In this case, all files in the source directory are copied to the destination directory, but subdirectories in source are not copied. Returns 0 when successful; returns a negative integer upon failure.
| $ZU(141) | Returns the number of actual parameters specified in the most recent entry to a function or subroutine. | $ZU(141) is not for customer use. You must evaluate $ZU(141) at the beginning of the routine before any other functions are called if you want to argument count of the current routine.
| $ZU(142) | Checks for valid literals
| $ZU(143) | Sends suspend/resume to job
| $ZU(144) | Quote string, add double quotes
| $ZU(145) | Executes a string in remote job
| $ZU(146) | Internal db locking support
| $ZU(147, pathname) | Handles spaces in pathnames for the host platform. | API: %Library.File.NormalizeFilenameWithSpaces()
| $ZU(148) | VMS internal tape support
| $ZU(149) | Windows up/down checking
| $ZU(150) | DebugBreak (cause core dump)
| $ZU(151) | ODBC data packing
| $ZU(152) | ODBC data packing
| $ZU(153) | Compact Unicode Encode
| $ZU(154) | invalidate global vectors
| $ZU(155) | SuperToken compiler
| $ZU(156) | internal new lock support
| $ZU(157) | comm. Ports
| $ZU(158,0) | Returns the number of printers currently installed on your system, counting from 1. | %Library.Device.InstalledPrinters()
| $ZU(158,1,n) | Returns the pathname of the printer currently installed on your system that corresponds to n. Caché counts printers from 1, and assigns a sequential integer to each. If n is a number that does not correspond to a printer, Caché issues a <FUNCTION> error. | %Library.Device.GetPrinters()
| $ZU(159) | obsolete printer wizard login support
| $ZU(160) | Saves/restores job state
| $ZU(161) | fastcloseobj
| $ZU(162) | seizespin stuff
| $ZU(163) | $ZS stuff
| $ZU(163,n) | Changes the value of $zs/$zstorage to n. $zs = max amount of job memory
| $ZU(164) | rem_all_oid
| $ZU(165,1,range) | Returns a random number from 1-range. 
| $ZU(165,0) | Returns the last random number generated
| $ZU(165,0,val) | sets seed value | see also: $random,$system.Encryption.GenCryptRand()
| $ZU(166) | TCP B mode for Weblink et al
| $ZU(167) | Used by REPAIR to analyze nodes
| $ZU(168) | Returns current working directory | API: %SYSTEM.Process.CurrentDirectory()
| $ZU(168,dir) | Changes working directory to dir | API: %SYSTEM.Process.CurrentDirectory()
| $ZU(169) | Returns info for a debugger
| $ZU(170) | crypt support
| $ZU(171,1) | Returns CPU time (in milliseconds) on any OS, as a string in format SYS_time,USER_time
| $ZU(171,1,pid) | Returns total CPU time (system + user) for process pid.
| $ZU(172,0) | Superserver port
| $ZU(173,sfn) | Designates sfn as "cachetemp" database for this system
| $ZU(174) | 
| $ZU(175) | 
| $ZU(176) | 
| $ZU(177) | 
| $ZU(178,ns,global,collation,protection,journaling,keep,pointer block,growth block) | Creates a global with no data in the specified namespace with no data but with the specified characteristics. All parameters but ns and glo are optional. A value of -1 means use the defaults. | API: %Library.GlobalEdit.Create()
| $ZU(179) | audit setup
| $ZU(180) | Runs prefetch background job
| $ZU(181) | Returns current maxpid
| $ZU(181,num) | Expands pidtab by num slots
| $ZU(182,0) | Returns wdsuspd
| $ZU(182,1) | Returns gbackupreq
| $ZU(182,1,0) | Frees a suspended Write Daemon
| $ZU(182,1,n) | Sets gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to 0 and gbackupmaxtime to 0 
| $ZU(182,1,n,m) | set gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to <m> and gbackupmaxtime to 0 gwdmaxsusptime is only changed when n>0
| $ZU(182,1,n,m,t) | Sets gbackupreq to n (n>0) or clear (n=0) and gwdmaxsusptime to <m> and gbackupmaxtime to <t> 
| $ZU(182,2,i) | Returns gbackupsfn[i] (i>=0)
| $ZU(182,2,i,n) | Sets gbackupsfn[i] (i>=0) to sfn n
| $ZU(182,3[,0/1]) | get[,clear/set] bckjob to pjobnum.clear/set: return 1 on success or <=0
| $ZU(182) | wdsusp and gbackupreq
| $ZU(183) | ECPWork daemon
| $ZU(184) | Changes ECP State
| $ZU(185) | Compares/swaps global node
| $ZU(186,n) | Sets display in programmer prompt for the current process. n An integer code or a comma-separated list of integer codes that specify what element(s) to include in the terminal prompt. Integer codes should be specified in the order in which you wish the elements tobe displayed. | API: %SYSTEM.Process.TerminalPrompt()
| $ZU(186,0) | Host name, also known as the current system name. The name assigned to your computer. For example,LABLAPTOP>. This is the same for all of your terminal processes. Refer to $ZUTIL(110) for further details.
| $ZU(186,1) | Namespace name. For example, %SYS>. To set your terminal prompt to just the current namespacename, you can use $ZUTIL(68,26,1). The current namespace name is contained in the $ZNSPACE special variable, and can be changed using the ZNSPACE command. It can be an explicit namespacename or an implied namespace name.
| $ZU(186,2) | Config name. The name of your Caché installation. For example, CACHE2>. This is the same for all of your terminal processes.
| $ZU(186,3) | Current time, expressed as local time in 24-hour format with whole seconds. For example, 15:59:36>.This is the static time value for when the prompt was returned. This value changes for each prompt.
| $ZU(186,4) | pid. The Process ID for your terminal. For example, 2336>. This is different for each terminal process. This value can also be returned from the $JOB special variable.
| $ZU(186,5) | Username. For example, fred>. This is the same for all of your terminal processes.
| $ZU(186,6) | Elapse time executing the last command, in seconds.milliseconds. For example, .000495>. Leadingand trailing zeros are suppressed.This changes for each prompt.
| $ZU(187) | | Removed, never used
| $ZU(188) | Returns local date and time with fractional seconds system-wide. | <Function>.$NOW
| $ZU(189) | Checks if TCP device is disconnected. | API: %SYSTEM.INetInfo.Connected()
| $ZU(190) | SNMP support
| $ZU(191) | 
| $ZU(192) | 
| $ZU(193,timestamp,direction) | Converts Coordinated Universal Time (UTC) to local date and time (and vice versa). direction (optional) A boolean values specifying the direction in which to convert timestamp. If 0, timestamp is interpreted as a UTC value and converted to local time. If 1, timestamp is interpreted as a local date/time value and is converted to UTC. The default is 0 | <Function>.$ZDATETIMEH
| $ZU(194,1) | Returns 1 if emergency startup,otherwise 0.
| $ZU(194,1,uname,pwd) | 1 if uname,pwd good,otherwise 0.
| $ZU(194,2) | Returns comma-sep list uid,gid,ownerid.
| $ZU(194,3,uname,pwd) | Sets username/pw into emergency space.
| $ZU(194,4) | Resturns 1 if private routine on stack
| $ZU(195) |
| $ZU(196) |
| $ZU(197) |
| $ZU(198) |
| $ZU(199) |
| $ZU(200) | Obsolete License support
| $ZU(201) | 5.0 License Support
| $ZU(202) |
| $ZU(203) |
| $ZU(204) |
| $ZU(205) |
| $ZU(206) |
| $ZU(207) |
| $ZU(208) |
| $ZU(209) |
| $ZU(210,0) | Support for %FromJSON()
| $ZU(210,1) | Support for %OnClose(), i.e. when object is killed
| $ZU(210,2) | Unused
| $ZU(210,3) | Support for %Dump()
| $ZU(210,4) | Dynamic dispatch for %Get on %DynamicObject
| $ZU(210,5) | Support for dynamic dispatch for set, and %Set
| $ZU(210,6) | Type of a PV, but usually used by %Iterator
to ensure a specified PV exists.
| $ZU(210,7) | Create a new PVA, as used by %OnNew().
| $ZU(210,8) | Compare key name maps for document database
| $ZU(210,9) | Support %Clone()
| $ZU(210,10) | Support %Get on %DynamicArray
| $ZU(210,11) | Support %GetTypeOf on %DynamicArray
| $ZU(210,12) | Support %GetAt on %DynamicObject
| $ZU(210,13) | Support %GetTypeof on %DynamicObject
| $ZU(210,14) | Ret statistics about number of calls we've made.
| $ZU(210,15) | Zero the stats about number of calls we've made
| $ZU(210,16) | Support %Clear()
| $ZU(210,17) | Support for %Set and %SetAt on %DynamicArray
| $ZU(210,18) | Display diagnostics for objects.
| $ZU(210,19) | Support for %Remove for %DynamicArray
| $ZU(210,20) | Support %Push for %DynamicArray
| $ZU(210,21) | Support %Remove for %DynamicObject
| $ZU(210,22) | Support for %GetNext on %DynamicArray
| $ZU(210,23) | Support for %GetNext on %DynamicObject
| $ZU(210,24) | Support %Pop for %DynamicArray
| $ZU(210,25) | Set metadata in a PVA
| $ZU(210,26) | Get metadata in a PVA
| $ZU(210,27) | Support for %ToJSON()
| $ZU(210,28) | Support for %ToJSONFormat()
| $ZU(210,29) | Temp function to allow %Set() to over-ride rules
| $ZU(210,30) | Import a hash table in %Array format
| $ZU(210,31) | Export a hash table in %Array format
| $ZU(210,32) | %ToPVA() - create internal serialised format from the in-memory model | Unimplemented?
| $ZU(210,32) | %ToPVA() - fetch internal serialised format | Unimplemented?
| $ZU(210,34) | %FromPVA() - Build an in-memory model from the serialised format | Unimplemented?
| $ZU(210,35) | %FromPVA() - Append a string to the internal serialised format | Unimplemented?
| $ZU(210,36) | %FromPVA() and %ToPVA() -- kill the serialised format in the object | Unimplemented?
| $ZU(210,38) | %Delete of a %Array
| $ZU(210,39) | %Delete of a %Object