# PKS Pre-Pleating Services - Admin Panel Setup Guide

## Overview
Your website now includes a comprehensive Content Management System (CMS) that allows you to edit all text, images, and settings across all pages without touching any code.

## Admin Panel Features

### ✅ What You Can Edit:
1. **Text Content** - All headings, descriptions, and paragraphs on every page
2. **Images** - Hero images, product images, service images, portfolio images, and logos
3. **Site Settings** - Business information, contact details, social media links
4. **Products** - Add, edit, delete products with images and pricing
5. **Services** - Manage service offerings with descriptions and pricing
6. **Portfolio** - Upload and manage your work gallery
7. **Colors & Branding** - Customize the website's color scheme

---

## Step 1: Create Your Admin Account

### Register as Admin:
1. Open your browser and go to: **`/admin/register`**
2. Fill in the registration form:
   - **Username**: Choose a username (letters, numbers, and underscores only)
   - **Password**: Create a strong password
   - **Full Name**: Your name
3. Click **"Register"**

**IMPORTANT**: The **first user** to register will automatically become the admin!

---

## Step 2: Login to Admin Panel

1. Go to: **`/admin/login`**
2. Enter your username and password
3. Click **"Sign In"**
4. You'll be redirected to the Admin Dashboard

---

## Step 3: Using the Admin Dashboard

The Admin Dashboard has 5 main tabs:

### 📦 **Products Tab**
- **Add New Product**: Click "Add Product" button
  - Enter product name, description, and price
  - Upload product image
  - Set stock quantity
  - Click "Save"
- **Edit Product**: Click the edit icon on any product
- **Delete Product**: Click the delete icon

### ✂️ **Services Tab**
- **Add New Service**: Click "Add Service" button
  - Enter service name and description
  - Set service price
  - Upload service image
  - Click "Save"
- **Edit/Delete**: Same as products

### 🖼️ **Portfolio Tab**
- **Upload Work Images**: Click "Add Portfolio Item"
  - Upload image of your completed work
  - Add title and description
  - Click "Save"
- **Manage Gallery**: Edit or delete portfolio items

### ⚙️ **Settings Tab**
Edit global site settings:

#### **Site Branding**
- **Website Logo**: Upload your business logo
  - Click "Choose File" or drag and drop
  - Recommended size: 200x60px
  - Transparent PNG format works best
  - Logo will appear in the header automatically

#### **Payment Options**
- Enable/disable Cash on Delivery
- Enable/disable Online Payment
- Upload QR code for online payments
- Set UPI ID

#### **Delivery Charges**
- Base delivery charge
- Additional charges per kilometer
- Delivery radius settings

#### **Business Information**
- Business name
- Phone number
- WhatsApp number
- Location details

### 📝 **CMS Tab** (Most Important!)
Edit content on all pages:

#### **Home Page - Hero Section**
- Title (main heading)
- Subtitle
- Description
- Background image

#### **Home Page - About Section**
- About title
- About description
- About image

#### **Contact Page**
- Phone number
- Location
- Full address
- Email
- WhatsApp number

#### **Products Page Header**
- Page title
- Page description

#### **Services Page Header**
- Page title
- Page description

---

## Step 4: Editing Content

### To Edit Text:
1. Go to the **CMS Tab** in Admin Dashboard
2. Find the section you want to edit
3. Type directly in the text field
4. Changes are saved automatically when you finish typing

### To Upload Images:
1. Find the image upload section
2. Click **"Choose File"** or drag and drop
3. Select your image (JPG, PNG, or WebP)
4. Image will be uploaded and displayed immediately
5. The website will automatically use the new image

### To Change Colors:
1. Go to **Settings Tab**
2. Find "Primary Color"
3. Click the color picker
4. Choose your desired color
5. Click "Save"

---

## Step 5: Managing Products & Services

### Adding a Product:
1. Go to **Products Tab**
2. Click **"Add Product"**
3. Fill in:
   - **Name**: Product name (e.g., "Girls Saree Aari Belt - Gold")
   - **Description**: Detailed description
   - **Price**: Price in rupees (e.g., 500)
   - **Stock**: Available quantity
   - **Image**: Upload product photo
4. Click **"Save"**

### Adding a Service:
1. Go to **Services Tab**
2. Click **"Add Service"**
3. Fill in:
   - **Name**: Service name (e.g., "Saree Pre-Pleating")
   - **Description**: What's included
   - **Price**: Service price
   - **Image**: Upload service photo
4. Click **"Save"**

---

## Step 6: Managing Orders

### View Customer Orders:
1. Go to **Admin CRM** (separate page at `/admin/crm`)
2. View all customer inquiries and bookings
3. See customer details, order items, and delivery information
4. Track order status

---

## Important Notes

### 🔒 Security:
- **Never share your admin credentials**
- Use a strong password
- Only trusted staff should have admin access

### 💾 Backups:
- All content is automatically saved to the database
- Images are stored securely in cloud storage
- No manual backup needed

### 📱 Mobile Friendly:
- Admin panel works on desktop, tablet, and mobile
- Best experience on desktop for image uploads

### 🎨 Image Guidelines:
- **Logo**: 200x60px, transparent PNG recommended (appears in header)
- **Products**: Square images (500x500px or larger)
- **Services**: Landscape images (1200x800px or larger)
- **Hero/Banner**: Wide images (1920x1080px or larger)
- **File Size**: Keep under 1MB for faster loading

---

## 🗺️ Setting Your Business Location on Map

### How to Update Map Location:

1. **Go to Settings Tab** in Admin Dashboard
2. **Scroll down to "Map Location" section**
3. **Get Your Google Maps Embed URL**:

#### Step-by-Step: Getting Embed URL from Google Maps

1. **Open Google Maps** in your web browser: [https://www.google.com/maps](https://www.google.com/maps)
2. **Search for your business** or navigate to your exact location
3. **Click the "Share" button** (usually at the bottom or in the info panel)
4. **Select the "Embed a map" tab**
5. **Copy the iframe src URL**:
   - You'll see HTML code like: `<iframe src="https://www.google.com/maps/embed?pb=..." ...></iframe>`
   - **Copy ONLY the URL** inside the `src="..."` part
   - The URL should start with: `https://www.google.com/maps/embed`
6. **Go back to the Admin Settings page**
7. **Paste the URL** in the "Google Maps Embed URL" field

4. **Enter Your Address**:
   - Type your complete business address in the "Business Address" field
   - Example: "PKS - Saree Pre-pleating, Rajiv Gandhi St, Kamarajapuram, Sembakkam, Chennai, Tamil Nadu 600073"

5. **Preview Your Location**:
   - The map will automatically show a preview below the URL field
   - Make sure the location matches your business

6. **Save Location**:
   - Click the **"Save Location"** button
   - You'll see a success message
   - The Contact page map will automatically update

### What Happens After Saving:
- ✅ Contact page displays an interactive Google Map with your location
- ✅ Address is displayed on the Contact page
- ✅ "Get Directions" button uses your saved location
- ✅ Customers can easily find your business
- ✅ Map is fully interactive (zoom, pan, street view)


### Tips:
- 🔍 Make sure you select the correct location on Google Maps before getting the embed URL
- 📋 Copy the ENTIRE embed URL (it's usually quite long)
- 🔄 You can update the location anytime
- 💡 Use the preview in the admin panel to verify the map before saving
- ⚠️ The URL must start with `https://www.google.com/maps/embed`

---

## Quick Access Links

- **Admin Login**: `/admin/login`
- **Admin Dashboard**: `/admin/dashboard`
- **Admin CRM**: `/admin/crm`
- **Website Home**: `/`

---

## Troubleshooting

### Can't Login?
- Make sure you registered first at `/admin/register`
- Check username and password (case-sensitive)
- Clear browser cache and try again

### Images Not Uploading?
- Check file size (must be under 1MB)
- Use JPG, PNG, or WebP format
- Check internet connection

### Changes Not Showing?
- Refresh the page (Ctrl+F5 or Cmd+Shift+R)
- Clear browser cache
- Wait a few seconds for changes to save

### Need Help?
- Contact your web developer
- Check browser console for error messages (F12 key)

---

## Summary

You now have full control over your website content! You can:
- ✅ Edit all text on every page
- ✅ Upload and change all images
- ✅ Manage products and services
- ✅ Update contact information
- ✅ Customize colors and branding
- ✅ View customer orders
- ✅ Set your business location on the map

**No coding knowledge required!**

---

## Next Steps

1. **Register your admin account** at `/admin/register`
2. **Login** at `/admin/login`
3. **Start editing** your website content in the CMS tab
4. **Add your products** in the Products tab
5. **Upload your work** in the Portfolio tab

Enjoy managing your website! 🎉
