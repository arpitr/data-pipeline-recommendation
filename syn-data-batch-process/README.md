# Synthesize Data for Batch Processing


## Synthesize Product Data

- Setup topic "products" on confluent cloud.
- Setup schema for products to be used by datagen connector plugin to synthesize data. ref: syn-product-schema.json
- In confluent cloud under connectors search for "datagen" and select "datagen source". Now start configure the plugin.
  - Select topic as products
  - Select Kafka credentials - My Account for simplicity and learning purpose.
  - Select Json as output format and select "Provide your own schema" under "Select a Schema".
