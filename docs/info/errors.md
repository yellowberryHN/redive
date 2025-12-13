# Error Dictionary

This page contains many possible errors you may run into with WACCA

## Red/Blue Error Screens

### 800-0: Unknown Error { #800-0 }
This just happens sometimes. Supposedly an auth server error. Check the AMDaemon console for any unusual errors,
and then try again.

### 1102-1: Touch Board Invalid Side { #1102-1 }
Both touch sync boards were reported to be the same side, which is not a valid configuration. Ensure the rotary DIP
switch on the sync boards are set properly. The left side board should be 7, and the right side board should be 8.

### 1103-1: No Touch Unit Boards Found { #1103-1 }
No touch unit boards (the boards in the individual panels) were found. Ensure that the cable which attaches the unit
boards to the sync board is connected properly.

### 1104-1: Touch Board Communication Failed { #1104-1 }
Connection to the touch sync boards could not be established due to the COM port being in use. Make sure there aren't
any other applications using the COM ports for the touch boards.

### 1104-2: Touch Get Version Timeout { #1104-2 }
The request to get the version of the touch boards has timed out. There is likely something wrong with your hardware,
or your software implementation is not correct.

### 1104-3: Touch Set Threshold Timeout { #1104-3 }
The request to set the sensitivity thresholds of the touch boards has timed out. There is likely something wrong with
your hardware, or your software implementation is not correct.

### 1105-1: Touch Key Data Timeout { #1105-1 }
The touch boards did not respond with key data fast enough. There is likely something wrong with your hardware,
or your software implementation is not correct.

### 1105-2: Touch Signal Data Timeout { #1105-2 }
The touch boards did not respond with raw sensor data fast enough. This functionality is unused by the game itself,
and is only accessible in the development menu. There is likely something wrong with your hardware, or your software
implementation is not correct.

### 1106-1: Touch Unit Board Error { #1106-1 }
One of the touch unit boards did not respond correctly. There is likely something wrong with your hardware, 
or your software implementation is not correct.

### 1107-0: Touch Sync Board Param Fixed { #1107-0 }
Unsure, assume it has something to do with trying to write a parameter on the sync board which is read-only.

### 1107-1: Touch Sync Board Param Write Failed { #1107-1 }
Unsure, assume it has something to do with failing to write a sync board parameter.

### 1200-0: Generic LED Error { #1200-0 }
LED controller threw an exception. Not really useful. Check consoles?

### 1201-1: Failed to find LED DLL { #1201-1 }
The LED DLL (`USBIntLED.dll`) was not found. Make sure it's exists in 
`WindowsNoEditor\Mercury\Plugins\ElizabethPlugin\Source\LEDDevice\Source\Runtime\Public\Externals\`.

### 1201-2: Failed to load LED DLL { #1201-2 }
The LED DLL could not be loaded. This is typically due to architecture mismatch on the DLL and the game. Make sure the
DLL was compiled as x86-64.

### 1202-1: Failed to init LED DLL { #1202-1 }
The LED DLL could not be initialized. This either means that the hardware check failed, or the init method was not found.

### 1203-1: Invalid LED configuration { #1203-1 }
The LED DLL doesn't like how you've configured your LEDs. Typically, you won't ever see this.

### 1300-0: Generic Title Server Error { #1300-0 }
The game is unhappy about how the title server responded. Check your networking.

### 1301-1: Title Server Get Housing ID Failed { #1301-1 }
The title server failed to provide you with a housing (cab) ID. Check your networking. This might also mean your cab is
banned from the server.

### 1302-1: Title Server Get Area ID Failed { #1302-1 }
The title server failed to provide you with an area ID. Check your networking. This might also mean your cab is banned
from the server.

### 1900-0: Generic Network Error { #1900-0 }
There was an error with the network. Check your network? Restart the game?

### 1901-1: Network Error (IP Address) { #1901-1 }
IP address was not assigned to this machine. Check your network DHCP settings.

### 1902-1: Network Error (Gateway) { #1902-1 }
Network gateway was not assigned or not valid. Check your network DHCP settings.

### 1903-1: Network Error (DNS) { #1903-1 }
DNS lookup failed. Check your network settings, and also make sure that they are pointed to the right server.

### 1904-1: Network Error (Hops) { #1904-1 }
Too many hops between the auth server and you. This should not ever happen in a properly configured network.

### 1905-1: Network Error (Line Type) { #1905-1 }
The DNS resolved for a router on a line type that is invalid for this game configuration. This shouldn't happen.

### 1906-1: Network Error (ALL.Net Auth) { #1906-1 }
Connection to auth server was not successful. This could either mean it could not connect to the server at all, or you
were forcefully kicked off for not being validated on the server you're connecting to.

### 4105-0: Unexpected Error { #4105-0 }
AMDaemon is angry. If you're running data, check the AMDaemon window for anything that says `Runtime exception occured.`

### 6501-0: Card Reader Not Found { #6501-0 }
The game was unable to detect your card reader. Ensure you have a reader connected, and that the game configuration
and the reader have a matching baud rate configured.

## AMDaemon Errors

This section is only relevant if you're running data. If not, you shouldn't really be getting these errors anyway???

### amGfetcherInit(). ErrCode -1 { #amGfetcherInit }

ICF1 file was not found. Make sure you have one in the `bin/amfs` folder. When adding one, make sure to delete `sysfile.dat`,
as it must be regenerated with the data in the ICF file.

TODO: links to ICF files

### amSysFileInitEx(). ErrCode -5 { #amSysFileInitEx }

`sysfile.dat` failed to be written. Make sure `bin/amfs` folder is writable.

### CreateFileMappingW failed. { #CreateFileMappingW }

Computer hostname and account username cannot be identical. Change the hostname of the machine to something other
than the username.

