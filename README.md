# IOanyT Operations Pulse

Real-time operational health metrics for IOanyT - our commitment to transparency.

## Current Status

[![Operational Status](https://img.shields.io/badge/Status-Healthy-brightgreen)](pulse.json)

See [pulse.json](pulse.json) for the latest operational pulse.

---

## What is Operations Pulse?

IOanyT Operations Pulse is our public transparency initiative. We publish our operational health metrics, showing the same data we use internally to run our operations.

**We run our operations the same way we run yours - with visibility and accountability.**

### Data Included
- Organizational health status (healthy/attention/critical)
- Client project delivery metrics (counts, not names)
- System escalation levels (none/few/several)
- Compliance status (on_target/needs_attention)
- Issues resolved and deployments completed

### Data Excluded (Privacy Protected)
- Client names or identities
- Specific issue details
- Internal escalation descriptions
- Team member information
- Exact internal health scores
- Repository URLs

---

## Repository Structure

```
operations-pulse/
├── README.md                    # This file
├── pulse.json                   # Current pulse (latest snapshot)
├── history.json                 # Rolling 30-day summary
│
├── data/                        # Historical weekly data
│   ├── 2026/
│   │   ├── Q1/
│   │   │   ├── W01.json        # Week 1 pulse
│   │   │   ├── W02.json        # Week 2 pulse
│   │   │   ├── W03.json        # Week 3 pulse
│   │   │   └── Q1-summary.json # Quarterly rollup
│   │   ├── Q2/
│   │   ├── Q3/
│   │   └── Q4/
│   └── yearly/
│       └── 2026-summary.json   # Annual rollup
│
├── reports/                     # Human-readable reports
│   ├── quarterly/
│   │   └── 2026-Q1.md          # Quarterly transparency report
│   └── yearly/
│       └── 2026.md             # Annual transparency report
│
└── linkedin/                    # Posted LinkedIn content archive
    └── 2026/
        ├── W03.md              # Week 3 post
        └── ...
```

---

## Update Frequency

| Data Type | Frequency | Description |
|-----------|-----------|-------------|
| `pulse.json` | Every 6 hours | Current operational snapshot |
| `history.json` | Every 6 hours | Rolling 30-day summary |
| `data/YYYY/QN/WNN.json` | Weekly (Fridays) | Permanent weekly archive |
| Quarterly summaries | End of quarter | Q1, Q2, Q3, Q4 rollups |
| Annual summaries | End of year | Yearly rollup |

---

## Data Schema

### pulse.json (Current Status)

```json
{
  "generated_at": "2026-01-14T08:26:20Z",
  "version": "2.0",
  "status": {
    "overall": "healthy",
    "emoji": "🟢",
    "escalations": "none",
    "compliance": "on_target"
  },
  "delivery": {
    "projects_tracked": 2,
    "projects_on_track": 2,
    "projects_at_risk": 0,
    "issues_resolved": 0,
    "deployments": 3
  },
  "display": {
    "headline": "All systems operational",
    "delivery_headline": "2 projects on track",
    "last_updated": "2026-01-14 08:26 UTC"
  },
  "linkedin_draft": "IOanyT Operations Pulse | Week 3, 2026..."
}
```

### Weekly Archive (data/YYYY/QN/WNN.json)

```json
{
  "week": "W03",
  "week_number": 3,
  "year": 2026,
  "quarter": "Q1",
  "period": {
    "start": "2026-01-13",
    "end": "2026-01-19"
  },
  "generated_at": "2026-01-14T09:11:31Z",
  "status": {
    "overall": "healthy",
    "emoji": "🟢",
    "health_score": 100,
    "escalations": 0,
    "compliance": "on_target"
  },
  "delivery": {
    "projects_tracked": 2,
    "projects_on_track": 2,
    "deployments": 3
  },
  "linkedin": {
    "posted": true,
    "posted_at": "2026-01-14T10:00:00Z"
  }
}
```

### Quarterly Summary (data/YYYY/QN/QN-summary.json)

```json
{
  "quarter": "2026-Q1",
  "period": {
    "start": "2026-01-01",
    "end": "2026-03-31"
  },
  "weeks_tracked": 13,
  "health": {
    "healthy_weeks": 12,
    "attention_weeks": 1,
    "critical_weeks": 0,
    "average_score": 96,
    "uptime_percentage": 99.2
  },
  "delivery": {
    "total_deployments": 45,
    "projects_delivered": 3,
    "avg_projects_on_track_pct": 95
  },
  "linkedin": {
    "posts_published": 13
  }
}
```

---

## Use Cases

### Website Badge

Embed operational status on your website:

```html
<div id="ioanyt-pulse"></div>
<script>
  fetch('https://raw.githubusercontent.com/ioanyt/operations-pulse/main/pulse.json')
    .then(r => r.json())
    .then(pulse => {
      document.getElementById('ioanyt-pulse').innerHTML = `
        <div class="pulse-badge">
          <span>${pulse.status.emoji}</span>
          <span>${pulse.display.headline}</span>
        </div>
      `;
    });
</script>
```

### LinkedIn Posts

Weekly operations pulse updates are published to [IOanyT LinkedIn](https://linkedin.com/company/ioanyt).
All posted content is archived in the `/linkedin/` folder.

### Quarterly/Annual Reports

Use the data in `/data/` to generate transparency reports:
- Quarterly summaries auto-generated at end of each quarter
- Human-readable reports in `/reports/`
- Machine-readable JSON for integrations

### Historical Analysis

Access any week's data:
```bash
# Get Week 3 of Q1 2026
curl https://raw.githubusercontent.com/ioanyt/operations-pulse/main/data/2026/Q1/W03.json

# Get Q1 2026 summary (when available)
curl https://raw.githubusercontent.com/ioanyt/operations-pulse/main/data/2026/Q1/Q1-summary.json
```

---

## Why We Do This

**Transparency builds trust.** We believe in running operations with the same visibility and accountability we provide to our clients.

When we say "we run our operations the same way we run yours," we mean it. This data proves it.

### Our Commitment

- **Weekly transparency**: Every Friday, we publish our operational health
- **Real data**: No sanitization of bad weeks - we show reality
- **Recovery stories**: When issues happen, we show how fast we respond
- **Historical accountability**: Full history preserved for review

---

## About IOanyT

IOanyT provides DevOps-as-a-Service to startups and enterprises. We handle:
- Infrastructure management
- CI/CD pipelines
- Monitoring and alerting
- Security and compliance
- Cost optimization

Learn more at [ioanyt.com](https://ioanyt.com)

---

## Related Resources

- **Decision Document**: DEC-STR-004 (Internal)
- **Technical Architecture**: Available upon request
- **LinkedIn**: [IOanyT Company Page](https://linkedin.com/company/ioanyt)

---

**Generated by:** IOanyT CTO Governance System  
**Started:** Week 3, 2026  
**License:** Public Data (Attribution appreciated)
