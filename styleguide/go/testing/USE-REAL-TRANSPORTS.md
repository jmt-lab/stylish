---
type: Styleguide Rule
description: |-
  For integration tests over HTTP or RPC, use the real production client
  connected to a test double of the server instead of hand-written fake
  clients.
language: go
category: testing
rule_id: USE-REAL-TRANSPORTS
priority: info
tags:
- testing
- rpc
- integration
- google-style
---
For integration tests over HTTP or RPC, use the real production client
connected to a test double of the server instead of hand-written fake
clients.

## Good

- srv := httptest.NewServer(fakeOperationsHandler())
defer srv.Close()
client := operations.NewClient(srv.URL) // real client

## Bad

- type fakeOperationsClient struct{} // reimplements client behavior by hand
