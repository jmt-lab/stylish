---
type: Styleguide Rule
description: |-
  Keep every letter of an initialism in the same case (URL/url, ID/id, DB/db,
  XMLAPI/xmlAPI). Initialisms with lowercase letters (iOS, gRPC, DDoS) keep
  their prose form unless exportedness forces a change, then use one case.
language: go
category: naming
rule_id: INITIALISM-CASE
priority: warn
tags:
- initialisms
- acronyms
- google-style
---
Keep every letter of an initialism in the same case (URL/url, ID/id, DB/db,
XMLAPI/xmlAPI). Initialisms with lowercase letters (iOS, gRPC, DDoS) keep
their prose form unless exportedness forces a change, then use one case.

## Good

- func ServeHTTP(w http.ResponseWriter, r *http.Request)
- userID, xmlAPI, urlPony := 1, newAPI(), "pony"
- type GRPCClient struct{}
- iOSVersion := "17"

## Bad

- func ServeHttp(w http.ResponseWriter, r *http.Request)
- userId, xmlApi := 1, newAPI()
- type GrpcClient struct{}
- var Ios string
