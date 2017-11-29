---
layout: wmt/docs
side-navigation: user-navigation.html
title: Transition Best Practices
---

# Transition Best Practices

In the Transition phase, use the following best practices:

* Ensure that the design is deployed in proper clouds
* Check the organization report for available capacity
* Keep Monitoring turned on
* When creating a new environment, DO NOT Use Debug Mode. This is strictly to be used by Ops for debugging purposes.
* Configure <a href="/user/transition/configure-ecv-check-url-on-oneops.html">ECV</a> to check the LB component
* If you don't want to accidentally override design values on pull, keep variables/attributes locked in the Transition phase.
* Review <a href="/user/operation/monitors.html">monitors and their thresholds</a>, to add or edit more alerts to be suitable for your application
* Add CEN to the individual monitors in your production environment
* <a href="/user/operation/ensure-that-alerts-for-production-environment-are-sent-to-noc.html">Enable NOC alerts</a> for your production environment
* Add your own <a href="/user/transition/add-cname.html">CNAME</a> to give to your customers
* Keep watch on your environment and compute usage. If an environment is not in use,
<a href="./delete-an-environment.html">disable the environment</a>.
* Tomcat Log Files: The location of log and access log should be `/log/apache-tomcat`.

>* The computes *can not* be resized once provisioned. So, if you change the size to be different from the design, lock the attribute.
* The volume "app" size by default, is 10G (in the case of Tomcat). If needed, adjust and lock the size.
* Don't rely on the storage in the volume. It is ephemeral and only remains until the compute is there.
