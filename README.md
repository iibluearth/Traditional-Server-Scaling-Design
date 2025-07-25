﻿# Traditional-Server-Scaling-Design Part 1
<p align="center">
<img src="https://i.imgur.com/ZLNJXB4.png">
</p>

<h2>Architecture Goals </h2>

- Load Balancer
- Web servers
- Application servers
- Database
- Caching Layers
- Storage Systems

<h2>Web Application Architecture  </h2>

Frontend (www.fenty.com)

Backend (Web Server, App Server, Object Storage, Cache, Database)
- Microservices Split (Product,Cart, Order)
- Load Balancer Layer 
- SDN + Cache hit/miss path 

Cache Layer:
- Cache hit = return data from cache
- Cache miss = fetch from Database or Object Storage, then update cache
- CDN serves static assets (images, CSS, JS) from edge locations

Scaling Section:

Vertical Scaling includes
- Upgrading CPU/RAM/Storage
- Trade-off like cost, EC2 resizing, and upgrade limitations

Horizontal Scaling includes
- Use of Auto Scaling Groups (ASGs), CloudWatch alarms, and Load Balancer 
- Awareness of session state across multiple instances 
- Scaling metrics (CPU, network I/O, request count)

<h2>Scaling Strategies </h2>

Vertical Scaling 
- Upgrade EC2 instance types 
- Pros: Simpler, fewer architectural changes 
- Cons: Costly, hard limits, single point of failure 

Horizontal Scaling 
- Use Auto Scaling Groups (ASG) for web/app servers 
- Load Balancer Routes requests
- Trigger policies via CloudWatch (CPU, I/O, requests)
- Requires session management (sticky sessions, shared cache)

<h2> When/Why Fenty might use each? </h2>

Vertical Scaling
- Simpler to implement, useful in early stages or for legacy workloads 
- But limited in scale; costly and risky (single point of failure) 

Horizontal Scaling 
- Better long-term for unpredictable traffic spikes (product droups, sales)
- Supports fault tolerance and high availability
