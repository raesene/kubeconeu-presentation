<section data-background-image="images/Pirate-Intro-text.jpg" width="60%">
</section>
Note: One of the reasons for doing this research and contributing to the CIS standard was the lack of existing information on Kubernetes Security.  That said there are some good presentations to go watch https://www.youtube.com/watch?v=BER8uridVIs - Securing Kubernetes, Jesse Endahl. https://www.youtube.com/watch?v=xpFpdYtSoBw - Security Best Practices for Kubernetes Deployment - Michael Cherny

---

# About Me

 - 18 Years in IT/Information Security
 - Managing Consultant at NCC Group PLC
 - Contributor at Security Stack Exchange
 - Contributing author to the CIS Docker and Kubernetes Standards

--

<img src="/images/Loch_goil_hebridean_princess.jpg"/>

--

<img src="/images/lochgoilhead_internet_access.jpg"/>

---

# Topics

* Threat Models {% fragment %}
* Attack Surface {% fragment %}
* External Attackers {% fragment %}
* Compromised Containers {% fragment %}
* Top 10 Things to do {% fragment %}

Note:

Threat modelling/Attack Surface (put the bit about secure defaults under attack surface)
Internet focused attackers (finding interesting information on the Internet, and some examples of what we can already see as problems)
Compromised containers (mentioning the controversy around whether this is an issue or not, the increased attack surface, service tokens etc)
Top 5 recommendations of places to start looking (insecure API Server port usage, exposed kubelet without authentication, exposed etcd without authentication, cluster-admin service tokens, Privileged container usage)
Next 5 recommendations of things to do (implementing RBAC, ensuring good Authentication practice (e.g. not using client certs), implementing PodSecurityPolicy, implementing NetworkPolicy, preparing for regular upgrades (9 month support cycle) (possibly change out one of these for restricting cloud rights)
