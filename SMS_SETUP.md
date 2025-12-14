# SMS Notification Setup Guide

## Overview
The PKS Pre-Pleating Services website includes automatic SMS notifications to customers about their order status. SMS messages are sent when:
- Order is placed (pending status)
- Order is confirmed (with expected delivery date)
- Order is completed (delivered)
- Order is cancelled

## SMS Service Provider: Twilio

### Step 1: Create a Twilio Account
1. Go to [https://www.twilio.com/](https://www.twilio.com/)
2. Sign up for a free account
3. Verify your phone number
4. Get your free trial credits (₹1000+ worth of SMS)

### Step 2: Get Twilio Credentials
After signing up, you'll need three pieces of information:
1. **Account SID** - Found on your Twilio Console Dashboard
2. **Auth Token** - Found on your Twilio Console Dashboard
3. **Phone Number** - Get a Twilio phone number that supports SMS for India

### Step 3: Configure Supabase Secrets
Add the following secrets to your Supabase project:

```bash
# In Supabase Dashboard > Project Settings > Edge Functions > Secrets
TWILIO_ACCOUNT_SID=your_account_sid_here
TWILIO_AUTH_TOKEN=your_auth_token_here
TWILIO_PHONE_NUMBER=your_twilio_phone_number_here
```

### Step 4: Test SMS Functionality
1. Register as an admin at `/admin/register`
2. Login at `/admin/login`
3. Go to Admin Dashboard > Bookings Management
4. When you confirm an order:
   - Set the expected delivery date
   - Click "Confirm Order"
   - Customer will receive an SMS notification

## SMS Message Templates

### Order Placed (Pending)
```
Dear [Customer Name], your order #[ORDER_ID] has been received. We'll confirm it shortly. - PKS Pre-Pleating
```

### Order Confirmed
```
Dear [Customer Name], your order #[ORDER_ID] is confirmed! Expected delivery: [DATE]. - PKS Pre-Pleating
```

### Order Completed
```
Dear [Customer Name], your order #[ORDER_ID] has been delivered! Thank you for choosing PKS Pre-Pleating. Call 8056289435 for any queries.
```

### Order Cancelled
```
Dear [Customer Name], your order #[ORDER_ID] has been cancelled. For queries, call 8056289435. - PKS Pre-Pleating
```

## Cost Estimation
- Twilio SMS to India: ~₹0.50 - ₹1.00 per SMS
- Free trial credits: ₹1000+ (approximately 1000-2000 SMS)
- Monthly cost depends on order volume

## Alternative SMS Providers
If you prefer other providers, you can modify the Edge Function at:
`supabase/functions/send_sms_notification/index.ts`

Popular alternatives:
- **MSG91** (Indian provider, cheaper rates)
- **AWS SNS** (Amazon's SMS service)
- **Vonage** (formerly Nexmo)
- **Plivo**

## Troubleshooting

### SMS Not Sending
1. Check Supabase Edge Function logs
2. Verify Twilio credentials are correct
3. Ensure Twilio phone number supports SMS to India
4. Check Twilio account balance

### Customer Not Receiving SMS
1. Verify customer phone number is correct (10 digits)
2. Check if phone number is in DND (Do Not Disturb) list
3. Verify Twilio number is not blocked

## Customer Login & Order Tracking

Customers can:
1. Register at `/customer/register` with their phone number
2. Login at `/customer/login`
3. View all their orders and delivery status at `/customer/dashboard`
4. Track order status in real-time

## Admin Features

Admins can:
1. View all bookings in Admin Dashboard
2. Set expected delivery dates when confirming orders
3. Update order status (pending → confirmed → completed)
4. Automatic SMS sent to customers on status changes

## Support
For technical support or questions:
- Phone: 8056289435
- Location: Kamarajapuram, Tambaram
