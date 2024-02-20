# Configuration Management

To manage the bare metal machines upon which Kubernetes will run, configuration management software is necessary. Although a small cluster, such as the one I am working with here, could potentially get by with a parallel shell program, scaling beyond a handful of machines quickly becomes unwieldy. Based on my cursory research, cluster management was a big topic in the early to mid 2010s. Since then, the number of blog posts and help topics seems to have decreased substantially. This could be for a number of reasons, but my guess is most new application development is happening at a higher level than bare metal hosts. I.e. Kubernetes or Cloud. It is likely the shops that are running bare metal have their configuration management sorted already and new shops are starting from an existing Kubernetes or Cloud environment.

Another explanation could be that, if one chooses a popular distro such as a redhat or debian derivative, the cluster management software is quite mature and can be setup relatively quickly without much difficulty.

In the end, most of my time setting up configuration management came down to running Gentoo. Although there is nothing fundamentally limiting about running a distro that is a little off the beaten path, the set of features that support Gentoo out of the box for most config management tools is smaller than Redhat/Debian derivatives.

The cluster management software I investigated were:

1. Ansible
2. [Puppet](Puppet.md)
3. [CFEngine](CFengine.md)
4. BCFG2

In the end I only seriously considered Puppet and CFEngine, ultimately choosting CFEngine.

I initially attempted to use Puppet but found the ecosystem a bit sprawling. It is a mature piece of software so some amount of quirkiness is expected due to the amount of time it has been under development, but it became difficult to understand the various components of the tool which were each written in different languages (Ruby, Clojure etc). The installation felt very heavyweight requiring Java and Ruby installs. In addition, getting Gentoo specific components installed was difficult as the Ruby modules did not appear to be kept up to date.

On the other hand CFEngine is written in C, which, to my initial surprise, makes installation very easy. In addition, even though CFEngine is also very mature, it seems to have been able to maintain a better vision. Although the language learning curve was a bit difficult to start, the ability to create custom plugins allowed me to work around a few Gentoo specific issues I was having.


Working with CFEngine led to one of my key learnings from this project which was that C is very portable and static binaries are easy to deploy. Although this is obvious in hindsight, I came from a higher level language background (Python, Clojure (JVM) ) which are touted for their portability. However, in the real world you quickly find that these languages are also under development and your software will depend on a specific version. When moving to a new platform, with an older version of a runtime, you find your software no longer works. In the end, the overall cononclusion is not too surprising, working lower in the tech stack, you naturally have fewer dependencies and with fewer dependencies it will be easier to get all of the versions to align.


