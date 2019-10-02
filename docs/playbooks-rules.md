---
id: playbooks-rules
title: Playbooks and Rules
---

Once Devices are registered within Healthbot and assigned to one or more Device Groups, the remaining part of the configuration stage is to instantiate one or more Playbooks against the set of Device Groups. If you have worked through the Quickstart Guide, you will remember that Playbooks are a key abstraction within Healthbot, through Rules they provide a language for describing KPI's and how-to react to them.

So to better understand Playbooks, we first need to understand Rules.

## Rules

Healthbot is about capturing and reacting to Telemetry data, defining how-to capture and what way to react is the role of a [Rule](glossary#rule).

Therefore, when defining a Rule we need a language that describes what a Rule is and does, where to receive data from, a way to filter or manipulate the data and then a way to react to this data meaningfully. In software terms, this type of language is called a **Domain Specific Language** (DSL), i.e. a language that is a specific to one domain, in our case Healthbot Telemetry.

![Rules Components](assets/rules/rule-components.png)

Healthbot is shipped with a set of default Rules, these Rules are available on Github at the [healthbot-rules](https://github.com/Juniper/healthbot-rules) repository. An example from this website shows an instance of the DSL targeted at defining a KPI for Temperature fluctuations within a Chassis [chassis-temperature.rule](https://raw.githubusercontent.com/Juniper/healthbot-rules/master/juniper_official/Chassis/chassis-temperature.rule), note the DSL instance definition ends with an extension **.rule** and follows a clear structure for the concepts I described above.

The default set of Rules can be extended either through [community supplied](https://github.com/Juniper/healthbot-rules/tree/master/community_supplied) Rules, or through a Healthbot user creating their own Rules, this guide will predominantly be concerned with the latter.

### Dashboard

Rules can be created, updated and deleted through the Dashboard, there is a dedicated screen specifically for manipulating Rules.

![Rules Overview](assets/rules/rules-overview.png)

This screen provides a visual representation of the Rules DSL. In this example we can see for the Topic system.processes, there is a rule called check-process-memory, which analyses the system processes memory utilization. You can also see the components available within the DSL for defining a Rule.

## Playbooks
