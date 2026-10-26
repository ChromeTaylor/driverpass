
**Project summary**

The client was DriverPass, a driver education company owned by Liam. DriverPass offers training to people preparing for their DMV driving test, and the problem was that students were failing because they were ill-prepared due to limited resources, and the available materials didn't align with what the test actually covered. The company wanted a web-based, cloud-hosted system combining two things in one place: online classes and practice tests students could take from home, and scheduling for real on-the-road lessons with an instructor and a car. The system also needed role-based access for customers, the secretary, instructors, the IT officer, and the owner, along with reporting, auditing of all reservation activity, and a connection to the DMV for current rules and sample questions.

**What I did well**

What I did well was traceability in my project. Nearly every design element ties back to a specific statement from the interview rather than something I invented because it seemed like good practice. The double-booking prevention, the separate secretary path for customers who prefer to call, the owner’s ability to disable a package without disabling it for existing customers, and the self-service password reset so the IT officer is not interrupted for routine requests. Each of these exists because someone asked for it. I also think the technical requirements section holds up well, because I sized the infrastructure from the client’s actual operating numbers, ten cars running two-hour lessons, rather than guessing at hardware. That gave me a defensible reason to argue that a single cloud region with automated failover was sufficient and that a more expensive multi-region setup would have been over-engineering.

**What I would revise**

If I could revise one thing, it would be the use case diagram. I tried to fit every use case for all five roles plus two external systems onto a single canvas, and the result became crowded enough that the relationships are hard to follow. I also duplicated one use case without noticing, which is exactly why this layout produces this kind of error. If I were to redo it, I’d split it into a core diagram covering the customer and scheduling use cases, where most of the include and extend relationships live, and a second diagram covering the administrative use cases for the IT officer and owner. The same information would be present, but each diagram would be readable on its own, and a client could easily follow it during a presentation.

**Interpreting user needs**

My approach was to treat the interview transcript as the authoritative source and return to it rather than design from assumptions. I worked outward in layers: pull concrete statements from the interview into requirements, group these requirements by the actor who needs them, then model the behavior those actors drive. Where the interview left things unknown, I noted those in section notes, like refund policy, cancellation fees, and data retention, as unresolved. This matters because undocumented assumptions look like requirements once they reach a developer.

Considering user needs is important. A technically sound system that doesn’t match how people actually work will not get used. The clearest example from this project is the secretary. It would have been simpler to build a customer-only booking portal, but the client explicitly said some customers prefer to call. If I had designed only for the online path, the system would have handled the easy case and left the staff to do the hard case on paper, which means the reservation records could have been incomplete and the owner’s activity reports would not have reflected reality.

**How I approach software design**

I work from the outside in. I understand who uses the system and what they are trying to accomplish before deciding how to build anything. Starting with use cases keeps the early conversation in the client’s language rather than mine, and it also lets you validate the understanding with someone non-technical before any code exists. From there, move to behavior with activity and sequence diagrams, and only then to structure with a class diagram, because the data model is easier to get right once you know what the system has to do with the data.

Going forward, the techniques I would carry into future work are using multiple diagram types for the same feature rather than relying on one, since each exposes different gaps; the activity diagram showed me the retry path on a declined payment, while the sequence diagram forced me to decide which calls block and which do not.
