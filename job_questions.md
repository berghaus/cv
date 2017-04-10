Job Related Questions
=====================

How have you been working with Linux? Please provide details of a project you have worked on.
---------------------------------------------------------------------------------------------

I have used Linux systems both at home and at work, as user and as administrator. At home I have been using various flavors of Linux since late in 1997\. At work and school I have been using Linux since the later part of my undergraduate experience in ~2001.

My professional experience with administrating Linux systems comes from the work with the HEP Research Computing group at the University of Victoria. Two related projects which run we operate on CentOS or Scientific Linux platforms are: cloud scheduler and DynaFed. Let me focus on cloud scheduler since it is the more mature system at this moment. Cloud scheduler is a service written in python which monitors a batch queue and manages Virtual Machine instance on IaaS cloud services in response to load on the batch queue. We chose HTCondor as the batch system, since it easily adapts to work with ephemeral worker nodes. The cloud services expose a variety of APIs and are distributed globally. The worker nodes were originally custom build Linux Virtual Machines, configured as KVM or Xen guests depending on the cloud infrastructure. Later we adopted CernVM. Further contextualization of the virtual machines is applied using cloud-init scripts. This system was running as a production site for the ATLAS and Belle II experiments. As such there were some other complimentary services, the necessary plugins for ATLAS's Panda and Belle II's DIRAC workload management system, the proxy squid servers for distributed, caching HTTP-based file system CVMFS employed by both experiments, the monitoring system and the accounting system. All of these services were run on Linux virtual machines managed using first chef and then Ansible at the University of Victoria and Puppet at CERN.

Can you describe your knowledge and experiences with virtualization and clouds such as KVM and OpenStack?
---------------------------------------------------------------------------------------------------------

Since this question and the next are closely related for the cloud scheduler system I operated I will focus here on the operation of the system, and the dig into configuration details during the next question. 

After finishing my PhD in February 2013, I joined the research computing group at UVic. The group focus on developing and operating tools to allow scientific workloads on cloud infrastructure. When I started, they had already developed the cloud scheduler and were operating it with a few hundred cores on a collection of Nimbus clouds. Between 2013 and 2015 we switched to using OpenStack clouds, Amazon's EC2, and Google's GCE. As an expert with the experiment software I was tasked to create VM worker nodes that could run ATLAS and Belle II tasks. Initially I built Virtual Machines for KVM and Xen hypervisors based on Scientific Linux (5 and 6) using libvirt and the qemu tools. The difference between the two images was the configuration of the grub boot-loader.

Have you already dealt with the management of clusters and other large distributed systems? Describe the approach you took for installation, configuration and monitoring.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The cloud scheduler system I operated operates up to 10,000 cores distributed around ~30 clouds in North America, Europe and Australia for the ATLAS and Belle II experiments. The systems require both permanent services such as the cloud scheduler, the HTCondor system, proxy squid caches, or the dynamic data federator and ephemeral worker nodes. Both permanent and ephemeral systems exist on Virtual Machine instances of appropriate flavor in some IaaS cloud. The permanent systems were managed with Puppet at CERN and first via Chef and later Ansible at the University of Victoria. The ephemeral nodes used first custom VM images and later the CernVM micro VM image. Further contextualization was added using a mime-formatted block delivering configuration instructions - some specific to CernVM some steering cloud-init plugins via yaml. Due to size limitations on the configuration instructions those blocks were compressed. The idea is that permanent systems would need to pick up updates continuously while ephemeral VMs would boot with the most recent configuration and old VMs would eventually be discarded. Furthermore, the ephemeral VMs only held short lived secrets with very limited access privileges. 

The monitoring philosophy is also split between the long-lived and short-lived nodes: scripts on the permanent nodes pushed information to Elasticsearch (for logs via Logstash). The information which operational experience had shown to be useful was displayed in the monitoring user interface. The ephemeral nodes were configured to run ganglia's gmond and report to a central (long running) ganlgia service, different worker node configurations (ATLAS vs Belle, user analysis vs central production, etc.) report to different ganglia monitors and ports on that ganglia instance. This allows us to resolve easily between individual configurations. Further resolution is provided by the hostnames - which contains a UUID for the ephemeral nodes.

A user is reporting a performance problem with an application. What would be your steps to understand the situation and address it?
-----------------------------------------------------------------------------------------------------------------------------------

First, ensure that I clearly understand what the problem is. Next, take a look at the monitoring to see if anything related shows up. If so drill down from there. If not try to reproduce the problem the user is experiencing, requiring help from the user as the situation demands. Once I understand, and addressed what went wrong include the related information in the monitoring system, such that we can more quickly detect such issues in the future. Follow up with the caller to ensure they are happy with the system's function after the fix.

As further steps in the future, where possible write a script to alert me of such problems in the future. Depending on the complexity of the problem write a wiki entry describing what the problem was, how the solution was found, and how to identify the behavior in the monitoring in the future.

Motivation for Applying to this Job
===================================

With the LHC, CERN is the world leader in particle physics. As a computing expert with a background in particle physics, I feel very connected to the research environment at CERN. I value my continued involvement and contributions the experimental programme at CERN.

As a fellow I became to know CERN as a great place to learn and expand my expertise. I like the promise of professional development that CERN offers.

The working environment in a scientific or academic institution is very open to new questions and ideas. I find it a pleasure to work with people who are genuinely interested in new ideas, even if they may lead nowhere.

After two and a half years in Geneva I have come to very much enjoy living here. Given my experitise and interests, CERN is the ideal employer for me.