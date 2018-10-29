---
layout: wmt/docs
side-navigation: user-navigation.html
title: Variables Override Prevention
id: avoid-override-variables
---

# Override Prevention

Variables and configuration parameters can be edited any time in the design or transition phase. A <a href="/user/design/add-a-variable.html">new variable</a> can only be added in design and then can be pulled into the environment
On design pull, any variable which were edited in environment (transition phase) are overridden by design values.

To prevent any accidental transitional updates, a __locking feature__ is available in the Transition phases.

## Solution

The following are steps to retain transitional values:


1. Edit the component or variable to be retained in the Transition phase.
2. Click the **unlock** icon.

    ![Unlock](/assets/docs/local/images/unlock.png)

    The lock icon changes to locked.

    ![Lock](/assets/docs/local/images/lock.png)

3. Save your changes.
4. Commit and deploy.
