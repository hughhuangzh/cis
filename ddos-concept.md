---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-25"

keywords: Attack Concepts, Application layer attacks, common types of internet attacks

subcollection: cis

---

{{site.data.keyword.attribute-definition-list}}

# Dealing with Distributed Denial of Service attacks
{: #distributed-denial-of-service-ddos-attack-concepts}

Distributed Denial of Service (DDoS) attacks are among the most common types of internet attacks that your website or host can encounter.

## What is a DDoS attack?
{: #what-is-a-ddos-attack}

A distributed denial of service (DDoS) attack is a malicious attempt to disrupt normal traffic of a server, service, or network by overwhelming the target or its surrounding infrastructure with a flood of internet traffic. DDoS attacks achieve effectiveness by utilizing many compromised computer systems as sources of attack traffic. Exploited machines can include computers and other networked resources such as IoT devices. From a high level, a DDoS attack is like a traffic jam clogging up a highway, preventing regular traffic from arriving at its destination.
{: shortdesc}

## How DDoS attacks work
{: #how-does-a-ddos-attack-work}

An attacker gains control of a network of online machines to carry out a DDoS attack. Computers and other machines (such as IoT devices) are infected with malware, turning each one into a bot (or zombie). The attacker controls the group of bots, which is called a _botnet_.

After establishing a botnet, the attacker directs the machines by sending updated instructions to each bot using remote control. A targeted IP address can receive requests from a multitude of bots, causing the targeted server or network to overflow capacity. This creates a denial-of-service to normal traffic. Because each bot is a legitimate internet device, separating the attack traffic from normal traffic can be difficult.

## Common types of DDoS attacks
{: #what-are-common-types-of-ddos-attacks}

DDoS attack vectors target varying components of a network connection. While nearly all DDoS attacks involve overwhelming a target device or network with traffic, attacks can be divided into three categories. An attacker can use one or multiple attack vectors, and might even cycle through these attack vectors based on countermeasures taken by the target.

Common types are:

* Application layer attacks (Layer 7)
* Protocol attacks (Layer 3 and Layer 4)
* Volumetric attacks (amplification attacks)

### Application layer attacks
{: #application-layer-attacks}

An application layer attack is sometimes referred to as a _Layer-7 DDoS attack_ (in reference to the 7th layer of the OSI model). The goal of these attacks is to exhaust the resources of the victim, by targeting the layer where web pages are generated on the server and delivered to the visitors in response to HTTP requests (that is, the application layer). Layer-7 attacks are challenging, because the traffic can be difficult to identify as malicious.

### Protocol attacks
{: #protocol-attacks}

Protocol attacks utilize weaknesses in Layer 3 and Layer 4 of the ISO protocol stack to render the target inaccessible. These attacks, also known as a state-exhaustion attacks, cause a service disruption by consuming all the available _state table_ capacity of web application servers, or of intermediate resources such as firewalls and load balancers.

### Volumetric attacks
{: #volumetric-attacks}

This category of attacks attempts to create congestion by consuming all available bandwidth between the target and the wider internet. Large amounts of data are sent to a target using a form of amplification, or by other means of creating massive traffic, such as requests from a botnet.

## What do I do if I’m under a DDoS attack?
{: #under-ddos-attack}

**Step 1:** Turn on “Defense mode" from the **Overview** screen.

**Step 2:** Set your DNS records for maximum security.

**Step 3:** Do not rate-limit or throttle requests from IBM {{site.data.keyword.cis_short_notm}}, we need the bandwidth to assist you with your situation.

**Step 4:** Block specific countries and visitors if necessary.
