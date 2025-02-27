# KAHU Radar Hub protocol
*A radar crowdsourcing protocol*

Contribute AIS and ARPA targets from your vessel to crowdsourcing for marine safety!

This is the ptotocol specification used by our plugins and clients as well as server code (e.g. [radarhub-opencpn](https://github.com/KAHU-radar/radarhub-opencpn) and [radarhub-signalk](https://github.com/KAHU-radar/radarhub-signalk)) that lets you upload AIS and radar ARPA targets (or any NMEA) to an internet server.
The communication protocol is based on [Apache Avro](https://avro.apache.org/) and batches track points so that the overhead for each point above timestamp and lat/lon is low, meaning it is designed to be as bandwidth conservative as possible.

Note: This protocol does **not** use the Avro RPC mechanism, as it is not well supported in all languages, and adds extra requirements such as adding run-length framing to each message. Instead, it relies on a simple union of message types.

## Database schema

The protocol includes a client side database schema used to cache tracks in an sqlite3 database. It is provided as a series of migration SQL files, to be applied in alphabetical order.
