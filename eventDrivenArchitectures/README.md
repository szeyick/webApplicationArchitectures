# Event Driven Architectures

## Organisms Sense and Response: EDA

The idea is to sense what is around you and make a decision on what to do. This is the concept behind event driven architectures, where you react to a particular thing.

The streams of data or event, are triggered from an external source, such as from senses (sight, sound, touch, etc).

## Internet of Things (IoT)

Devices are now more interconnected, providing the state of the environment that they are in. It provides a more responsive environment since you can get updates in real-time.

## Events and Complex Events

A event is classified as something that the system senses or is of interest to the system.

A complex event is defined as an event involving more than a single event. It could be dependent on several events occcuring at the same time.

### Time, Causality and Aggregation

Three most common and important relation between events are

- Time - The relationship that orders the events.
- Cause - The dependancy of activites in the system
- Aggregation - The combined relationship of activities that create an event.

## Event Driven Architectures (EDA)

Processes communicate by accessing shared events in a "event cloud". Each part of the system (a process) communicates with each other through a listener/observer pattern.

It is a asynchronous architecture.

It can also have a set of rules that react to certain events. 

### Features

- Captures asynchronous events occuring in parallel.
- Senses real time events and conditions.
- Initiates the appropriate response, action or process.
- It modifies processes in real-time to respond to changing conditions.

## Publish Subscribe Architectures

It is a type of architecture for subscribing to events. The internal network within the system connects the publishers and subscribers together.

## Basic Architecture

Event Publisher is the one that generates the events.

Event Subscriber is the one that subscribes to events.

## Event Processing Styles

## Complex Event Processing - CEP

Is a set of techniques and tools to help understand and control event driven information systems. Such examples include a combination of events that lead to a complex event to be triggered.

For example, an event of loud noises, cars, and screetching of tires. Those three events can form a complex event which would be a car race.

## How EDA relates to SOA

- Event driven architectures promotes decoupling of business processes.
- The same event can be consumed by multiple processes.
- SOA and EDA are complementary

- SOA requires knowledge of where the service is, however in EDA, you generate the event but don't care who responds to it.
- SOA is a one-one connection, however in EDA many services can respond/react to events, there is no direct connection between processes/services.
- SOA primarily uses a request-response message exchange, however in EDA can process asynchronous calls. The events are triggered and any number of processes can respond.

## Implementing EDA

- ESBs - Enterprise Service Buses
- Event drive processing and rule engines.

