Here is a detailed documentation of all the utility functions in the Ticketless project:

### Utility Functions

1. **Create Ticket**
   - **Function**: create_ticket


   - **File Path**: apps/ticket/utils.py
   - **Description**: Creates a ticket based on the request data and order ID.
   - **Parameters**:
     - request: The HTTP request object containing ticket data.
     - order_id: The order ID associated with the ticket.
   - **Usage**:
     ```python
     create_ticket(request, order_id)
     ```
   - **Exceptions**:
     - Raises an exception if the serializer data is invalid.

2. **Generate Ticket Image**
   - **Function**: generate_ticket_image
   - **File Path**: apps/ticket/utils.py
   - **Description**: Generates a ticket image with a QR code and sends the ticket via email.
   - **Parameters**:
     - ticket_id: The ID of the ticket.
   - **Usage**:
     ```python
     generate_ticket_image(ticket_id)
     ```
   - **Returns**: The URL of the generated ticket image.

3. **Generate QR Code**
   - **Function**: generate_qr_code
   - **File Path**: apps/ticket/utils.py
   - **Description**: Generates a QR code for a given ticket ID.
   - **Parameters**:
     - ticket_id: The ID of the ticket.
   - **Usage**:
     ```python
     generate_qr_code(ticket_id)
     ```
   - **Returns**: The QR code image bytes.

4. **Send Ticket**
   - **Function**: send_ticket
   - **File Path**: apps/ticket/utils.py
   - **Description**: Sends the ticket via email to the customer.
   - **Parameters**:
     - ticket_id: The ID of the ticket.
   - **Usage**:
     ```python
     send_ticket(ticket_id)
     ```
   - **Returns**: `True` if the email is sent successfully.

5. **Encrypt/Decrypt Ticket ID**
   - **Function**: encrypt_decrypt_ticket_id
   - **File Path**: apps/ticket/utils.py
   - **Description**: Encrypts or decrypts a ticket ID.
   - **Parameters**:
     - ticket_id: The ID of the ticket.
     - decrypt (optional): A boolean indicating whether to decrypt the ticket ID. Default is `False`.
   - **Usage**:
     ```python
     encrypt_decrypt_ticket_id(ticket_id, decrypt=False)
     ```
   - **Returns**: The encrypted or decrypted ticket ID.

6. **Handle Price Calculation**
   - **Function**: HandlePriceCalculation
   - **File Path**: apps/transactions/utils.py
   - **Description**: Calculates the total price for an event, including sub-events and addons.
   - **Parameters**:
     - request: The HTTP request object containing event and addon data.
   - **Usage**:
     ```python
     HandlePriceCalculation(request)
     ```
   - **Returns**: The total price.

7. **Payment Gateway**
   - **Function**: payment_gateway
   - **File Path**: apps/transactions/utils.py
   - **Description**: Creates an order in the payment gateway.
   - **Parameters**:
     - request: The HTTP request object containing payment data.
   - **Usage**:
     ```python
     payment_gateway(request)
     ```
   - **Returns**: Payment information including order ID, amount, currency, and callback URL.

8. **Verify Payment (Razorpay)**
   - **Function**: verify_payment_razorpay


   - **File Path**: apps/transactions/utils.py
   - **Description**: Verifies a payment using Razorpay.
   - **Parameters**:
     - request: The HTTP request object containing payment data.
   - **Usage**:
     ```python
     verify_payment_razorpay(request)
     ```
   - **Returns**: The transaction object if the payment is verified successfully, otherwise an HTML response indicating the failure reason.

9. **Export All Data**
   - **Function**: export_all_data
   - **File Path**: apps/base/tasks.py
   - **Description**: Exports all ticket, transaction, and check-in data to an SFTP server.
   - **Usage**:
     ```python
     export_all_data()
     ```

This documentation covers all the utility functions in the project.