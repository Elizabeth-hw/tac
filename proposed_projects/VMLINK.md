# VMLINK Automounter

## Description
A VMLINK-like automounter script combining the function of
`vmcp link`, `chccwdev`, and `mount` in one fell swoop.

Use `/etc/auto.net` as a starting reference.
`vmcp link` may fail (e.g., if the virtual machine attempting the link
is not authorized). `mount` may fail (e.g., if there is no filesystem
or is not a known filesystem).

The automount point should be identified by

* vmid
of the owning virtual machine
* address
of the disk on the owning virtual machine, and optionally
* partition
if the disk has multiples

Note that a 3390 CKD volume in "compatible layout" can have
1, 2, or 3 partitions. Other layouts can have 1 partition
or 0 (meaning the entire disk from the starting block, offset zero)

## Additional Information
*See the `vmlink` command in the CMS guide.*

## Desirable Skills
*Mostly shell scripting.
Familiarity with the `mount` command (or acquired during the project)
is a must. Familiarity with `vmcp link` needed too, but can be learned.

## Expected Outcome
*Users should be able to `cd /vmlink/vmid.addr`
or `cd /vmlink/vmid.addr.part` and have access to the filesystem(s)
available on the linked virtual disk.

## Difficultly
*Medium*

## Mentors
  * *Rick Troth <rmt@casita.net>*

## Additional Contacts
*See the `vmlink` command in the CMS guide.*

In one shop, we did a lot of sharing of disks among virtual machines. 
Doing a 'vmcp link' was no big deal for the VMers. Use of 'mount' was 
second nature for the Linux guys. The combination was always a mental 
stretch. Eventually we coaxed the automounter into doing it all for us.

Most Linux distros include /etc/auto.net which serves as an example. 
(Usually also /etc/auto.smb if you like.) Maybe create /etc/auto.vmlink 
to handle linking, varying online, and mounting of disks owned by other 
virtual machines (assuming your v-machine has the rights to read it, 
which is a whole other story). So then one could simply ...

Partitioning is another matter. If a disk has one (or zero) partitions, 
the script could just figure things out. If the disk has multiple 
partitions, maybe tack-on an extra dotted indicator for the partition of 
interest.

I call it "VMLINK-like" because in CMS there is the 'vmlink' command 
which provides a simila


