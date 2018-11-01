# ResponderMITM is a modified copy of the original Responder.py packaged with the Responder Man-in-the-Middle tool.

There is only one modification that has been made. This version listens on port 4445 rather than 445.

By listening on a non-standard port, we can runin 'Analyze' mode (i.e. -A) to only listen for SMB connections, handle authentication
and capture hashes. We can use a different tool to perform the man-in-the-middle attack, such as ettercap, bettercap, MITM Framework, etc.
Once all traffic between our victims is flowing through our attack host, we can use iptables to redirect all port 445 packets to port 4445
and have Repsonder do its thing. Watch the hashes roll in.

Example IPTables rule: iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 445 -j REDIRECT --to-port 4445
