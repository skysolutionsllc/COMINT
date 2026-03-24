# COMment INTelligence Solution

AI-Enabled Public Comment Intelligence & Substantiveness Platform

# Overview

COMINT is designed to address a very specific and persistent challenge in federal rulemaking: making sense of large-scale public comment data in a way that is structured, defensible, and usable.

Under the Administrative Procedure Act, agencies are required to review and respond to public comments submitted during the notice-and-comment process. In practice, this often means working through tens of thousands of submissions that vary widely in quality, intent, and relevance.

The problem is not just volume. It is distinguishing meaningful input from noise, identifying patterns across submissions, and doing all of this in a way that can stand up to legal and policy scrutiny.

COMINT approaches this as an augmentation problem. The system does not replace human reviewers. It gives them structure, prioritization, and traceable insight so they can make better decisions faster.

# Data Strategy

A deliberate choice was made to build COMINT on real-world data rather than synthetic or generated datasets.

We use the Regulations.gov API as a primary source of public comments. This gives us direct access to input from citizens, advocacy groups, and domain experts at a scale that reflects actual rulemaking conditions.

The system performs scheduled ingestion of large comment volumes on a daily basis. Each ingestion cycle brings in thousands of new records, allowing the analytical models to operate on continuously evolving data rather than static snapshots.

This matters because campaign behavior, sentiment shifts, and thematic patterns only emerge at scale.

# Processing Pipeline
Ingestion and Normalization

COMINT uses n8n as the orchestration layer for ingestion.

The ingestion process:

Retrieves comments using paginated API calls
Normalizes incoming JSON structures
Preserves the full comment text without truncation
Captures all available metadata, including identifiers, timestamps, and document relationships

Each comment is stored in its entirety. No summarization or filtering is applied at this stage. The goal is to maintain complete source fidelity for downstream analysis and auditability.

# Contextual Linking

Every comment is linked to its parent rule or document using the object identifier provided by the source system.

This relationship is central to the platform.

It allows COMINT to determine whether a comment is actually engaging with the proposed rule or simply contributing unrelated or low-value content. The distinction between contextual and non-contextual input becomes a foundational signal for all subsequent analysis.

# Analytical Enrichment

Once ingested, each comment passes through a structured enrichment pipeline.

The system evaluates:

Sentiment
Relevance
Novelty

In parallel, COMINT performs similarity analysis to identify duplicate and near-duplicate submissions. This allows the system to detect coordinated campaigns and quantify their scale without discarding them.

All derived attributes are stored alongside the original comment. Nothing is overwritten or abstracted away.

# Comment Impact Scoring

COMINT assigns a Comment Impact Score to each submission.

This is not a black-box metric. The score is constructed from observable factors, including:

Volume of similar arguments
Presence of legal or economic reasoning
Thematic relevance to the rule
Degree of novelty compared to existing submissions

Each score can be decomposed into its contributing components. This ensures that reviewers can understand not just the outcome, but the reasoning behind it.

# ServiceNow Integration

ServiceNow serves as the primary interface for interacting with COMINT data.

It is used not just as a display layer, but as an operational environment where users can explore, filter, and interpret comment data at multiple levels of detail.

Users can:

Drill down to individual comments and view full text
Navigate across rules, themes, and impact scores
Analyze sentiment and substantiveness distributions

The interface is designed to support both detailed analyst workflows and high-level executive review. It is also configurable to meet the needs of different agencies or programs.

# Access Information
ServiceNow Instance

Instance URL: https://skysolutionsllcdemo3.service-now.com/x/sks/Sky-Assure-COMINT/home

Username: Regulationcomments

Password: dQ}GPMjgq5UFWTdmxQ4{U8KRB2;C)C]

n8n Orchestration Environment

URL: <INSERT_N8N_URL>

Username: <INSERT_USERNAME>

Password: <INSERT_PASSWORD>

n8n is responsible for ingestion, transformation, and pipeline orchestration. All data flows originate here before entering the analytical layer.
