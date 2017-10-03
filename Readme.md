Sync remote services into consul

 - cleaned up removed
 - updates changed
 - adds new

Install
=======

```Bash
gem install consul_syncer
```

Usage
=====

```Ruby
syncer = ConsulSyncer.new('http://localhost:8500', logger: Logger.new(STDOUT))
syncer.sync(
  [
    {node: 'N', address: 'A', service: 'S', service_id: 'ID', service_address: 'A', port: 123, tags: ['abc']},
    # ...
  ], 
  ['managed-by-consul-syncer']
)  
```

To identify the origin of consul requests or send other information along, use `params`.
They will get logged in consuls log `consul monitor --log-level=debug` and will tell others who made updates.

```Ruby
ConsulSyncer.new('http://localhost:8500', logger: Logger.new(STDOUT), params: {host: Socket.gethostname, app: 'consul-filler'})
```

Author
======
[Michael Grosser](http://grosser.it)<br/>
michael@grosser.it<br/>
License: MIT<br/>
[![Build Status](https://travis-ci.org/grosser/consul_syncer.png)](https://travis-ci.org/grosser/consul_syncer)
