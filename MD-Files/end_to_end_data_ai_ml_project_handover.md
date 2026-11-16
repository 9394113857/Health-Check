# Personal End-to-End Data Engineering, Analytics, Data Science & MLOps Project

**Purpose:** Continue this project in another ChatGPT account. This
document captures the conversation, current application architecture,
learning goals, proposed implementation, and the next steps.

------------------------------------------------------------------------

## 1. My current application and infrastructure

I have an existing personal full-stack application that I want to use as
the foundation for a realistic, end-to-end data and AI/ML project.

  -----------------------------------------------------------------------
  Area                                Current setup
  ----------------------------------- -----------------------------------
  Frontend                            Angular, deployed on Vercel

  Backend                             Python Flask microservices

  Services mentioned                  Authentication service, Product
                                      service, Cart service; order
                                      placement/cancellation flow is also
                                      present

  Databases                           Three Supabase databases

  Backend hosting                     Three Render accounts/services

  Cloud / DevOps                      GCP, Kubernetes, CI/CD pipelines

  Existing business flow              Users can add products to cart,
                                      place/check orders, and cancel
                                      orders

  Inventory behaviour                 Cancelling an order restores the
                                      product stock

  Availability                        Services are intended to run
                                      continuously (24/7)
  -----------------------------------------------------------------------

I want to share safe project code, folder structures, database schemas,
and architecture details so the assistant can inspect the actual
implementation and guide improvements. Do not assume details that have
not yet been inspected.

### Security rule

**Never ask me to paste passwords, API keys, database URLs containing
credentials, Supabase service-role keys, Render tokens, GCP
service-account private keys, or other secrets.**

Use redacted configuration such as:

``` env
SUPABASE_URL=REDACTED
SUPABASE_SERVICE_ROLE_KEY=REDACTED
DATABASE_URL=REDACTED
SECRET_KEY=REDACTED
```

Share schema-only SQL, table names, column names, sample rows with
personal information removed, sanitized logs, and code with secrets
replaced by placeholders. Prefer read-only access and a separate
development/staging environment. Do not run experiments against live
production data without an explicit plan, backup, and approval.

------------------------------------------------------------------------

## 2. The four roles I want to learn and demonstrate

The learning path is:

1.  **Data Engineer**
2.  **Data Analyst**
3.  **Data Scientist**
4.  **ML Engineer / MLOps Engineer**

I want to understand what each role receives, what they build, which
tools and skills they use, what they deliver, and how work is assigned
and reported.

### Role 1 --- Data Engineer

**Goal:** Reliably collect data from application systems, transform and
validate it, and load it into an analytics data warehouse or lakehouse.

Typical source data from my app:

-   Users and account events (with privacy-safe identifiers)
-   Product catalogue and product categories
-   Product views and searches, if event tracking exists
-   Cart additions, removals, and abandoned carts
-   Orders and order items
-   Payments and payment status, if available
-   Order cancellations and stock-restoration events
-   Reviews and ratings, if available
-   Notification delivery, opens, clicks, and opt-outs, if tracked

Typical tools and skills to learn:

-   SQL and relational database concepts
-   Python
-   PostgreSQL / Supabase
-   REST APIs and database connectors
-   ETL / ELT pipeline design
-   Data validation and reconciliation
-   Incremental loading and change-data capture concepts
-   Airflow or another scheduler/orchestrator
-   dbt for SQL transformations
-   Object storage and warehouse concepts
-   Spark/Kafka later, only if volume or streaming needs justify them
-   Logging, retries, idempotency, alerting, and pipeline monitoring

Typical responsibilities:

1.  Identify and document source systems and schemas.
2.  Extract data safely from the application databases or event streams.
3.  Land raw data in a controlled staging area.
4.  Clean, standardize, deduplicate, and validate records.
5.  Transform operational data into analytics-friendly models.
6.  Load warehouse tables incrementally.
7.  Track pipeline runs, failures, late-arriving records, and data
    freshness.
8.  Document lineage: which source created each warehouse field.

**Output:** trusted, documented, analytics-ready data.

### Role 2 --- Data Analyst

**Goal:** Use warehouse data to understand business performance and
communicate findings.

Typical tools and skills:

-   SQL
-   Excel / Google Sheets
-   Power BI or Tableau
-   Basic statistics
-   Data visualization
-   KPI definition and business communication

Questions to investigate in this application:

-   How many users register and log in?
-   How many products are viewed or searched?
-   How many carts are created?
-   What percentage of carts become orders?
-   What is the order cancellation rate?
-   Which products and categories sell most?
-   What is the average order value?
-   How much stock is restored after cancellations?
-   Which users are repeat customers?
-   What are daily, weekly, and monthly sales trends?

**Output:** dashboards, KPI reports, SQL analyses, and actionable
business insights for product/business managers.

### Role 3 --- Data Scientist

**Goal:** Use historical data to build and evaluate statistical or
machine-learning models.

Typical tools and skills:

-   Python
-   Pandas and NumPy
-   Matplotlib / visualization
-   Statistics and probability
-   Scikit-learn
-   Feature engineering
-   Model training, validation, and testing
-   Classification, regression, ranking, and recommendation methods
-   Model evaluation, experiment tracking, and responsible use of data

Possible models for my application:

-   Product recommendation / ranking
-   Likelihood that a user will purchase a product
-   Cart abandonment prediction
-   Repeat-purchase prediction
-   Product demand forecasting
-   Cancellation-risk prediction (only if the data and business use case
    justify it)

**Output:** a tested model, its feature requirements, evaluation
results, model artefact, and documentation describing limitations.

### Role 4 --- ML Engineer / MLOps Engineer

**Goal:** Make models reliable, secure, scalable, versioned, monitored
services that the application can use.

Typical tools and skills:

-   Python
-   Flask or FastAPI for model-serving APIs
-   Docker
-   CI/CD
-   GCP and Kubernetes (where appropriate)
-   MLflow or another model registry/tracking tool
-   Model/version management
-   Automated tests
-   Monitoring, logging, latency and error tracking
-   Data/model drift monitoring
-   Rollback and retraining workflows

Typical responsibilities:

1.  Package the approved model and its dependencies.
2.  Create a prediction API or batch-scoring job.
3.  Validate request data and model output.
4.  Deploy to a staging environment and test.
5.  Release safely to production.
6.  Monitor latency, errors, resource usage, and prediction quality.
7.  Version models and retain a rollback option.
8.  Coordinate retraining when data or performance changes.

**Output:** a deployed, monitored prediction service or scheduled
scoring pipeline.

------------------------------------------------------------------------

## 3. End-to-end flow for my application

``` text
                    USERS
                      |
                      v
          ANGULAR WEBSITE / FRONTEND
                 (Vercel)
                      |
                      v
            FLASK MICROSERVICES
       Auth | Product | Cart | Orders
                      |
                      v
         SUPABASE / OPERATIONAL DATABASES
                      |
          Application data and events
                      |
                      v
        +-------------------------------+
        |       1. DATA ENGINEER        |
        | Python + SQL + ETL/ELT        |
        | Extract -> Stage -> Validate  |
        | Transform -> Incremental Load |
        +-------------------------------+
                      |
                      v
           ANALYTICS WAREHOUSE
     Raw / Staging / Clean / Mart layers
                      |
             +--------+---------+
             |                  |
             v                  v
   +------------------+  +---------------------+
   | 2. DATA ANALYST  |  | 3. DATA SCIENTIST  |
   | SQL, BI, Excel   |  | Python, ML, Stats   |
   | KPIs, dashboards|  | Features, training  |
   | Business insight|  | Testing, evaluation |
   +------------------+  +---------------------+
             |                  |
             v                  v
       Managers /          Approved model
       Product team         + feature contract
                                |
                                v
                    +------------------------+
                    | 4. ML ENGINEER / MLOps |
                    | Package, API/batch     |
                    | CI/CD, deploy, monitor |
                    +------------------------+
                                |
                                v
                    PREDICTION SERVICE
                    or batch prediction job
                                |
                                v
                 PREDICTION / RECOMMENDATION
                         STORAGE
                    (optional, when useful)
                                |
                                v
                   FLASK BACKEND / API
                                |
                                v
                   ANGULAR WEBSITE (Vercel)
                                |
                                v
                PERSONALIZED USER EXPERIENCE
```

This is a practical architecture, not a rule that every company must use
exactly this sequence. Data Analyst and Data Scientist work can happen
in parallel after trustworthy data is available. Data Scientists may
also work with curated feature tables or feature stores. Some companies
use streaming pipelines as well as scheduled batch pipelines.

------------------------------------------------------------------------

## 4. What data is captured, and where does it come from?

The first step is to inspect the actual database schemas and application
code. Do not invent tables or assume every event is already tracked.

  -----------------------------------------------------------------------
  Business action         Possible source         Useful fields (example
                                                  only)
  ----------------------- ----------------------- -----------------------
  User registers          Auth service / auth     internal user ID,
                          database                created timestamp

  User logs in            Auth event or           user ID, timestamp,
                          application event log   success/failure

  Product is viewed       Frontend event sent to  user ID, product ID,
                          backend/event collector timestamp

  Product is searched     Search event            query category,
                                                  timestamp, anonymized
                                                  session ID

  Product added to cart   Cart service            cart ID, product ID,
                                                  quantity, timestamp

  Cart item removed       Cart service            cart ID, product ID,
                                                  quantity, timestamp

  Order placed            Order service / order   order ID, user ID,
                          database                order items, total,
                                                  timestamp

  Order cancelled         Order service           order ID, cancellation
                                                  timestamp, reason if
                                                  collected

  Stock restored          Inventory/product       product ID, quantity
                          service                 delta, event timestamp

  Payment status changes  Payment service, if     order ID, status,
                          present                 timestamp

  Notification            Notification            campaign ID, channel,
  sent/clicked            provider/event          delivery/click status
                          collector, if present   
  -----------------------------------------------------------------------

Use internal surrogate IDs or pseudonymous identifiers in analytics. Do
not copy passwords, authentication tokens, payment-card data, or
unnecessary personal details into the warehouse or ML training dataset.
Apply access controls, retention limits, and consent/opt-out rules.

------------------------------------------------------------------------

## 5. A safe warehouse design to start with

A free or low-cost learning setup can begin with a separate PostgreSQL
analytics database or a local PostgreSQL/DuckDB environment. Supabase
may be suitable for a small development warehouse if resource limits and
separation are respected. Later, evaluate BigQuery on GCP or another
warehouse based on cost, scale, and learning goals.

Suggested layers:

``` text
SOURCE APPLICATION DATABASES
             |
             v
        RAW / LANDING
             |
             v
       STAGING TABLES
             |
             v
    CLEAN / TRANSFORMED
             |
             v
       ANALYTICS MARTS
             |
       +-----+------+
       |            |
       v            v
   BI REPORTS    ML DATASETS
```

Possible starter tables (to be finalized after inspecting the real
schema):

-   `raw_users`
-   `raw_products`
-   `raw_cart_events`
-   `raw_orders`
-   `raw_order_items`
-   `raw_inventory_events`
-   `stg_orders`
-   `stg_order_items`
-   `dim_users`
-   `dim_products`
-   `dim_date`
-   `fact_orders`
-   `fact_order_items`
-   `fact_cart_events`
-   `fact_inventory_movements`
-   `mart_sales_daily`
-   `mart_product_performance`

Use a star-schema approach where it helps: fact tables contain
measurable events, while dimension tables describe users, products,
dates, and categories. Avoid blindly copying these names; align the
final model to the real application schema and business definitions.

### Pipeline engineering requirements

-   Incremental extraction using reliable timestamps or change markers.
-   A unique source key for every record.
-   Idempotent loads: rerunning a pipeline must not create duplicates.
-   Upserts where appropriate.
-   Watermarks and handling of late-arriving updates.
-   Data-quality checks for nulls, duplicates, invalid quantities,
    impossible dates, and inconsistent totals.
-   Reconciliation between source and warehouse row counts/totals.
-   Run logs, retries, alerting, and a failure/recovery plan.
-   Read-only source credentials wherever possible.
-   Separate development/staging warehouse from production.

------------------------------------------------------------------------

## 6. Data Analyst work using the warehouse

Build SQL queries and dashboards for:

1.  Daily/weekly/monthly order count.
2.  Gross sales and net sales, with clear definitions.
3.  Average order value.
4.  Product/category sales ranking.
5.  Order cancellation rate.
6.  Cart-to-order conversion rate.
7.  Repeat customer rate.
8.  Stock restored due to cancelled orders.
9.  New versus returning users.
10. Product views-to-purchase conversion, if view tracking exists.

Power BI or another BI tool can connect to curated warehouse marts. The
analyst should document the definition of every KPI so different
dashboards do not calculate the same metric differently.

------------------------------------------------------------------------

## 7. Data Scientist work: create features and train models

A recommendation model needs examples of user-item interactions. Orders
alone can be used as an initial baseline, but richer recommendations
benefit from views, searches, cart additions, purchases, and possibly
ratings.

Example feature ideas (only use fields that actually exist and are
appropriate):

  -----------------------------------------------------------------------
  Feature                             Meaning
  ----------------------------------- -----------------------------------
  `orders_last_30d`                   Number of orders in the previous 30
                                      days

  `spend_last_90d`                    Amount spent in the previous 90
                                      days

  `product_views_30d`                 Views of a product/category in the
                                      previous 30 days

  `cart_adds_30d`                     Cart additions in the previous 30
                                      days

  `category_purchase_count`           Purchases in a category

  `days_since_last_order`             Recency of the last order

  `cancel_rate`                       Historical cancellation ratio,
                                      calculated carefully

  `product_popularity`                Product interaction/purchase
                                      popularity
  -----------------------------------------------------------------------

A sensible first project is a product recommender:

``` text
Curated warehouse data
        |
        v
Build user-product interaction dataset
        |
        v
Create training / validation / test split
        |
        v
Train baseline recommender
        |
        v
Evaluate against baseline
        |
        v
Measure ranking quality (e.g. Precision@K,
Recall@K, NDCG@K where appropriate)
        |
        v
Document limitations and approve model
```

Do not use random train/test splitting blindly for time-dependent
behaviour. Use time-aware splits where appropriate to avoid training on
future events and testing on the past. Compare against simple baselines
such as popular products or most popular products within a category. A
complex model is not automatically better.

------------------------------------------------------------------------

## 8. How predictions reach users: real-time versus stored predictions

The earlier question was whether predictions are saved in a table and
then shown when users log in. **Both patterns are valid.** A practical
project can implement batch predictions first and later add real-time
inference.

### Option A --- Batch predictions stored in a table

Useful when recommendations can be refreshed on a schedule and need to
load quickly.

``` text
Scheduled scoring job (e.g. hourly/nightly)
             |
             v
       Load eligible users
             |
             v
      Load latest features
             |
             v
       Run model scoring
             |
             v
 Rank products per user (top K)
             |
             v
 UPSERT prediction rows
             |
             v
 recommendation_predictions table
             |
             v
 User logs in / opens home page
             |
             v
 Backend reads valid top-ranked rows
             |
             v
 Angular displays recommendations
```

Example table design (illustrative; finalize after schema review):

``` sql
CREATE TABLE recommendation_predictions (
    user_id          TEXT NOT NULL,
    product_id       TEXT NOT NULL,
    model_version    TEXT NOT NULL,
    score            DOUBLE PRECISION NOT NULL,
    rank_position    INTEGER NOT NULL,
    generated_at     TIMESTAMPTZ NOT NULL,
    expires_at       TIMESTAMPTZ,
    PRIMARY KEY (user_id, product_id, model_version)
);
```

In a real implementation, consider whether to keep multiple model
versions, how to atomically replace a user's current recommendation set,
and how to expire stale rows. Use a transaction or staging-and-swap
pattern so users do not see a half-written recommendation list. Check
product availability and visibility at read time. Never expose
recommendations for products that are unavailable or ineligible.

### Option B --- Real-time predictions

Useful when the latest session context must influence the result.

``` text
User opens app
     |
     v
Angular calls backend
     |
     v
Backend obtains safe user/context features
     |
     v
Calls deployed model API
     |
     v
Model returns scores / ranked products
     |
     v
Backend validates availability and response
     |
     v
Angular displays recommendations
```

### Option C --- Hybrid (often practical)

Precompute candidate products and scores in a batch, then use a
real-time service to filter or re-rank them using current session
context, stock availability, and current business rules.

### Insert versus upsert

-   **Insert:** add a new row.
-   **Update:** change an existing row.
-   **Upsert:** insert if it does not exist, otherwise update.
-   For recommendation refreshes, upsert or replace a user's current set
    in a transaction.
-   Keep `generated_at`, `model_version`, and possibly `expires_at` so
    the application can reject stale predictions.
-   Use a stable uniqueness key and avoid duplicate rows.
-   Keep model scores separate from final display rank if business rules
    adjust the ranking.

------------------------------------------------------------------------

## 9. Rule-based ranking versus ML predictions

These are related but different. They can work together.

### Rule-based logic

Examples:

-   Hide out-of-stock products.
-   Exclude products the user has blocked or already purchased if the
    business rule requires it.
-   Promote a selected category during a campaign.
-   Apply delivery-region or eligibility restrictions.
-   Use a popular-products fallback for a new user with no history.

Rules are explicitly written by developers/business teams. They are not
necessarily machine learning.

### ML-based scoring

The model estimates relevance or likelihood based on patterns learned
from historical data. For example, it may return a score for each
candidate product for a particular user.

### Combined ranking

``` text
Candidate products
       |
       v
ML model generates scores
       |
       v
Business rules filter ineligible items
       |
       v
Combine/adjust ranking where justified
       |
       v
Sort by final score
       |
       v
Store top-K results or return them live
       |
       v
Show products to user
```

For a new user with little or no history, use a cold-start fallback such
as popular products, trending products, or category-level
recommendations. Do not pretend the model has learned personal
preferences when it has no evidence.

------------------------------------------------------------------------

## 10. Email, SMS, WhatsApp and push notifications

Recommendations can be used in communication channels, but a model does
not automatically send messages. A separate notification/campaign system
handles delivery.

``` text
Prediction / recommendation output
              |
              v
   Eligibility + consent checks
              |
              v
   Campaign / notification service
       |       |       |       |
       v       v       v       v
     Email    SMS   WhatsApp  Push
              |
              v
 Track sent / delivered / clicked /
 bounced / failed / opted-out events
              |
              v
 Feed permitted events back into
 analytics pipelines and reporting
```

Respect user consent, opt-outs, applicable messaging regulations,
provider policies, frequency caps, and privacy requirements. Start with
in-app recommendations; add external messaging only when the application
has compliant consent and a legitimate provider integration. Do not send
promotional messages just because a model produces a high score.

------------------------------------------------------------------------

## 11. Who assigns work and who reports to whom?

There is no universal reporting hierarchy. It varies by company. A
common cross-functional arrangement is:

``` text
Business stakeholder / Product Manager
                  |
          Defines business problem
                  |
      +-----------+-----------+-----------+
      |           |           |           |
      v           v           v           v
 Data Eng Lead  Analytics   Data Science  ML Platform /
      |         Lead        Lead          Engineering Lead
      |           |           |           |
      v           v           v           v
 Data Engineer  Analyst   Data Scientist  ML Engineer
      |
      v
 Data pipelines and trusted data
```

The Product Manager or business stakeholder often defines the problem
and priorities. Each role generally receives technical direction and
performance management from its own lead/manager. Teams collaborate; it
is not always true that one of these four roles directly manages all the
others.

Example project task:

-   Product Manager: "Improve relevant product recommendations on the
    home page."
-   Data Engineer: "Build a reliable interaction dataset and daily
    pipeline."
-   Data Analyst: "Measure current conversion and define the baseline."
-   Data Scientist: "Train and evaluate a recommender."
-   ML Engineer: "Deploy it safely and monitor the service."
-   Frontend/backend engineers: "Integrate the recommendation response
    into the app."

------------------------------------------------------------------------

## 12. Learning and implementation sequence

Work on the existing app in small, reviewable steps. Do not rewrite
everything at once.

### Phase 0 --- Architecture and safety audit

-   Inspect repositories and folder structures.
-   Map Angular routes and API calls.
-   Map Flask services and service-to-service calls.
-   Identify the three Supabase databases and their actual tables.
-   Document relationships and key fields.
-   Understand the order placement, cancellation, and stock-restoration
    transaction flow.
-   Identify existing GCP, Kubernetes, Render, Vercel, and CI/CD usage.
-   Redact all secrets and use a safe development environment.

### Phase 1 --- Data Engineering

-   Create a source-to-target mapping.
-   Choose a separate warehouse target.
-   Build a small Python + SQL extraction pipeline.
-   Load one subject area first (for example, orders and order items).
-   Add staging, validation, deduplication, incremental loading, and
    upsert logic.
-   Add logs, retries, and a scheduler.
-   Reconcile warehouse results with source totals.

### Phase 2 --- Data Analytics

-   Create a curated sales/order mart.
-   Write SQL for KPIs.
-   Build a dashboard.
-   Explain each KPI and validate it against known application records.

### Phase 3 --- Data Science

-   Create a user-product interaction dataset.
-   Build a popularity baseline.
-   Train a first recommendation model.
-   Use time-aware evaluation.
-   Compare model results with the baseline.
-   Save the model artefact and document its features and version.

### Phase 4 --- ML Engineering / MLOps

-   Create a prediction API or batch scoring job.
-   Add input validation and tests.
-   Containerize the service.
-   Add CI/CD and staging deployment.
-   Register/version the model.
-   Add health checks, logs, monitoring, and rollback.
-   Integrate the service with the Flask backend and Angular frontend.
-   Start with a small controlled test before production rollout.

### Phase 5 --- Production-quality enhancement

Review and improve only where useful:

-   Security and secret management
-   Database indexes and query performance
-   API authentication and authorization
-   Rate limiting and input validation
-   Data privacy and retention
-   Observability and alerting
-   Backup and recovery
-   CI/CD quality gates
-   Kubernetes resource limits and health probes
-   Model drift and performance monitoring
-   Documentation and architecture diagrams

------------------------------------------------------------------------

## 13. What I should share first in the next conversation

Start with safe, non-secret materials:

1.  **Repository structure** for Angular and each Flask microservice.
2.  **Database schema** for each Supabase database: table names,
    columns, primary keys, foreign keys, indexes, and relationships.
3.  Sanitized example rows for products, carts, orders, and order items.
4.  The code path for add-to-cart, place-order, cancel-order, and stock
    restoration.
5.  API endpoint list and service communication diagram.
6.  Current deployment overview (Vercel, Render, GCP, Kubernetes,
    CI/CD), without tokens or credentials.
7.  Any existing event tracking, logs, or analytics tables.

If sharing source files, remove secrets first. Do not provide production
credentials or grant access to live systems. We can work from schemas
and sanitized code, and I can provide commands for you to run locally or
in a staging environment.

------------------------------------------------------------------------

## 14. Interview-ready explanations

### What is AI?

Artificial Intelligence (AI) is the broader field of building computer
systems that perform tasks commonly associated with human intelligence,
such as understanding information, reasoning, recognizing patterns, and
making decisions.

### What is Machine Learning?

Machine Learning (ML) is a subset of AI in which systems learn patterns
from data and use those patterns to make predictions, classifications,
or recommendations on new data.

### Explain the four roles in one answer

"In a data-driven application, the Data Engineer collects data from
application databases and events, builds ETL/ELT pipelines, validates
it, and loads it into a data warehouse. The Data Analyst uses the
warehouse with SQL and BI tools to create KPIs, dashboards, and business
insights. The Data Scientist uses historical data to engineer features,
train models, and evaluate predictions. The ML Engineer or MLOps
Engineer packages, deploys, versions, and monitors those models so
application services can request predictions. The backend then returns
eligible results to the frontend, where users see recommendations or
other personalized features."

### Explain the recommendation example

"When a customer views products, adds items to a cart, places orders, or
cancels orders, the application records those events. A data pipeline
moves permitted data into an analytics warehouse. A Data Scientist
trains and evaluates a recommendation model using historical
user-product interactions. The model can score candidate products. Those
scores may be generated in real time or precomputed and stored in a
prediction table with user ID, product ID, score, rank, model version,
and timestamp. When the user opens the application, the backend
retrieves valid recommendations or calls the model, checks current
product availability and business rules, and returns the ranked products
to Angular."

------------------------------------------------------------------------

## 15. Working agreement for the next ChatGPT conversation

Please act as my practical mentor and technical reviewer.

-   Use **my existing application and my actual schemas** as the primary
    learning project.
-   Teach one role at a time, beginning with Data Engineering.
-   Explain each step in simple language, with diagrams, SQL, Python,
    and practical examples.
-   Tell me exactly which file or service to inspect and what safe
    information to share.
-   Review the current architecture before suggesting major changes.
-   Do not invent table names, fields, deployment details, or features
    as if they already exist.
-   Clearly label examples as proposed designs until confirmed against
    my code.
-   Prefer free/open-source or low-cost tools initially; explain any
    cloud costs before recommending paid services.
-   Do not run destructive changes or experiments on live company or
    production data.
-   Keep the existing application working while adding analytics and ML
    capabilities separately.
-   Help me build genuine, demonstrable project experience and prepare
    honest interview explanations. Do not claim I have professional
    experience with tools or tasks until I have actually implemented and
    understood them.
-   Explain not just what to do, but why it is done, how to test it, how
    to debug it, and how to describe it in an interview.

**First task in the next chat:** Begin Phase 0. Ask me to share the
sanitized repository folder structure and database schemas. Then map the
real source tables and services before designing the first Data
Engineering pipeline.

------------------------------------------------------------------------

**End of handover document.**
