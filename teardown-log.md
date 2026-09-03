# 🧹 Teardown Log

## AWS DevOps Observability Engineering

**Status:** Completed  
**Purpose:** Record the post-validation cleanup of lab infrastructure and prevent continued cloud charges.

---

## Why this log exists

The observability assignment treats cost hygiene as part of the technical deliverable. AWS resources such as EC2, OpenSearch, Firehose, and EKS can continue generating charges after the functional work is finished, so the infrastructure was removed after all required evidence had been captured.

The assignment specifically requires a teardown record and complete deletion of task resources. fileciteturn28file2L174-L183

---

## Teardown Timeline

| Stage | Status |
|---|:---:|
| Functional validation completed | ✅ |
| Required screenshots captured | ✅ |
| Evidence redacted / organized | ✅ |
| Task 1 resources removed | ✅ |
| Task 2 resources removed | ✅ |
| Task 3A resources removed | ✅ |
| Task 3B resources removed | ✅ |
| Repository evidence preserved | ✅ |

**Teardown completed:** September 2026, after final task validation.

---

## Task 1 — CloudWatch

### Resources cleaned up

- Observability EC2 instance
- SNS resources no longer required
- CloudWatch log groups/resources no longer required

### Validation completed before deletion

- Nginx traffic generated
- Access/error logs confirmed in CloudWatch
- 5xx metric filter tested
- `Nginx-5xx-Error-Alarm` reached a real `ALARM` state
- SNS notification email received

---

## Task 2 — Firehose + OpenSearch

### Resources cleaned up

- Amazon OpenSearch domain
- Kinesis Data Firehose delivery stream
- S3 failed-record backup bucket
- Lambda transformation function

### Validation completed before deletion

- Lambda transformation test succeeded
- Firehose transformation enabled
- OpenSearch destination validated
- Failed-record-only S3 backup configured
- Nginx documents visible in OpenSearch Discover
- Index pattern verified
- Visualizations created
- Nginx analytics dashboard validated

---

## Task 3A — Prometheus + Grafana on EC2

### Resources cleaned up

- Observability EC2 instance
- Monitoring EC2 instance

### Validation completed before deletion

- Prometheus targets confirmed `UP`
- `up` query returned healthy values
- Node Exporter dashboard validated
- NGINX exporter dashboard validated
- High-CPU alert intentionally triggered
- Firing notification received
- Alert recovery confirmed
- Resolved notification received

---

## Task 3B — Prometheus + Grafana on EKS

### Resources cleaned up

- Helm-installed monitoring stack
- EKS cluster
- Managed worker/node infrastructure created for the cluster

The cluster was removed through the cluster lifecycle rather than treating worker EC2 instances as independent lab resources.

### Validation completed before deletion

- EKS cluster healthy
- Worker nodes available
- Sample application running
- ServiceMonitor created and discovered
- Prometheus target confirmed `UP`
- `up{job="sample-app"}` validated
- PrometheusRule created and validated
- Sample application scaled to zero
- Alert reached firing state
- Firing notification received
- Application restored
- Alert resolved
- Recovery notification received

---

# 🔍 Evidence Preservation

The infrastructure is intentionally gone, but the implementation evidence remains in GitHub.

```text
docs/screenshots/
├── task-1-cloudwatch/
├── task-2-firehose-opensearch/
├── task-3a-ec2-prometheus-grafana/
└── task-3b-eks-prometheus-grafana/
```

The README presents selected screenshots for readability. The complete screenshot sets are retained in the repository for detailed review.

---

# 💰 Cost-Hygiene Outcome

The teardown was performed **after validation**, not before.

This preserved the evidence needed to demonstrate the assignment while minimizing the chance of leaving billable lab infrastructure running unnecessarily.

The assignment's own teardown checklist highlights OpenSearch, EC2, Firehose, S3, Lambda, and EKS as resources that should be removed after the work is complete. fileciteturn28file2L176-L183

---

## Final Status

> **Implementation validated → evidence captured → resources removed → repository preserved.**

✅ Task 1 cleaned up  
✅ Task 2 cleaned up  
✅ Task 3A cleaned up  
✅ Task 3B cleaned up  
✅ Evidence retained in GitHub  
✅ Teardown completed
