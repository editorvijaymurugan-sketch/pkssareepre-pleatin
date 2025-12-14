# Cart Page - User Guide

## Page Overview

The cart page is now your complete checkout destination. Everything you need to place an order is on this single page.

## Page Layout

```
┌─────────────────────────────────────────────────────────────────┐
│                    Shopping Cart & Checkout                      │
│                     X items in your cart                         │
└─────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────┐  ┌────────────────────────┐
│         YOUR ITEMS               │  │   ORDER SUMMARY        │
│  ┌────────────────────────────┐  │  │                        │
│  │ [Image] Product Name       │  │  │ Subtotal: ₹XXX        │
│  │         Product Type       │  │  │ Items: X              │
│  │  [-] 1 [+]    ₹XXX  [🗑️]  │  │  │ Delivery: ₹XXX        │
│  └────────────────────────────┘  │  │                        │
│  ┌────────────────────────────┐  │  │ ─────────────────────  │
│  │ [Image] Service Name       │  │  │                        │
│  │         Service Type       │  │  │ Total: ₹XXX           │
│  │  [-] 2 [+]    ₹XXX  [🗑️]  │  │  │                        │
│  └────────────────────────────┘  │  │ [Place Order]         │
│                                   │  │                        │
│      DELIVERY DETAILS             │  │ [Continue Shopping]   │
│  ┌────────────────────────────┐  │  │                        │
│  │ Full Name: [_____________] │  │  │ Terms & conditions... │
│  │ Phone: [__________________] │  │  └────────────────────────┘
│  │ Address: [________________] │  │
│  │          [________________] │  │
│  │ Distance: [___] km         │  │
│  │ Base: ₹100 up to 10km...   │  │
│  └────────────────────────────┘  │
│                                   │
│      PAYMENT METHOD               │
│  ┌────────────────────────────┐  │
│  │ ○ Cash on Delivery         │  │
│  │   Pay when you receive     │  │
│  │                            │  │
│  │ ○ Online Payment (QR)      │  │
│  │   Scan QR code to pay      │  │
│  └────────────────────────────┘  │
└──────────────────────────────────┘
```

## Section Breakdown

### 1. Your Items Section
**What it shows:**
- All products and services in your cart
- Product/service image
- Name and type
- Quantity controls (- and +)
- Price per item
- Total price for that item
- Delete button (trash icon)

**What you can do:**
- Increase quantity: Click [+] button
- Decrease quantity: Click [-] button
- Remove item: Click trash icon [🗑️]
- View item details: See image, name, type

### 2. Delivery Details Section
**Required fields (marked with *):**
- **Full Name**: Your complete name
- **Phone Number**: 10-digit mobile number
- **Delivery Address**: Complete address with landmarks
- **Distance**: Distance from Tambaram in kilometers

**Tips:**
- If logged in, name and phone auto-fill
- Enter accurate distance for correct delivery charge
- Include landmarks in address for easy delivery

**Delivery Charge Calculation:**
```
Distance     | Delivery Charge
─────────────┼────────────────
0-10 km      | ₹100
11-15 km     | ₹150
16-20 km     | ₹200
21-25 km     | ₹250
26-30 km     | ₹300
```

Formula: ₹100 base + ₹50 per 5km beyond 10km

### 3. Payment Method Section
**Options:**

**Option 1: Cash on Delivery (COD)**
- Pay when you receive your order
- No advance payment needed
- Cash payment to delivery person

**Option 2: Online Payment (QR Code)**
- Scan QR code to pay
- UPI/Bank transfer
- Payment before delivery

### 4. Order Summary Section (Sidebar)
**Displays:**
- **Subtotal**: Total of all items
- **Items**: Number of items in cart
- **Delivery Charge**: Based on distance entered
- **Total Amount**: Subtotal + Delivery Charge

**Actions:**
- **Place Order**: Submit your order
- **Continue Shopping**: Go back to products

**Information:**
- Terms and conditions note
- WhatsApp confirmation message

## Step-by-Step Guide

### Step 1: Review Your Cart
1. Check all items in "Your Items" section
2. Verify quantities are correct
3. Update quantities if needed (use + and - buttons)
4. Remove unwanted items (click trash icon)

### Step 2: Enter Delivery Details
1. Fill in your full name
2. Enter 10-digit phone number
3. Type complete delivery address
4. Enter distance from Tambaram in km
5. Watch delivery charge update automatically

### Step 3: Select Payment Method
1. Choose between Cash on Delivery or Online Payment
2. Click the radio button next to your choice
3. Read the description to understand the option

### Step 4: Review Order Summary
1. Check subtotal is correct
2. Verify delivery charge matches distance
3. Confirm total amount
4. Review number of items

### Step 5: Place Order
1. Click "Place Order" button
2. Wait for confirmation (button shows "Placing Order...")
3. Success message appears
4. WhatsApp opens with order details
5. Cart clears automatically
6. Redirected to home page

## Features Explained

### Auto-fill for Logged-in Users
**If you're logged in:**
- Name automatically filled
- Phone number automatically filled
- Just enter address and distance
- Saves time on repeat orders

**If you're a guest:**
- Fill all fields manually
- Consider registering for faster checkout next time

### Real-time Delivery Charge
**How it works:**
- As you type distance, delivery charge updates
- No surprises at checkout
- See exact cost before placing order

**Example:**
- Type "5" → See ₹100
- Type "15" → See ₹150
- Type "25" → See ₹250

### WhatsApp Integration
**After placing order:**
- WhatsApp opens automatically
- Message pre-filled with order details
- Sent to business number: 8056289435
- Includes:
  - Your details (name, phone, address)
  - Order items with quantities and prices
  - Subtotal, delivery charge, total
  - Payment method selected

### Form Validation
**The system checks:**
- ✅ Name is not empty
- ✅ Phone is exactly 10 digits
- ✅ Address is not empty
- ✅ Distance is greater than 0
- ✅ Payment method is selected

**If something is wrong:**
- Red error message appears below field
- Cannot submit until fixed
- Clear instructions on what to fix

## Common Scenarios

### Scenario 1: First-time Customer
1. Browse products/services
2. Add items to cart
3. Go to cart page
4. Fill all delivery details manually
5. Select payment method
6. Place order
7. Consider registering for easier future orders

### Scenario 2: Returning Customer (Logged In)
1. Browse products/services
2. Add items to cart
3. Go to cart page
4. Name and phone already filled
5. Just enter address and distance
6. Select payment method
7. Place order quickly

### Scenario 3: Updating Order Before Checkout
1. View cart items
2. Realize need more quantity
3. Click [+] to increase
4. Or click [-] to decrease
5. Or click trash to remove
6. Continue with checkout

### Scenario 4: Checking Delivery Cost First
1. Add items to cart
2. Go to cart page
3. Enter distance in delivery details
4. See delivery charge calculate
5. Decide if acceptable
6. Either proceed or adjust order

## Tips for Best Experience

### 1. Accurate Distance
- Use Google Maps to check distance from Tambaram
- Enter accurate distance for correct charges
- Round to nearest kilometer

### 2. Complete Address
- Include house/flat number
- Add street name
- Mention landmarks
- Specify area/locality
- Add pincode if possible

### 3. Verify Phone Number
- Double-check phone number
- Must be 10 digits
- No spaces or special characters
- This is how business will contact you

### 4. Review Before Submitting
- Check all items one last time
- Verify quantities
- Confirm delivery address
- Review total amount
- Ensure payment method is correct

### 5. Save Order Details
- Take screenshot of order summary
- Note down order details
- Keep WhatsApp message for reference
- Check customer dashboard later (if logged in)

## Troubleshooting

### Problem: Can't click "Place Order"
**Solution:**
- Check all required fields are filled (marked with *)
- Ensure phone number is exactly 10 digits
- Verify distance is greater than 0
- Make sure payment method is selected

### Problem: Delivery charge seems high
**Solution:**
- Check distance entered
- Verify it's in kilometers, not meters
- Use formula: ₹100 + ₹50 per 5km beyond 10km
- Contact business if still unclear: 8056289435

### Problem: Name and phone not auto-filling
**Solution:**
- You might not be logged in
- Login to your account first
- Or fill manually as guest

### Problem: WhatsApp not opening
**Solution:**
- Check popup blocker settings
- Allow popups for this website
- Try different browser
- WhatsApp must be installed (mobile) or use WhatsApp Web (desktop)

### Problem: Order not in dashboard
**Solution:**
- Make sure you're logged in
- Use same phone number for order and account
- Wait a few seconds and refresh
- Contact support if issue persists

## Mobile Experience

### On Mobile Devices:
- All sections stack vertically
- Order summary appears at bottom
- Easy to scroll through sections
- Large touch targets for buttons
- Responsive form fields
- Smooth scrolling

### Tips for Mobile:
- Use portrait mode for best experience
- Zoom in if needed for form fields
- Scroll slowly to see all sections
- Double-check entries before submitting

## Security & Privacy

### Your Data:
- ✅ Stored securely in database
- ✅ Used only for order processing
- ✅ Not shared with third parties
- ✅ WhatsApp messages encrypted

### Payment:
- ✅ No credit card data collected
- ✅ COD option available
- ✅ Online payment via secure QR code
- ✅ No payment gateway fees

## Need Help?

### Contact Information:
- **Phone**: 8056289435
- **Business**: PKS Pre-Pleating Services
- **Location**: Kamarajapuram, Tambaram

### Before Calling:
- Have your order details ready
- Note any error messages
- Take screenshot if possible
- Mention what step you're stuck on

---

**Last Updated**: December 11, 2025  
**Page Version**: 2.0.0  
**Status**: ✅ Active
