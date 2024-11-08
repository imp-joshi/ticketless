Here is a detailed documentation of all the API calls in the Ticketless project, including success and error messages:

### Ticket APIs

1. **Get Tickets by Filter**
   - **Endpoint**: `/api/ticket/get_tickets_by_filter/`
   - **Method**: POST
   - **Description**: Get tickets by email, phone, name, or ticket ID.
   - **File Path**: apps/ticket/views.py
   - **Function**: get_tickets_by_filter


   - **Success Response**:
     ```json
     {
       "customer_name": "Test User",
       "customer_email": "example@example.com",
       "customer_phone": "1234567890",
       "event_id": 1,
       "selected_sub_events": [],
       "selected_addons": [],
       "transaction_id": 1
     }
     ```
   - **Error Responses**:
     - `{"message": "Ticket does not exist or isn't active"}`
     - `{"message": "At least one of email, phone or name is required"}`
     - `{"message": "No tickets found"}`

2. **Handle Check-In**
   - **Endpoint**: `/api/ticket/handle_check_in/`
   - **Method**: POST
   - **Description**: Check in a ticket.
   - **File Path**: apps/ticket/views.py
   - **Function**: handle_check_in


   - **Success Response**:
     ```json
     {
       "message": "Ticket checked in successfully"
     }
     ```
   - **Error Responses**:
     - `{"message": "ticket_id is required"}`
     - `{"message": "ticket_id, operator and method are required"}`
     - `{"message": "Ticket does not exist or is not active"}`
     - `{"message": "Event has ended"}`
     - `{"message": "Ticket already checked in today"}`
     - `{"message": "Ticket is not active"}`

3. **Get Check-In Data**
   - **Endpoint**: `/api/ticket/get_check_in_data/`
   - **Method**: POST
   - **Description**: Get check-in data of a ticket.
   - **File Path**: apps/ticket/views.py
   - **Function**: get_check_in_data


   - **Success Response**:
     ```json
     [
       {
         "ticket_id": 1,
         "check_in_time": "2023-09-26T12:34:56Z",
         "operator": "admin",
         "method": "QR"
       }
     ]
     ```
   - **Error Responses**:
     - `{"message": "ticket_id is required"}`
     - `{"message": "Ticket does not exist"}`
     - `{"message": "Ticket has not been checked in"}`
     - `{"message": "Ticket is not active"}`

4. **Resend Ticket Email**
   - **Endpoint**: `/api/ticket/resend_email/`
   - **Method**: POST
   - **Description**: Resend ticket email.
   - **File Path**: apps/ticket/views.py
   - **Function**: resend_email


   - **Success Response**:
     ```json
     {
       "message": "Ticket email sent successfully"
     }
     ```
   - **Error Responses**:
     - `{"message": "ticket_id is required"}`
     - `{"message": "Ticket does not exist"}`
     - `{"message": "Ticket is not active"}`

5. **Get Tickets by Sub Events**
   - **Endpoint**: `/api/ticket/get_ticket_by_subevents/`
   - **Method**: POST
   - **Description**: Get tickets by sub events.
   - **File Path**: apps/ticket/views.py
   - **Function**: get_ticket_by_subevents


   - **Success Response**:
     ```json
     [
       {
         "customer_name": "Test User",
         "customer_phone": "1234567890"
       }
     ]
     ```
   - **Error Responses**:
     - `{"message": "ID is required"}`
     - `{"message": "Sub Event does not exist or is not active"}`
     - `{"message": "No tickets found"}`

6. **Get Tickets by Addons**
   - **Endpoint**: `/api/ticket/get_ticket_by_addons/`
   - **Method**: POST
   - **Description**: Get tickets by addons.
   - **File Path**: apps/ticket/views.py
   - **Function**: get_ticket_by_addons


   - **Success Response**:
     ```json
     [
       {
         "customer_name": "Test User",
         "customer_phone": "1234567890"
       }
     ]
     ```
   - **Error Responses**:
     - `{"message": "ID is required"}`
     - `{"message": "Addon does not exist or is not active"}`
     - `{"message": "No tickets found"}`

7. **Get Ticket by Task**
   - **Endpoint**: `/api/ticket/get_ticket_by_task/`
   - **Method**: POST
   - **Description**: Get ticket by task ID.
   - **File Path**: apps/ticket/views.py
   - **Function**: get_ticket_by_task


   - **Success Response**:
     ```json
     {
       "result": "Ticket generation successful"
     }
     ```
   - **Error Responses**:
     - `{"message": "task_id is required"}`
     - `{"message": "Task does not exist"}`
     - `{"message": "Task is not complete"}`

### Transaction APIs

1. **Handle Payment**
   - **Endpoint**: `/api/transactions/handle-payment/`
   - **Method**: POST
   - **Description**: Handle payment.
   - **File Path**: apps/transactions/views.py
   - **Function**: HandlePayment


   - **Success Response**:
     ```json
     {
       "message": "Payment successful"
     }
     ```
   - **Error Responses**:
     - `{"message": "Payment failed"}`
     - `{"message": "Backend Error"}`

2. **Handle Payment Success**
   - **Endpoint**: `/api/transactions/handle-payment-success/`
   - **Method**: POST
   - **Description**: Handle payment success.
   - **File Path**: apps/transactions/views.py
   - **Function**: HandlePaymentSuccess


   - **Success Response**:
     ```json
     {
       "message": "Payment successful"
     }
     ```
   - **Error Responses**:
     - `{"message": "Invalid Payment"}`
     - `{"message": "Payment Already Done"}`
     - `{"message": "Ticket Generation Pending"}`
     - `{"message": "The Payment failed"}`

3. **Payment Webhook**
   - **Endpoint**: `/api/transactions/payment-webhook/`
   - **Method**: POST
   - **Description**: Handle payment webhook.
   - **File Path**: apps/transactions/views.py
   - **Function**: PaymentWebhook


   - **Success Response**:
     ```json
     {
       "message": "Webhook received"
     }
     ```
   - **Error Responses**:
     - `{"message": "Invalid Webhook Signature"}`
     - `{"message": "Webhook Confirmation already Received"}`
     - `{"message": "Payment Captured Notified"}`
     - `{"message": "Payment Disputed Notified"}`
     - `{"message": "Payment Refunded Notified"}`

### Event APIs

1. **Get Active Event**
   - **Endpoint**: `/api/event/get_event/`
   - **Method**: GET
   - **Description**: Get all active events.
   - **File Path**: apps/event/views.py
   - **Function**: GetActiveEvent


   - **Success Response**:
     ```json
     [
       {
         "id": 1,
         "name": "Event Name",
         "description": "Event Description",
         "start_date": "2023-09-26",
         "end_date": "2023-09-29",
         "location": "Event Location",
         "price": 300.00,
         "sub_events_included_allowed": 3,
         "is_active": true,
         "event_page": ""
       }
     ]
     ```
   - **Error Response**:
     - `"No Active Event"`

2. **Get Sub Event**
   - **Endpoint**: `/api/event/get_sub_event/<int:pk>/`
   - **Method**: GET
   - **Description**: Get all active sub events for a specific event.
   - **File Path**: apps/event/views.py
   - **Function**: GetSubEvent


   - **Success Response**:
     ```json
     [
       {
         "id": 1,
         "name": "Sub Event Name",
         "description": "Sub Event Description",
         "start_date": "2023-09-26",
         "end_date": "2023-09-29",
         "price": 100.00,
         "event": 1,
         "is_active": true
       }
     ]
     ```
   - **Error Responses**:
     - `"No Active Sub Event"`
     - `{"error": "Sub Event does not exist"}`

3. **Get Addon**
   - **Endpoint**: `/api/event/get_addon/<int:pk>/`
   - **Method**: GET
   - **Description**: Get all active addons for a specific event.
   - **File Path**: apps/event/views.py
   - **Function**: GetAddon


   - **Success Response**:
     ```json
     [
       {
         "id": 1,
         "name": "Addon Name",
         "icon": "hotel",
         "price": 300.00,
         "event": 1,
         "stock": 10,
         "is_active": true
       }
     ]
     ```
   - **Error Responses**:
     - `"No active Addon"`
     - `{"error": "Addon does not exist"}`

4. **Process Promo Code**
   - **Endpoint**: `/api/event/process_promo_code/`
   - **Method**: POST
   - **Description**: Process promo code.
   - **File Path**: apps/event/views.py
   - **Function**: ProcessPromoCode


   - **Success Response**:
     ```json
     {
       "discount": 50.00
     }
     ```
   - **Error Responses**:
     - `{"error": "Promo code out of stock"}`
     - `{"error": "Promo code not valid for this event"}`
     - `{"error": "Promo code does not exist"}`

5. **Get Max Ticket Sales**
   - **Endpoint**: `/api/event/get_max_ticket_sales/<int:pk>/`
   - **Method**: GET
   - **Description**: Get max ticket sales for a specific event.
   - **File Path**: apps/event/views.py
   - **Function**: get_max_ticket_sales


   - **Success Response**:
     ```json
     {
       "total_tickets": 100,
       "total_amount": 30000.00
     }
     ```

6. **Get Sub Event Sales**
   - **Endpoint**: `/api/event/get_sub_event_sales/<int:pk>/`
   - **Method**: GET
   - **Description**: Get sub event sales for a specific event.
   - **File Path**: apps/event/views.py
   - **Function**: get_sub_event_sales


   - **Success Response**:
     ```json
     {
       "data": [10, 20],
       "label": ["Sub Event 1", "Sub Event 2"]
     }
     ```

7. **Get Addon Sales**
   - **Endpoint**: `/api/event/get_addon_sales/<int:pk>/`
   - **Method**: GET
   - **Description**: Get addon sales for a specific event.
   - **File Path**: apps/event/views.py
   - **Function**: get_addon_sales


   - **Success Response**:
     ```json
     {
       "data": [5, 15],
       "label": ["Addon 1", "Addon 2"]
     }
     ```

This documentation covers all the API endpoints and utility functions found in the current codebase of the Ticketless project, including success and error messages.