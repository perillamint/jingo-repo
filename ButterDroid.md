# What is it
Android with BtrFS /data.

# Expected benefits
* Snapshots
* Boot into subvolume & run multiple subvolumes

# Plan
* Hack vold to support BtrFS subvolume mount
* Hack framework to show subvolume select dialogue before boot.