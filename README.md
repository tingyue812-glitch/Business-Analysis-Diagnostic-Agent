# Business Analysis Diagnostic Agent

An AI-powered business analysis agent built with **Dify**, designed to support structured business problem diagnosis, data quality validation, metric analysis, and evidence-based decision-making.

## 1. Project Overview

Business analysis requires more than identifying changes in metrics. Analysts must first validate data reliability, clarify metric definitions, investigate potential drivers, and distinguish genuine business problems from data quality issues.

This project aims to design an AI Agent that follows a structured business analysis process instead of generating conclusions directly from a business question.

Built with Dify, the agent combines prompt engineering, business analysis frameworks, and structured reasoning to support a more systematic approach to diagnosing business problems.

## 2. Design Objectives

* **Structured problem-solving:** Break down business questions into clear analytical steps.
* **Data reliability:** Check data quality before interpreting business metrics.
* **Metric-driven analysis:** Identify relevant metrics and clarify their calculation logic.
* **Hypothesis-driven diagnosis:** Organize potential explanations and assess them against available evidence.
* **Actionable recommendations:** Translate analytical findings into business actions and follow-up validation plans.
* **Evidence-based reasoning:** Distinguish confirmed facts, analytical interpretations, and unverified hypotheses.

## 3. Core Design

### 3.1 Data Quality Validation

The agent is designed to assess whether the available data is reliable enough to support business conclusions.

The validation logic covers:

* Missing values and incomplete records.
* Duplicate records and potential aggregation issues.
* Date coverage and data format consistency.
* Metric definition and denominator consistency.
* Potential timestamp anomalies.
* Risks associated with table joins and user identifier matching, when relevant data is available.

A key design principle is to **validate the data before interpreting the business outcome**. An unusual metric may reflect a real business change, a data collection issue, or an inconsistency in metric definitions.

### 3.2 Business Problem Structuring

The agent first clarifies the business question and defines the scope of analysis.

It then identifies the relevant business metrics, comparison periods, segmentation dimensions, and additional data required to investigate the problem.

For operational and e-commerce scenarios, the analytical framework considers dimensions such as:

* **People:** user activity, new and existing users, and user conversion.
* **Products and supply:** product availability and merchant participation.
* **Traffic and touchpoints:** exposure, clicks, and traffic sources.
* **Conversion funnel:** browsing, interaction, add-to-cart, ordering, and payment.

The framework is selected according to the business question and the fields available in the dataset.

### 3.3 Metric Analysis and Anomaly Identification

The agent is designed to use uploaded structured data to calculate relevant metrics and compare performance across available time periods or business segments.

Its analytical approach includes:

* Establishing a baseline for comparison.
* Measuring absolute and relative changes.
* Identifying metrics with notable changes.
* Comparing affected segments with relevant reference groups.
* Exploring relationships between upstream indicators and downstream business outcomes.

The goal is to identify which metrics warrant further investigation, rather than assuming that a single metric explains the entire business problem.

### 3.4 Hypothesis Tree Design

The agent organizes potential explanations into a hypothesis tree.

Each hypothesis is assessed according to the evidence available. The agent should distinguish between supported explanations, partially supported explanations, unsupported assumptions, and questions that cannot yet be answered.

When evidence is insufficient, the agent identifies the additional data needed to evaluate the hypothesis.

This design helps prevent unsupported conclusions and makes the analytical process easier to review.

### 3.5 Business Recommendations and Validation

The agent's final stage connects analytical findings with potential business actions.

Recommendations are expected to include:

* The issue requiring further investigation.
* The potential driver supported by current evidence.
* The next analytical check or data source required.
* The proposed business action, where appropriate.
* The metric or outcome that should be monitored afterward.

This creates a feedback loop between business diagnosis, decision-making, and subsequent validation.

## 4. Agent Workflow Design

The agent follows a structured workflow:

1. **Understand the business question**
2. **Validate data quality**
3. **Clarify metric definitions**
4. **Identify relevant metrics and dimensions**
5. **Calculate and compare available data**
6. **Locate potential anomalies**
7. **Construct and assess a hypothesis tree**
8. **Summarize evidence-based findings**
9. **Propose business recommendations and follow-up validation**

The overall design principle is:

**Data Quality → Metric Analysis → Anomaly Diagnosis → Hypothesis Assessment → Business Recommendations**

## 5. Implementation Approach

### Dify Application Design

Dify is used as the platform for configuring the AI Agent and managing its instructions and available tools.

### Prompt Engineering

The system prompt defines the agent's role, analytical responsibilities, problem-solving sequence, data validation requirements, and expected output structure.

Rather than instructing the model to answer business questions immediately, the prompt guides it through a consistent analytical process.

### Structured Output Design

The agent is instructed to organize its analysis into clear sections, including:

* Data quality assessment.
* Business problem definition.
* Metric decomposition.
* Required data and analytical approach.
* Hypothesis tree.
* Evidence-based conclusions.
* Business recommendations.
* Follow-up validation.

### Data-Aware Reasoning

The agent is instructed to use actual uploaded data when available, avoid inventing figures, and explicitly state when the available fields are insufficient to support a conclusion.

SQL may be suggested as an analytical approach when appropriate, but the current implementation does not automatically execute SQL against a database.

## 6. Technology Stack

* **Dify:** AI Agent configuration and orchestration.
* **Large Language Model (LLM):** natural language understanding and analytical reasoning.
* **Prompt Engineering:** structured business analysis instructions and output design.
* **Excel / Structured Data:** input data for analysis.
* **GitHub:** project configuration backup and documentation.

## 7. Repository Structure

```text
business-analysis-diagnostic-agent/
├── README.md
└── 商业分析助手.yml
```

* `README.md`: project objectives, design principles, analytical workflow, and implementation approach.
* `商业分析助手.yml`: exported Dify application configuration.

Additional documentation, prompt files, and screenshots can be added as the project evolves.

## 8. Current Scope and Limitations

The current project is an early-stage AI Agent prototype focused on structured business analysis.

* It analyzes data supplied through supported file-upload workflows.
* It does not currently connect directly to a live business database.
* It does not automatically execute SQL queries.
* Its analysis depends on the quality, granularity, and completeness of the provided data.
* Its hypotheses and recommendations require validation before being used for consequential business decisions.
* The use of a structured prompt does not guarantee that every calculation or conclusion will be correct.

These limitations define the current implementation scope and provide a basis for future development.

## 9. Future Development

Potential improvements include:

* More systematic and reusable data quality validation rules.
* Additional business diagnosis scenarios and evaluation cases.
* More reliable and reproducible quantitative calculations.
* Integration with SQL-based analytical workflows.
* Controlled database connectivity and query execution.
* Evaluation of analytical accuracy, hypothesis quality, and recommendation usefulness.
* Iterative prompt refinement based on observed failure cases.

These items represent future development directions rather than currently implemented capabilities.

## 10. Design Philosophy

The central idea of this project is to design an AI Agent that supports **structured, data-aware, and evidence-based business analysis**.

Instead of treating an AI model as a tool that simply generates explanations, the project emphasizes a disciplined analytical process:

**Validate the data first, define the metrics, investigate the evidence, assess hypotheses, and recommend actions that can be tested.**

---
