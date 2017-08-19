Tunneling Instructions
=========================================

The the following commands to set up the alias for the tunnels in both directions.  It is most convenient to run these alias within a "screen"
  alias tunnel_to_external='ssh -N -L 22000:edda.vpac.org:22 <intermediary_login_name>@<intermediary_machine_address>'
  alias tunnel_from_external='echo "Making a tunnel from external machine"; ssh -N -R 22001:localhost:22 -p 22000 <external_login_name>@localhost'

To secure copy to the external machine:
  scp -p 22000 <files on local machine> <external_login_name>@localhost:~
To secure copy from the external machine:
  scp -P 22001 <files on external machine> <local_login_name>@localhost:~/Desktop/

To avoid know hosts problems set the following lines in "/etc/hosts"
  127.0.0.1   			  localhost
  255.255.255.255 	  broadcasthost
  ::1             	  localhost
  <local_machine_IP> 	<local_machine_name> 		<local_machine_full_address>
  127.0.0.1   			  <external_machine_name> <external_machine_full_address>

To avoid writing "localhost" all the time when using "scp" add the following lines in ~/.ssh/config
  host <exeternal_machine_name>
  port 22000
  host <external_machine_full_address>
  port 22000
