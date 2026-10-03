# Call-by-Jev demo

Play at https://kserrec.github.io/call-by-jev-demo/

This repository contains only the built static website. The implementation and
project documentation are maintained in a separate private repository.

Jev is connected. Select Mixed choice, then Step, to let Jev choose between the
current legal reductions. The evaluator performs exactly the selected reduction
and shows Jev's probabilities. STLC subset and Polymorphic identity reduce locally
without an API call.

When there are multiple choices, the current term and complete candidate menu go
through a Cloudflare Worker to TypeSafe's Jev. The private API credential stays in
the Worker. There are no browser analytics or saved derivations.

The public service shares 100 calls and 1,048,576 serialized input bytes per UTC
day, with six calls per IP address per minute. Failed provider attempts count
toward these limits. A refusal or failed decision leaves the current term intact;
there are no automatic retries. Worker storage contains usage counters and daily
hashed visitor identifiers, not terms or choices.
