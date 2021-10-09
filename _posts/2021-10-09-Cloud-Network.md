---
published: true
---
## E-mail to the CTO

Hello, I know you said you didn't want the application in the cloud due to that data can't be allowed to be transffered in the open like that. But have you heard of Azure Private Link? No? Then let me explain what it does and why I think we should use it. 

Azure Private Link provides private connectivity from ta virtual network to Azure platform as a service, customer-owned, or Microsfot partner services. It simplifies the network architecture and secures the connection between endpoints in Azure by eliminating data expsure to the public internet. All traffic to the service can be routed through the private endpoint, so no gateways, NAT devices, ExpressRoute or VPN connections, or public IP addresses are needed. 

Here is one of many key benefits described by Microsft themselves: **Protection against data leakage**: A private endpoint is mapped to an instance of a PaaS resource instead of the entire service. Consumers can only connect to the specific resource. Access to any other resource in the service is blocked. This mechanism provides protection against data leakage risks.

This is not locally either, it has global reach. We can connect privately to services running in other regions which could **increase our productivity** by a lot. 

If we were to do this we would then be able to use Azure Service Bus which is a fully managed enterprise message broker with message queues and publish-subscribe topics. The benefits of this would be load-balancing work across competing workers, safely routing and trasnferring data and control across service and application boundaries and finally, coordinating transactional work that requires a high degree of reliability. 

Also, the private link service itself is free, what we'd pay for is the end point, 0,088kr per hour, processed data is also 0,088kr per GB. We could atleast try it out and see how it works.  

I remember when you and I had a drink a couple of years ago, you talked about how easy worklife would be if we had a simpler way of handling our internal network. Well, here it is!  

If you have any further questions about this I'd gladly explain it to you in more detail!
