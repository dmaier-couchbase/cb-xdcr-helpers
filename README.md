# XDCR helper scripts in Python

## List all replication tasks

The following example lists you all XDCR replication tasks

```python
import xdcrclient
xdcrclient.list("http://192.168.7.188:8091", "couchbase", "couchbase")
```
The output is the XDCR replication id:
```
5b039e49fbdec518548250a7900377b1/travel-sample/travel-sample-xdcr
```
Whereby the components are:

* The UUID of the cluster reference
* The source bucket 
* The target bucket

## Get the UUID from the name of a cluster reference

The following example shows how to get the UUID of a cluster reference based on it's name

```python
import xdcrclient
xdcrclient.resolve_uuid("http://192.168.7.188:8091", "couchbase", "couchbase", "local")
```
The return value is:

```
'5b039e49fbdec518548250a7900377b1'
```

## Build a XDCR replication id from the name

The following example shows how to create the 

```python
import xdcrclient
xdcrclient.link_id("http://192.168.7.188:8091", "couchbase", "couchbase", "b_source", "b_target", "local")
```
The return value is the XDCR replication id

```
'5b039e49fbdec518548250a7900377b1%2Fb_source%2Fb_target'
```

The components are:

* The UUID of the cluster reference
* The source bucket
* The target bucket

The '/' was escaped by is HTML encoded in order to use the id directly in further REST calls.

