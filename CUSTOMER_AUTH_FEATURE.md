# Customer Authentication Feature

## Overview
The PKS Pre-Pleating Services website now includes a simple customer authentication system that allows customers to:
- Register with their name and phone number
- Login using their phone number
- Track their orders in a personalized dashboard
- Continue as guest without registration

## Features

### 1. Authentication Popup
- **Auto-Display**: Popup appears 2 seconds after visiting the website
- **One-Time Display**: Only shows once per browser session
- **Skip Option**: Users can continue as guest
- **Two Tabs**: Login and Register options in one dialog

### 2. Registration
- **Required Fields**:
  - Full Name
  - Phone Number (10 digits)
- **Validation**:
  - Name cannot be empty
  - Phone must be exactly 10 digits
  - Phone number must be unique
- **Success**: Automatically logs in and redirects to dashboard

### 3. Login
- **Required Field**:
  - Phone Number (10 digits)
- **Validation**:
  - Phone must be exactly 10 digits
  - Account must exist
- **Success**: Logs in and redirects to dashboard

### 4. Customer Dashboard
- **Access**: Available at `/customer/dashboard`
- **Features**:
  - View customer profile (name, phone)
  - View all orders/bookings
  - Order details with status
  - Logout button
- **Order Information**:
  - Booking ID
  - Items ordered
  - Total amount
  - Delivery address
  - Payment method
  - Order status (Pending, Confirmed, Completed, Cancelled)
  - Order date

### 5. Header Integration
- **Desktop View**:
  - User icon button appears when logged in
  - Hover shows "Welcome, [Name]"
  - Click navigates to dashboard
- **Mobile View**:
  - "My Account ([Name])" link in menu
  - Only visible when logged in

### 6. Logout
- **Location**: Customer Dashboard
- **Action**: Clears all session data
- **Redirect**: Returns to home page
- **Notification**: Success toast message

## Technical Implementation

### Database Schema

#### customer_accounts Table
```sql
CREATE TABLE customer_accounts (
  id uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  phone text UNIQUE NOT NULL,
  name text NOT NULL,
  created_at timestamptz DEFAULT now()
);
```

### Authentication Flow

#### Registration Flow
1. User enters name and phone number
2. System checks if phone already exists
3. If unique, creates new account
4. Stores customer data in localStorage:
   - `pks-customer-logged-in`: "true"
   - `pks-customer-id`: UUID
   - `pks-customer-name`: Customer name
   - `pks-customer-phone`: Phone number
5. Redirects to dashboard

#### Login Flow
1. User enters phone number
2. System queries database for matching account
3. If found, stores customer data in localStorage
4. Redirects to dashboard
5. If not found, shows error message

#### Session Management
- Uses browser localStorage for session persistence
- No password required (phone-based authentication)
- Session persists across browser sessions
- Cleared only on explicit logout

### Components

#### CustomerAuthDialog (`src/components/CustomerAuthDialog.tsx`)
- Modal dialog with tabs for Login/Register
- Auto-displays on first visit
- Handles form validation
- Manages authentication logic
- Stores session data

#### Customer Dashboard (`src/pages/customer/CustomerDashboard.tsx`)
- Protected route (redirects if not logged in)
- Displays customer information
- Lists all customer orders
- Provides logout functionality

### Security Considerations

#### Current Implementation
- Simple phone-based authentication
- No password required
- Public access to customer_accounts table
- Suitable for low-security use cases

#### Recommendations for Production
- Add OTP verification for phone numbers
- Implement proper session tokens
- Add rate limiting for login attempts
- Enable Row Level Security (RLS) on database
- Add password or PIN for additional security
- Implement HTTPS for all communications

## User Experience

### First-Time Visitor
1. Lands on website
2. After 2 seconds, sees authentication popup
3. Can choose to:
   - Register (if new customer)
   - Login (if returning customer)
   - Skip and continue as guest

### Registered Customer
1. Logs in via popup or manually
2. Sees user icon in header
3. Can access dashboard anytime
4. Views order history
5. Tracks order status
6. Logs out when done

### Guest User
1. Skips authentication popup
2. Can browse and shop normally
3. Can still place orders
4. Orders tracked by phone number
5. Can register/login later to view orders

## Benefits

### For Customers
- **Easy Registration**: Only name and phone required
- **Order Tracking**: View all orders in one place
- **No Password**: Simple phone-based login
- **Guest Option**: Can shop without registration
- **Persistent Session**: Stay logged in across visits

### For Business
- **Customer Database**: Build customer list
- **Order History**: Track customer purchases
- **Repeat Business**: Easy for customers to return
- **Customer Insights**: Understand buying patterns
- **Communication**: Have customer contact info

## Integration with Existing Features

### Shopping Cart
- Cart works for both logged-in and guest users
- Cart persists independently of login status
- Orders linked to customer account if logged in

### Booking System
- Bookings can be placed by guests or logged-in users
- Logged-in users see their bookings in dashboard
- Guest bookings tracked by phone number

### Order Tracking
- Logged-in customers: View all orders in dashboard
- Guest customers: Can register later to view past orders (if same phone)

## Future Enhancements
- Email notifications for order updates
- SMS notifications via WhatsApp
- Order cancellation from dashboard
- Reorder functionality
- Wishlist feature
- Address book for multiple delivery addresses
- Order rating and review system
- Loyalty points program
- Referral system
