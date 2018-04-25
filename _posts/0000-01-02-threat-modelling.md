<image src="/images/threat-model.jpg"/>

Note:

Threat models are very important in security.  First question in response to "Is this secure?" is "From what?".  Also very important when discussing Kubernetes security with developers or other stake holders as they may feel that a deployment is secure when they've explicitly ruled out some threat models (e.g. an attacker who can get access to a container on your platform)

--

<image src="/images/random-attacker.jpg"/>

Note:  There are a wide variety of attackers these days who might try and compromise systems.  They don't particularly care about hitting your system they're just looking for resources. Pretty much this is a fact of life when it comes to modern operation. A good illustration of this was https://blog.webernetz.net/internets-noise/ which showed over 1000 IP addresses scanning a newly stood up host in under 24 hours.  Also https://medium.com/handy-tech/analysis-of-a-kubernetes-hack-backdooring-through-kubelet-823be5c3d67c which showed an attack on a k8s cluster that was just designed to mine monero

--

<image src="/images/targeted-attack.jpg"/>

--

<image src="/images/nation-state.jpg"/>

Note:

Worth noting that even though Nation state attackers undoubtedly have access to "0-day" style exploits, they won't use them unless they have to. From https://www.cyberscoop.com/dod-apache-struts-equifax-david-hogue-nsa/ the NSA haven't seen them used in the last 24 months.