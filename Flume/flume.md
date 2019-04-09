#Flume
```
#Name the components on this agent
agent2.sources = mySource
agent2.sinks = mySink
agent2.channels = myChannel

# Describe/configure the source
agent2.sources.mySource.type = netcat
agent2.sources.mySource.bind= localhost
agent2.sources.mySource.port = 44444

# Describe the sink
agent2.sinks.mySink.type = logger

# Use a channel which buffers events in memory
agent2.channels.myChannel.type = memory
agent2.channels.myChannel.capacity = 1000
agent2.channels.myChannel.transactionCapacity = 100


#Bind the source and sink to the channel
agent2.sources.mySource.channels = myChannel
agent2.sinks.mySink.channel = myChannel

```
