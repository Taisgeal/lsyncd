---
layout: default
title: "Examples"
---
Layer 4 Examples
----------------

bash sync:
<pre>
sync{bash, source="/home/lonewolf/teste1", target="/home/lonewolf/teste2"}
</pre>

rsyncssh option:

<pre>
sync{default.rsyncssh,
        source="/var/www/live_site_resources",
        host="192.168.129.90",
        targetdir="/var/www/live_site_resources",
        delete="running",
        exclude={ ".*", "*.tmp" },
        rsync = {
                compress = false,
                checksums = false,
                _extra = {"--bwlimit=50000"},
        }
}
</pre>

Layer 3 Examples
----------------
 * [GForce](gforce): forces a local directory tree to be read/writable by a group.

Layer 2 Examples
----------------

Layer 1 Examples
----------------
 * [Auto Image Magic](auto-image-magic): creates a "magic" directory in which all images placed into will be converted to other file formats
 
 Multi-File Example
 --------------------
 settings  {
	logfile = "/var/log/lsyncd/lsyncd.log",
	statusFile = "/var/log/lsyncd/lsyncd.status",
	insist = true,
}

local confdir = '/etc/lsyncd/lsyncd.d/'
local entries = readdir( confdir )
for name, isdir in pairs( entries ) do
    if not isdir then
        dofile( confdir .. name )
    end
end
