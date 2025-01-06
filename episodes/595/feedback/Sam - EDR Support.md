Sam - EDR support for the BSDs

Dear Benedict, Jason, JT, and Tom,

My workgroup has until recently enjoyed the autonomy to run the OS
that best fits our needs. In our case, that's FreeBSD. Unfortunately,
we've had to migrate to Linux due to a company-wide mandate for all
systems to run an endpoint detection & response (EDR) agent. There
were a lot of reasons for this decision, but there's one in particular
I want to raise awareness about among companies running BSDs:
third-party requirements.

Third-parties (regulators, insurers, customers, etc.) want to see that
you're using best-in-class security controls. To satisfy their
check-boxes, EDR became a mandate for our company, and since none of
the big EDR vendors support FreeBSD, corporate told us we had to get
off of FreeBSD. If just one third party with enough impact on your
bottom line says "we're not renewing with you this year unless you
have EDR on all of your endpoints", it can put an end to your BSD
deployment.

The only tools similar to a commercial EDR solution for the BSDs seem
to be OSSEC, and its modern, maintained descendant Wazuh. OSSEC is
insufficient for the modern EDR use case: its malware detection
features are weak, it needs a lot of tuning, and isn't actively
developed. Wazuh has promise, but while the company offers support for
the deployment you run yourself, they don't seem to offer MSSP
services. Having our systems monitored 24/7 by our EDR vendor was a
requirement.

Do you know of anyone lobbying Wazuh to better support BSDs, and
provide 24/7 monitoring? It wouldn't have helped us, since our company
wouldn't want multiple EDR vendors, but it would be an option for
companies more invested in deploying BSDs. Are you aware of any
companies offering MSSP services who will monitor customers' Wazuh
deployments? Is this something Klara Systems has considered offering?
Do you know of any alternatives to Wazuh? We can scoff all we like
about how EDR increases attack surface, makes a troubleshooting
nuisance of itself, causes global outages, or mainly satisfies suits
with clipboards, but companies using BSDs may find themselves forced
onto other platforms if they don't start asking for an EDR solution
soon.

Thank you for taking my questions and being a great resource for us all.

--Sam.
