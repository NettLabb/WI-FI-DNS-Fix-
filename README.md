# WI-FI-DNS-FIX
Scripts, notes, and reflections for diagnosing and fixing Wi-Fi/DNS issues on Linux/macOS terminals
Context 
After a router firmware update, my laptop lost internet connectivity while all other devices worked fine.
I needed internet to test the scripts commands in the VM I had jsut set up and the outage had simply blocked the workflow and forced to me to dig into the network and find out what was going on. 
**INVESTIGATION**
Ran ifconfig: IP checked out okay 
ping 8.8.8.8: No response 
nslookup google.com:DNS not resolveing 
Checked routing table: Default gateway correct, but DNS entries missing. 
Hypothesis: Router reboot reset network configs, local DNS entries corrupted. 
Tried temp fixes restart NetworkManager reboot: Didnt fully resolve issue.
**FIX**
Edited/etc/resolv.conf to manually set DNS servers 8.8.8.8 and 1.1.1.1 
Restarted network interface: sudo systemctl restart NetworkManager 
Verifed connectivity with ping google.com  **Success** 
OPT: Run traceroute google.com to confirm routing was correct 
**Prevention** 
Keep a backup of working DNS/Network configs for quick recovery. 
Maintain a quick fix script for common network issues. 
Document system or router changes to trace problems faster.
Systematic approach: Ping-DNS-logs 
**Reflection** 
This experience taught me pateince and the value of a through investigation 
**Approach**
Test network for stablity build the skill that develops as fundamental knowledge in handleing this scenario
Overall this made feel a mix of frustraion and relief once I fixed the network, I fell I can handle any network issue now as long as methodically approcah each step and take my time.
