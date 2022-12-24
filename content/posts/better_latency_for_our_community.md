---
title: "Better Latency for Our Community"
date: 2022-12-24T12:52:06+01:00
# bookComments: false
# bookSearchExclude: false
---

Since we experience a lot of user activity from the US, we decided to improve the loading times for our users in the US. We considered setting up a new server in the US, but we decided against it for now because the situation in the US is not stable enough for us to keep user data there. Additionally, the legal implications of having a server there are also a big concern.

Instead, we decided to move our server to another datacenter located in Germany that has significantly better peering with the US. There were two datacenters that we considered, one in Nürnberg and one in Falkenstein, both run by Hetzner.

We've decided to move the server to Nürnberg in the coming days because it has better peering with the US, the rest of Europe and Asia than Falkenstein.

In the following Table, you can see the latency to the US from the different datacenters:

| Datacenter  | Latency to NY | Latency to SF | Latency to Ohio |
| ----------- | ------------- | ------------- | --------------- |
| Nürnberg    | 166ms         | 324ms         | 197ms           |
| Falkenstein | 198ms         | 336ms         | 202ms           |
| Sweden      | 209ms         | 341ms         | 234ms           |
| Ashburn     | 16ms          | 152ms         | 27ms            |
| ----------- | -----------   | -----------   | -----------     |
| Difference  | between       | Sweden and    | Nürnberg        |
|             | -43ms         | -17ms         | -37ms           |


## Methodology for the latency measurements:

We created four servers with nginx running on Hetzner Cloud and measured the latency with the Grafana Cloud Synthetic Monitoring service. We used the "HTTP" checks without SSL and with a 10-second interval over a period of 3 hours to get a good average.

### Note
Please note that the latency is higher for the first connection in real life since the SSL handshake needs to be done before the first data request can be sent. After that, the latencies should be similar to real life, especially with HTTP2 that can reuse the SSL connection for multiple requests.

## Latency measurement graphs

Latency from Falkenstein 
![Falkenstein latency](/better_latency_for_our_community/falk.png)

Latency from Nürnberg
![Nürnberg latency](/better_latency_for_our_community/nuern.png)

Latency from Sweden
![Sweden latency](/better_latency_for_our_community/sweden.png)

Latency from Ashburn
![Ashburn latency](/better_latency_for_our_community/ash.png)