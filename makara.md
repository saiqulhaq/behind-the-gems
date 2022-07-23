Gem link: https://github.com/instacart/makara  
This note is based on this commit https://github.com/instacart/makara/commit/30b01111fa02ee5983007236c50de864b4a5ebcd

# Summary

xxx

# What I've learned

WIP

# Diagram

```mermaid
classDiagram

    Makara__Strategies__Abstract <|-- Makara__Strategies__PriorityFailover
    Makara__Strategies__Abstract <|-- Makara__Strategies__RoundRobin
    Makara__Strategies__Abstract <|-- Makara__Strategies__ShardAware

    class Makara__ConnectionWrapper {
        # for every connection to makara DB, it's wrapped by this class
	# so this class is responsible to blacklist or whitelist the connection
	# in case there is error
    }

    class Makara__Strategies__Abstract {
    	<<abstract>>
        pool
        init()
	connection_added()
	current()
	next()
    }

    class Makara__Pool {
    	# by using Makara, we can use many replica databases
	# to manage those databases, we need to use pooling feature
	# so it is easier to manage
	# each connection that available on the pool is an instance of Makara__ConnectionWrapper
    }

    class Makara__Context {
    	# uses Ruby Thread to store the current context
	# for example, we set the current context to use primary db
	# then all of active_record connection on the current process will use primary db
    }


    class Makara__Proxy {
        # entry point of the gem
    }
```
