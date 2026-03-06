# [Data] Build Call Analytics Dashboard

## Overview

Build a **real-time analytics dashboard** for the Call Analytics feature that surfaces key metrics — sentiment scores, call duration trends, and agent performance — to Operations Managers and Team Leads. This dashboard derives from the [Call Analytics Metric Sheet](https://notion.so/call-analytics-metrics) and serves as the primary interface for monitoring call quality at scale.

## Why This Matters

Call quality monitoring is currently a manual, reactive process — ops teams only discover issues after customer complaints. A real-time dashboard enables proactive intervention, reducing escalation rates and improving CSAT. Early adopter feedback from 3 enterprise accounts identified live dashboards as a top-3 requirement for expanding their seat count.

## High-Level Approach

Use the existing event pipeline to feed a **pre-aggregated metrics layer** (5-minute rollups) into the dashboard backend. Build the frontend as a new tab within the existing Analytics module to minimize navigation overhead. Start with 4 core widgets (sentiment trend, call volume, avg duration, top issues) and instrument dashboard interactions to validate which views drive the most engagement before expanding.

## Acceptance Criteria

- [ ] **Sentiment trend widget** displays average sentiment score over configurable time ranges (1h, 24h, 7d, 30d)
- [ ] **Call volume widget** shows total calls segmented by outcome (completed, dropped, transferred) with hourly granularity
- [ ] **Average duration widget** calculates mean call duration with breakdowns by team and agent
- [ ] **Top issues widget** surfaces the 5 most frequent call categories ranked by volume
- [ ] **Data refresh cadence** is 5 minutes or less for all widgets
- [ ] **Access control** restricts dashboard visibility to users with the `analytics:read` permission
- [ ] **CSV export** allows users to download the underlying data for any widget
- [ ] **Dashboard load time** is under 3 seconds for datasets up to 100K calls
- [ ] **Mobile responsiveness** renders correctly on tablet-sized viewports (768px+)

## Dependencies

- Call Analytics event pipeline must be deployed and emitting events to the data warehouse
- `analytics:read` permission must be added to the RBAC configuration

## Source Document Link

[Call Analytics Metric Sheet](https://notion.so/call-analytics-metrics)
