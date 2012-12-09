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
