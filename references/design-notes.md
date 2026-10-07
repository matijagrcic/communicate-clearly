# Design notes and sources

## Purpose and values

The working premise is that capability does not determine purpose. Communication should connect an agent's competence to the outcome, constraints, and values established by the user and the surrounding system. An agent may propose a different framing, but should not silently replace the objective or treat a convenient metric as the whole definition of success.

This is a design choice for this skill, developed from the user's discussions about competence, purpose, and reflective practice. It is not a claim that a communication protocol can settle ethical disagreements, that agents cannot contribute to defining tasks, or that a skill replaces governance. The surrounding system still establishes authority, access, and stopping conditions.

## What comes from each influence

| Influence | Adopted idea | Boundary |
|---|---|---|
| IMO Standard Marine Communication Phrases | Make a message's communicative purpose explicit | The local eight-marker vocabulary is an adaptation for agents, not official maritime phraseology |
| ASD-STE100 | Reduce avoidable ambiguity and preserve meaning during revision | No controlled dictionary is bundled and no compliance certification is offered |
| Donald Schön's reflective practice | Treat surprise and misunderstanding as reasons to revisit an approach or framing | Reflection depends on the situation; it is not a universal approval ritual or a prescribed list of values |
| The user's competence-and-purpose discussion | Make intended benefit, constraints, and success criteria visible when they matter | Capability and execution evidence do not themselves justify an objective |

### IMO SMCP

[IMO's official overview](https://www.imo.org/en/ourwork/safety/pages/standardmarinecommunicationphrases.aspx) describes the maritime scope. [Resolution A.918(22)](https://wwwcdn.imo.org/localresources/en/OurWork/Safety/Documents/A.918%2822%29.pdf), General pages 14–15 and message-marker definitions on pages 46–47, defines Instruction, Advice, Warning, Information, Question, Answer, Request, and Intention.

In that context, an instruction presupposes authority, while advice leaves a decision to its recipient. Several definitions are navigation-specific. This skill retains the distinction between advice and required action but does not import maritime authority or domain restrictions. It adds explicit treatment of inference, results, evidence, and uncertainty.

### ASD-STE100

[The official ASD-STE100 site](https://www.asd-ste100.org/), [Issue 9](https://www.asd-ste100.org/assets/files/ASD-STE100_ISSUE9.pdf), and [the official FAQ](https://www.asd-ste100.org/STE_faq.html) distinguish the standard's writing rules and dictionary from general plain language. Issue 9, writing practices page 1-9-2, addresses preserving meaning while restructuring sentences or replacing words.

This skill uses clarity and semantic preservation as design principles. It neither reproduces the dictionary nor equates short sentences, automatic linting, or fluent prose with compliance.

### Reflective practice

In [Reflective Conversation with Materials](https://hci.stanford.edu/publications/bds/9-schon.html), a primary interview published in *Bringing Design to Software* (1996), Schön discusses knowledge expressed in action, surprise, and reflection during practice. Unexpected consequences and users' interpretations can cause a practitioner to reconsider both understanding and design choices.

The [publisher's page for *The Reflective Practitioner*](https://www.routledge.com/The-Reflective-Practitioner-How-Professionals-Think-in-Action/Schon/p/book/9781315237473) identifies the book's movement from technical rationality to reflection-in-action. The publisher's synopsis is not a substitute for the full argument. This repository's account of purpose, authorization, and value trade-offs is an operational synthesis, not a quotation or purported checklist from Schön.

### Related skill

[danyuchn/asd-ste100-skill](https://github.com/danyuchn/asd-ste100-skill) was an inspiration discussed by the user, particularly its emphasis on preserving uncertainty, conditions, and scope. Communicate Clearly is an original implementation focused additionally on intent, evidence, authority, and purpose. No upstream code, dictionary, or examples are bundled.

## What remains a hypothesis

Explicit message distinctions may improve interpretation and handoffs, but their presence does not establish truth or reliability. Fluent wording, marker consistency, and valid YAML are insufficient measures of success.

The repository's behavioral cases check observable interpretation risks. They are a development smoke check, not evidence of superior performance over STE or other approaches. A stronger evaluation would compare unaided communication, STE-inspired rewriting, marker-only communication, and this hybrid on the same held-out tasks. A separate receiving agent or reader should identify facts versus inferences, obligations versus advice, ownership, prerequisites, and actual completion. Measure lost conditions, invented claims, unnecessary exchanges, and reading effort as well as correctness. Record model, prompts, artifacts, and repeat runs before claiming improvement.

Public sources checked on 7 October 2026. Private conversation transcripts are not included in this repository.
