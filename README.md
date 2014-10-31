BGP convergence time monitor
============================

# Description

The script will connect to a network element to monitor convergence
time for each BGP peer.


# Mode of operation

It uses the VTY service set to execute the related show commands.
Basically the script uses a simple logic to verify the peer convergence
status. it assumes that a peer has converged if and only if the following
two conditions are met:

    i-  the BGP table version should be equal to the main routing table version
        (TblVer == RTv) and:
    ii- Both InQ and OutQ are == 0


The script will listen for a change on the peer status and will start a timer.
The timer will stop once converged has been achieved and the diff
is graphed for every neighbor.

In real work scenarios, the tblversion would increase constantly so the scripts
accepts an option to only verify condition ii.


# How to use

The idea is mainly to be able to track anomalies on BGP convergence time by 
having an event history. 

It can also be used only to raise an alert if convergence has not been achieved
with a specific neighbor after an specified amount of time.

# Requirements

This script uses the VTY service set from the onepk Cisco API.



