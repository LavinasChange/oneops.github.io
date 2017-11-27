---
layout: wmt/docs
side-navigation: dev-navigation.html
title: Content Development Introduction
---

# Content Development Introduction

Use this section to set up your environment for OneOps pack (circuits)/cookbook development on a Mac OS X or a
Linux system and to create a new component (cookbook) with its accompanying pack.

## Prerequisite

For both API and Circuit development you need access to a running OneOps deployment. To build your own deployment,
start with the <a href="/admin/installation.html">Installation</a> section.

## Circuit Developer

For Circuit development, follow the instructions below.

## Installation

Installation of OneOps is described in the
[administration section](/admin/installation.html).

## Setup and Configuration

### Development

The easiest way to start is to copy an existing cookbook and pack (for example, Tomcat) and develop on that. To do
it from scratch, follow the procedure described below:

1. Select the circuit repo.
2. To create a new component (cookbook), use the knife command.

### Create a Cookbook

1. To create a cookbook, enter the following:

## Change to repo

```
$ cd circuit-oneops-1
```

## Create new component called "mycomp"

```
$ bundle exec knife cookbook create mycomp
** Creating cookbook mycomp
** Creating README for cookbook: mycomp
** Creating CHANGELOG for cookbook: mycomp
** Creating metadata for cookbook: mycomp
```

## Start defining the attributes

```
$ vi components/cookbooks/mycomp/metadata.rb
```

3. Develop the recipes for your component (for example, `add`, `delete`, `update`, `replace`, `repair` lifecycle actions).
4. After you complete the cookbook design, create the pack under the `/packs` directory.
5. Define its resources (components) and relationship between them. For more details, refer to an existing pack
   (for example, Tomcat).

### Create a Pack

To create a pack, follow these steps:

```
$ cd circuit-oneops-1/packs
$ cp tomcat.rb mypack.rb
$ vi mypack.rb
```

As in the case of chef recipes, a OneOps pack is also defined using a custom Ruby DSL with syntax like variable,
resource, relation, etc. Because the Pack DSL is a Ruby DSL, anything that can be done using Ruby can also be done
in a Pack, including if and case statements, using the include? Ruby method, etc.
For detailed information on how to develop a pack, see [Add a Platform](/developer/content-development/add-a-platform.html).

### Create a Circuit

To create a circuit, refer to:

* [Add a New Component](/developer/content-development/add-a-new-component.html)

## Confirming it Works

### Testing

> This section is useful if you are using a shared dev instance in your organization .

Before you start the testing, make sure you have access to your OneOps dev instance and have added your SSH keys
to the Inductor.

```
# Sync the metadata and packs.
# This is only required if there are any changes in the metadata or pack:
# Pack sync commands.
cd circuit-oneops-1/
```

## Export the OneOps CMS API.

```
export CMSAPI=http://<your OneOps instance>:8080/
```

## Sync the mycomp metadata.

```
bundle exec knife model sync mycomp
```

## Sync mypack

```
bundle exec knife pack sync packs/mypack --reload
```

## Clear the Cache

```
curl http://<your OneOps instance>:8080/transistor/rest/cache/md/clear
```

## Select the Repo.

```
cd circuit-oneops-1
```

## Copy the Cookbook to the Corresponding Repo in the Inductor (/opt/oneops)

```
scp -r components/cookbooks/mycomp ooadmin@<your OneOps instance inductor>:/opt/oneops/circuit-oneops-1/current/components/cookbooks/
```

## Copy the Pack File to the Corresponding Repo in the Inductor (/opt/oneops)

```
 scp packs/mypack.rb ooadmin@<your OneOps instance inductor>:/opt/oneops/circuit-oneops-1/current/packs/
```

## Add an icon image for the pack

* Component Icon : **128x128 PNG** graphic - Add to circuit-oneops-1/components/cookbooks/<mycomp>/doc (ex. apache_cassandra)
* Pack(Platform) Icon : **128x128 PNG** graphic - Add to circuit-oneops-1/packs/doc/
* see https://github.com/oneops/circuit-oneops-1/tree/master/packs/doc

## Testing via GUI

1. Create a new *Assembly* and **environment**.
2. Now you are ready to test the pack by creating a new assembly and env in `https://<your OneOps instance inductor>/`.
    >Do not store any of your source code in oneops/inductor dev env. This env is upgraded every Wednesday as part of the regular OneOps release cycle.
3. Create a pull request.
     After you make sure that everything is working fine in the dev env, commit the code and create a pull request from your forked repo.
