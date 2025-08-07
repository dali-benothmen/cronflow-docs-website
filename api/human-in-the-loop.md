# Human-in-the-Loop

Functions for managing workflows that require human approval.

## `workflow.humanInTheLoop(options)`

Pauses a workflow for human intervention.

```typescript
workflow.humanInTheLoop({
  timeout: "24h",
  description: "Manual review required",
  onPause: async (ctx, token) => {
    await sendApprovalRequest(ctx.payload.email, token);
  },
  onTimeout: async (ctx) => {
    await sendTimeoutNotification(ctx.payload.email);
  },
});
```

**Parameters:**

- `options` (HumanInTheLoopOptions):
  - `timeout` (string): Timeout duration (e.g., '1h', '24h', '72h')
  - `description` (string): Description of what needs approval
  - `onPause` (function): Callback when workflow is paused
  - `onTimeout` (function): Callback when timeout occurs

## `cronflow.resume(token, payload)`

Resumes a workflow paused by `.humanInTheLoop()`.

```typescript
await cronflow.resume("approval_token_123", {
  approved: true,
  approvedBy: "user-456",
  approvedAt: new Date().toISOString(),
  comments: "Looks good, approved",
});
```

**Parameters:**

- `token` (string): The pause token
- `payload` (object): Resume data with approval decision

## `cronflow.getPausedWorkflow(token)`

Retrieves information about a specific paused workflow by its token.

```typescript
const pausedWorkflow = await cronflow.getPausedWorkflow("approval_token_123");
```

## `cronflow.listPausedWorkflows()`

Returns an array of all currently paused workflows waiting for human approval.

```typescript
const pausedWorkflows = await cronflow.listPausedWorkflows();
```
