DistStat
========

A simple utility for collect CPU/MEM/DISK/NET statistics from small cluster.

<b>distat</b> is designed as a lightweight and standalone tool to collects statistics 
from cluster. Current statistics include:
<ul>
    <li>CPU usage</li>
    <li>Memory usage</li>
    <li>Disk read rate (in KB)</li>
    <li>Disk write rate (in KB)</li>
    <li>Network read rate (in KB)</li>
    <li>Network write rate (in KB)</li>
</ul> 

Dependencies
============
<ul>
    <li><b>ssh</b>: <b>dist</b> currently use ssh to execute command on remote hosts.
             Also make sure that remote hosts can be login via ssh without password.</li>
    <li><b>sar</b>: use to do the stat work. All remote hosts should have sar installed.</li>
    <li><b>bash</b>: since <b>dist</b> is written in bash.</li>
    
</ul>

Usage
=====

<ol>
    <li>Edit configuration distat-env.sh (optional, maybe default setting is cool for you).</li>
    <li>Run distat.</li>
</ol>

Output
======
The result files will be in RESULT_DIR. The result produce timing will be control by 
MAX_FILETIME and MAX_FILESIZE(max file open time).<br/>
The format of the result file is delimited, and the field delimiter is customizable
with DELIMITER. A result file may contains lines of statistics. Each line is of format
(take DELIMITER=, for example):<br/>
<code>
HOSTNAME,CPU,MEM,DISK_READ,DISK_WRITE,NET_READ,NET_WRITE
</code>
<br/>
One line for each host at every collect interval.<br/>


