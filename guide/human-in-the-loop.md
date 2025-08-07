# Human-in-the-Loop

Cronflow provides powerful human-in-the-loop capabilities that allow you to pause workflows for manual approval, review, or intervention. This is perfect for workflows that require human oversight, such as approval processes, content moderation, or complex decision-making.

## Basic Human-in-the-Loop

### Simple Approval Workflow

```typescript
const approvalWorkflow = cronflow.define({
  id: "approval-workflow",
  name: "Approval Workflow",
});

approvalWorkflow
  .step("submit-request", async (ctx) => {
    return await createRequest(ctx.payload);
  })
  .humanInTheLoop({
    timeout: "24h",
    description: "Manual review required",
    onPause: async (ctx, token) => {
      await sendApprovalRequest(ctx.payload.email, token);
    },
    onTimeout: async (ctx) => {
      await sendTimeoutNotification(ctx.payload.email);
    },
  })
  .step("process-approved-request", async (ctx) => {
    return await processApprovedRequest(ctx.last);
  });
```

### Approval with Custom Logic

```typescript
const customApprovalWorkflow = cronflow.define({
  id: "custom-approval-workflow",
  name: "Custom Approval Workflow",
});

customApprovalWorkflow
  .step("create-expense", async (ctx) => {
    return await createExpense(ctx.payload);
  })
  .humanInTheLoop({
    timeout: "48h",
    description: "Expense approval required",
    onPause: async (ctx, token) => {
      const expense = ctx.last;
      await emailService.send({
        to: expense.approverEmail,
        subject: "Expense Approval Required",
        template: "expense-approval",
        data: {
          expenseId: expense.id,
          amount: expense.amount,
          description: expense.description,
          approvalUrl: `https://app.example.com/approve/${token}`,
        },
      });
    },
    onTimeout: async (ctx) => {
      const expense = ctx.last;
      await emailService.send({
        to: expense.requesterEmail,
        subject: "Expense Approval Timed Out",
        template: "expense-timeout",
        data: {
          expenseId: expense.id,
          amount: expense.amount,
        },
      });
    },
  })
  .step("process-expense", async (ctx) => {
    return await processExpense(ctx.last);
  });
```

## Advanced Human-in-the-Loop Patterns

### 1. Conditional Approval

```typescript
const conditionalApprovalWorkflow = cronflow.define({
  id: "conditional-approval-workflow",
  name: "Conditional Approval Workflow",
});

conditionalApprovalWorkflow
  .step("process-order", async (ctx) => {
    return await processOrder(ctx.payload);
  })
  .if("requires-approval", (ctx) => ctx.last.amount > 1000)
  .humanInTheLoop({
    timeout: "12h",
    description: "High-value order approval required",
    onPause: async (ctx, token) => {
      const order = ctx.last;
      await slackService.sendMessage("#approvals", {
        text: `High-value order requires approval: $${order.amount}`,
        attachments: [
          {
            title: "Approve Order",
            title_link: `https://app.example.com/approve/${token}`,
            fields: [
              { title: "Order ID", value: order.id, short: true },
              { title: "Amount", value: `$${order.amount}`, short: true },
            ],
          },
        ],
      });
    },
    onTimeout: async (ctx) => {
      const order = ctx.last;
      await slackService.sendMessage("#approvals", {
        text: `⚠️ Order approval timed out: ${order.id}`,
      });
    },
  })
  .else()
  .step("auto-approve", async (ctx) => {
    return { autoApproved: true, order: ctx.last };
  })
  .endIf()
  .step("finalize-order", async (ctx) => {
    return await finalizeOrder(ctx.last);
  });
```

### 2. Multi-Level Approval

```typescript
const multiLevelApprovalWorkflow = cronflow.define({
  id: "multi-level-approval-workflow",
  name: "Multi-Level Approval Workflow",
});

multiLevelApprovalWorkflow
  .step("submit-request", async (ctx) => {
    return await submitRequest(ctx.payload);
  })
  .if("requires-manager-approval", (ctx) => ctx.last.amount > 5000)
  .humanInTheLoop({
    timeout: "24h",
    description: "Manager approval required",
    onPause: async (ctx, token) => {
      const request = ctx.last;
      await emailService.send({
        to: request.managerEmail,
        subject: "Manager Approval Required",
        template: "manager-approval",
        data: {
          requestId: request.id,
          amount: request.amount,
          approvalUrl: `https://app.example.com/manager/approve/${token}`,
        },
      });
    },
    onTimeout: async (ctx) => {
      const request = ctx.last;
      await emailService.send({
        to: request.requesterEmail,
        subject: "Manager Approval Timed Out",
        template: "manager-timeout",
        data: { requestId: request.id },
      });
    },
  })
  .if("requires-director-approval", (ctx) => ctx.last.amount > 10000)
  .humanInTheLoop({
    timeout: "48h",
    description: "Director approval required",
    onPause: async (ctx, token) => {
      const request = ctx.last;
      await emailService.send({
        to: request.directorEmail,
        subject: "Director Approval Required",
        template: "director-approval",
        data: {
          requestId: request.id,
          amount: request.amount,
          approvalUrl: `https://app.example.com/director/approve/${token}`,
        },
      });
    },
    onTimeout: async (ctx) => {
      const request = ctx.last;
      await emailService.send({
        to: request.requesterEmail,
        subject: "Director Approval Timed Out",
        template: "director-timeout",
        data: { requestId: request.id },
      });
    },
  })
  .endIf()
  .endIf()
  .step("process-approved-request", async (ctx) => {
    return await processApprovedRequest(ctx.last);
  });
```

### 3. Content Moderation

```typescript
const contentModerationWorkflow = cronflow.define({
  id: "content-moderation-workflow",
  name: "Content Moderation Workflow",
});

contentModerationWorkflow
  .step("submit-content", async (ctx) => {
    return await submitContent(ctx.payload);
  })
  .humanInTheLoop({
    timeout: "4h",
    description: "Content moderation required",
    onPause: async (ctx, token) => {
      const content = ctx.last;
      await moderationService.createTask({
        contentId: content.id,
        content: content.text,
        author: content.authorId,
        approvalUrl: `https://app.example.com/moderate/${token}`,
        priority: content.flagged ? "high" : "normal",
      });
    },
    onTimeout: async (ctx) => {
      const content = ctx.last;
      await moderationService.autoApprove(content.id);
      await emailService.send({
        to: content.authorEmail,
        subject: "Content Auto-Approved",
        template: "content-auto-approved",
        data: { contentId: content.id },
      });
    },
  })
  .step("publish-content", async (ctx) => {
    return await publishContent(ctx.last);
  });
```

### 4. Risk Assessment

```typescript
const riskAssessmentWorkflow = cronflow.define({
  id: "risk-assessment-workflow",
  name: "Risk Assessment Workflow",
});

riskAssessmentWorkflow
  .step("analyze-risk", async (ctx) => {
    return await analyzeRisk(ctx.payload);
  })
  .if("high-risk", (ctx) => ctx.last.riskScore > 0.8)
  .humanInTheLoop({
    timeout: "2h",
    description: "High-risk transaction requires review",
    onPause: async (ctx, token) => {
      const risk = ctx.last;
      await riskService.flagForReview({
        transactionId: risk.transactionId,
        riskScore: risk.riskScore,
        riskFactors: risk.riskFactors,
        reviewUrl: `https://app.example.com/risk/review/${token}`,
        priority: "urgent",
      });
    },
    onTimeout: async (ctx) => {
      const risk = ctx.last;
      await riskService.autoBlock(risk.transactionId);
      await notificationService.send({
        type: "risk-timeout",
        transactionId: risk.transactionId,
        riskScore: risk.riskScore,
      });
    },
  })
  .elseIf("medium-risk", (ctx) => ctx.last.riskScore > 0.5)
  .humanInTheLoop({
    timeout: "12h",
    description: "Medium-risk transaction review",
    onPause: async (ctx, token) => {
      const risk = ctx.last;
      await riskService.flagForReview({
        transactionId: risk.transactionId,
        riskScore: risk.riskScore,
        reviewUrl: `https://app.example.com/risk/review/${token}`,
        priority: "normal",
      });
    },
    onTimeout: async (ctx) => {
      const risk = ctx.last;
      await riskService.autoApprove(risk.transactionId);
    },
  })
  .endIf()
  .step("process-transaction", async (ctx) => {
    return await processTransaction(ctx.last);
  });
```

## Resume Workflow

### Manual Resume

```typescript
// Resume a paused workflow with approval
await cronflow.resume(token, {
  approved: true,
  approvedBy: "user-456",
  approvedAt: new Date().toISOString(),
  comments: "Looks good, approved",
});

// Or reject the workflow
await cronflow.resume(token, {
  approved: false,
  rejectedBy: "user-456",
  rejectedAt: new Date().toISOString(),
  comments: "Missing required documentation",
});
```

### Resume with Custom Data

```typescript
await cronflow.resume(token, {
  approved: true,
  approvedBy: "manager-123",
  approvedAt: new Date().toISOString(),
  comments: "Approved with modifications",
  modifications: {
    amount: 950, // Reduced from 1000
    reason: "Budget constraints",
  },
  nextSteps: ["process-payment", "send-confirmation"],
});
```

## Best Practices

### 1. Set Appropriate Timeouts

```typescript
// Short timeout for urgent requests
.humanInTheLoop({
  timeout: '1h',
  description: 'Urgent approval required',
  onPause: async (ctx, token) => {
    await sendUrgentNotification(ctx.payload.urgentContact, token);
  },
  onTimeout: async (ctx) => {
    await handleUrgentTimeout(ctx);
  }
})

// Medium timeout for normal requests
.humanInTheLoop({
  timeout: '24h',
  description: 'Standard approval required',
  onPause: async (ctx, token) => {
    await sendStandardNotification(ctx.payload.approver, token);
  },
  onTimeout: async (ctx) => {
    await handleStandardTimeout(ctx);
  }
})

// Long timeout for complex decisions
.humanInTheLoop({
  timeout: '72h',
  description: 'Complex decision requires review',
  onPause: async (ctx, token) => {
    await sendComplexReviewRequest(ctx.payload.expert, token);
  },
  onTimeout: async (ctx) => {
    await handleComplexTimeout(ctx);
  }
})
```

### 2. Provide Clear Descriptions

```typescript
.humanInTheLoop({
  timeout: '24h',
  description: `Please review expense request #${ctx.last.id} for $${ctx.last.amount} from ${ctx.last.requester}. Category: ${ctx.last.category}`,
  onPause: async (ctx, token) => {
    await sendDetailedApprovalRequest(ctx.last, token);
  },
  onTimeout: async (ctx) => {
    await sendTimeoutNotification(ctx.last);
  }
})
```

### 3. Handle Different Outcomes

```typescript
workflow
  .humanInTheLoop({
    timeout: "24h",
    description: "Review and approve",
    onPause: async (ctx, token) => {
      await sendApprovalRequest(ctx.payload, token);
    },
    onTimeout: async (ctx) => {
      await sendTimeoutNotification(ctx.payload);
    },
  })
  .if("approved", (ctx) => ctx.last.approved === true)
  .step("process-approval", async (ctx) => {
    return await processApprovedRequest(ctx.last);
  })
  .else()
  .step("handle-rejection", async (ctx) => {
    return await handleRejectedRequest(ctx.last);
  })
  .endIf();
```

### 4. Track Approval History

```typescript
workflow
  .step("create-request", async (ctx) => {
    return await createRequest(ctx.payload);
  })
  .humanInTheLoop({
    timeout: "24h",
    description: "Approve request",
    onPause: async (ctx, token) => {
      await sendApprovalRequest(ctx.last, token);
    },
    onTimeout: async (ctx) => {
      await sendTimeoutNotification(ctx.last);
    },
  })
  .action("log-approval", async (ctx) => {
    const approval = ctx.last;
    await auditLog.create({
      action: approval.approved ? "request_approved" : "request_rejected",
      requestId: approval.requestId,
      approver: approval.reviewedBy,
      timestamp: new Date().toISOString(),
      comments: approval.comments,
    });
  });
```

## API Reference

### `workflow.humanInTheLoop(options)`

Pauses the workflow for human intervention.

**Parameters:**

- `options` (HumanInTheLoopOptions):
  - `timeout` (string): Timeout duration (e.g., '1h', '24h', '72h')
  - `description` (string): Description of what needs approval
  - `onPause` (function): Callback when workflow is paused
  - `onTimeout` (function): Callback when timeout occurs

### `cronflow.resume(token, data)`

Resumes a paused workflow.

**Parameters:**

- `token` (string): The pause token
- `data` (object): Resume data with approval decision

## Related Topics

- **[Error Handling](/guide/error-handling)** - Basic error handling and recovery
- **[Testing](/guide/testing)** - Testing workflows and components
- **[Performance](/guide/performance)** - Optimizing workflow performance
