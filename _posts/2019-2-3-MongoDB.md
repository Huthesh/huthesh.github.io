---
title: MongoDB Part I
layout: default
description: huthesh.github.io
---
<div>
        {{ page.date | date: "%-d %B %Y" }}
</div>
<br>
<br>
This part will explain installing MongoDB and connecting to the instance through CLI
## Install on MAC using Homebrew

Run following commands in sequence. Before running these commands make sure that Homebrew is already installed.

```
$brew update
$brew install mongodb
```

## Run Mongo Daemon 

1  <b>Create Data directory</b> 

```
$mkdir -p /data/db
```

2  <b>Run Mongod</b>

```
$mongod --dbpath <path to data directory>
```

By Default mongod uses ./data/db as data directory. We can specify any other location through "dbpath" argument
```
ex. $mongod --dbpath ./mongo/data/db/ 
```
<div class="alert alert-warning" role="alert">
  User account should have the read/write permission on data directory
</div>

## IP address

mongod runs on "localhost" by  default. If you want mongod to use specific IP on host then use "bind_ip" argument. In the following example mongod will be listening on "192.168.0.5". Any host in the subnet will be able to access this mongo instance.

```
$mongod --dbpath ./mongo/data/db/ --bind_ip 192.168.0.5
```
<div class="alert alert-warning" role="alert">
  <b>--bind_ip_all</b> will bind to all Network Interface available on host 
</div>

## Change port

MongoDB by defaut uses port 27017. We can change the port by <b>--port</b> option
```
$mongod --port 27018
```
## Configuration file

Mongod can also accept the config from a file specified in YAML format

```
$mongod --config /etc/mongod.conf
```

<div class="alert alert-primary" role="alert">
On Linux, a default <b>/etc/mongod.conf</b> configuration file is included when using a package manager to install MongoDB.
</div>

<div class="alert alert-success" role="alert">
On Windows, a default <b>&lt;install directory&gt;/bin/mongod.cfg</b> configuration file is included during the installation.
</div>

<div class="alert alert-warning" role="alert">
  On macOS, the installation does not include a default configuration file; instead, create a file and specify the location in the command
</div>

Following config will change the bind IP and Port
<pre>
    net:
        bindIp: 192.168.0.5
        port: 27018
</pre>

[More on external config file](https://docs.mongodb.com/manual/reference/configuration-options/)

## Connect to DB

We can connect to mongo instance by using CLI "mongo".  By default "mongo" CLI will connect to "localhost" port "27017"
```
$mongo
```
To connect to mongo instance running at specific IP and port, we should specify the Connection URL 
```
$mongo mongodb://192.168.0.5:27018
```
## Validate connection
On connecting to db you should see following console log
<pre>
MONGO:~ huthesh$ mongo
MongoDB shell version v4.0.3
connecting to: mongodb://127.0.0.1:27017
Implicit session: session { "id" : UUID("*****-****-****-****-*************") }
MongoDB server version: 4.0.3
>
</pre>
Enter  command "db", this will return "test"
```
>db 
test
```