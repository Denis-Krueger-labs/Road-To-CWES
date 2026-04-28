---
layout: log
title: "Day 41 - HTTP Peer Discovery and Messaging Prototype"
date: 2026-04-28
topics: ["P2P Backup System", "C#", "HTTP Messaging", "Peer Discovery", "Superpeer", "Routing", "Sprint 1"]
summary: "Pivoted from the TCP demo path to an HTTP-based Sprint 1 prototype with superpeer discovery, peer registration, routing, forwarding, TTL handling, and Windows/WSL communication."
status: complete
---

# Day 41 - HTTP Peer Discovery and Messaging Prototype

## What I did today

Today was the big pivot day for the P2P backup system.

After realizing that the Sprint 1 implementation should use **HTTP** instead of the TCP demo path, I reworked the prototype direction and got a working HTTP-based discovery and messaging flow.

Also today, I:

- attended the group meeting
- had my internship interview
- fought GitLab 403 errors again
- wrote the internal documentation for the current Sprint 1 prototype

---

## Summary of concepts

The current Sprint 1 prototype uses the following flow:

```text
Discovery -> PeerDirectory -> Router -> HTTP Transport -> /message -> Delivery
```

The older TCP path still exists, but it should now be treated as **legacy/demo code**.

The current HTTP path supports:

- starting one node as a superpeer
- starting normal peers
- registering peers with ID and advertised URL
- exposing discovered peers
- refreshing discovery manually
- mapping discovered peers into messaging endpoints
- sending and receiving messages over HTTP
- routing through intermediate peers
- decrementing TTL on forwarding
- avoiding forwarding directly back to the last hop
- deduplicating messages using a nonce
- communicating across Windows and WSL with correct advertised URLs

---

## Deeper understanding

The biggest lesson today:

> Discovery and messaging are connected, but they are not the same thing.

Discovery answers:

> Who exists, and where can they be reached?

Messaging answers:

> How do I send this message to the target peer?

That is why the system currently uses two related models.

For discovery:

```csharp
Peer(Id, Url)
```

For messaging:

```csharp
PeerEndpoint(PeerId, Host, Port)
```

The `PeerEndpointMapper` bridges those two formats.

Another important lesson:

> Routing metadata must be precise, or distributed systems become cursed very quickly.

Fields like the following all need clear meaning:

- `FromPeerId`
- `ToPeerId`
- `TargetPeerId`
- `LastHopPeerId`
- `TTL`
- `Nonce`

---

## What I actually implemented / worked on

### Core runtime

Worked on the core HTTP path in the CLI project.

Relevant files:

- `p2p_backup_cli/Core/core.cs`
- `p2p_backup_cli/Core/CoreNodeOptions.cs`
- `p2p_backup_cli/Core/CoreDiscoveryService.cs`
- `p2p_backup_cli/Core/CoreMessagingService.cs`
- `p2p_backup_cli/Core/CoreEndpointMappings.cs`
- `p2p_backup_cli/Core/SendMessageRequest.cs`

### Messaging and discovery

Worked on:

- message service contracts
- message transport contracts
- basic message service implementation
- HTTP-based message transport
- in-memory message transport / demo support
- message envelope validation
- incoming and outgoing message handling
- superpeer discovery registration
- discovery refresh
- mapping discovery peers into messaging endpoints

### HTTP endpoints

Current endpoints include:

```http
POST /message
GET  /peers
POST /send/{targetPeerId}
GET  /discover
POST /refresh-discovery
POST /register
```

`/register` is only mapped on superpeer nodes.

---

## Tested scenarios

Successfully tested:

- direct HTTP messaging between peers
- core-to-core communication
- superpeer registration
- discovery refresh
- mapping discovery data into the messaging directory
- multi-hop routing through an intermediate peer
- TTL decrement during forwarding
- Windows peer to WSL peer messaging
- Windows -> Windows -> WSL multi-hop routing
- advertised URL override for WSL
- nonce-based duplicate suppression observed manually

---

## What went well

- successfully pivoted from TCP to HTTP
- got the Sprint 1 prototype working
- connected discovery and messaging
- proved direct messaging
- proved multi-hop messaging
- proved TTL decrement
- solved the WSL advertised URL issue
- documented the current system clearly
- got the prototype to a state where others can understand and test it

---

## What was challenging

- realizing the TCP work from Day 40 was not the main path anymore
- being extremely tired
- working after very little sleep
- GitLab 403 errors wasting time
- WSL networking complexity
- routing metadata requiring careful thinking
- old TCP demo code still existing and potentially confusing the project structure
- manual testing taking a lot of effort

---

## Mistakes / friction

- discovery refresh is still manual
- `/send/{targetPeerId}` is a debug endpoint, not final application behavior
- no automated tests yet
- no delivery acknowledgments yet
- no retry or offline queue yet
- no authentication or encryption yet
- TCP demo code needs to be marked as legacy or removed

---

## What I think I understand now

- HTTP is easier to test and debug for this Sprint 1 prototype
- peer discovery is only useful if messaging can consume the discovered data
- advertised URLs matter a lot in mixed Windows / WSL environments
- routing needs clear metadata, or debugging becomes painful
- nonce deduplication is necessary when flooding or forwarding can create duplicate paths
- wrong-path work from Day 40 still helped clarify the final design

---

## What I need to improve

- add automated tests for routing and mapping
- test TTL expiration properly
- test duplicate suppression in a structured way
- improve HTTP error responses
- document old TCP code as legacy or remove it
- add authentication and encryption later
- avoid destroying my sleep schedule for prototype work if possible

---

## Recommended next steps

### Must-have before Sprint 1 submission

- push the branch
- make sure `dotnet build` succeeds
- update README / internal docs with HTTP commands
- document tested scenarios
- mark TCP as legacy/demo if it stays
- clean up merge request

### Nice-to-have

- automatic discovery refresh
- unit tests for routing and mapping
- cleaner JSON error responses
- rename `config` to `Config`
- reduce or structure debug logs
- move reusable logic further into the library project

---

## Real life context

- worked from afternoon into evening
- returned around 2am
- continued until around 7am
- attended the group meeting around 11
- completed internship interview
- fought GitLab 403 errors again
- wrote the internal Sprint 1 documentation after finishing my prototype part

---

## Session info

**Duration:** project-heavy day  
**Energy:** exhausted but productive

---

## Small note

The Sprint 1 HTTP prototype now works.

That is the important part.

࿔‧ ֶָ֢˚˖𐦍˖˚ֶָ֢ ‧࿔  
emotional support moth
