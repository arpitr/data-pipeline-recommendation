# Synthesize Data for Stream Processing

## Synthesize Clickstream Data

- Setup topic "clickstream_product_visits" on confluent cloud.
- Setup schema for orders to be used by datagen connector plugin to synthesize data. ref: syn-clickstream-product-schema.json
- In confluent cloud under connectors search for "datagen" and select "datagen source". Now start configure the plugin.
  - Select topic as clickstream_product_visits
  - Select Kafka credentials - My Account for simplicity and learning purpose.
  - Select Json as output format and select "Provide your own schema" under "Select a Schema".
