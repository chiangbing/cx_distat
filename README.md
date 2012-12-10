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
The result files will be in RESULT_DIR. A result file is produced by one of below timings:<br/>
<ul>
    <li>The size of temporary resutl file(stored in TMP_DIR) reach MAX_FILETIME limit.</li> 
    <li>The time of temporary result file is longer than MAX_FILESIZE(max file open time).</li>
    <li>A new day come.</li>
</ul>

The format of the result file is delimited, and the field delimiter is customizable
with DELIMITER. A result file may contains lines of statistics. Each line is of format
(take DELIMITER=, for example):<br/>
<code>
TIMESTAMP,HOSTNAME,CPU,MEM,DISK_READ,DISK_WRITE,NET_READ,NET_WRITE
</code>
<br/>
One line for each host at every collect interval.<br/>

Configuration
=============
<table>
    <tr>
        <th>Item</th>
        <th>Description</th>
        <th>Default Value</th>
    </tr>
    <tr>
        <td>MAX_FILESIZE</td>
        <td>Max size of result file (in bytes)</td>
        <td>1048576 (1M)</td>
    </tr>
    <tr>
        <td>MAX_FILETIME</td>
        <td>Max open time of result file (in seconds)</td>
        <td>3153600000 (10 years)</td>
    </tr>
    <tr>
        <td>MAX_SEQ</td>
        <td>Max sequence number of result file (as suffix)</td>
        <td>9999</td>
    </tr>
    <tr>
        <td>TMP_DIR</td>
        <td>Temporary directory for intermediate files.</td>
        <td>tmp</td>
    </tr>
    <tr>
        <td>PID_FILE</td>
        <td>PID_FILE contains pid of running script (for manually killing).</td>
        <td>tmp/distat.{instanceid}.pid</td>
    </tr>
    <tr>
        <td>LOG_DIR</td>
        <td>Log directory.</td>
        <td>logs</td>
    </tr>
    <tr>
        <td>RESULT_DIR</td>
        <td>Result file directory.</td>
        <td>results</td>
    </tr>
    <tr>
        <td>SLAVES</td>
        <td>A list of hosts to collect statistics.</td>
        <td>localhost</td>
    </tr>
    <tr>
        <td>NET_IFACE</td>
        <td>Net interface device name pattern (regex).</td>
        <td>bond0</td>
    </tr>
    <tr>
        <td>DISK_DEV</td>
        <td>Disks device name pattern (regex).</td>
        <td>sd (for SATA disks)</td>
    </tr>
    <tr>
        <td>INTERVAL</td>
        <td>Collecting interval (in seconds).</td>
        <td>60 (1 minute)</td>
    </tr>
</table>
