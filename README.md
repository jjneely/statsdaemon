statsdaemon
==========

Port of Etsy's statsd (https://github.com/etsy/statsd), written in Go (originally based
on [amir/gographite](https://github.com/amir/gographite)).

This is a fork of Bitly's Statsdaemon code.  Goals for this fork are:

* Support float64 timers - done
* Support float64 gauges - done
* Support float64 counters
* Add timer statistics
    * standard deviation (`std`)
    * count per second (`count_ps`)
    * sum (`sum`)
    * sum of sqaures (`sum_squares`)
    * median (`median`)
    * count percentiles
    * mean percentiles
    * sum percentiles
    * sum of squares percentiles

Supports

* Timing (with optional percentiles)
* Counters (positive and negative with optional sampling)
* Gauges (including relative operations)
* Sets

Installing
==========

### Building from Source
```
git clone https://github.com/jjneely/statsdaemon
cd statsdaemon
go get github.com/bmizerany/assert #for tests
go build
```


Command Line Options
====================

```
Usage of ./statsdaemon:
  -address=":8125": UDP service address
  -debug=false: print statistics sent to graphite
  -delete-gauges=true: don't send values to graphite for inactive gauges, as opposed to sending the previous value
  -flush-interval=10: Flush interval (seconds)
  -graphite="127.0.0.1:2003": Graphite service address (or - to disable)
  -max-udp-packet-size=1472: Maximum UDP packet size
  -percent-threshold=[]: percentile calculation for timers (0-100, may be given multiple times)
  -persist-count-keys=60: number of flush-intervals to persist count keys
  -postfix="": Postfix for all stats
  -prefix="": Prefix for all stats
  -receive-counter="": Metric name for total metrics received per interval
  -tcpaddr="": TCP service address, if set
  -version=false: print version string
```
