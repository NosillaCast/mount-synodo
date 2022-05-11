Purpose: to find out if a specific server is alive on the network and if so, mount a specific share. If the server is shut down, or the Mac running this Shortcut is away from the network, no attempt to mount the share should occur. Also, if the share is already mounted, the Shortcut should take no action.

This Shortcut will be part of my Hazel rules so that Hazel won’t yell at me when my Mac is away from my home network, or we’ve shut down our NAS.

Shell script tests first to see if the IP address of the server answers a single ping in one millisecond. If it responds, we know it’s on the network. The next step is to search for the file share name in the results of the mount command (which shows all mounted volumes).

If the share is already mounted, the script stops (silently). If the IP responds to the ping, and it does not find the share in mount (meaning it’s unmounted), only THEN does it mount the volume. If it does find the share in mount, then it does nothing.