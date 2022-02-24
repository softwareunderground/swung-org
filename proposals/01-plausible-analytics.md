# Proposal: Plausible Analytics account for OSS projects

Authors:
* Leonardo Uieda

## Description

The proposal is for the Software Underground to fund the website analytics for
several different projects under their umbrella (websites and docs for SimPEG,
Fatiando, emsig, etc), including the main softwareunderground.org website.

These analytics provides an important metric for determining OSS project usage,
which is notoriously hard to quantify. It's a sign of engagement and interest
in a project and can provide evidence of an existing user-base. All of this is
crucial information when applying for funding and support.

### Context

We've recently completed a migration from Google Analytics to
[Plausible](https://plausible.io/) across all
[Fatiando a Terra](https://www.fatiando.org/) websites
(the main project website and all documentation pages).
This particularly
timely given this recent ruling against Google Analytics in Europe:
https://tutanota.com/blog/posts/google-analytics/

We've made the analytics dashboard public so anyone can have a look here:
https://plausible.io/fatiando.org

Plausible has no tracking cookies (so doesn't need the annoying GDPR banners)
and doesn't identify visitors.
But it still gives pretty good information about where visitors come from,
which pages are viewed, Google search terms, etc.
It's also open-source, simple, and well documented (which is not something I
can say about GA).
The project management is pretty good and it's easy to add admins for each
website separately, we could have many different websites under a single
account with independent administrators for each.

For now, I'm (Leo) paying the minimum tier plan (10,000 monthly page views
across all sites). I'd be paying for this for my own sites and with the
Fatiando traffic at around 5000 / month I'm well within the cheapest tier.

## Costs

The pricing for Plausible is reasonable with different tiers depending on
monthly page views across all websites under an account.
Paying on a monthly basis is slightly more expensive (we get 2 months free with
yearly billing).

| Page views | Price per year (£) |
|:-----------|--------------------|
| 10k | 90 |
| 100k | 190 |
| 200k | 290 |
| 500k | 490 |
| 1000k | 690 |

The Fatiando a Terra websites combined average about 5k views per month.
I imagine many other projects will also fall within this range.
The softwareunderground.org website may have higher traffic but it's difficult
to say since there are no data on this.

For 5 different projects (including SwUng), the 100k or 200k should be more
than enough. It's relatively easy to start with a lower tier and upgrade if
page views are exceeding the limit.
The number 5 was chosen assuming that the projects involved initially would be
Fatiando, SimPEG, emsig, SwUng, and maybe one more.

Having a single account paying for the 200k tier for 5 projects (290) is
cheaper than 5 projects paying for the 10k tier individually (90 x 5 = 450).
So this makes a lot of financial sense.

There is a free 30-day trial

## Implementation

Setup is pretty easy:

* Create the property on Plausible.
* Add admins from the project.
* Put the little JS snippet in the `<head>` of the website.

Santiago has even made a Python script that replaced GA in all our old HTML
with the new Plausible snippet:
https://github.com/fatiando/community/issues/46

My proposal would be to:

1. Create a SwUng account and start a 30-day trial.
1. Identify the projects who want to take part in a trial. The Fatiando domains have already implemented so it would only be a matter of transferring the domain to a SwUng account. Maybe start with those who expressed interest in the Slack thread (SimPEG and emsig).
1. Add the Plausible snippet along side any existing GA tracking on 1 website for each project (the home page makes a lot of sense).
1. Experiment and try it out for the duration of the trial.
1. Request feedback after a period (say 20 days) to see if projects want to keep this.
1. If positive, SwUng signs up for a year and we start the process of migrating existing analytics to Plausible (slight mods to Santiago's script should be easy enough).

## Challenges

1. Defining which projects qualify for this support. This is part of larger question of what constitutes a SwUng affiliate project.
1. Continued funding, even though the initial cost is not high. If more projects start joining or becoming more popular then the price will increase.
