---
title: Task Assigned
description: Work item handoff notification.
hidden: false
recipe:
  color: '#D97706'
  icon: 📋
---
```curl cURL
curl -X POST https://api.falco.dev/v1/messages \
  -H "Authorization: Bearer $FALCO_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "channel": "in_app",
    "to": "con_88120a",
    "template_id": "tmpl_task_assigned",
    "variables": {
      "task": "Review OAS diff"
    }
  }'
```

```javascript Node
import Falco from "@falco/node";

const falco = new Falco(process.env.FALCO_API_KEY);

await falco.messages.create({
  channel: "in_app",
  to: "con_88120a",
  templateId: "tmpl_task_assigned",
  variables: {
    task: "Review OAS diff"
  },
});
```

```json Response Example
{
  "id": "msg_01HQ8XZ3K2",
  "status": "queued",
  "channel": "in_app",
  "created_at": "2026-07-31T09:14:22Z"
}
```

# Authenticate your request

<!-- curl@1 -->
<!-- javascript@3 -->

Every Falco call takes a bearer token. Use a server-side key, never ship one to the browser.

# Target the in_app channel

<!-- curl@5 -->
<!-- javascript@6 -->

Set `channel` to `in_app` and address the message with a verified contact id.

# Reference your template

<!-- curl@7 -->
<!-- javascript@7 -->

`tmpl_task_assigned` holds the copy, so it can change without a deploy.

# Personalize with variables

<!-- curl@8 -->
<!-- javascript@10 -->

Variables merge into the template at send time. Missing keys fall back to the template default.
