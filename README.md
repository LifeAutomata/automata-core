# Automata Core

The Life Automata Core provides an foundation on which other automation systems can be built.

Example use cases include:

- Home Automation
  - Turn on the lights when your driveway door is closed
  - Take a screen shot from a camera when an alarm goes off
  - Turn on Christmas lights at sunset
  - Notify you when you forget to close the garage
  - Etc.
- Quantified Home
  - Keep a record of thermostat temperature
  - Graph how much water the sprinklers use
  - Get up-to-date information about your car
  - Know when it is time to change the filter in the air conditional
  - Etc.
- Self Automation
  - Auto-reply when a VIP sends you an email
  - Alert you when a news article you care about is published
  - Take action when someone posts something about you on Twitter
  - Let you know when you should bring an umbrella
  - Order pizza
  - Etc.
- Quantified Self
  - Record and graph your weight
  - Keep journal entries
  - Track your steps
  - Map your location
  - Etc.

The core itself contains utilities for managing automata, brokering messages, and providing a
simple REST API.

## Architecture Principals

An automata with fewer moving parts is an automata that is less likely to break.

At the core of Life Automata is an event bus that brokers messages between home and personal
automomation systems. It is designed to work as an event machine but does not offer any event
persistance or replay itself.

This architecture provides for a huge amount of flexibility in designing automata.

The core project also provides a web server that can be used to expose a REST API interface
for all installed moduled. As well as a job queue to ensure that automation events happen in order.

## Events

Events are the core concept of Life Automata. There are eight built-in events:

- `plugins-loaded`
- `paused`
- `resumed`
- `shutdown`
- `device-added`
- `device-removed`
- `device-state-changed`
- `api-called`

All plugins should prefix their events with the plugin name.

## Device State

Device states should be an object. At the root level that object should only contain the following
pre-defined boolean states:

- `on`
- `armed`
- `open`
- `locked`
- `motion`

And the following integer values:

- `temperature`
- `humidity`
- `brightness`
- `battery_level`

It may also have the object value `device_defined` which may contain device specific states.
