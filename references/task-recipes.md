# Agent task recipes

Corpus SHA-256: `681581c9e3d3f3525520c7923978bcbd967cc8b203e8ec9733c381946c3cc63b`

These recipes are retrieval and planning evidence. They never authorize API execution.

## `authentication-cancelpreview-sessioncookie` — authentication

How is SessionCookie authentication applied to cancelPreview? Cite exactly: operation:cancelPreview, auth:SessionCookie

Intent: Recover the exact authentication scheme, location or flow, and required scopes.

Expected evidence:

- operation: `cancelPreview`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/cancelPreview`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-cancelpreview` — discovery

Find the exact operation cancelPreview (POST /v1/projects/{projectId}/previews/{previewId}/cancel) for cancelPreview. Cite exactly: operation:cancelPreview, schema:ApiError, schema:CancelRequest, schema:CancellationReceipt, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `cancelPreview`
- schema: `ApiError`
- schema: `CancelRequest`
- schema: `CancellationReceipt`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/cancelPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/CancelRequest`
- `omniwrap://semantic/schema/CancellationReceipt`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-createconfigurationrevision` — discovery

Find the exact operation createConfigurationRevision (POST /v1/projects/{projectId}/configuration-revisions) for createConfigurationRevision. Cite exactly: operation:createConfigurationRevision, schema:ApiError, schema:ConfigurationRequest, schema:ConfigurationRevision, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `createConfigurationRevision`
- schema: `ApiError`
- schema: `ConfigurationRequest`
- schema: `ConfigurationRevision`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/createConfigurationRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/ConfigurationRequest`
- `omniwrap://semantic/schema/ConfigurationRevision`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-createpreview` — discovery

Find the exact operation createPreview (POST /v1/projects/{projectId}/previews) for createPreview. Cite exactly: operation:createPreview, schema:ApiError, schema:OpaqueId, schema:Preview, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `createPreview`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `Preview`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/createPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/Preview`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getartifact` — discovery

Find the exact operation getArtifact (GET /v1/projects/{projectId}/artifacts/{artifactId}) for getArtifact. Cite exactly: operation:getArtifact, schema:ApiError, schema:Artifact, schema:OpaqueId, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getArtifact`
- schema: `ApiError`
- schema: `Artifact`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getArtifact`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Artifact`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getconfigurationrevision` — discovery

Find the exact operation getConfigurationRevision (GET /v1/projects/{projectId}/configuration-revisions/{revisionId}) for getConfigurationRevision. Cite exactly: operation:getConfigurationRevision, schema:ApiError, schema:ConfigurationRevision, schema:OpaqueId, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getConfigurationRevision`
- schema: `ApiError`
- schema: `ConfigurationRevision`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getConfigurationRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/ConfigurationRevision`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getevidence` — discovery

Find the exact operation getEvidence (GET /v1/projects/{projectId}/evidence/{evidenceId}) for getEvidence. Cite exactly: operation:getEvidence, schema:ApiError, schema:Evidence, schema:OpaqueId, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getEvidence`
- schema: `ApiError`
- schema: `Evidence`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getEvidence`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Evidence`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getpreview` — discovery

Find the exact operation getPreview (GET /v1/projects/{projectId}/previews/{previewId}) for getPreview. Cite exactly: operation:getPreview, schema:ApiError, schema:OpaqueId, schema:Preview, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getPreview`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `Preview`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/Preview`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getpreviewevents` — discovery

Find the exact operation getPreviewEvents (GET /v1/projects/{projectId}/previews/{previewId}/events) for getPreviewEvents. Cite exactly: operation:getPreviewEvents, schema:ApiError, schema:Cursor, schema:EventPage, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getPreviewEvents`
- schema: `ApiError`
- schema: `Cursor`
- schema: `EventPage`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreviewEvents`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Cursor`
- `omniwrap://semantic/schema/EventPage`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getpreviewlogs` — discovery

Find the exact operation getPreviewLogs (GET /v1/projects/{projectId}/previews/{previewId}/logs) for getPreviewLogs. Cite exactly: operation:getPreviewLogs, schema:ApiError, schema:Cursor, schema:LogPage, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getPreviewLogs`
- schema: `ApiError`
- schema: `Cursor`
- schema: `LogPage`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreviewLogs`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Cursor`
- `omniwrap://semantic/schema/LogPage`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getproject` — discovery

Find the exact operation getProject (GET /v1/projects/{projectId}) for getProject. Cite exactly: operation:getProject, schema:ApiError, schema:OpaqueId, schema:Project, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getProject`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `Project`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getProject`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/Project`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getsourcerevision` — discovery

Find the exact operation getSourceRevision (GET /v1/projects/{projectId}/source-revisions/{revisionId}) for getSourceRevision. Cite exactly: operation:getSourceRevision, schema:ApiError, schema:OpaqueId, schema:SourceRevision, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getSourceRevision`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `SourceRevision`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getSourceRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/SourceRevision`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `discovery-getusercontext` — discovery

Find the exact operation getUserContext (GET /v1/me/context) for getUserContext. Cite exactly: operation:getUserContext, schema:ApiError, schema:OpaqueId, schema:UserContext, auth:SessionCookie

Intent: Identify the operation without inventing a route or method.

Expected evidence:

- operation: `getUserContext`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `UserContext`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getUserContext`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/UserContext`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-cancelpreview` — error-recovery

Which failure responses and error schemas apply to cancelPreview? Cite exactly: operation:cancelPreview, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `cancelPreview`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/cancelPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-createconfigurationrevision` — error-recovery

Which failure responses and error schemas apply to createConfigurationRevision? Cite exactly: operation:createConfigurationRevision, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `createConfigurationRevision`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/createConfigurationRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-createpreview` — error-recovery

Which failure responses and error schemas apply to createPreview? Cite exactly: operation:createPreview, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `createPreview`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/createPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-getartifact` — error-recovery

Which failure responses and error schemas apply to getArtifact? Cite exactly: operation:getArtifact, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `getArtifact`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getArtifact`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-getconfigurationrevision` — error-recovery

Which failure responses and error schemas apply to getConfigurationRevision? Cite exactly: operation:getConfigurationRevision, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `getConfigurationRevision`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getConfigurationRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-getevidence` — error-recovery

Which failure responses and error schemas apply to getEvidence? Cite exactly: operation:getEvidence, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `getEvidence`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getEvidence`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-getpreview` — error-recovery

Which failure responses and error schemas apply to getPreview? Cite exactly: operation:getPreview, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `getPreview`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `error-recovery-getpreviewevents` — error-recovery

Which failure responses and error schemas apply to getPreviewEvents? Cite exactly: operation:getPreviewEvents, schema:ApiError, schema:OpaqueId, auth:SessionCookie

Intent: Recover non-success response selectors and their declared error payloads.

Expected evidence:

- operation: `getPreviewEvents`
- schema: `ApiError`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreviewEvents`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-cancelpreview` — integration

Plan a correct SDK integration for cancelPreview (POST /v1/projects/{projectId}/previews/{previewId}/cancel). Cite exactly: operation:cancelPreview, schema:ApiError, schema:CancelRequest, schema:CancellationReceipt, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `cancelPreview`
- schema: `ApiError`
- schema: `CancelRequest`
- schema: `CancellationReceipt`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/cancelPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/CancelRequest`
- `omniwrap://semantic/schema/CancellationReceipt`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-createconfigurationrevision` — integration

Plan a correct SDK integration for createConfigurationRevision (POST /v1/projects/{projectId}/configuration-revisions). Cite exactly: operation:createConfigurationRevision, schema:ApiError, schema:ConfigurationRequest, schema:ConfigurationRevision, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `createConfigurationRevision`
- schema: `ApiError`
- schema: `ConfigurationRequest`
- schema: `ConfigurationRevision`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/createConfigurationRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/ConfigurationRequest`
- `omniwrap://semantic/schema/ConfigurationRevision`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-createpreview` — integration

Plan a correct SDK integration for createPreview (POST /v1/projects/{projectId}/previews). Cite exactly: operation:createPreview, schema:ApiError, schema:OpaqueId, schema:Preview, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `createPreview`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `Preview`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/createPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/Preview`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getartifact` — integration

Plan a correct SDK integration for getArtifact (GET /v1/projects/{projectId}/artifacts/{artifactId}). Cite exactly: operation:getArtifact, schema:ApiError, schema:Artifact, schema:OpaqueId, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getArtifact`
- schema: `ApiError`
- schema: `Artifact`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getArtifact`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Artifact`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getconfigurationrevision` — integration

Plan a correct SDK integration for getConfigurationRevision (GET /v1/projects/{projectId}/configuration-revisions/{revisionId}). Cite exactly: operation:getConfigurationRevision, schema:ApiError, schema:ConfigurationRevision, schema:OpaqueId, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getConfigurationRevision`
- schema: `ApiError`
- schema: `ConfigurationRevision`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getConfigurationRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/ConfigurationRevision`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getevidence` — integration

Plan a correct SDK integration for getEvidence (GET /v1/projects/{projectId}/evidence/{evidenceId}). Cite exactly: operation:getEvidence, schema:ApiError, schema:Evidence, schema:OpaqueId, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getEvidence`
- schema: `ApiError`
- schema: `Evidence`
- schema: `OpaqueId`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getEvidence`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Evidence`
- `omniwrap://semantic/schema/OpaqueId`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getpreview` — integration

Plan a correct SDK integration for getPreview (GET /v1/projects/{projectId}/previews/{previewId}). Cite exactly: operation:getPreview, schema:ApiError, schema:OpaqueId, schema:Preview, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getPreview`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `Preview`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreview`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/Preview`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getpreviewevents` — integration

Plan a correct SDK integration for getPreviewEvents (GET /v1/projects/{projectId}/previews/{previewId}/events). Cite exactly: operation:getPreviewEvents, schema:ApiError, schema:Cursor, schema:EventPage, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getPreviewEvents`
- schema: `ApiError`
- schema: `Cursor`
- schema: `EventPage`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreviewEvents`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Cursor`
- `omniwrap://semantic/schema/EventPage`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getpreviewlogs` — integration

Plan a correct SDK integration for getPreviewLogs (GET /v1/projects/{projectId}/previews/{previewId}/logs). Cite exactly: operation:getPreviewLogs, schema:ApiError, schema:Cursor, schema:LogPage, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getPreviewLogs`
- schema: `ApiError`
- schema: `Cursor`
- schema: `LogPage`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getPreviewLogs`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/Cursor`
- `omniwrap://semantic/schema/LogPage`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getproject` — integration

Plan a correct SDK integration for getProject (GET /v1/projects/{projectId}). Cite exactly: operation:getProject, schema:ApiError, schema:OpaqueId, schema:Project, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getProject`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `Project`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getProject`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/Project`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getsourcerevision` — integration

Plan a correct SDK integration for getSourceRevision (GET /v1/projects/{projectId}/source-revisions/{revisionId}). Cite exactly: operation:getSourceRevision, schema:ApiError, schema:OpaqueId, schema:SourceRevision, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getSourceRevision`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `SourceRevision`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getSourceRevision`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/SourceRevision`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.

## `integration-getusercontext` — integration

Plan a correct SDK integration for getUserContext (GET /v1/me/context). Cite exactly: operation:getUserContext, schema:ApiError, schema:OpaqueId, schema:UserContext, auth:SessionCookie

Intent: Recover exact wire parameters, request media, responses, and safety traits.

Expected evidence:

- operation: `getUserContext`
- schema: `ApiError`
- schema: `OpaqueId`
- schema: `UserContext`
- authentication: `SessionCookie`
- criterion: return the expected entity identifiers
- criterion: cite only resolvable OmniWrap resources
- criterion: stay within the declared result, context, and tool-call budgets
- criterion: perform none of the forbidden actions

Citations:

- `omniwrap://semantic/auth/SessionCookie`
- `omniwrap://semantic/operation/getUserContext`
- `omniwrap://semantic/schema/ApiError`
- `omniwrap://semantic/schema/OpaqueId`
- `omniwrap://semantic/schema/UserContext`

Budgets: at most 5 results, 8192 context bytes, and 3 tool calls.
