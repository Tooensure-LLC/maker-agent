# Maker input and output

The command is `/maker:make`. Its input is validated by `input.schema.json`; its role-owned output is validated by `output.schema.json`.

The raw seed is carried verbatim from the original request. This phase receives only its declared prior result: plan_ref and one authorized_step with step_id, scope, and authorization_ref. `phase` is command metadata and is not a separate skill input field. The role emits only the `maker.result` message kind.

The API adapter serializes the typed command input into the protobuf `PhaseRequest.payload` string. `PhaseReply` remains exactly `{ verdict, reason, evidence_reference }`. See the repository-level API/Trail contract before changing either boundary.

## Plugin mention

The first emitted line of the message is the plugin mention. Its plain form is `@maker`; its exact link form for hosts that render mentions is `[@maker](plugin://maker@maker-agent)`.
