# redis-bin
Redis binaries for integration tests to be used along with embedded-redis librires like 
https://github.com/ozimov/embedded-redis
or
https://github.com/kstyrc/embedded-redis (no longer maintained)

# Motivation 
Libraries mentioned above provides only old verison of the redis binaries 2.8.19. Since this is pretty outdated I have decided to release newer version of the binaries that may be used with the libraries. 

# Usage
In order to use new binaries you need to add both `embedded-redis` and `redis-bin` as dependencies to your project.

Once you do it you can create RedisServer using following code to override default binaries included in the libries. 

```
RedisExecProvider redisExecProvider = RedisExecProvider.defaultProvider();
redisExecProvider.override(OS.UNIX, "com/github/tpakula/redis-bin/redis-server-3.2.11");
redisExecProvider.override(OS.WINDOWS, "com/github/tpakula/redis-bin/redis-server-3.2.100.exe");
redisExecProvider.override(OS.MAC_OS_X, "com/github/tpakula/redis-bin/redis-server-3.2.11.app");

RedisServer redis = RedisServer.builder().redisExecProvider(redisExecProvider).build();
```

For further information about library used please refer to documentation available in: 

https://github.com/ozimov/embedded-redis/blob/master/README.md

# Versioning convention
First free digits corresponds to version of redis-server.
Least significant digit is used for library versioning. 
Therefore 3.2.11.0 corresponds to version of redis server 3.2.11.

Currently only one version has been released. 

# Maven Central
https://search.maven.org/#artifactdetails%7Ccom.github.tpakula%7Credis-bin%7C3.2.11.0%7Cjar

Maven dependency
==============

```xml
<dependency>
  <groupId>com.github.tpakula</groupId>
  <artifactId>redis-bin</artifactId>
  <version>3.2.11.0</version>
</dependency>
```
Gradle dependency
==============
```
testCompile group: 'com.github.tpakula', name: 'redis-bin', version: '3.2.11.0'
```
