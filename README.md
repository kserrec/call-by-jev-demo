# Call-by-Jev demo

Play at https://kserrec.github.io/call-by-jev-demo/

This repository contains only the built static website. The implementation and
project documentation are maintained in a separate private repository.

The page opens with **Skip unused work**. Press **Ask Jev to choose** to see which
of two valid steps Jev selects. The result appears in the same panel, with a
before/after view and an explanation of what changed.

**Edit or try another** contains other examples and the editor. **Details** contains
types, Jev's reported probabilities, previous steps and automatic running.
**Return an input** and **Fill in a type** each run locally without an API call;
the page explicitly says when Jev is used. No request is sent merely by opening it.

When there are multiple choices, the current term and complete candidate menu go
through a Cloudflare Worker to TypeSafe's Jev. The private API credential stays in
the Worker. There are no browser analytics or saved derivations.

The public service shares 100 calls and 1,048,576 serialized input bytes per UTC
day, with six calls per IP address per minute. Failed provider attempts count
toward these limits. A refusal or failed decision leaves the current term intact;
there are no automatic retries. Worker storage contains usage counters and daily
hashed visitor identifiers, not terms or choices.
