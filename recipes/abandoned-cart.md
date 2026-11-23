---
title: Abandoned Cart
description: Win back shoppers who did not check out.
hidden: false
recipe:
  color: '#4F46E5'
  icon: 🛒
---
```curl cURL
curl -X POST https://api.falco.dev/v1/messages \
  -H "Authorization: Bearer $FALCO_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "channel": "email",
    "to": "ada@example.com",
    "template_id": "tmpl_abandoned_cart",
    "variables": {
      "cart_url": "https://shop.example.com/c/7d1",
      "item_count": "3"
    }
  }'
```

```javascript Node
import Falco from "@falco/node";

const falco = new Falco(process.env.FALCO_API_KEY);

await falco.messages.create({
  channel: "email",
  to: "ada@example.com",
  templateId: "tmpl_abandoned_cart",
  variables: {
    cart_url: "https://shop.example.com/c/7d1",
    item_count: "3"
  },
});
```

```json Response Example
{
  "id": "msg_01HQ8XZ3K2",
  "status": "queued",
  "channel": "email",
  "created_at": "2026-07-31T09:14:22Z"
}
```

# Authenticate your request

<!-- curl@1 -->
<!-- javascript@3 -->

Every Falco call takes a bearer token. Use a server-side key, never ship one to the browser.

# Target the email channel

<!-- curl@5 -->
<!-- javascript@6 -->

Set `channel` to `email` and address the message with a verified email address.

# Reference your template

<!-- curl@7 -->
<!-- javascript@7 -->

`tmpl_abandoned_cart` holds the copy, so it can change without a deploy.

# Personalize with variables

<!-- curl@8 -->
<!-- javascript@11 -->

Variables merge into the template at send time. Missing keys fall back to the template default.
