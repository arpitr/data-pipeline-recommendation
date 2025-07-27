# data-pipeline-recommendation

## Goal

- Build a multi-modal data pipeline with an AI model and inference endpoint for
  the ecommerce domain.
- Hyper-personalization: Based on who the user is, and their prior order history,
  show relevant products
- Achieve this using:
  ○ Confluent Cloud (Kafka)
  ○ Databricks

## HLD

```mermaid
flowchart TD
  %% Entities
  ProductData["**Product Data**
<span style='color:#e53935'>sku</span>
<span style='color:#e53935'>product_name</span>
<span style='color:#e53935'>category</span>
<span style='color:#e53935'>inventory</span>
<span style='color:#e53935'>price</span>"]

  OrderData["**Order Data**
  <span style='color:#e53935'>product_x</span>
  <span style='color:#e53935'>quantity</span>
  <span style='color:#e53935'>price</span>
  <span style='color:#e53935'>customer_id</span>
  <span style='color:#e53935'>price_discount)</span>"]

  CustomerData["**Customer Data**
  <span style='color:#e53935'>customer_id</span>
  <span style='color:#e53935'>age</span>
  <span style='color:#e53935'>location</span>
  <span style='color:#e53935'>gender</span>"]

  ClickstreamData["**Clickstream Data**
  <span style='color:#e53935'>event</span>
  <span style='color:#e53935'>payload</span>"]

  Confluent["**Confluent Cloud**"]

  %% Destinations
  Flink["**Apache Flink**
  <span style='color:#e53935'> Streaming Processing"]
  Databricks["**Databricks**
  <span style='color:#e53935'> Batch Processing"]

  %% Relationships
  ProductData -- datagen --> Confluent
  OrderData -- datagen --> Confluent
  CustomerData -- datagen --> Confluent
  ClickstreamData -- datagen --> Confluent
  Confluent -- Flink Consumer --> Flink
  Confluent -- Databricks Connector --> Databricks
```

## What drives customer behavior

- Prior history
  - Wishlist & preferences
  - Orders
- Demographics
  - Age/Gender
  - Gen Z? Millennial
- Product preference bundle and inherent affinity
  - People who bought X also typically buy Y
- Seasonality
- Discounts and offers (Pricing)
