# Testing Guide - Customer Authentication System

## Quick Test Checklist

### ✅ Test 1: Authentication Popup Appears
**Steps:**
1. Open website in new browser tab (or incognito mode)
2. Wait 2 seconds
3. Authentication popup should appear

**Expected Result:**
- Popup appears with "Welcome to PKS Pre-Pleating" title
- Two tabs visible: "Login" and "Register"
- "Skip" button at bottom

**If Failed:**
- Check browser console for errors (F12)
- Verify JavaScript is enabled
- Try clearing localStorage and refresh

---

### ✅ Test 2: Register New Account
**Steps:**
1. Click "Register" tab in popup
2. Enter name: "Test User"
3. Enter phone: "9876543210"
4. Click "Register" button

**Expected Result:**
- Success toast: "Registration Successful! 🎉"
- Redirects to customer dashboard
- User icon appears in header

**If Failed:**
- Check if phone already exists (try different number)
- Check browser console for error details
- Verify database connection

---

### ✅ Test 3: Login with Existing Account
**Steps:**
1. Logout from dashboard
2. Refresh page, wait for popup
3. Click "Login" tab
4. Enter phone: "9876543210"
5. Click "Login" button

**Expected Result:**
- Success toast: "Login Successful! 👋"
- Redirects to customer dashboard
- Shows correct customer name

**If Failed:**
- Verify account exists (register first)
- Check phone number is correct (10 digits)
- Check browser console for errors

---

### ✅ Test 4: Skip Authentication (Guest Mode)
**Steps:**
1. Clear localStorage (see below)
2. Refresh page, wait for popup
3. Click "Skip" button

**Expected Result:**
- Popup closes
- Toast: "You can register anytime..."
- Can browse website normally
- No user icon in header

**If Failed:**
- Check if already logged in
- Try incognito mode

---

### ✅ Test 5: Customer Dashboard Access
**Steps:**
1. Login with test account
2. Click user icon in header (desktop)
3. Or click "My Account" in mobile menu

**Expected Result:**
- Navigates to `/customer/dashboard`
- Shows customer profile card
- Shows "Your Orders" section
- Shows logout button

**If Failed:**
- Verify logged in (check localStorage)
- Check browser console for errors
- Try manual navigation to `/customer/dashboard`

---

### ✅ Test 6: View Order History
**Steps:**
1. Login to dashboard
2. Scroll to "Your Orders" section
3. Should see list of orders (if any)

**Expected Result:**
- Shows orders with matching phone number
- Each order shows: ID, items, amount, status, date
- If no orders: "No orders found" message

**If Failed:**
- Verify orders exist in database
- Check phone number matches
- Check browser console for errors

---

### ✅ Test 7: Logout Functionality
**Steps:**
1. From customer dashboard
2. Click "Logout" button
3. Confirm logout

**Expected Result:**
- Success toast: "Logged out successfully"
- Redirects to home page
- User icon disappears from header
- Auth popup will appear on next visit

**If Failed:**
- Check browser console for errors
- Manually clear localStorage (see below)

---

### ✅ Test 8: Session Persistence
**Steps:**
1. Login to account
2. Close browser tab
3. Open website in new tab
4. Check if still logged in

**Expected Result:**
- User icon still visible in header
- Can access dashboard without login
- Session persists across browser sessions

**If Failed:**
- Check if localStorage is enabled
- Check browser privacy settings
- Try different browser

---

### ✅ Test 9: Duplicate Registration Prevention
**Steps:**
1. Register account with phone "9876543210"
2. Logout
3. Try to register again with same phone

**Expected Result:**
- Error toast: "Account Already Exists"
- Message: "...already exists. Please login."
- Registration blocked

**If Failed:**
- Check database for duplicate prevention
- Check browser console for errors

---

### ✅ Test 10: Invalid Phone Number Validation
**Steps:**
1. Try to register with phone "123" (too short)
2. Try to register with phone "12345678901" (too long)
3. Try to register with phone "abcdefghij" (letters)

**Expected Result:**
- Error toast: "Invalid Phone Number"
- Message: "Please enter a valid 10-digit phone number"
- Registration blocked

**If Failed:**
- Check validation logic in CustomerAuthDialog.tsx
- Check browser console for errors

---

## Manual Testing Commands

### Check Login Status
```javascript
// Open browser console (F12) and run:
console.log('Logged In:', localStorage.getItem('pks-customer-logged-in'));
console.log('Customer ID:', localStorage.getItem('pks-customer-id'));
console.log('Customer Name:', localStorage.getItem('pks-customer-name'));
console.log('Customer Phone:', localStorage.getItem('pks-customer-phone'));
```

### Clear All Session Data
```javascript
// Open browser console (F12) and run:
localStorage.removeItem('pks-customer-logged-in');
localStorage.removeItem('pks-customer-id');
localStorage.removeItem('pks-customer-name');
localStorage.removeItem('pks-customer-phone');
localStorage.removeItem('pks-auth-dialog-seen');
console.log('Session cleared!');
location.reload();
```

### Force Show Auth Popup
```javascript
// Open browser console (F12) and run:
localStorage.removeItem('pks-auth-dialog-seen');
localStorage.removeItem('pks-customer-logged-in');
location.reload();
```

### Check Database Connection
```javascript
// Open browser console (F12) and run:
console.log('Supabase URL:', import.meta.env.VITE_SUPABASE_URL);
console.log('Has Anon Key:', !!import.meta.env.VITE_SUPABASE_ANON_KEY);
```

---

## Database Testing

### Check if Table Exists
```sql
-- Run in Supabase SQL Editor
SELECT * FROM customer_accounts LIMIT 5;
```

### Check Table Structure
```sql
-- Run in Supabase SQL Editor
SELECT column_name, data_type, is_nullable 
FROM information_schema.columns 
WHERE table_name = 'customer_accounts' 
ORDER BY ordinal_position;
```

### Check RLS Status
```sql
-- Run in Supabase SQL Editor
SELECT tablename, rowsecurity 
FROM pg_tables 
WHERE tablename = 'customer_accounts';
```
**Expected**: `rowsecurity` should be `false`

### Test Insert
```sql
-- Run in Supabase SQL Editor
INSERT INTO customer_accounts (name, phone) 
VALUES ('Test User', '0000000000') 
RETURNING *;
```

### Test Select
```sql
-- Run in Supabase SQL Editor
SELECT * FROM customer_accounts 
WHERE phone = '0000000000';
```

### Clean Up Test Data
```sql
-- Run in Supabase SQL Editor
DELETE FROM customer_accounts 
WHERE phone = '0000000000';
```

---

## Integration Testing

### Test 1: Register → Shop → Checkout
**Steps:**
1. Register new account
2. Browse products
3. Add items to cart
4. Proceed to checkout
5. Complete booking

**Expected:**
- All steps work smoothly
- Order linked to customer account
- Order appears in dashboard

### Test 2: Guest → Shop → Register → View Orders
**Steps:**
1. Skip authentication (guest mode)
2. Add items to cart
3. Complete booking as guest
4. Register account with same phone
5. Check dashboard for order

**Expected:**
- Guest booking works
- Can register later
- Order appears in dashboard (if same phone)

### Test 3: Login → Logout → Login
**Steps:**
1. Login to account
2. Navigate to dashboard
3. Logout
4. Login again

**Expected:**
- All transitions smooth
- No errors
- Dashboard loads correctly each time

---

## Mobile Testing

### Test on Mobile Devices
1. **iPhone Safari**
   - Test popup appearance
   - Test form inputs
   - Test navigation

2. **Android Chrome**
   - Test popup appearance
   - Test form inputs
   - Test navigation

3. **Tablet**
   - Test responsive layout
   - Test touch interactions

**Expected:**
- Popup fits screen
- Forms easy to fill
- Buttons easy to tap
- Navigation smooth

---

## Browser Compatibility Testing

### Test on Different Browsers
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)

**Expected:**
- Works on all modern browsers
- Consistent behavior
- No visual glitches

---

## Performance Testing

### Test Load Times
1. Open website
2. Measure time to popup appearance
3. Should be ~2 seconds

### Test Form Submission
1. Fill registration form
2. Click submit
3. Measure time to redirect
4. Should be < 2 seconds

---

## Error Handling Testing

### Test Network Errors
1. Disable internet
2. Try to register
3. Should show error message

### Test Invalid Data
1. Try empty name
2. Try invalid phone
3. Should show validation errors

### Test Database Errors
1. Temporarily break database connection
2. Try to register
3. Should show error message with details

---

## Security Testing

### Test Session Security
1. Login on one browser
2. Copy localStorage data
3. Try to use on another browser
4. Should work (simple auth)

### Test Phone Number Privacy
1. Register account
2. Check if phone visible in HTML
3. Should only be in localStorage

---

## Regression Testing

After any code changes, re-run:
1. ✅ Test 1: Popup appears
2. ✅ Test 2: Register works
3. ✅ Test 3: Login works
4. ✅ Test 7: Logout works
5. ✅ Test 8: Session persists

---

## Test Data

### Sample Test Accounts
```
Name: Test User 1
Phone: 9876543210

Name: Test User 2
Phone: 9876543211

Name: Test User 3
Phone: 9876543212
```

**Note**: Use these for testing, delete after testing complete.

---

## Automated Testing (Future)

### Unit Tests Needed
- [ ] Phone number validation
- [ ] Form submission logic
- [ ] localStorage operations
- [ ] Navigation logic

### Integration Tests Needed
- [ ] Registration flow
- [ ] Login flow
- [ ] Logout flow
- [ ] Dashboard access

### E2E Tests Needed
- [ ] Complete user journey
- [ ] Guest to registered user
- [ ] Order tracking flow

---

## Bug Reporting Template

When reporting bugs, include:

```
**Bug Title**: [Short description]

**Steps to Reproduce**:
1. Step 1
2. Step 2
3. Step 3

**Expected Result**:
[What should happen]

**Actual Result**:
[What actually happened]

**Browser**: [Chrome/Firefox/Safari/Edge]
**Device**: [Desktop/Mobile/Tablet]
**Console Errors**: [Copy from F12 console]
**Screenshots**: [If applicable]
```

---

**Last Updated**: December 11, 2025
**Version**: 1.0.0
