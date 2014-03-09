# Technology

## Architecture
* Decoupling is a key value.
* Yay, SOAs! That said, having a separate service for each object is almost always a bad idea.
* Services should be able to run happily in isolation; all services should provide mocking libraries that are automatically validated against the real code and can be easily used by collaborators in dev and test environments.

## Infrastructure

* Deployment infrastructure is tested and validated.
* System configuration is done as readably as it can be (so we favor, e.g., Ansible over Chef).
* Servers are immutable below the application level (i.e., you can deploy to an existing instance, but you have to spin up new instances if you want to change anything outside of the application repo).
* We will work towards *eliminating SSH access* to production servers, but we'll do our best to be safe until we get to that point. That includes setting up the default application console to access a read-only copy of the database, for instance.
* Standing up a new instance of a service should be trivial; load balancers, etc. should automatically take the new resource into account.
* Standing up a new service should be nearly as trivial, which means it should be as automated as we can make it.
* Continuous deployment is the name of the game, with CI as a gatekeeper and feature flags aplenty.

## Monitoring

* System / operational metrics are available in real-time.
* Everything is set up to be measured, but we don't have to measure everything all the time.
* Any time you deploy, you're on the hook to watch the key system metrics for unanticipated effects.

## Quality

* The build is sacred. If someone cared enough to write a test, you should care enough to keep it green -- or make an argument for why it's unneeded (and then remove it).
* The quality and integrity of our code is important to everyone.
* We don't have to test everything, but you should be able to make a convincing argument to your peers when you don't.
* Clarity is important. Code should be regularly reviewed by devs who don't know anything about it.
* We have and run integration tests across all systems.
* QA is everyone's job.

## Languages and frameworks

* We don't have to write everything the same way, but that should be the default. If you want to do it differently, make your case to the wider team. An app that can only be maintained by one person might as well not have been written.
