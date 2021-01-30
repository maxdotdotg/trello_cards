> Share with us code or describe a project that you are especially proud of and explain why you are proud of it. If you have participated in free or open source software development previously, please direct us to your contributions.

One project that I'm really proud of is migrating an application from manual provisioning to autoscaling groups with infra-as-code (in this case, using Terraform). This app had an unpredictable and bursty usage pattern, frequently needing more capacity during off-hours. An alert would fire late at night or early in the morning, waking up the on-call app engineer to provision more nodes. The new nodes would process the work and then sit mostly idle, frequently for days at a time, until they were remembered and terminated. 

This presented a few problems: first, the app wasn't able to respond to demand, causing delayed and degraded service; second, the app engineers were frequently interrupted and/or woken up off-hours, making them unhappy and less productive; third, unneeded idle nodes were staying online, costing money.

I worked with the app engineers to figure out what was driving the alerts (queue size representing units of work), maximum/minimum capacity targets, and scale-up/down patterns. Based on that, I wrote a Terraform module that would provision the app into an autoscaling group that would provision a few more nodes for every 30 minutes that the queue was over a given threshold, and would terminate them once the queue dropped below another threshold.

The service became more reliable and cost-efficient, and my team earned some good will from an app engineering team that wasn't getting woken up in the middle of the night to address capacity demands.

