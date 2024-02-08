# pkts.io

This is Mobot's fork of [pkts.io](https://github.com/aboutsip/pkts).

We use this in our projects to parse pcap files, process the packets contained within, and re-write the pcap files.

There was a bug in the original pkts.io where writing big-endian pcap files would cause the sizes set in the packet headers (`PcapRecordHeader`) to get corrupted. This fork adds a small fix for that where we simply don't update headers prior to write. This serves our purposes as we're not manipulating the payload of the packets contained within the pcap files.

## Building

We only use the `pkts-core` module. To build the uberjar for that module:

```
cd pkts-core
mvn clean install -Dmaven.test.skip
```

This will install the repo your local `~/.m2` cache which allows you to build other JVM resources that depend on it

**Note:** Some versions of java / mvn are unable to build the test dependencies, so `-Dmaven.test.skip` can be used to skip test compilation

## Distribution

This fork is not distributed anywhere, so you need to build it yourself

----------------------------------------
--- From the original repo ---
----------------------------------------

pkts.io is a pure java library for reading and writing pcaps. It's primary purpose is to manipulate/analyze existing pcaps, allowing you to build various tools around pcaps.

For full documentation, please see [aboutsip.com](http://www.aboutsip.com/pktsio/)
