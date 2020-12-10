---
title: "Read this week: 7th-11th December 2020"
categories:
  - Blog
  - Reading
tags:
  - AWS
  - Python
  - Docker
  - Cache
---

# Background

List of what I've read in the last week with a quick summary on what I've learnt. This is largely used as a diary for me, so that I can go back over articles I find interesting. It also helps me memorise and take in what I am reading by writing about it.

# What I've read:

## 1. [All the new AWS announcements](https://aws.amazon.com/about-aws/whats-new/2020/)


## 2. [Raising Custom Exception Classes in Python](https://towardsdatascience.com/how-to-define-custom-exception-classes-in-python-bfa346629bca)

I find that most people have a pretty good understanding of the basics of python - it's a very readable language and very quick and easy to pick up. Perfect for beginners. But plenty of people don't have the skills in place to produce a robust application that can be relied on in production scenarios, especially if high availability is essential. Skills such as coherent logging and custom errors is such an important skill.

## 3. [You Don’t Have to Use Docker Anymore](https://towardsdatascience.com/its-time-to-say-goodbye-to-docker-5cfec8eff833)

I was wary of this article as it sounds a little clickbait-y however it proposes the following readhat alternatives:

- An alternative to the Docker container engine is [podman](https://podman.io/), which doesn't need a daemon to run or root privileges. It can also run pods rather than just individual containers which helps bridge the gap with kubernetes
- An alternative to building containers is [buildah](https://buildah.io/)

## 4. [Distributed Cache Design](https://medium.com/rtkal/distributed-cache-design-348cbe334df1)

Whilst it's fairly obvious the reasons why a distributed cache is useful i.e. for scalability, high available and fault-tolerance. This article gives a good reminder of difference cache procedures:
- Read-through - The data is written into the cache and the corresponding database at the same time, ensuring consistency between the two whilst sacrificing latency (every write done twice).
- Write-Through - Data written directly to database, this results in higher latency but ensures no data loss. If a read occurs before data is written to cache there will be a cache miss
- Write-Back - Data is written directly to the cache then persisted to permanent storage afterwards. This results in lower latency however can result in data loss if cache fails before data is persisted.

Whilst I was only familiar with Redis and Memcached it also mentions the following other popular caches: Eh-cache, Riak, Hazelcast.

