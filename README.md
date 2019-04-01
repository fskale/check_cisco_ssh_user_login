# check_cisco_ssh_user_login 1.0

# License
 This nagios plugin is free software, and comes with ABSOLUTELY NO WARRANTY.
It may be used, redistributed and/or modified under the terms of the GNU
General Public Licence (see http://www.fsf.org/licensing/licenses/gpl.txt).

# What it does
* Using state of the art non-blocking/async IO (EV and Mojolicious)
* Proper error handling !
* Login via SSH (hostname, username, password)
* Issue command "show users"
* Parse the output and find the user which we use for the connection
*  Disconnect properly (no needless log violations in the cisco device)
*  Return the correct exit value according to the output or errors (ssh->error)

# Usage:
check_cisco_ssh_user [ -V|--version ] [-H|--hostname <host>]
[-U|--username <Username>] [-P|--password <password>]
[-p|--port <tcp port>] [-t|--timeout <timeout>]

`` -?, --usage | Print usage information ``
`` -h, --help | Print detailed help screen ``
``-V, --version | Print version information ``
 ``--host, -H | IP address or hostname of cisco device ``
 ``--username, -U | username``
 ``--password, -P | password ``
 ``--port, -p | tcp port to use (optional)``
 ``-t, --timeout=INTEGER |Seconds before plugin times out (default: 10) ``
 
  **This plugin was not tested on Windows. Feel free to do so  and report back !**
  **At least use perl version 5.20 !**
  **The user must have the privilege to issue the command 'show users'**

  ## Prerequisites (Linux and other derivates):
  ### Debian (Build essentials) needed for EV and IO::Tty
  `apt-get install build-essential`
  ### Redhat (Devtools)
  `yum groupinstall 'Development Tools'`
  ## Installation of dependend modules
  ### Using cpan:
  `cpan Mojolicous EV IO::Tty Net::OpenSSH Monitoring::Plugin`
  ### Using cpanm:
  `cpanm Mojolicous EV IO::Tty Net::OpenSSH Monitoring::Plugin`
  
  ### Example output
  ```CISCO_SSH_USER_LOGIN OK - Found username autobackup on host 192.168.1.1```
  #### Timeout error 
  ```CISCO_SSH_USER_LOGIN CRITICAL - Error: Timeout (5s) connecting to host: example.com User: test Port: 22```
  
  ## Credits:
  * [Mojolicious realtime framework](https://mojolicious.org)
  * [EV](https://metacpan.org/pod/EV)
  * [Net::OpenSSH](https://metacpan.org/pod/Net::OpenSSH)
  * [Monitoring::Plugin](https://metacpan.org/pod/Monitoring::Plugin)
  * [IO::Tty](https://metacpan.org/pod/IO::Tty)
