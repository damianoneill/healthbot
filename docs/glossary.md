---
id: glossary
title: Glossary
---

This guide contains a glossary for the common terms used within the Healthbot documentation. An understanding of these is required to work through the guides on this site.

## Device

From Healthbot's perspective a Device is something that emits Telemetry using one of four mechanisms; OpenConfig, JTI Native, NETCONF and SNMP. Therefore in the context of networking a Device could be a Router, Switch, Bridge, Transponder, ROADM, ILA or any piece of Network Equipment, virtual or physical that emits using one of the aforementioned mechanisms. Healthbot is not limited to a Networking context, other context such as General Computing, IOT or any other context that generates sensor data could be considered a candidate for Healthbot.

## Device Group

A Device Group is a means to classify a set of Devices that reflect a business function within an organization. E.g. classifying by region, protocol, business unit or by customer, in fact, any grouping that may be relevant to the organization.

## Operational intelligence

Operational intelligence (OI) is a category of real-time dynamic, business analytics that delivers visibility and insight into data, streaming events and business operations. OI solutions run queries against streaming data feeds and event data to deliver analytic results as operational instructions. OI provides organizations the ability to make decisions and immediately act on these analytic insights, through manual or automated actions.

## Playbook

Playbooks are the key abstractions within Healthbot, they provide a language for describing Key Performance Indicators(KPIs), through applying rules against sensor data. The rules can describe in(valid) thresholds or conditions and what actions should be triggered in the event of a threshold crossing or a condition being met.

## Telemetry

Telemetry is the collection of measurements or other data at remote or inaccessible points and their automatic transmission to receiving equipment for monitoring. In Healthbot telemetry is used to gather data on the use and performance of hardware, protocols, applications, application components and processes e.g. measurements of start-up time and processing time, hardware, application crashes, and general usage statistics and/or user behavior.

## Topic

Rules within Healthbot are organized by Topics. Topics provide a classification for a set of rules for e.g. rules relating to chassis sensors would be categorized under the chassis topic. Further sub classification can occur by post-pending a period to a high level Topic for e.g. chassis.temperature would contain rules pertaining to Chassis Temperature Sensors. After Rules are classified, Topic names can be used as visual clues in dashboard widgets to group indicators together. For e.g. on the Device Health screen, CPU health can be grouped with a collection of icons, labelled using the Topic name system.cpu.
