Hey Allan and Benedict,

I'm pretty new to your podcast, but I'm really enjoying it. If you don't think this question fits with the direction of your show, I totally understand skipping it.

I know FreeBSD is heavily used across the internet, but when people talk about multi-cloud and microservices, infra providers like AWS and GCP are pushing their managed Kubernetes offerings, their Docker container services, and their Linux distros. From my perspective, I need to think about how my code will run on Linux. There's no reason to consider how it'll run on BSD because I know it'll run in a Docker container, ultimately running on Linux.

I would love to see FreeBSD front and center the way Linux is right now. Is that something the BSD community wants? Do they want Docker to toggle between cgroups or jails, depending on the OS (eg: a Dockerfile containing FROM freebsd:12)? Nomad runs on FreeBSD natively, but Kubernetes needs Docker so I guess that goes back to my previous question.

After writing all of this, I think my question is... it feels like today's best practices for developing web services, distributed systems, etc. are to build for Docker ultimately building for Linux only. Can FreeBSD compete more here and is that something the community wants?

Thank you both!