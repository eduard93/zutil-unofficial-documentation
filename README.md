# zutil-unofficial-documentation
An unofficial documentation of $zu and $zutil function in IRIS/Ensemble/Caché

## Link to the official documentation

https://docs.intersystems.com/priordocexcerpts/rzut.pdf

## Official replacement

https://docs.intersystems.com/latest/csp/docbook/DocBook.UI.Page.cls?KEY=RCOS_replacements

## Table of commands

$zu(4) -> (4,pid) Terminate a process (^RESJOB), 

API: SYS.Process.Terminate()

$zu(5)			Print current namespace
$zu(5, "namespace")	Switch to namespace

Can also be done with write $namespace or set $namespace="namespace"

$zu(6)			Dead process clean up

$zu(9,device,message)	Print message to cconsole log (device = "" is the default device)

API for this: %SYS.System.WriteToConsoleLog()



$zu(12)			Print the full path of the mgr directory
$zu(12,dir,2)  		Validate and check that dir exists. A null string return means not a valid directory.

API: %Library.File.ManagerDirectory and %Library.File.DirectoryExists()

         
$zu(33,lockitem,ownerjob,ownersys)	removes one item from the Lock Table. Use class calls for this if actually on a customer system.

API: SYS.Lock.DeleteOneLock()

$zu(49)			sfn info of mgr directory
$zu(49,"")		sfn info of current directory
$zu(49,"dir")		sfn info of database located in directory dir
$zu(49,"dir",0)		complete sfn info of db in dir                        

$zu(51)			Returns value of WDSTOP
$zu(51,1)		Start the Write Daemon if necessary

$zu(53)			TCP Device name assigned by parent process
$zu(53,#)		Various TCP information

$zu(54,0)		See $zu(110)

$zu(56,0) 		return C module name that generated last Cache' error
$zu(56,1) 		return C line number that generated last Cache' error
$zu(56,2)  		return C mod name & line # that generated last Cache' err
$zu(56,3)  		return the error that caused the last job not to start

$zu(56,4) returns offset into routine buffer of current object code pointer
$zu(56,5) extended error information associatedwith the most recent error for which such information is maintained in perritem.
$zu(56,6) returns any OS error message associated with the COS error code, in the format "<code> text"



$zu(67,pid)		returns the job number of process "pid" if it is alive, else 0
$ZU(67,0,pid)	returns 2 if pid is active, 0 if not there, 1 if job is dead but pidtab is still in pidtab.
$ZU(67,1,pid)	same as $zu(67,0,pid) except it will clean up the pidtab if job is dead.
$zu(67,15,$J)		IP Address of current job
$zu(67,32,pid)		Return %SS name of pid

%SYS.ProcessQuery.Open() and .%OpenID() can also be used to check the state of a process.

You can Open a %SYS.ProcessQuery object by job number or process ID, then look at the JobNumber or Pid property

Also, see the ClientIPAddress and StartupClientIPAddress properties of that class

$zu(68,x)	set config options for current process
$zu(68,11)	set Read Line Recall (arrow keys in terminal)
$zu(69,x)	set config options system-wide


$zu(71,date)	set $H 
	>w $ZU(71,$H+2) would make $H always think it is the day-after-tomorrow 
$zu(71,0)	set $H to default


$zu(78,3)               returns current journal file
$zu(78,22)              returns whether journalling is enabled

API: %SYS.Journal.System.GetCurrentFileName() and .IsDisabled()

$zu(78,21)		Oldest TSTART


$ZU(88,2,j,n) get value of local variable n for job j


$ZU(94,pid,message)	sends message to process "pid".  Similar to $zu(9)


$ZU(110)        returns computer name 

You can also get the computer name from the $SYSTEM string - "write $SYSTEM" returns MachineName:InstanceName

$zu(112,0)	returns 1 if this process has a license, else 0
$zu(112,3)	Returns # of license units available on this system.
$zu(112,4)	Returns authorized license units in working memory

$zu(112,15,0)	Maximum license units.
$zu(112,15,1)	Currently available license units.

API:$system.License.LUAvailable()

$zu(112,15,2)	Minumum available license units.

API:$system.License.LUMinAvailable()

$zu(112,15,3)   $system.License.SetUserLimit maximum.
$zu(112,15,10)	Maximum CSP active session count.
$zu(112,15,11)	Current CSP active session count.
$zu(112,15,20)	Maximum CSP grace period session count.
$zu(112,15,21)	Current CSP grace period session count.
$zu(112,15,30)	Maximum Non-CSP session count.
$zu(112,15,31)	Current Non-CSP session count.

$zu(112,19) 	Return 1 if clustered, 0 otherwise.

$zu(132)	Make the current device the $principal device. 1 = success, else 0

$zu(136,21) - return current lowtimeprecision flag.
$zu(136,21,0) - switch to low time precision for $ZH and $zu(188). It clears lowtimeprecision.   Return original lowtimeprecision value.
$zu(136,21,1) - switch to high time precision for $ZH  and $zu(188). It sets lowtimeprecision.  Return original lowtimeprecision value.

$zu(141)	return the number of actual parameters specified in the most recent entry to a function or subroutine.  Be careful!!  $ZU(141) is not for customer use. You must evaluate $ZU(141) at the beginning of the routine before any other functions are called if you want to argument count of the current routine.

$zu(158,0)      On Windows, returns the number of printers defined on
                the system.  On other OS's this is a <FUNCTION> error.
$zu(158,1,{#})  On Windows, eturns the name of printer {#} as it needs
                to be referenced within Cache. On other OS's this is a
                <FUNCTION> error.
 Notes:       * f Idx=1:1:$ZU(158,0) w Idx,") ",$ZU(158,1,Idx),! will list all printers.
              * %Library.Device.InstalledPrinters() is the class wrapper and makes this
                functionality available to customers.

$zu(163,n)	Change the value of $zs/$zstorage to n. $zs = max amount of job memory

$zu(165,1,range)	Returns a random number from 1-range.  
$zu(165,0)		Returns the last random number generated
$zu(165,0,val) - sets seed value
see also: $random, $system.Encryption.GenCryptRand()
$zu(168)		Returns current working directory
$zu(168,"newdir")	Changes working directory to newdir


$ZU(171,1)      returns CPU time (in milliseconds) on any OS, as a string in format 			SYS_time,USER_time
$ZU(171,1,pid)  returns total CPU time (system + user) for process pid.

$ZU(172,0)		Superserver port

$zu(173,sfn)		Designates sfn as "cachetemp" database for this system

$zu(178,ns,global,collation,protection,journaling,keep,pointer block, growth block)
Create a global with no data in the specified namespace with no data but with the specified characteristics. All parameters but ns and glo are optional. A value of -1 means use the defaults.
API: %Library.GlobalEdit.Create()
$zu(181)	Returns current maxpid
$zu(181,num)	Expand pidtab by num slots

$zu(182,0): return wdsuspd
$zu(182,1): return gbackupreq
$zu(182,1,0): Free a suspended Write Daemon
$zu(182,1,n): set gbackupreq to n (n>0) or clear (n=0)
	      and gwdmaxsusptime to 0
	      and gbackupmaxtime to 0     
$zu(182,1,n,m):                            
	      set gbackupreq to n (n>0) or clear (n=0)
	      and gwdmaxsusptime to <m>    
	      and gbackupmaxtime to 0      
     		 gwdmaxsusptime is only changed when n>0
$zu(182,1,n,m,t):                          
	      set gbackupreq to n (n>0) or clear (n=0)
	      and gwdmaxsusptime to <m>
	      and gbackupmaxtime to <t>   
$zu(182,2,i): return gbackupsfn[i] (i>=0)
$zu(182,2,i,n): set gbackupsfn[i] (i>=0) to sfn n
$zu(182,3[,0/1]): get[,clear/set] bckjob to pjobnum.clear/set: return 1 on success or <=0


$ZU(186,func1,func2,...) -> build a terminal prompt by concatenating the n elements.  
                       values of func(n) are:
                        1 - Host Name - $zu(110)             
                        2 - NameSpace name - $zu(86)
                        3 - Config name
                        4 - Current time
                        5 - pid
                        6 - Username
                        7 - Time executing last command (in seconds.milliseconds)


$zu(188)	Returns $h with milliseconds
see also: $now
$zu(189)	Peek and see if TCP socket is disconnected

$zu(193)	Convert UTC date/time to local date/time

$zu(194,1) return 1 if emergency startup, otherwise 0.
$zu(194,1,uname,pwd) 1 if uname,pwd good, otherwise 0.
$zu(194,2) return comma-sep list uid,gid,ownerid.
$zu(194,3,uname,pwd) Set username/pw into emergency space.
$zu(194,4) return 1 if private routine on stack