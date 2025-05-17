# High level schema of what happens when you type `https://www.google.com` and hit Enter:

```mermaid
flowchart TD
  A[User’s Browser]
  B[DNS Resolution]
  C["IP Address & Port (e.g. 172.217.12.46:443)"]
  D[TCP 3‑Way Handshake]
  E["TLS Handshake (Encryption Established)"]
  F[Firewall Inspection]
  G[Load Balancer]
  H[Web Server]
  I[Application Server]
  J[Database]

  A --> B
  B --> C
  C --> D
  D --> E
  E --> F
  F --> G
  G --> H
  H --> I
  I --> J

  classDef stroke-width:1px;
  class B,C,D,E,F,G,H,I,J proc;
```

**Step-by-step mapping:**

1. **DNS Resolution (B):** Browser looks up `www.google.com` → IP.
2. **IP & Port (C):** Browser now knows to connect to `172.217.12.46` on port `443`.
3. **TCP 3‑Way Handshake (D):** SYN → SYN‑ACK → ACK establishes a reliable channel.
4. **TLS Handshake (E):** ClientHello/ServerHello, cert exchange, key derivation → encryption enabled.
5. **Firewall Inspection (F):** Both client‑side and server‑side firewalls verify the connection is allowed.
6. **Load Balancer (G):** Distributes your encrypted request across Google’s server pool.
7. **Web Server (H):** Receives HTTPS request; serves static assets or proxies to application logic.
8. **Application Server (I):** Generates the dynamic HTML, fetching any needed data.
9. **Database (J):** Application server queries for user info, search indexes, etc., then assembles the page.
