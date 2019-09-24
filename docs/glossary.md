---
id: glossary
title: Glossary
---

This guide contains a glossary for the common terms used within the Healthbot documentation. An understanding of these is required to work through the guides on this site.

## Device

From Healthbot's perspective a Device is something that emits Telemetry using one of four mechanisms; OpenConfig, JTI Native, NETCONF and SNMP. Therefore in the context of networking a Device could be a Router, Switch, Bridge, Transponder, ROADM, ILA or any piece of Network Equipment, virtual or physical that emits using one of the aforementioned mechanisms. Healthbot is not limited to a Networking context, other context such as General Computing, IOT or any other context that generates sensor data could be considered a candidate for Healthbot.

## Device Group

A Device Group is a means to classify a set of Devices that reflect a business function within an organization. E.g. classifying by region, protocol, business unit or by customer, in fact, any grouping that may be relevant to the organization.

## Playbook

Playbooks are the key abstractions within Healthbot, they provide a language for describing Key Performance Indicators(KPIs), through applying rules against sensor data. The rules can describe in(valid) thresholds or conditions and what actions should be triggered in the event of a threshold crossing or a condition being met.
