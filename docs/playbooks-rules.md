---
id: playbooks-rules
title: Playbooks and Rules
---

Once Devices are registered within Healthbot and assigned to one or more Device Groups, the remaining part of the configuration stage is to instantiate one or more Playbooks against the set of Device Groups. If you have worked through the Quickstart Guide, you will remember that Playbooks are a key abstraction within Healthbot, through Rules they provide a language for describing KPI's and how-to react to them.

So to better understand Playbooks, we first need to understand Rules.

## Rules

Healthbot is about capturing and reacting to Telemetry data, defining how-to capture and what way to react is the role of a [Rule](glossary#rule).

Therefore, when defining a Rule we need a language that describes what a Rule is and does, where to receive data from, a way to filter or manipulate the data and then a way to react to this data meaningfully. In software terms, this type of language is called a **Domain Specific Language** (DSL), i.e. a language that is specific to one domain, in our case Healthbot Telemetry.

![Rules Components](assets/rules/rule-components.png)

Healthbot is shipped with a set of default Rules, these Rules are available on Github at the [healthbot-rules](https://github.com/Juniper/healthbot-rules) repository. An example from this website shows an instance of the DSL targeted at defining a KPI for Temperature fluctuations within a Chassis [chassis-temperature.rule](https://raw.githubusercontent.com/Juniper/healthbot-rules/master/juniper_official/Chassis/chassis-temperature.rule), note the DSL instance definition ends with an extension **.rule** and follows a clear structure for the concepts I described above.

The default set of Rules can be extended either through [community supplied](https://github.com/Juniper/healthbot-rules/tree/master/community_supplied) Rules or through a Healthbot user creating their own Rules, this guide will predominantly be concerned with the latter.

### Dashboard

Rules can be created, updated and deleted through the Dashboard, there is a dedicated screen specifically for manipulating Rules.

![Rules Overview](assets/rules/rules-overview.png)

This screen provides a visual representation of the Rules DSL. In this example, we can see for the Topic **system.processes**, there is a rule called **check-process-memory**, which analyses the system processes memory utilization. You can also see the **components** available within the DSL for defining a Rule.

Rather than using the Dashboard to define a Rule, we will use the Rule Builder CLI to construct our sample Rule.

#### Rule Builder CLI

The Rule Builder CLI is an extension to the JUNOS System Management Daemon (mgd).

The management daemon (mgd) provides a mechanism to process information for both network operators and daemons.

The interactive component of mgd is the JUNOS cli; this is a terminal-based application that allows the network operator an interface into JUNOS. The other side of mgd is the extensible markup language (XML) remote procedure call (RPC) interface; This provides an API through Junoscript and NETCONF to allow for the development of automation applications.

The cli responsibilities are:

- Command-line editing
- Terminal emulation
- Terminal paging
- Displaying command and variable completions
- Monitoring log files and interfaces
- Executing child processes such as ping, traceroute, and ssh

mgd responsibilities include:

- Passing commands from the cli to the appropriate daemon
- Finding command and variable completions
- Parsing commands

To access the cli we will use ssh forwarding to the Healthbot server and connect to the cli through the mgd container running in Healthbot.

```sh
$ ssh-copy-id jcluser@66.129.235.13 -p 43001 # optionally use a different port for SSH if required
$ DOCKER_HOST=ssh://jcluser@66.129.235.13:43001 sh -c 'docker exec -it healthbot_mgd_1 cli' # note the use of the non-default SSH port
```

Note in my example the use of a non root user (**jcluser**), Healthbot Server (**66.129.235.13**) and a non default SSH port (**43001**) as well as using **healthbot_mgd_1** as the name of the mgd container running on the Healthbot Server.

This will drop you into the cli, which can be confirmed by typing ?

```sh
root@ce2568758089> ?
Possible completions:
  clear                Clear information in the system
  configure            Manipulate software configuration information
  monitor              Show real-time debugging information
  op                   Invoke an operation script
  quit                 Exit the management session
  request              Make system-level requests
  set                  Set CLI properties, date/time, craft interface message
  show                 Show system information
  start                Start shell
root@ce2568758089>
```

From here we can create, read, update and delete Healthbot configuration to do this we first need to load the Healthbot configuration into mgd.

```sh
root@ce2568758089> request iceberg load
Getting "retention-policy" hierarchy configuration
Done
Getting "notification" hierarchy configuration
Done
Getting "device" hierarchy configuration
Done
Getting "topic" hierarchy configuration
Done
Getting "playbook" hierarchy configuration
Done
Getting "device-group" hierarchy configuration
Done
Getting "network-group" hierarchy configuration
Done
Getting "system-settings" hierarchy configuration
Done

Configuration load complete
```

We can confirm that the load worked correctly by querying one of the configuration hierarchies for e.g.

```sh
root@ce2568758089> show configuration iceberg topic chassis.temperatures rule check-chassis-temperature sensor components
synopsis "Chassis components sensor definition";
description "/components open-config sensor to collect telemetry data from network device";
open-config {
    sensor-name /components/;
    frequency 60s;
}
```

This shows that we can see the configuration for the OpenConfig sensor **components**, that exist in **check-chassis-temperature**, which is a System Rule in the Topic **chassis.temperatures**.

### Components that make up a Rule

In this section, we will look at the parts that make up a Rule. We will see how these components interact with each other to provide a Rule definition. Rule definition begins with identifying and describing the source of Telemetry that will 'feed' this rule, this is described in the Sensors component.

#### Sensors

#### Fields

#### Vectors

#### Variables

#### Functions

#### Triggers

#### Rule Properties

## Playbooks
