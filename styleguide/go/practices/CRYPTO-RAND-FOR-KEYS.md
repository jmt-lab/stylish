---
type: Styleguide Rule
description: |-
  Never use math/rand to generate keys or tokens, even throwaway ones; it is
  predictable. Use crypto/rand and encode the bytes as hex or base64 if you
  need text.
language: go
category: practices
rule_id: CRYPTO-RAND-FOR-KEYS
priority: error
tags:
- security
- randomness
- google-style
---
Never use math/rand to generate keys or tokens, even throwaway ones; it is
predictable. Use crypto/rand and encode the bytes as hex or base64 if you
need text.

## Good

- import "crypto/rand"

func Key() string {
    buf := make([]byte, 16)
    if _, err := rand.Read(buf); err != nil {
        log.Fatalf("Out of randomness: %v", err)
    }
    return hex.EncodeToString(buf)
}

## Bad

- import "math/rand"

func Key() string { return fmt.Sprintf("%x", rand.Int63()) } // predictable
