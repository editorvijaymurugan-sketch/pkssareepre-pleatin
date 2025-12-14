# Troubleshooting Guide - PKS Pre-Pleating Services

## Customer Authentication Issues

### Problem: "Login Failed" or "Registration Failed" Error

#### Possible Causes:
1. Database connection issue
2. Supabase credentials incorrect
3. customer_accounts table doesn't exist
4. Network connectivity problem

#### Solutions:

**Step 1: Check Database Connection**
```javascript
// Open browser console (F12) and run:
console.log(import.meta.env.VITE_SUPABASE_URL);
console.log(import.meta.env.VITE_SUPABASE_ANON_KEY);
```
- Both should show valid values
- If undefined, check `.env` file

**Step 2: Verify Table Exists**
- Go to Supabase Dashboard
- Navigate to Table Editor
- Look for `customer_accounts` table
- Should have columns: id, phone, name, created_at

**Step 3: Check Browser Console**
- Open Developer Tools (F12)
- Go to Console tab
- Look for detailed error messages
- Error message will show specific issue

**Step 4: Test Database Manually**
```sql
-- Run in Supabase SQL Editor
SELECT * FROM customer_accounts LIMIT 1;
```
- Should return empty array or data
- If error, table doesn't exist

**Step 5: Re-apply Migration**
If table doesn't exist, contact support to re-apply migration:
`00003_update_customer_accounts_for_simple_auth.sql`

### Problem: "Account Already Exists" When Registering

#### Cause:
Phone number already registered in database

#### Solution:
1. Use the Login tab instead
2. Enter the same phone number
3. Or use a different phone number

### Problem: "Account Not Found" When Logging In

#### Cause:
No account exists with that phone number

#### Solution:
1. Switch to Register tab
2. Create a new account
3. Double-check phone number is correct

### Problem: Authentication Popup Doesn't Appear

#### Possible Causes:
1. Already seen popup in this session
2. Already logged in
3. JavaScript error

#### Solutions:

**Check if Already Logged In:**
```javascript
// Open browser console (F12) and run:
console.log(localStorage.getItem('pks-customer-logged-in'));
```
- If "true", you're already logged in
- Look for user icon in header

**Clear Session and Retry:**
```javascript
// Open browser console (F12) and run:
localStorage.removeItem('pks-auth-dialog-seen');
localStorage.removeItem('pks-customer-logged-in');
localStorage.removeItem('pks-customer-id');
localStorage.removeItem('pks-customer-name');
localStorage.removeItem('pks-customer-phone');
// Then refresh page
location.reload();
```

**Check for JavaScript Errors:**
- Open Developer Tools (F12)
- Go to Console tab
- Look for red error messages
- Report errors to support

## Shopping Cart Issues

### Problem: Cart Items Disappear After Refresh

#### Cause:
localStorage not working or disabled

#### Solutions:

**Check localStorage:**
```javascript
// Open browser console (F12) and run:
console.log(localStorage.getItem('pks-cart'));
```
- Should show cart data
- If null, localStorage not working

**Enable localStorage:**
1. Check browser privacy settings
2. Disable "Block all cookies"
3. Allow localStorage for this site
4. Try incognito/private mode

**Clear and Retry:**
```javascript
// Open browser console (F12) and run:
localStorage.removeItem('pks-cart');
location.reload();
```

### Problem: Cart Count Not Updating

#### Cause:
React state not syncing

#### Solution:
1. Refresh the page
2. Clear browser cache
3. Try adding item again

### Problem: "Add to Cart" Button Not Working

#### Possible Causes:
1. JavaScript error
2. Product data missing
3. Cart context not loaded

#### Solutions:

**Check Console for Errors:**
- Open Developer Tools (F12)
- Look for error messages
- Report to support

**Try "Buy Now" Instead:**
- Use "Buy Now" button
- Goes directly to checkout
- Bypasses cart system

## Customer Dashboard Issues

### Problem: Dashboard Shows "No Orders Found"

#### Possible Causes:
1. No orders placed yet
2. Phone number mismatch
3. Orders placed as guest with different phone

#### Solutions:

**Verify Phone Number:**
```javascript
// Open browser console (F12) and run:
console.log(localStorage.getItem('pks-customer-phone'));
```
- Check if matches phone used for orders

**Check Order History:**
- Orders must have same phone number
- Guest orders with different phone won't show
- Contact support to link orders

### Problem: Can't Access Dashboard (Redirects to Home)

#### Cause:
Not logged in

#### Solution:
1. Login using authentication popup
2. Or manually go to home page
3. Wait for popup to appear
4. Login with your credentials

### Problem: Logout Doesn't Work

#### Solution:
```javascript
// Manual logout - Open browser console (F12) and run:
localStorage.removeItem('pks-customer-logged-in');
localStorage.removeItem('pks-customer-id');
localStorage.removeItem('pks-customer-name');
localStorage.removeItem('pks-customer-phone');
localStorage.removeItem('pks-auth-dialog-seen');
location.reload();
```

## General Issues

### Problem: Page Not Loading

#### Solutions:
1. Check internet connection
2. Clear browser cache
3. Try different browser
4. Disable browser extensions
5. Try incognito/private mode

### Problem: Images Not Loading

#### Solutions:
1. Check internet connection
2. Wait a few seconds (slow connection)
3. Refresh page
4. Clear browser cache

### Problem: Buttons Not Clickable

#### Solutions:
1. Wait for page to fully load
2. Disable browser extensions
3. Try different browser
4. Check for JavaScript errors in console

## Browser Compatibility

### Recommended Browsers:
- ✅ Google Chrome (latest)
- ✅ Mozilla Firefox (latest)
- ✅ Microsoft Edge (latest)
- ✅ Safari (latest)

### Not Recommended:
- ❌ Internet Explorer (any version)
- ❌ Very old browser versions

## Mobile Issues

### Problem: Popup Doesn't Fit Screen

#### Solution:
- Rotate device to portrait mode
- Zoom out if needed
- Use desktop version if available

### Problem: Can't Click Buttons on Mobile

#### Solution:
- Tap directly on button text
- Disable "zoom on double tap"
- Try landscape orientation

## Data Privacy

### Clearing All Data

To completely clear all stored data:

```javascript
// Open browser console (F12) and run:
localStorage.clear();
location.reload();
```

**Warning**: This will:
- Log you out
- Clear your cart
- Remove all preferences
- You'll need to login again

## Getting Help

### Before Contacting Support:

1. **Check Browser Console**
   - Press F12
   - Go to Console tab
   - Take screenshot of errors

2. **Note What You Were Doing**
   - What page were you on?
   - What button did you click?
   - What error message appeared?

3. **Try Basic Fixes**
   - Refresh page
   - Clear cache
   - Try different browser
   - Check internet connection

### Contact Information:

**Phone**: 8056289435
**Business**: PKS Pre-Pleating Services
**Location**: Kamarajapuram, Tambaram

### Information to Provide:

1. What were you trying to do?
2. What error message did you see?
3. What browser are you using?
4. Are you on mobile or desktop?
5. Screenshot of error (if possible)
6. Console error messages (if any)

## Common Error Messages

### "Failed to fetch"
- **Cause**: Network connection issue
- **Solution**: Check internet, retry

### "Invalid phone number"
- **Cause**: Phone not 10 digits
- **Solution**: Enter exactly 10 digits

### "An error occurred"
- **Cause**: Generic error
- **Solution**: Check console for details

### "Account already exists"
- **Cause**: Phone already registered
- **Solution**: Use login instead

### "Account not found"
- **Cause**: Phone not registered
- **Solution**: Register first

## Performance Issues

### Problem: Website Loading Slowly

#### Solutions:
1. Check internet speed
2. Close other tabs/apps
3. Clear browser cache
4. Try different network
5. Wait for peak hours to pass

### Problem: Images Loading Slowly

#### Solutions:
1. Wait for images to load
2. Scroll slowly to allow loading
3. Check internet connection
4. Images are optimized, should load quickly

## Security Notes

### Protecting Your Account:

1. **Don't Share Phone Number**: Keep your registered phone private
2. **Use Private Browsing**: On shared computers
3. **Logout When Done**: Especially on public computers
4. **Clear Data**: On shared devices after use

### If Account Compromised:

1. Contact support immediately: 8056289435
2. Provide your phone number
3. Request account review
4. Change phone number if needed

---

**Last Updated**: December 11, 2025
**Version**: 1.0.0

For additional help, call: **8056289435**
