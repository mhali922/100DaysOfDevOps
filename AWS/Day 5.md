# Elastic Load Balancer

1) Elastic Load Balancing automatically distributes your incoming traffic across multiple targets, such as EC2 instances, containers, and IP addresses,
in one or more Availability Zones. It monitors the health of its registered targets, and routes traffic only to the healthy targets.
Elastic Load Balancing scales your load balancer capacity automatically in response to changes in incoming traffic.
2) It handle the load of your application across single or multiple az.
3) Elastic Load Balancing supports the following load balancers: Application Load Balancers, Network Load Balancers, Gateway Load Balancers, and Classic Load Balancers.
4) automatically meet user's demands by sutoscaling i.e scaling in and scaling out.
5) you get a dns name that you can bind with security group.
6) monitor your applications and their performance in real time with amazon cloudwatch metrics, logging, request tracing etc.
7) you can configure stickiness. (not sure if I understand this point)

# Why you should use ec2 load balancers?
1) AWS managed
2) reduces cost
3) load balancers are intergrated with other services as well like RDS, SNS, VPC, Route 53, Amazon AMI etc.


# Types of Load Balancers:

1) Network Load Balancers(2017)
 - It works over tcp, udp and tls. Maintains ultra low latency. operates on layer 4

2) Application Load Balancers(2016)
 - load balancing of http and https traffic. For microservices and container based applications. operates on layer 7

3) Classic Load Balancers (2009)
 - AWS first loadbalancer
 - can balance http, https, tcp traffics (not at the same time)
 - It will respond with 504(timeout) if the underlying application is not responding
 - old generation not recommended.
 
 
 # Health checks in Load Balancing
 
 - uses active and passive health checks.
 ## Active
  load balancer periodically sends a request to each registered target to check its status.
 - after that it closes the connection that was made established for health check.
 ## Passive
 - Load balancer observeshow targets respond to connections.
 - enables the LB to detect unhealthy targets before it is reported unhealthy by active checks.
 - Health checks are done on url routes or ports. Expects 200 response to term it as healthy. 

<img width="561" alt="hc" src="https://user-images.githubusercontent.com/85761276/190865474-fd2cc3cc-719d-430c-ad19-3c3a33edc852.png">

## Listener
 - It is a process/rule that checks for connection requests, using the protocol and port that you have configure.


## Sticky Sessions
<img width="574" alt="sticky" src="https://user-images.githubusercontent.com/85761276/190865218-fa5c279b-4707-498a-96a1-07665c619681.png">
(image from freecodecamp)


## X-Forwarded-For(XFF) Header
<img width="582" alt="17 09 2022_21 19 15_REC" src="https://user-images.githubusercontent.com/85761276/190865337-62415aa0-7afc-402e-9438-84b60f571a06.png">

## Cross Zone LoadBalancing

<img width="547" alt="czl" src="https://user-images.githubusercontent.com/85761276/190865731-6aeb1f96-b878-4ef1-bdf8-5c0d9b3760dd.png">