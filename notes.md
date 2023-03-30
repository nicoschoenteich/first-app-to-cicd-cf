# Vom ersten App-Deployment zu CI/CD mit Cloud Foundry

Wie funktioniert Cloud Foundry eigentlich wirklich?<br>
In diesem Vortrag erkunden wir die Struktur von Apps und Services auf der SAP BTP, Cloud Foundry environment und lernen dabei, wie diese administriert werden können. Wir starten mit dem einfachen Deployment einer App, um dann Schritt für Schritt die Komplexität zu erhöhen und schlussendlich eine CI/CD Pipeline zu aufzusetzen. Geeignet für Entwickler/innen und technisch Interessierte.

> From your first app deployment to CI/CD with Cloud Foundry
>
> How does Cloud Foundry actually work?
>In this talk we will explore the structure of apps and services on the SAP BTP, Cloud Foundry environment and learn how to administer them. We will start with the simple deployment of an app, then increase the complexity step by step and finally set up a CI/CD pipeline. Suitable for developers and technically interested people.

- starten mit Frage nach Erfahrung mit CF
  - wer hat schonmal eine App auf CF deployed?

---

# General

- open source application development platform
- platform as a service
- focus on developer experience
- developers can focus on developing solutions instead of how to run those solutions
- "here is my code, just run it"
- polyglot environment
- interoperable -> support for K8s via project eirini
- Diego, Garden -> scheduling and managing -> CF application runtime
- Diego Cell: virtual machine that virtualizes runtime environment for Garden container
- Garden is also based on Open Container Initiave like Docker and K8s
- Open Service Broker API allows to integrate external services into cf marketplace
- SAP BTP handles the operation (e.g. deployment) of CF itself for us
- BOSH creates and deploys VMs on top of infrastructure

- Built-in: load balancing, user management, monitorin

# How Apps Are Staged

cf CLI (A) --> Cloud Controller (B) --> Diego (C)

- A. Command Line Tool the developer uses
- B. Cloud Controller maintains a database with tables for orgs, spaces, services, user roles, and more
- C. Diego: self-healing container management system

SIMPLYFIED:
- Cloud Controller passes requests to run apps to the Diego
- Auctioneer (Diego) finds available Diego Cell
- Executor (Diego) creates Garden container in the Diego Cell
- Route is being created
- Logging

---

Ich bin ein großer Fan von praktischen Beispielen und möchte deshalb zu aller erst zeigen, wie wir Cloud Foundry nutzen können, bevor ich in ein bisschen Theorie einsteige. Ich glaube es ist wichtig beim Lernen von neuen Technologien komplett bei Null anzufangen und wirklich - ohne Templates - jeden Schritt manuell zu machen, damit man wirklich versteht welche Zeile oder Datei was macht und wie die Zusammenhänge sind. Und deshalb ist unser Projekt bisher auch komplett leer - bis auf mein Skript.