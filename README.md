## INTRODUCTION
It is a painful work to read dories profile, especially when there are multi-parallel instances.
This tool helps us to grasp the main information of profile in a graphical view.

The profile is represented by a tree graph.
a tree node reprents a sql operator
   - operation type, such as join, scan
   - operation node id and fragment id, used to locate it position in profile
   - some associated information, e.g. table name for scan node
An arrowed edge represents data flow. The number on the arrow means how many rows transferred from child node to its parent. For multi-parallel instance,
this number is the sum of all intances. For example, we have a scan node on lineitem table in plan, there are 4 parallel instances, 
and each ScanNode output 10 rows, the number is 40.

Here is a demo 
[![tpch Q2](https://github.com/englefly/profile_viewer/blob/main/q2.nrf.png?raw=true)](https://github.com/englefly/profile_viewer/blob/main/q2.nrf.png?raw=true)

## USAGE
`python profile_viewer.py [PATH_TO_PROFILE]`

for example:

after running
`python profile_viewer.py tpchq2.profile`

we will get tpchq2.profile.png

## PREREQUISITE
    graphviz is required(https://graphviz.org/)
    on linux: apt install graphvize
    on mac: brew install graphvize 
