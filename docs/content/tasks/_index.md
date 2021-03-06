+++
title = "Puppet Tasks"
pre = "<b>3. </b>"
weight = 30
+++

## Introduction

Puppet Tasks are new containers for commands, much like Choria Agents they have metadata that can describe their inputs and outputs and they are distributed using the Puppet Forge.

These can be much easier to write than Choria Agents as their metadata is very light weight and can progressively become more complex as your needs grow.  Tasks can be written using any Programming Language.

Tasks are distributed using the Puppet Forge and one can search for [all modules with tasks](https://forge.puppet.com/modules?utf-8=%E2%9C%93&sort=rank&q=&endorsements=&with_tasks=yes).

Choria provides support for tasks as a new first class agent type, accessible over the normal RPC api and provides a rich CLI.

## Benefits

Choria provides support for Puppet Tasks to the Open Source Community, it provides a strong enterprise focussed workflow with the following features:

  * Tasks are downloaded from the Puppet Server to the nodes. You have a single point of code management and it's not 100s of admins home directory
  * Does not need SSH or direct access to nodes
  * Individual Tasks are subject to Role Based Access Control using the standard Action Policy
  * Individual Task invocations are audited using the standard Choria Auditing
  * Tasks run in the background and are suitable for long running actions like system updates
  * A _mco tasks_ command that behaves like a typical mcollective utility
  * Tasks can be used from your ruby code or playbooks using the _bolt\_tasks_ agent

## Demonstration

The pages in this section will provide a thorough reference for this feature, you can also watch a video showcasing the capabilities of Puppet Tasks in Choria

<iframe width="560" height="315" src="https://www.youtube.com/embed/LLyjPjZW7TE" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## Status

At present I consider this feature a mature feature, it's functional and complete, but we do have a few key issues outstanding.

The reason this took several months to ship is because I needed to ensure we have strong input validation. Today we do have strong input validation on the client but on the
nodes we do not have it. There's a major short coming in the Puppet Server APIs in that it does not tell us what version of metadata we look at and so there are trivial
timing based problems. Until the feature I requested is implemented in Puppet Server a strong reliable server side input validation method is impossible.
