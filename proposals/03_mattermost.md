# Software Underground x Mattermost

Slack is becoming expensive and Software Underground will move off it. This has
the added benefit of putting more power into the community's hands by
permitting free software clients and a higher degree of trust to the operator.

This document proposes some operating principals and cost estimates for the new
Software Underground Mattermost (instant chat) service.

# Server

To start with, I propose a single, cheap Hetzner server. Hetzner's data
centres are mostly in Europe (mostly Germany and Finland) and are quite
cost effective. By going for a dedicated instance we should not experience much
jitter due shared tenants workloads which should keep the operation smooth.
Until we understand the load, I also propose that all major components (front,
mattermost, database) run on the same host. This is a lot simpler to set up and
manage, and is likely to serve us well for a long time at the cost of a minor
risk for downtime if components should fail.

# Reliability and backups

Reliability and uptime should be achieved through a mix of a few different
factors:

## Frequent backups

The database should be backed up frequently to a remote storage solution, so
that restoring service should be possible at the speed of database restore.
Backups will be performed and test-restored frequently and automatically to
reduce the risk for operator negligence. This will consume some extra disk
space, but we probably only need to maintain the past few copies.

## Multiple maintainers

The main maintainer would be Jørgen Kvalsvik. At the time of writing there are
two more volunteers, ... Having multiple operators reduces the risk of
prolonged downtime due to timezone and availability issues.

## Automation

Setting up a new instance should be automated so that migrating the service to
a new host is doable with minimal human interaction. This would also serve as
documentation on how the service itself is configured. For the most part,
automation and configuration should be version controlled.

# Service

Software Underground has an extensive message archive from the Slack instance.
A copy of this archive can be served from the same server as mattermost.

Access to the server should be strict ssh key authentication, and the
mattermost should only be reachable through encrypted means. Let's encrypt is a
powerful and ready solution for this, and the renewal of the certificates
should be automated.

# Payment and cost

The hosting bill will be paid for directly by Software Underground, and the
maintainers will be given sufficient access to the instance and control panel
for the host.

The main operator will invoice Software Underground for support and services,
at these rates:

| Event                 | Rate (USD)    |
|-----------------------|---------------|
| Initial setup         | $500          |
| Monthly maintainance  | $50           |
| Large migrations      | $100          |
| Calamity              | $500          |

Large migrations includes events like significant changes in host operating
environment (incompatible OS, incompatible database etc.) that means updating
larger swaths of code, configuration.

Calamity includes unforseen large scale problems which essentially means large
recovery jobs or rearchitecting, like redesign to a multi-server setup, and is
meant to account for what is essentially a new initial setup or multiple days
of work.

After the initial setup, I _expect_, but do not _guarantee_, that large-scale
migrations should only happen possibly annually, more likely every other year,
and calamity maybe once in the services lifetime. This brings the expected
yearly cost post-init to USD 6-700, plus a Hetzner bill of some EUR
15-20/month for a total of approx USD 1000 year.

I also propose a yearly re-negotiation of both rates and maintainers. This
should account both for increased cost and poor estimates in maintainance load.
