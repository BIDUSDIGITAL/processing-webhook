# Webhook Documentation

## Overview

This document describes the structure and usage of the webhook endpoint. A POST request is sent to the webhook URL with a JSON payload containing specific fields relevant to the transaction being processed.

## Endpoint

**URL:** `http://your-webhook-url.com`

**Method:** `POST`

## Request Body

The body of the POST request is a JSON object containing the following fields:

```json
{
  "type": "PAYOUT or ORDER",
  "processing_id": "unique-identifier",
  "shop_order_id": "shop-specific-identifier",
  "state": "PENDING, SUCCESS, or CANCEL",
  "actual_amount": "transaction-amount"
}
```

## Field Descriptions
- type:
  - Description: Indicates the type of transaction. 
  - Possible Values:
    - PAYOUT: Represents a payout transaction. 
    - ORDER: Represents an order transaction.
- processing_id:
  - Description: A unique identifier for the transaction, which can be either the payout ID or the order ID. 
  - Example: "123e4567-e89b-12d3-a456-426614174000"
- shop_order_id:
  - Description: The identifier for the transaction within the shop's system. It can be the same as the payout ID or order ID. 
  - Example: "shop-unique-id-987654321"
- state:
  - Description: The current status of the transaction. 
    - Possible Values:
      - PENDING: The transaction is in progress. 
      - SUCCESS: The transaction has been successfully completed. 
      - CANCEL: The transaction has been canceled.
- actual_amount:
  - Description: The amount of money involved in the transaction. 
  - Example: "100.00"

## Example Request
Here is an example of what the JSON payload might look like for a payout transaction

```json
{
  "type": "PAYOUT",
  "processing_id": "123e4567-e89b-12d3-a456-426614174000",
  "shop_order_id": "shop-unique-id-987654321",
  "state": "SUCCESS",
  "actual_amount": "100.00"
}
```
And here is an example for an order transaction:
```json
{
"type": "ORDER",
"processing_id": "123e4567-e89b-12d3-a456-426614174000",
"shop_order_id": "shop-unique-id-987654321",
"state": "PENDING",
"actual_amount": "50.00"
}
```
