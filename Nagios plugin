#!/bin/bash
echo "CMD_TIME: curl -k --location --no-buffer --silent --output /dev/null \-w %{time_connect}:%{time_starttransfer}:%{time_total} $1"
time=$(curl -k --location --no-buffer --silent --output /dev/null \-w %{time_connect}:%{time_starttransfer}:%{time_total} $1)
connectTime=$( echo "$time" |cut -d: -f1|tr "," "." |cut -c1-5)
transfertTime=$( echo "$time" |cut -d: -f2|tr "," "." |cut -c1-5)
totalTime=$( echo "$time" |cut -d: -f3|tr "," "." |cut -c1-5)
echo "TEMPS: $connectTime:$transfertTime:$totalTime"
echo "TEMPS TOTAL: $totalTime"
r=$(echo "$totalTime < $2" |bc)
if [ $r == 1 ]
then
echo "OK - Site $1 time $totalTime | 'time'=$totalTime;$2"
else
echo "CRITICAL - Site $1 ne repond pas correctement, time $totalTime | 'time'=$totalTime;$2 "
fi
