
## Swan

[![Build Status](https://travis-ci.org/Dataman-Cloud/swan.svg?branch=master)](https://travis-ci.org/Dataman-Cloud/swan)
[![codecov](https://codecov.io/gh/Dataman-Cloud/swan/branch/master/graph/badge.svg)](https://codecov.io/gh/Dataman-Cloud/swan)
[![Go Report Card](https://goreportcard.com/badge/github.com/Dataman-Cloud/swan)](https://goreportcard.com/report/github.com/Dataman-Cloud/swan)
[![Join the chat at https://gitter.im/Dataman-Cloud/swan](https://badges.gitter.im/Dataman-Cloud/swan.svg)](https://gitter.im/Dataman-Cloud/swan?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

![Swan](img/swan.png)

#### swan is a mesos scheduling framework written in golang based on mesos new HTTP API.

#### you can use swan to deployment application on mesos cluster, and manage the entire lifecycle of the application. you can do rolling-update with new version, you can scale application, and you can do health check for your applications and auto failover when applications or services are not available.

#### swan is maintained by [dataman-cloud](https://github.com/Dataman-Cloud), and  licensed under the Apache License, Version 2.0. 

## Features
+ Application deployment
+ Application scaling
+ Rolling update
+ Version rollback
+ Health check
+ Auto failover

## Special features
+ The instance name is fixed during the application lifecycle. 
+ The instance index is continuously incremented from zero.

## Installation 
  ```
  git clone https://github.com/Dataman-Cloud/swan.git

  cd swan

  make

  ./swan --masters=192.168.1.50:5050 
  ```
## Getting Started
### swan has no ui, no command-line client at this time. you can use it with `curl`.

+ applicaiton deloyment

  `
  curl -X POST -H "Content-Type: application/json" -d@example.json http://localhost:9999/v1/apps
  `
+ application delete

  `
  curl -X DELETE http://localhost:9999/v1/apps/nginx0003
  `
+ application show

  `
  curl http://localhost:9999/v1/apps/nginx0003
  `
+ applications list

  `
  curl http://localhost:9999/v1/apps
  `
+ application scaling

  `
  curl -X POST http://localhost:9999/v1/apps/nginx0003/scale?instances=10
  `
  
  instances is used to specified the instances count you wanna scale to.
  
+ application rolling update

  `
  curl -X POST -H "Content-Type: application/json" -d@new_verison.json http://localhost:9999/v1/apps/nginx0003/update\?instances\=-1
  `
  
  instances -1 means updating all instances. other value means updating the specified instances at one time.
  
+ application versions
  
  `
  curl http://localhost:9999/v1/apps/nginx0003/versions
  `

## Contributing
If you want to contribute to swan, make a PR or report a issue.

## Licensing
Swan is licensed under the Apache License, Version 2.0. See 
[LICENSE](https://github.com/Dataman-Cloud/swan/blob/master/LICENSE) for the full
license text.
