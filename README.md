# Automata Core

The Life Automata Core provides an foundation on which other automation systems can be built.

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
