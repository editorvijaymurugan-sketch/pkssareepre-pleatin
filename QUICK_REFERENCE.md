# Quick Reference - Customer Authentication System

## 🚀 Quick Start

### For Customers:

**Register New Account:**
1. Visit website → Wait 2 seconds
2. Click "Register" tab
3. Enter name and phone (10 digits)
4. Click "Register" → Done! ✅

**Login to Existing Account:**
1. Visit website → Wait 2 seconds
2. Click "Login" tab
3. Enter phone (10 digits)
4. Click "Login" → Done! ✅

**View Orders:**
1. Login to account
2. Click user icon in header
3. View all your orders ✅

**Logout:**
1. Go to dashboard
2. Click "Logout" button
3. Confirm → Done! ✅

---

## 🔧 Quick Fixes

### Popup Not Appearing?
```javascript
// Browser console (F12):
localStorage.removeItem('pks-auth-dialog-seen');
location.reload();
```

### Can't Login?
```javascript
// Browser console (F12):
localStorage.clear();
location.reload();
// Then register again
```

### Check Login Status:
```javascript
// Browser console (F12):
console.log(localStorage.getItem('pks-customer-logged-in'));
```

---

## 📊 Database Quick Check

### Verify Table Exists:
```sql
SELECT * FROM customer_accounts LIMIT 1;
```

### Check Table Structure:
```sql
\d customer_accounts
```

### Count Customers:
```sql
SELECT COUNT(*) FROM customer_accounts;
```

---

## 🎯 Key Features

| Feature | Status | Location |
|---------|--------|----------|
| Registration | ✅ Working | Auth Popup |
| Login | ✅ Working | Auth Popup |
| Dashboard | ✅ Working | /customer/dashboard |
| Order History | ✅ Working | Dashboard |
| Logout | ✅ Working | Dashboard |
| Guest Mode | ✅ Working | Skip Button |
| Cart Integration | ✅ Working | All Pages |

---

## 📱 Contact

**Phone**: 8056289435  
**Business**: PKS Pre-Pleating Services  
**Location**: Kamarajapuram, Tambaram

---

## 📚 Documentation

- **CUSTOMER_AUTH_FEATURE.md** - Complete feature documentation
- **TROUBLESHOOTING.md** - Problem solving guide
- **TESTING_GUIDE.md** - Testing procedures
- **DATABASE_FIX_SUMMARY.md** - Recent database fix details
- **IMPLEMENTATION_SUMMARY.md** - Full implementation details

---

## ⚡ Quick Commands

### Clear All Data:
```javascript
localStorage.clear();
location.reload();
```

### Force Show Popup:
```javascript
localStorage.removeItem('pks-auth-dialog-seen');
localStorage.removeItem('pks-customer-logged-in');
location.reload();
```

### Manual Logout:
```javascript
localStorage.removeItem('pks-customer-logged-in');
localStorage.removeItem('pks-customer-id');
localStorage.removeItem('pks-customer-name');
localStorage.removeItem('pks-customer-phone');
location.reload();
```

---

**Last Updated**: December 11, 2025  
**Version**: 1.0.0  
**Status**: ✅ Production Ready
