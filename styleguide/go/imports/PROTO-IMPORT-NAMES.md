---
type: Styleguide Rule
description: |-
  Rename generated protobuf imports with a pb suffix and gRPC stubs with a
  grpc suffix. Prefer descriptive whole-word names over very short ones like
  xpb or pb.
language: go
category: imports
rule_id: PROTO-IMPORT-NAMES
priority: info
tags:
- imports
- protobuf
- grpc
- google-style
---
Rename generated protobuf imports with a pb suffix and gRPC stubs with a
grpc suffix. Prefer descriptive whole-word names over very short ones like
xpb or pb.

## Good

- import (
    foopb "path/to/package/foo_service_go_proto"
    foogrpc "path/to/package/foo_service_go_grpc"
    pushqueueservicepb "path/to/package/push_queue_service_go_proto"
)

## Bad

- import pb "path/to/package/foo_service_go_proto" // ambiguous
- import foo_service_go_proto "path/to/package/foo_service_go_proto"
