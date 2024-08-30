# Razorpay Integration

This project integrates Razorpay for handling payments in a Java-based application. It includes functionalities for creating Razorpay orders and handling webhooks for payment updates.

## Features

- **Create Order**:
  - **Endpoint**: `POST /api/payment/createOrder`
  - **Function**: Creates a new Razorpay order with the specified amount and currency. The order details are saved in the database.
  - **Description**: Uses the Razorpay API to create an order and store the order details, including the Razorpay order ID, receipt, amount, currency, notes, and status, in the database.

- **Webhook Handling**:
  - **Endpoint**: `POST /api/webhook`
  - **Function**: Receives Razorpay webhook events and updates the database based on the payment status.
  - **Description**: Processes incoming webhook events from Razorpay to update the payment status in the database. It handles events like `payment.authorized` and `order.paid`, updating the status and amount paid for corresponding orders.

## How It Works

1. **Order Creation**:
   - The `createOrder` method in the `PaymentController` class creates a new Razorpay order. The order request includes the amount, currency, and notes.
   - The order details are then saved to the `PaymentOrder` entity in the database.

2. **Webhook Processing**:
   - The `handleWebhook` method in the `WebhookController` class processes incoming webhook events. It reads the payload, extracts relevant payment details, and updates the `PaymentOrder` entity based on the event data.

## Setup

1. **Dependencies**: Ensure you have the Razorpay Java SDK included in your project dependencies.
2. **Configuration**: Set up your Razorpay API keys and configure them in the `PaymentController` constructor.
3. **Database**: Ensure your database is properly configured to store payment order details.

## Example Usage

- To create an order, send a `POST` request to `/api/payment/createOrder` with a JSON body containing the amount.
- Razorpay will send webhook events to `/api/webhook`, which will update the payment status in the database.

This integration provides a complete solution for managing payments with Razorpay in your application, from order creation to payment updates.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

