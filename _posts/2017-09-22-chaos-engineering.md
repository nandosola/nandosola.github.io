---
layout: post
title: "Madrid Devops 09/2017: Chaos Engineering with Adrian Cockroft"
author: "Nando"
---

Below are the notes I took during [the event](https://www.meetup.com/es-ES/madrid-devops/events/243278934/). The talk was pretty good. Full of details and interesting facts about this *new practice* of Chaos Engineering, born from the experiences at Netflix. The presentation material was still a WIP, only a couple of weeks old. Which means that we were honored to be among the first humans who watched it.

![placeholder](https://farm5.staticflickr.com/4482/23542909928_29671ec2b5_c.jpg "@adrianco en el barrio")

## Datacenter to cloud at Netflix
- Percentage-based a/b testing, by customer id
- Find a path: Oracle ~> Cassandra ~> DynamoDB
- Remote replication instead of SSD mirroring can be more resilient.
- Your infrastructure vs. a simian army:
  - Chaos gorilla: kill a whole region every month
  - Chaos Kong: divert traffic to a different region every month
  - [Blog post](https://medium.com/netflix-techblog/the-netflix-simian-army-16e57fbab116)
- Chaos engineering team: work a cloud-native availability model
  - No SPOF!
  - AWS has no shared resources inbetween regions
- Regional level of stickiness per account
- Reroute/switch customers on outages and back
- Errors are the least well tested parts of your application
- Applications: error returns, slow responses, network partitions
- Test to fail
- Microservices minimize permutations for testing 
- When applications behave inconsistently, people break them

![placeholder](https://farm5.staticflickr.com/4443/37138065470_4dd3dfed45_c.jpg "slide")

- Fire drill for IT ~> be on an incident call (Slack, PD, statuspage)
- Release your tools as FLOSS
  - Amazon is building an open source program, based on [NetflixOSS](https://netflix.github.io)

## Chaos Engineering at Netflix
- Derived from the experiences above

![placeholder](https://farm5.staticflickr.com/4383/37138065520_a04b607ea8_c.jpg "slide")
![placeholder](https://farm5.staticflickr.com/4511/36724852673_3208d1075a_c.jpg "slide")

- [Failure injection testing](https://medium.com/netflix-techblog/fit-failure-injection-testing-35d8e2a9bb2) (FIT)
- Gremlin: Network-level failure (block ports, …)
- Red teams: Chaos Engineering team
- Blue team: SRE team

![placeholder](https://farm5.staticflickr.com/4423/36724852663_b62f407015_c.jpg "slide")

- Break it to make it better
- Chaos manifestos:
  - [Principles Of Chaos](http://principlesofchaos.org)
  - [The Discipline Of Chaos Engineering](https://blog.gremlininc.com/the-discipline-of-chaos-engineering-e39d2383c459)
- Measure the 99.9% availability through all four layers 
- The weakest link is the people
- O’Reilly ops free ebooks
  - [Main site](http://www.oreilly.com/webops/free/) with lots of references
  - [Chaos Engineering](http://www.oreilly.com/webops-perf/free/chaos-engineering.csp)

![placeholder](https://farm5.staticflickr.com/4392/23542909878_942804f765_c.jpg "slide")

## Q&A
- Existing projects will break
- Fight the existing Entropy before you can fight Chaos
- Greenfield projects: start with *chaos monkey*, *chaos failover* and more tools.
- The app goes to production if it passes the failover: extreme QA
- Apps: no persistence: only retry policies and HA caches (state is its own layer)
- Pain points
  - What people are used to (*usaurios*)
  - You can’t really work out the [CAP theorem](https://en.m.wikipedia.org/wiki/CAP_theorem) ([revisited](http://robertgreiner.com/2014/08/cap-theorem-revisited/))
- Garbage collection === Network outage
- [“The Network Is Reliable”](http://www.bailis.org/papers/partitions-queue2014.pdf) paper
- Michael Nygard's book: [“Release it”](https://pragprog.com/book/mnee/release-it)
- Performance team relocates engineers/work to fix inefficient parts of the system
- SRE teams measure availability and rapid response to incidents
- Chaos mitigation: graceful failure absorption and capacity failure
- This is really an old concept: [“Improve the security of your system by breaking into it”](http://www.porcupine.org/satan/admin-guide-to-cracking.html)

![placeholder](https://farm5.staticflickr.com/4510/37138065560_0f0c6ba51e_c.jpg "slide")

> Follow [@MadridDevops](https://twitter.com/MadridDevops) on Twitter

