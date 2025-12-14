# Shopping Cart Feature

## Overview
The PKS Pre-Pleating Services website now includes a fully functional shopping cart system that allows customers to:
- Add products and services to cart
- View cart items with quantities
- Update item quantities
- Remove items from cart
- Proceed to checkout from cart
- Cart persists across page refreshes (stored in localStorage)

## Features

### 1. Add to Cart
- **Products Page**: Each product has an "Add to Cart" button
- **Services Page**: Each service has an "Add to Cart" button
- Clicking "Add to Cart" automatically adds the item to the cart
- Toast notification confirms the item was added
- If item already exists in cart, quantity is increased

### 2. Cart Icon in Header
- Shopping cart icon displayed in header (desktop and mobile)
- Badge shows total number of items in cart
- Clicking cart icon navigates to cart page
- Cart count updates in real-time

### 3. Cart Page (`/cart`)
- Displays all items in cart with:
  - Product/Service image
  - Name and type
  - Price per unit
  - Quantity controls (+ / -)
  - Total price per item
  - Remove button
- Order Summary section shows:
  - Subtotal
  - Total item count
  - Grand total
- "Proceed to Checkout" button navigates to booking page
- "Continue Shopping" button returns to products page
- Empty cart state with helpful message

### 4. Quantity Management
- Increase quantity: Click "+" button
- Decrease quantity: Click "-" button
- Minimum quantity: 1 (decreasing below 1 removes item)
- Remove item: Click trash icon

### 5. Cart Persistence
- Cart data stored in browser localStorage
- Cart persists across:
  - Page refreshes
  - Browser sessions
  - Navigation between pages
- Cart cleared after successful booking

### 6. Booking Integration
- Cart items automatically loaded in booking page
- Can still add items directly from product/service pages
- After successful booking:
  - Cart is cleared
  - User redirected to home page
  - Success notification displayed

## Technical Implementation

### Cart Context (`src/contexts/CartContext.tsx`)
Global state management for cart using React Context API:
- `cart`: Array of cart items
- `addToCart()`: Add item to cart
- `removeFromCart()`: Remove item from cart
- `updateQuantity()`: Update item quantity
- `clearCart()`: Clear all items
- `cartCount`: Total number of items
- `cartTotal`: Total price of all items

### Cart Item Structure
```typescript
interface CartItem {
  id: string;
  name: string;
  type: "product" | "service";
  price: number;
  quantity: number;
  image_url?: string;
}
```

### Pages Updated
1. **Products Page** (`src/pages/Products.tsx`)
   - Added "Add to Cart" button
   - Kept "Buy Now" button for direct checkout

2. **Services Page** (`src/pages/Services.tsx`)
   - Added "Add to Cart" button
   - Kept "Book Now" button for direct checkout

3. **Cart Page** (`src/pages/Cart.tsx`)
   - New dedicated cart page
   - Full cart management interface

4. **Booking Page** (`src/pages/Booking.tsx`)
   - Loads items from global cart
   - Clears cart after successful booking

5. **Header** (`src/components/common/Header.tsx`)
   - Added cart icon with item count badge
   - Available in desktop and mobile views

### Routes
- `/cart` - Shopping cart page (hidden from navigation menu)

## User Flow

### Adding Items to Cart
1. Customer browses products or services
2. Clicks "Add to Cart" button
3. Item added to cart with quantity 1
4. Toast notification confirms addition
5. Cart icon badge updates with new count
6. Customer can continue shopping or view cart

### Viewing Cart
1. Customer clicks cart icon in header
2. Navigates to `/cart` page
3. Sees all cart items with details
4. Can update quantities or remove items
5. Views order summary with total

### Checkout Process
1. From cart page, click "Proceed to Checkout"
2. Navigates to booking page with cart items pre-loaded
3. Fill in customer details and delivery address
4. Select payment method
5. Submit booking
6. Cart automatically cleared
7. Redirected to home page with success message

## Benefits

### For Customers
- **Convenience**: Add multiple items before checkout
- **Flexibility**: Review and modify cart before purchasing
- **Transparency**: See total cost before providing details
- **Persistence**: Cart saved even if they leave the site

### For Business
- **Higher Order Value**: Customers can easily add multiple items
- **Reduced Friction**: Streamlined shopping experience
- **Better UX**: Modern e-commerce experience
- **Increased Conversions**: Easier to complete purchases

## Future Enhancements
- Add wishlist functionality
- Implement cart item recommendations
- Add coupon/discount code support
- Show estimated delivery time in cart
- Add "Save for Later" feature
- Email cart reminders for abandoned carts
