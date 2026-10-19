# OmniWrap TypeScript API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6IjU2ZDRmMDhmN2FkMzg0ZTI0NzZmMTMxY2MzY2I2YzlkYTFkMjk0NTg2NWI0Y2QzODJlZWNhMzMwY2NkYTg4MDgiLCJvcGVyYXRpb25fY291bnQiOjE2LCJyZW5kZXJlciI6InR5cGVzY3JpcHQiLCJ2ZXJzaW9uIjoiMS40LjAifQ -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `56d4f08f7ad384e2476f131cc3cb6c9da1d2945865b4cd382eeca330ccda8808`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **verified**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`new Client({ hooks })` registers four callbacks. Every attempt starts with `beforeRequest` and ends with exactly one of `onRetry` (another attempt follows), `afterResponse` (the success the call returns) or `onError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. `beforeRequest` is the one hook that may change the request (the documented per-request credential contract, which also reads credentials masked); the other three receive frozen `HookContext` copies.

`new Client({ tracer })` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `ApiError`
- `Artifact`
- `CancelRequest`
- `CancellationReceipt`
- `ConfigurationRequest`
- `ConfigurationRevision`
- `Cursor`
- `Diagnostic`
- `ErrorDetail`
- `EventPage`
- `Evidence`
- `EvidenceBinding`
- `EvidencePage`
- `ExecutionBinding`
- `GateReport`
- `GateStatus`
- `LogEntry`
- `LogPage`
- `ObservedPhase`
- `OpaqueId`
- `Preview`
- `PreviewEvent`
- `PreviewInputs`
- `PreviewPage`
- `PreviewRequest`
- `PreviewState`
- `PrimaryArtifacts`
- `ProfileId`
- `Project`
- `ProjectPage`
- `Sha256`
- `SourceRevision`
- `StrongEtag`
- `Timestamp`
- `UserContext`

## Resource `artifacts`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhcnRpZmFjdHMuZ2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QXJ0aWZhY3QiLCJwYXRoIjoiL3YxL3Byb2plY3RzL3twcm9qZWN0SWR9L2FydGlmYWN0cy97YXJ0aWZhY3RJZH0iLCJyZXNvdXJjZSI6ImFydGlmYWN0cyIsInNlY3Rpb25fc2hhMjU2IjoiZjA4NmQ5NjUyOGViZDgzNzJjNjJhYzY2MzgzZmU1NjZlM2Y2NzNlNmNkZWYxN2I3MWRhOTgwOTM1YjI1MjRiOCIsInNpZ25hdHVyZV9zaGEyNTYiOiJjZGZkNDExN2FmMTAzOWRjODUxYTU0ODJlZjhhNzU1Yzc0M2Q4NWVmNjA1MzZjMGE2Yzc4OTczMzJkNTcxNjRmIn0 -->
### `client.artifacts.get`

Operation ID: `getArtifact`  
Route: `GET` `/v1/projects/{projectId}/artifacts/{artifactId}`  

#### Signature

```typescript
client.artifacts.get<Raw extends boolean = false>(projectId: OpaqueId, artifactId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<Artifact, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : WithRequestId<Artifact>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `artifactId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (Artifact) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "artifactId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.artifacts.get("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBcnRpZmFjdCJ9 -->

## Resource `configurations`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb25maWd1cmF0aW9ucy5jcmVhdGVSZXZpc2lvbiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVDb25maWd1cmF0aW9uUmV2aXNpb24iLCJwYXRoIjoiL3YxL3Byb2plY3RzL3twcm9qZWN0SWR9L2NvbmZpZ3VyYXRpb24tcmV2aXNpb25zIiwicmVzb3VyY2UiOiJjb25maWd1cmF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiODcwZTc3MDA2Y2UyYWRlMzM5MDRiZWQ5NmYxOGRhNDVmYTI5OWYzNzBlYmI4ZmU1OTM3YjhjMDkwMWRkOWNhOSIsInNpZ25hdHVyZV9zaGEyNTYiOiIyMGU1MDYwMmQyNDhlODRjMGVmNGRiYmFiOWQ3OTkzMjk3MTM0YzNkM2RiOGJlMzJjZGQxMGM2ZmFhNjM3ZmUwIn0 -->
### `client.configurations.createRevision`

Operation ID: `createConfigurationRevision`  
Route: `POST` `/v1/projects/{projectId}/configuration-revisions`  

#### Signature

```typescript
client.configurations.createRevision<Raw extends boolean = false>(projectId: OpaqueId, If_Match: StrongEtag, Idempotency_Key: string, X_CSRF_Token: string, body: ConfigurationRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<ConfigurationRevision, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : WithRequestId<ConfigurationRevision>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `If-Match` | `header` | yes | `StrongEtag` | Exactly one strong ETag. Configuration activation and preview creation compare the current Project ETag, including first activation. Cancellation compares the Preview ETag. Stale = 412; absent = 428. Wildcard, weak tags and lists are rejected. |
| `Idempotency-Key` | `header` | yes | `string` | Required on every mutation. Scope = organization + project + operation; fingerprint includes raw body bytes, media type, resource and If-Match. Same key/content replays the same receipt; changed content is 409. Retained for 86400 seconds; reconcile an ambiguous outcome within retention before retry, never silently allocate a new key. |
| `X-CSRF-Token` | `header` | yes | `string` | Session-bound synchronizer token from the trusted BFF bootstrap, independent of the unreadable session cookie. Validate same-origin Origin and CSRF before mutation. This contract does not implement or provision the session/CSRF exchange. |
| `body` | body | yes | `ConfigurationRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created and atomically activated after admitted engine resolution; response ETag identifies the immutable configuration. Reload Project to obtain the new Project ETag. | application/json (ConfigurationRevision) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `409` | idempotency_conflict/reconcile_idempotency, binding_conflict/refresh_snapshot, or retry_requires_reconciliation/refresh_snapshot. No additional effect. | application/json (allOf&lt;ApiError, object&gt;) |
| `412` | precondition_failed; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `413` | request_too_large; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `415` | unsupported_media_type; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `428` | precondition_required; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "body": {
    "profileId": "openapi-typescript-preview/1",
    "sourceRevisionId": "example"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "header",
      "name": "If-Match",
      "value": "\"A\""
    },
    {
      "in": "header",
      "name": "Idempotency-Key",
      "value": "AAAAAAAAAAAAAAAA"
    },
    {
      "in": "header",
      "name": "X-CSRF-Token",
      "value": "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.configurations.createRevision("example", "\"A\"", "AAAAAAAAAAAAAAAA", "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA", {"profileId": "openapi-typescript-preview/1", "sourceRevisionId": "example"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb25maWd1cmF0aW9uUmV2aXNpb24ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb25maWd1cmF0aW9ucy5nZXRSZXZpc2lvbiIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldENvbmZpZ3VyYXRpb25SZXZpc2lvbiIsInBhdGgiOiIvdjEvcHJvamVjdHMve3Byb2plY3RJZH0vY29uZmlndXJhdGlvbi1yZXZpc2lvbnMve3JldmlzaW9uSWR9IiwicmVzb3VyY2UiOiJjb25maWd1cmF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNGE1OTU1OTc5YjhlYTllNWU3ZjI5M2ViYmMyMDdiM2Q4NDA2NzRmNjYzODg3Y2FmMzY3YjcwZjg2ZThjNzY3YiIsInNpZ25hdHVyZV9zaGEyNTYiOiI1YmVmMzI0ZmY0YWEwOTZhOTFhNjE3MjhlMDYxMjMyYWIzZWFlMGFkYWI1MGI3ZDZmMGQ1N2FiOWFmM2QyYWFkIn0 -->
### `client.configurations.getRevision`

Operation ID: `getConfigurationRevision`  
Route: `GET` `/v1/projects/{projectId}/configuration-revisions/{revisionId}`  

#### Signature

```typescript
client.configurations.getRevision<Raw extends boolean = false>(projectId: OpaqueId, revisionId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<ConfigurationRevision, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : WithRequestId<ConfigurationRevision>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `revisionId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (ConfigurationRevision) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "revisionId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.configurations.getRevision("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDb25maWd1cmF0aW9uUmV2aXNpb24ifQ -->

## Resource `context`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb250ZXh0LmdldFVzZXIiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRVc2VyQ29udGV4dCIsInBhdGgiOiIvdjEvbWUvY29udGV4dCIsInJlc291cmNlIjoiY29udGV4dCIsInNlY3Rpb25fc2hhMjU2IjoiM2FhZjAzYzBmZjQyODdjNTY2ZTViMGVhYzMxMzhjMGYyMzA5NTk1NDVkZTEzZTEyMTIzN2MzNzU4YmY0ZDI5NSIsInNpZ25hdHVyZV9zaGEyNTYiOiIzZDk3NTdlMTJhNDQ4MTIyZTNlYzBjMDNiOTRmMTkxODk5M2U1YzFlYzFmZWEzNTQ0ODA2ZDYwYWQ1OWM2OTMxIn0 -->
### `client.context.getUser`

Operation ID: `getUserContext`  
Route: `GET` `/v1/me/context`  

#### Signature

```typescript
client.context.getUser<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<UserContext, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<UserContext>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (UserContext) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.context.getUser();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRVc2VyQ29udGV4dCJ9 -->

## Resource `evidence`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJldmlkZW5jZS5nZXQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRFdmlkZW5jZSIsInBhdGgiOiIvdjEvcHJvamVjdHMve3Byb2plY3RJZH0vZXZpZGVuY2Uve2V2aWRlbmNlSWR9IiwicmVzb3VyY2UiOiJldmlkZW5jZSIsInNlY3Rpb25fc2hhMjU2IjoiYWQwY2FlYmU1ODhmZGEyZjg4YWI2MjY5MWJjNzE4Y2ZiMmRmYjY3Y2I4ODliMWI4ZDY4NTg4YTEzY2VmYmI1MyIsInNpZ25hdHVyZV9zaGEyNTYiOiJjZTJiNzlhYjE3MjkwNmMyNDc5ODcwYTI5OTBmZjU4YTUyM2YyN2FmNzg2MWI1MjUzN2E0MjQ4ZTRkYWQyMjI3In0 -->
### `client.evidence.get`

Operation ID: `getEvidence`  
Route: `GET` `/v1/projects/{projectId}/evidence/{evidenceId}`  

#### Signature

```typescript
client.evidence.get<Raw extends boolean = false>(projectId: OpaqueId, evidenceId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<Evidence, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : Evidence>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `evidenceId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (Evidence) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "evidenceId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.evidence.get("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRFdmlkZW5jZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJldmlkZW5jZS5saXN0UHJldmlldyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RQcmV2aWV3RXZpZGVuY2UiLCJwYXRoIjoiL3YxL3Byb2plY3RzL3twcm9qZWN0SWR9L3ByZXZpZXdzL3twcmV2aWV3SWR9L2V2aWRlbmNlIiwicmVzb3VyY2UiOiJldmlkZW5jZSIsInNlY3Rpb25fc2hhMjU2IjoiNjA2Yjg1M2I0ZmJjZDA0ZDUyNzRhMTYyOThjYjA4MDU4NmIzYzI0M2JiOGQ4ZmM3MzZjMDdiOTAwY2Q4M2U2YiIsInNpZ25hdHVyZV9zaGEyNTYiOiJiMGI3YzE5YTlhMWYyYjhmMWZkNmQ2MmI0MmVmZTM2Njc2MjdlNDczZTkxMGU5Zjg5YjM1NzNlNWY2MDEyZGVjIn0 -->
### `client.evidence.listPreview`

Operation ID: `listPreviewEvidence`  
Route: `GET` `/v1/projects/{projectId}/previews/{previewId}/evidence`  

#### Signature

```typescript
client.evidence.listPreview<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<EvidencePage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<EvidencePage>>;
client.evidence.listPreview<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, limit?: number, gateId?: string, availability?: "available" | "missing" | "expired" | "hash_mismatch", requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<EvidencePage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<EvidencePage>>;
client.evidence.listPreview<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, gateId?: string, availability?: "available" | "missing" | "expired" | "hash_mismatch", requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<EvidencePage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<EvidencePage>>;
client.evidence.listPreview<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, limit?: number, availability?: "available" | "missing" | "expired" | "hash_mismatch", requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<EvidencePage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<EvidencePage>>;
client.evidence.listPreview<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, limit?: number, gateId?: string, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<EvidencePage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<EvidencePage>>;
client.evidence.listPreview<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, limit?: number, gateId?: string, availability?: "available" | "missing" | "expired" | "hash_mismatch", requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<EvidencePage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<EvidencePage>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `previewId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `cursor` | `query` | no | `Cursor` | Opaque scope-bound continuation, never an offset or authority token. Expired/gap = 410 refresh_snapshot; invalid/tampered/wrong filters = 422. Denied objects remain uniform404. |
| `limit` | `query` | no | `integer` | Maximum page size; default 50. |
| `gateId` | `query` | no | `string` |  |
| `availability` | `query` | no | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (EvidencePage) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `410` | cursor_expired; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "previewId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.evidence.listPreview("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UHJldmlld0V2aWRlbmNlIn0 -->

## Resource `previews`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcmV2aWV3cy5jYW5jZWwiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY2FuY2VsUHJldmlldyIsInBhdGgiOiIvdjEvcHJvamVjdHMve3Byb2plY3RJZH0vcHJldmlld3Mve3ByZXZpZXdJZH0vY2FuY2VsIiwicmVzb3VyY2UiOiJwcmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiNzc0ZTM3N2Y0OTQ1NGViMTgwNTI4ODJhOGZmMDM4ZWViNTE1Yzc1Zjg1NDY5ZDhjNjg3YzYzNTlmNzM4ODAwMSIsInNpZ25hdHVyZV9zaGEyNTYiOiIzYTllODJlMWQyOWY4MjBjNDBjZmRiODkwYzk4M2EwNmIxZmIxYzRjZmVkOTgyMDAxMTdiNDA1Mzc3NjE2OWFkIn0 -->
### `client.previews.cancel`

Operation ID: `cancelPreview`  
Route: `POST` `/v1/projects/{projectId}/previews/{previewId}/cancel`  

#### Signature

```typescript
client.previews.cancel<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, If_Match: StrongEtag, Idempotency_Key: string, X_CSRF_Token: string, body: CancelRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<CancellationReceipt, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<CancellationReceipt>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `previewId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `If-Match` | `header` | yes | `StrongEtag` | Exactly one strong ETag. Configuration activation and preview creation compare the current Project ETag, including first activation. Cancellation compares the Preview ETag. Stale = 412; absent = 428. Wildcard, weak tags and lists are rejected. |
| `Idempotency-Key` | `header` | yes | `string` | Required on every mutation. Scope = organization + project + operation; fingerprint includes raw body bytes, media type, resource and If-Match. Same key/content replays the same receipt; changed content is 409. Retained for 86400 seconds; reconcile an ambiguous outcome within retention before retry, never silently allocate a new key. |
| `X-CSRF-Token` | `header` | yes | `string` | Session-bound synchronizer token from the trusted BFF bootstrap, independent of the unreadable session cookie. Validate same-origin Origin and CSRF before mutation. This contract does not implement or provision the session/CSRF exchange. |
| `body` | body | yes | `CancelRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `202` | Accepted for asynchronous processing; not a completed effect. | application/json (CancellationReceipt) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `409` | idempotency_conflict/reconcile_idempotency, binding_conflict/refresh_snapshot, or retry_requires_reconciliation/refresh_snapshot. No additional effect. | application/json (allOf&lt;ApiError, object&gt;) |
| `412` | precondition_failed; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `413` | request_too_large; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `415` | unsupported_media_type; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `428` | precondition_required; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "body": {
    "reason": "user_requested"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "previewId",
      "value": "example"
    },
    {
      "in": "header",
      "name": "If-Match",
      "value": "\"A\""
    },
    {
      "in": "header",
      "name": "Idempotency-Key",
      "value": "AAAAAAAAAAAAAAAA"
    },
    {
      "in": "header",
      "name": "X-CSRF-Token",
      "value": "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.previews.cancel("example", "example", "\"A\"", "AAAAAAAAAAAAAAAA", "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA", {"reason": "user_requested"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjYW5jZWxQcmV2aWV3In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcmV2aWV3cy5jcmVhdGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlUHJldmlldyIsInBhdGgiOiIvdjEvcHJvamVjdHMve3Byb2plY3RJZH0vcHJldmlld3MiLCJyZXNvdXJjZSI6InByZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiJlZmEwNmNmMTEyNTdlMGVjNTFiYTc2ZmM2MDczYjg3MzYwNzBkYzkwYzhkYjViNWI5NWZhOWFkMmQwNjg4MDVkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjFmZmVkNGFlMzVlN2M5ZjExNWI0MjViMjU3M2JkM2QyYzVmYmI5MmQzNmVmN2RlZTEyNWU2NDVjMmI3ZmU1N2UifQ -->
### `client.previews.create`

Operation ID: `createPreview`  
Route: `POST` `/v1/projects/{projectId}/previews`  

#### Signature

```typescript
client.previews.create<Raw extends boolean = false>(projectId: OpaqueId, If_Match: StrongEtag, Idempotency_Key: string, X_CSRF_Token: string, body: PreviewRequest, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" }): Promise<Raw extends true ? RawResponse<Preview, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : WithRequestId<Preview>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `If-Match` | `header` | yes | `StrongEtag` | Exactly one strong ETag. Configuration activation and preview creation compare the current Project ETag, including first activation. Cancellation compares the Preview ETag. Stale = 412; absent = 428. Wildcard, weak tags and lists are rejected. |
| `Idempotency-Key` | `header` | yes | `string` | Required on every mutation. Scope = organization + project + operation; fingerprint includes raw body bytes, media type, resource and If-Match. Same key/content replays the same receipt; changed content is 409. Retained for 86400 seconds; reconcile an ambiguous outcome within retention before retry, never silently allocate a new key. |
| `X-CSRF-Token` | `header` | yes | `string` | Session-bound synchronizer token from the trusted BFF bootstrap, independent of the unreadable session cookie. Validate same-origin Origin and CSRF before mutation. This contract does not implement or provision the session/CSRF exchange. |
| `body` | body | yes | `PreviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `202` | Accepted for asynchronous processing; not a completed effect. | application/json (Preview) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `409` | idempotency_conflict/reconcile_idempotency, binding_conflict/refresh_snapshot, or retry_requires_reconciliation/refresh_snapshot. No additional effect. | application/json (allOf&lt;ApiError, object&gt;) |
| `412` | precondition_failed; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `413` | request_too_large; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `415` | unsupported_media_type; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `428` | precondition_required; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "body": {
    "configurationRevisionId": "example"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "header",
      "name": "If-Match",
      "value": "\"A\""
    },
    {
      "in": "header",
      "name": "Idempotency-Key",
      "value": "AAAAAAAAAAAAAAAA"
    },
    {
      "in": "header",
      "name": "X-CSRF-Token",
      "value": "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.previews.create("example", "\"A\"", "AAAAAAAAAAAAAAAA", "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA", {"configurationRevisionId": "example"}, { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVQcmV2aWV3In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcmV2aWV3cy5nZXQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRQcmV2aWV3IiwicGF0aCI6Ii92MS9wcm9qZWN0cy97cHJvamVjdElkfS9wcmV2aWV3cy97cHJldmlld0lkfSIsInJlc291cmNlIjoicHJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6IjE3N2MwYWRiMDg3ZmM3MGNhYzY4ZjI1MWNjODM0MTI3NDRiMmQxYTgzMzNkNGQ3MGJlOTQyNDNjNzFjZDhiYjQiLCJzaWduYXR1cmVfc2hhMjU2IjoiZjZiZjFmNDhhNTFhNjk2MjQxY2FkZGY5NzQ2OTg4M2M0YmRmOWI2ZTcxYjc0MGQwZmJlYjdlMjc2ZGIzN2FlZCJ9 -->
### `client.previews.get`

Operation ID: `getPreview`  
Route: `GET` `/v1/projects/{projectId}/previews/{previewId}`  

#### Signature

```typescript
client.previews.get<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<Preview, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : WithRequestId<Preview>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `previewId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (Preview) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "previewId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.previews.get("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQcmV2aWV3In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcmV2aWV3cy5nZXRFdmVudHMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRQcmV2aWV3RXZlbnRzIiwicGF0aCI6Ii92MS9wcm9qZWN0cy97cHJvamVjdElkfS9wcmV2aWV3cy97cHJldmlld0lkfS9ldmVudHMiLCJyZXNvdXJjZSI6InByZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiIyMzE4Mzg3ZTRlNGY4YTEyOWFiZDI0MGNlYzBmYTYwZjRlMDI0NzUyYzQ2MzU4OWVlZWQzM2YwNjY4ZTg1NmMyIiwic2lnbmF0dXJlX3NoYTI1NiI6IjkxZDc5YjA4ZjBjMDNkMjM5MzcyODUzMTA0MjJiNGY3NDY2MjFmNzllOWJlZWU5ZDYzMjI1MGZhNWI1MjMxYjUifQ -->
### `client.previews.getEvents`

Operation ID: `getPreviewEvents`  
Route: `GET` `/v1/projects/{projectId}/previews/{previewId}/events`  

#### Signature

```typescript
client.previews.getEvents<Raw extends boolean = false, StreamResponse extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, optionalArguments?: { cursor?: Cursor; limit?: number; Last_Event_ID?: Cursor }, requestOptions?: RequestOptions<Raw> & { streamResponse?: StreamResponse }): Promise<Raw extends true ? RawResponse<EventPage | AsyncIterable<SSEEvent<string>>, { "cache-control"?: string; "x-accel-buffering"?: string; "x-correlation-id"?: string; }> : StreamResponse extends true ? AsyncIterable<SSEEvent<string>> : StreamResponse extends false ? EventPage : EventPage | AsyncIterable<SSEEvent<string>>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `previewId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `cursor` | `query` | no | `Cursor` | Opaque scope-bound continuation, never an offset or authority token. Expired/gap = 410 refresh_snapshot; invalid/tampered/wrong filters = 422. Denied objects remain uniform404. |
| `limit` | `query` | no | `integer` | Maximum page size; default 50. |
| `Last-Event-ID` | `header` | no | `Cursor` | SSE resume cursor; replay begins strictly after it. If query cursor also occurs the two must match, otherwise 422. Reauthorization is mandatory on reconnect. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (EventPage), text/event-stream (string) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `410` | cursor_expired; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "previewId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.previews.getEvents("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQcmV2aWV3RXZlbnRzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcmV2aWV3cy5nZXRMb2dzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0UHJldmlld0xvZ3MiLCJwYXRoIjoiL3YxL3Byb2plY3RzL3twcm9qZWN0SWR9L3ByZXZpZXdzL3twcmV2aWV3SWR9L2xvZ3MiLCJyZXNvdXJjZSI6InByZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiIyMTk5NGZjMmZiOTJkZDRlYWJiMDBhN2E3MmRlMmEyYjY1YzA3Y2JiMTA4ZGE4YmY4MDZiYjU3NDdiOGVjYzRmIiwic2lnbmF0dXJlX3NoYTI1NiI6IjA1NzcyNzJkM2I5MDkzYTg1ZDNkYzgyN2NmZTMyMmZlYTQxNDhjOGM4NDg5OWEyZjg5NjgzMDFlN2QzZGQwNmYifQ -->
### `client.previews.getLogs`

Operation ID: `getPreviewLogs`  
Route: `GET` `/v1/projects/{projectId}/previews/{previewId}/logs`  

#### Signature

```typescript
client.previews.getLogs<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<LogPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<LogPage>>;
client.previews.getLogs<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, limit?: number, level?: "info" | "warning" | "error", phaseId?: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<LogPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<LogPage>>;
client.previews.getLogs<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, level?: "info" | "warning" | "error", phaseId?: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<LogPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<LogPage>>;
client.previews.getLogs<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, limit?: number, phaseId?: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<LogPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<LogPage>>;
client.previews.getLogs<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, limit?: number, level?: "info" | "warning" | "error", requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<LogPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<LogPage>>;
client.previews.getLogs<Raw extends boolean = false>(projectId: OpaqueId, previewId: OpaqueId, cursor?: Cursor, limit?: number, level?: "info" | "warning" | "error", phaseId?: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<LogPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<LogPage>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `previewId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `cursor` | `query` | no | `Cursor` | Opaque scope-bound continuation, never an offset or authority token. Expired/gap = 410 refresh_snapshot; invalid/tampered/wrong filters = 422. Denied objects remain uniform404. |
| `limit` | `query` | no | `integer` | Maximum page size; default 50. |
| `level` | `query` | no | `string` |  |
| `phaseId` | `query` | no | `OpaqueId` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (LogPage) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `410` | cursor_expired; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "previewId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.previews.getLogs("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQcmV2aWV3TG9ncyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcmV2aWV3cy5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFByZXZpZXdzIiwicGF0aCI6Ii92MS9wcm9qZWN0cy97cHJvamVjdElkfS9wcmV2aWV3cyIsInJlc291cmNlIjoicHJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6ImI1Y2Q0NzA5MzYzYTk2MDJlN2QzZmYzMDIxZmUyODc5MzEwNWRmZjAxZDExYTMwNjk4OTVjODE0YzE5YjU2M2UiLCJzaWduYXR1cmVfc2hhMjU2IjoiYmM3NGJiNTE0NDJiN2E4Nzk3MDFiNTRkMGQ0NDhmNmFhYzJlODc4YmFjODBlMTNjZDZlMDliNTc1YjVmYTAwZCJ9 -->
### `client.previews.list`

Operation ID: `listPreviews`  
Route: `GET` `/v1/projects/{projectId}/previews`  

#### Signature

```typescript
client.previews.list<Raw extends boolean = false>(projectId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<PreviewPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<PreviewPage>>;
client.previews.list<Raw extends boolean = false>(projectId: OpaqueId, limit?: number, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<PreviewPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<PreviewPage>>;
client.previews.list<Raw extends boolean = false>(projectId: OpaqueId, cursor?: Cursor, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<PreviewPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<PreviewPage>>;
client.previews.list<Raw extends boolean = false>(projectId: OpaqueId, cursor?: Cursor, limit?: number, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<PreviewPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<PreviewPage>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `cursor` | `query` | no | `Cursor` | Opaque scope-bound continuation, never an offset or authority token. Expired/gap = 410 refresh_snapshot; invalid/tampered/wrong filters = 422. Denied objects remain uniform404. |
| `limit` | `query` | no | `integer` | Maximum page size; default 50. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (PreviewPage) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `410` | cursor_expired; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.previews.list("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UHJldmlld3MifQ -->

## Resource `projects`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcm9qZWN0cy5nZXQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRQcm9qZWN0IiwicGF0aCI6Ii92MS9wcm9qZWN0cy97cHJvamVjdElkfSIsInJlc291cmNlIjoicHJvamVjdHMiLCJzZWN0aW9uX3NoYTI1NiI6ImMzNWQ0NWZlOWY5MjM2MmY4ODhlZTg0ODBmNzBjZGJjYzU2N2NlNTAyMWE2Y2RiMjJjZWFlNDE4YmUzNTE4MjEiLCJzaWduYXR1cmVfc2hhMjU2IjoiMTU5YTQzY2IxZDg4MmJmZmE4MjQ1YzIwOWM0ZGY3NWM0ZThhODBjM2VhMWMzNTAxNDVlYjc1MjhkZTc2NDdlNiJ9 -->
### `client.projects.get`

Operation ID: `getProject`  
Route: `GET` `/v1/projects/{projectId}`  

#### Signature

```typescript
client.projects.get<Raw extends boolean = false>(projectId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<Project, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : WithRequestId<Project>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (Project) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.projects.get("example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQcm9qZWN0In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwcm9qZWN0cy5saXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFByb2plY3RzIiwicGF0aCI6Ii92MS9wcm9qZWN0cyIsInJlc291cmNlIjoicHJvamVjdHMiLCJzZWN0aW9uX3NoYTI1NiI6IjI0ZjA3ZmVkZmRhMjZmNGE0NGI0ZGY5NDJkMmY4ZGI0ZjBhOWE2MDliYzNiYjcyNDJiMmVhNzRlOWRlNzcxNzMiLCJzaWduYXR1cmVfc2hhMjU2IjoiYzJmMTk1MDhkMGM5MWM4M2Y4ZDU1OTg3N2ZmMDI1ZGRkYjhiMTA0OTI0Y2Q4ZDBmZGNiMGU5MjNmYmRhZjYzNiJ9 -->
### `client.projects.list`

Operation ID: `listProjects`  
Route: `GET` `/v1/projects`  

#### Signature

```typescript
client.projects.list<Raw extends boolean = false>(requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<ProjectPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<ProjectPage>>;
client.projects.list<Raw extends boolean = false>(limit?: number, query?: string, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<ProjectPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<ProjectPage>>;
client.projects.list<Raw extends boolean = false>(cursor?: Cursor, query?: string, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<ProjectPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<ProjectPage>>;
client.projects.list<Raw extends boolean = false>(cursor?: Cursor, limit?: number, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<ProjectPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<ProjectPage>>;
client.projects.list<Raw extends boolean = false>(cursor?: Cursor, limit?: number, query?: string, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<ProjectPage, { "cache-control"?: string; "x-correlation-id"?: string; }> : WithRequestId<ProjectPage>>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `cursor` | `query` | no | `Cursor` | Opaque scope-bound continuation, never an offset or authority token. Expired/gap = 410 refresh_snapshot; invalid/tampered/wrong filters = 422. Denied objects remain uniform404. |
| `limit` | `query` | no | `integer` | Maximum page size; default 50. |
| `query` | `query` | no | `string` | Display-name substring filter, case-insensitive Unicode NFC matching. Bound to pagination cursor. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (ProjectPage) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `410` | cursor_expired; recovery=refresh_snapshot. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.projects.list();
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UHJvamVjdHMifQ -->

## Resource `sources`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzb3VyY2VzLmNyZWF0ZVJldmlzaW9uIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZVNvdXJjZVJldmlzaW9uIiwicGF0aCI6Ii92MS9wcm9qZWN0cy97cHJvamVjdElkfS9zb3VyY2UtcmV2aXNpb25zIiwicmVzb3VyY2UiOiJzb3VyY2VzIiwic2VjdGlvbl9zaGEyNTYiOiI4NjA1MTA0Y2NjMjU3OGY1MWI0M2QyOGFiODU4NjI1NWJmNDA1ZDI3Mzg5NzhkNWQ0ZDg5ZmNlODcxZjVhMzlkIiwic2lnbmF0dXJlX3NoYTI1NiI6IjA0MzdiMGM2NWMwYmMxMGMyNGRmNmUwN2E4NDMzZGU2MzRkYjJhYjQ2MDVjMmRlODEwOTk5ODgzYTVjY2NmNmEifQ -->
### `client.sources.createRevision`

Operation ID: `createSourceRevision`  
Route: `POST` `/v1/projects/{projectId}/source-revisions`  

#### Signature

```typescript
client.sources.createRevision<Raw extends boolean = false>(projectId: OpaqueId, Idempotency_Key: string, X_CSRF_Token: string, displayName: string, body: unknown | string, requestOptions?: RequestOptions<Raw> & { contentType?: "application/json" | "application/yaml" }): Promise<Raw extends true ? RawResponse<SourceRevision, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : SourceRevision>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `Idempotency-Key` | `header` | yes | `string` | Required on every mutation. Scope = organization + project + operation; fingerprint includes raw body bytes, media type, resource and If-Match. Same key/content replays the same receipt; changed content is 409. Retained for 86400 seconds; reconcile an ambiguous outcome within retention before retry, never silently allocate a new key. |
| `X-CSRF-Token` | `header` | yes | `string` | Session-bound synchronizer token from the trusted BFF bootstrap, independent of the unreadable session cookie. Validate same-origin Origin and CSRF before mutation. This contract does not implement or provision the session/CSRF exchange. |
| `displayName` | `query` | yes | `string` | Escaped display text only, never used as a filename or storage key; included in idempotency fingerprint. |
| `body` | body | yes | `any` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `202` | Accepted for asynchronous processing; not a completed effect. | application/json (SourceRevision) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `409` | idempotency_conflict/reconcile_idempotency, binding_conflict/refresh_snapshot, or retry_requires_reconciliation/refresh_snapshot. No additional effect. | application/json (allOf&lt;ApiError, object&gt;) |
| `413` | request_too_large; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `415` | unsupported_media_type; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "body": "example",
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "header",
      "name": "Idempotency-Key",
      "value": "AAAAAAAAAAAAAAAA"
    },
    {
      "in": "header",
      "name": "X-CSRF-Token",
      "value": "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
    },
    {
      "in": "query",
      "name": "displayName",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.sources.createRevision("example", "AAAAAAAAAAAAAAAA", "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA", "example", "example", { contentType: "application/json" });
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVTb3VyY2VSZXZpc2lvbiJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzb3VyY2VzLmdldFJldmlzaW9uIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0U291cmNlUmV2aXNpb24iLCJwYXRoIjoiL3YxL3Byb2plY3RzL3twcm9qZWN0SWR9L3NvdXJjZS1yZXZpc2lvbnMve3JldmlzaW9uSWR9IiwicmVzb3VyY2UiOiJzb3VyY2VzIiwic2VjdGlvbl9zaGEyNTYiOiJhYjJmMDk0N2Q2OWFlNmRkNmE5YjFjMzhlZjk2YzJlZThiNTk1NjljMDExNDAyOTkwZjQzZGZiOWJjZTZiZWQ0Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjYwN2E4ZTU4ODQ2OGFkZTc5YzkzNmYyOWI2Njk3Nzg2MmFlNWVhMzMwNjJkNmY3MjJkMjA2OTJmOTFiNzZjZDEifQ -->
### `client.sources.getRevision`

Operation ID: `getSourceRevision`  
Route: `GET` `/v1/projects/{projectId}/source-revisions/{revisionId}`  

#### Signature

```typescript
client.sources.getRevision<Raw extends boolean = false>(projectId: OpaqueId, revisionId: OpaqueId, requestOptions?: RequestOptions<Raw>): Promise<Raw extends true ? RawResponse<SourceRevision, { "cache-control"?: string; "etag"?: string; "x-correlation-id"?: string; }> : SourceRevision>;
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |
| `revisionId` | `path` | yes | `OpaqueId` | Opaque identity; authorize organization/project and verify every parent relation before lookup or mutation. Knowledge of an ID grants no access. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized resource snapshot. | application/json (SourceRevision) |
| `401` | unauthenticated; recovery=authenticate. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `403` | forbidden; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `404` | not_found; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `406` | not_acceptable; recovery=none. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `422` | invalid_request, source_not_valid or cursor_invalid; never reinterpret an invalid source as ready. | application/json (allOf&lt;ApiError, object&gt;) |
| `429` | rate_limited; recovery=retry_same_request. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `500` | internal_error; recovery=reconcile_idempotency. See the normative error mapping and operation retry policy. | application/json (allOf&lt;ApiError, object&gt;) |
| `503` | configuration_required/configure_authority when approved JackAI exchange or product configuration is absent; authority_unavailable/retry_same_request on outage/timeout. No fallback identity, cached authorization or synthetic data. | application/json (allOf&lt;ApiError, object&gt;) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "projectId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "revisionId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```typescript
const result = await client.sources.getRevision("example", "example");
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTb3VyY2VSZXZpc2lvbiJ9 -->

