---
description: Overview of polling usage.
icon: repeat
---

# Polling for Results

## Overview

The polling flow is simpler to set up, and allows a quick integration.

It's perfect for testing Mindee on a local machine, and is suitable for lightweight production use.

This flow can also be integrated with various 3rd party tooling such as MS Power Automate.

If you're not sure on what to use, choose this flow.

### Sequence Diagram

```mermaid
sequenceDiagram
    participant client as Client
    participant enqueue as /inferences/enqueue
    participant job as /jobs
    participant inference as /inferences
    client->>enqueue: POST file
    enqueue->>client: HTTP 202
    client->>client: wait 3 seconds
    client->>job: GET job.id
    job->>client: Processing - HTTP 200
    loop Loop until job.result_url is filled or HTTP 302 returned
      client->>client: wait 1 second
      client->>job: GET job.id
      job->>client: Processed - HTTP 302
    end
    client->>inference: GET inference.id
    inference->>client: HTTP 200
    client->>client: process JSON result
```

## Specifying on File Upload

This is the default behavior as described in the [quick-start.md](client-libraries-sdk/quick-start.md "mention") section.

Detailed instructions for your language of choice are detailed in the [#send-with-polling](client-libraries-sdk/send-a-file-or-url.md#send-with-polling "mention") section.
