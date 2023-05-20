# OpSec

Some quick notes on operational security when deploying infrastructure. I'll dive deeper into these and refine this section further in the future.&#x20;

1. If utilizing a dropbox with Kali Linux installed, ensure that you have removed both the Kali and Metasploit repositories from `sources`.&#x20;
   1. Reaching out to either of these domains is easily alerted on.
2. Ensure the hostname is not suspicious upon connecting to the network.&#x20;
3. Ensure that running a command such as `apt-get` results in expected repositories such as Ubuntu or Debian being called (this will depend on the network and systems in use).
4. Install all tooling and verify it is working as expected prior to deploying a machine on the network. (You don't want to be fighting dependencies after planting the machine).&#x20;
5. Type redacted commands to teammates over secure communications prior to running.&#x20;
   1. This will ensure that you can run/chain attacks together faster.&#x20;
   2. This will also ensure that you or a teammate may catch any typos in the command.&#x20;
6. If possible, ensure that full disk encryption is enabled on the dropbox. Otherwise, ensure that no sensitive information is stored on the system in the event that it is burned.&#x20;

### References

{% embed url="https://www.trustedsec.com/podcasts/episode-4-4-opsec-is-hard/" %}
