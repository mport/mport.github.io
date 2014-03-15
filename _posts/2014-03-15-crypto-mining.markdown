--- 
layout: post 
title:  "Building a Cryptocurrency Mining Rig" 
date:   2014-03-14 00:07:00
categories:
    - Cryptocurrency
    - Mining Rig
---

Cryptocurrencies such as Bitcoin, Litecoin and Dogecoin are popping all over
the news these days. With the ever-growing investment and market capitalization, 
it is clear that cryptocurrencies are here to stay. Even during this seemingly 
nascent stage in their evolution, cryptocurrencies are already having a 
profound impact on the "real-world"; whether for good, as in the case of
philanthropic Dogecoin's community; the bad, such as the downfall of Mt.Gox and 
450 million dollar loss of its customers' money; and the ugly, like money 
laundering and criminal activity facilitation.

So to say the least, cryptocurrency is something new and exciting, which
I wanted to understand better and experience first-hand. A mining-rig
was in order.

For the rig, I've used similar specs as described on:

[Building A Nice Dogecoin Mining Rig For Just 1000 Dollars](http://www.minedogecoin.com/building-a-nice-dogecoin-mining-rig-for-1000-dollars)

**What I Mine**

Any *scrypt* coins since GPU mining is still viable for these. I originally got
into mining Dogecoin, but moved to mining in a multipool since. I would say Dogecoin
is still my preferred coin due its vibrant community, growth potential, and capitalization.

*To the moon!*

**Hardware Specs**

|                     |                 |
|:--------------------|:--------------- |
| *Motherboard*       | ` ASUS M5A97 R2.0` |
| *CPU*               | ` AMD Sempron 145` |
| *Hard Drive*        | ` 32 GB SATA III Internal Solid State Drive` |
| *Memory*            | ` Kingston Hyper X Blu 4 GB 1600MHz DDR3 Non-ECC CL9 Desktop Memory` |
| *3 x Video Cards*   | ` Sapphire Vapour-X R9 280X OC Edition` |
| *Power Supply*      | ` Seasonic 80 Plus Platinum 1000W` |
| *Riser Cables*      | ` 2x PCI-E Express 16x (non-powered) and 1x PCI-E 1X to 16X (powered)` |


Additionally, I've tired using a couple of different wireless network cards, but the connections
were intermittent, which affected the overall hash-rate.

**Glorious Rig**

<img src="{{site.url}}/assets/images/2014-03-15-crypto-mining/rig.png" style="width: 100%;" alt="Mining Rig">

**cgminer 3.7.2 config**

The following is my cgminer config. I'm pretty sure I'm squeezing the most out of the GPUs
with this config. The cards run HOT, sometimes pushing over 90℃, so additional heat removal 
may be required. 

```
"pools" : [
        {
                "url" : "stratum+tcp://mp.ultimatecoinpool.com:6000",
                "user" : "myuser.worker1",
                "pass" : "mypass"
        },
        {
                "url" : "stratum+tcp://mp.ultimatecoinpool.com:8080",
                "user" : "myuser.worker2",
                "pass" : "mypass"
        }
],

"intensity" : "13",
"vectors" : "1",
"worksize" : "256",
"kernel" : "scrypt",
"lookup-gap" : "2",
"thread-concurrency" : "0",
"shaders" : "2048",
"gpu-engine" : "1080-1080",
"gpu-fan" : "0-100",
"gpu-memclock" : "1500",
"gpu-memdiff" : "0",
"gpu-powertune" : "0",
"gpu-vddc" : "1.200",
"temp-cutoff" : "90",
"temp-overheat" : "80",
"temp-target" : "70",
"api-mcast-port" : "4028",
"api-port" : "4028",
"api-listen" : true,
"auto-fan" : true,
"expiry" : "120",
"expiry-lp" : "3600",
"gpu-dyninterval" : "7",
"gpu-platform" : "0",
"gpu-threads" : "2",
"log" : "5",
"no-pool-disable" : true,
"no-show-processors" : true,
"no-show-procs" : true,
"no-unicode" : true,
"queue" : "3",
"scan-time" : "60",
"scrypt" : true,
"skip-security-checks" : "0",
"submit-stale" : true,
"temp-hysteresis" : "3",
"shares" : "0",
"kernel-path" : "/usr/local/bin"

```

**Hash Rate**

<img alt="Hash Rate" src="{{site.url}}/assets/images/2014-03-15-crypto-mining/hash_rate.png" style="width: 100%;">


**Tips**

- Be careful with un-powered riser cables, especially 1x, as your mobo could potentially fry.
- Multipools, such as [ultimatecoinpool.com](http://ultimatecoinpool.com) will mine the most profitable coin at the time,
  hence maximizing your profit.
- Encrypt and backup your wallet!
- Lots of info on [reddit](http://reddit.com/r/cryptocurrency)
