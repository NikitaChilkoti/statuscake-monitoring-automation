## statuscake-monitoring-automation
I worked on automating uptime monitoring and incident detection using Bash scripting, StatusCake API, and Linux automation workflows.

## Linux-Based Monitoring & Incident Alerting Automation

## The Idea

When multiple services start appearing:

* APIs
* dashboards
* internal tools
* staging environments

things become repetitive very quickly.

Creating monitors manually again and again is not difficult… just operationally annoying.

---

## What This Project Does

This project automates:

* uptime monitor creation
* monitor validation
* incident detection
* status reporting

using:

* Bash scripting
* StatusCake API
* Linux automation workflows

---

## What I have set as goal for this project?

The goal is understanding how operational monitoring workflows actually behave when services go down,  alerts trigger, monitoring data changes, teams investigate

And eventually repetitive operational tasks get automated.

---

## Project Flow

The project progresses with the following steps:

1. Configure StatusCake API access
2. Automate monitor creation using Bash
3. Validate monitor behavior
4. Simulate service failure
5. Observe alerting workflow
6. Generate monitoring reports

---

## I used all these:

* Bash
* curl
* jq
* StatusCake API
* Linux
* Nginx / sample application

---

## Project Structure

```text
statuscake-monitoring-automation/
|
├──
├── README.md
├── 01-project-overview.md
├── 02-statuscake-api-setup.md
├── 03-create-monitor.sh
├── 04-monitor-validation.md
├── 05-incident-simulation.md
├── 06-reporting-automation.md
├── 07-future-improvements.md
│
├── scripts/
│   ├── create-monitor.sh
│   ├── check-status.sh
│   ├── delete-monitor.sh
│   └── generate-report.sh
```

---

## What This Project Focuses On

This is all about
* operational automation
* monitoring workflows
* incident visibility
* scripting repetitive tasks