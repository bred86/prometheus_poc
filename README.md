# Prometheus

*Author: Frederico Ferreira

Publish Date: 2019-05-16

Review dua date: 2019-05-31*

## Problem statement
Our current alert solution isn't capable of more advanced configurations that could help Lucid understand the root cause of issues.
Configurations that Cabot, our current alert solution, handles:
* Graphite checks
  * metric based alerts
  * number of fails before alert  
* Http checks
  * almost never used
  * used to check if an application is answering requests
* Instances
  * manually link an alert to an instance
* Jenkins checks
  * never used
* Reports
  * brings everything Cabot has access to
* Recovery instructions
  * scripts that could be ran to solve things automatically

Using it, we undesrtod that its not enough for our case. During the 2019 year, at first half of the year, we had some issues with Hosted Graphite (HG).
There were times when HG was returning 503's and no metrics could be gathered, so, triggering alerts.

It was frustrating when people were in their resting time and received an alert because HG wasn't sending metrics instead of being alarmed by an application misfunction.

## Solution statement
Prometheus does everything that Cabot does, plus:
* Grouping alerts
  * grouping categorizes alerts of similar nature into a single notification, which is useful during larger outages when many systems fail at once and hundres of alerts may be firing simultaneously
* Inhibition
  * supress notifications for certain alerts if certain other alerts are already firing
  * could be used when HG isn't accessible
* Automation
  * brings the possibility to have alerts enabled by default
* Integration with Kubernetes
* Integration with AWS

The transition is invisible to the final user. Both Prometheus and Cabot reads metrics from Graphite (and many others, in Prometheus' case), with some particularities.

### (Hosted) Graphite


### Grafana
* https://grafana.com/plugins/camptocamp-prometheus-alertmanager-datasource

## Alternatives considered
Sensu

## PoC
I'm still developing a PoC to show how it works and a documentation to make the transition as smooth as it can be.
