# Domain Setup Guide - PKS Pre-Pleating Services

## Current Nameservers
Your domain is currently using GoDaddy nameservers:
- `ns39.domaincontrol.com`
- `ns40.domaincontrol.com`

## How to Connect Your Domain to This Website

### Step 1: Determine Your Hosting Provider
First, identify where this website is deployed:
- Vercel
- Netlify
- AWS
- DigitalOcean
- Other hosting service

### Step 2: Get Required Information

Contact your hosting provider or check their dashboard to get:

**Option A: IP Address (for A Record)**
- Example: `123.45.67.89`
- Use this if keeping GoDaddy nameservers

**Option B: Nameservers (for full DNS management)**
- Example: `ns1.hostingprovider.com` and `ns2.hostingprovider.com`
- Use this if transferring DNS management to hosting provider

### Step 3: Configure DNS at GoDaddy

#### Method 1: Using A Records (Keep GoDaddy Nameservers)

1. Log in to [GoDaddy](https://www.godaddy.com)
2. Go to **My Products** → **Domains**
3. Click **DNS** next to your domain
4. Click **Add** to create new records

**Add these DNS records:**

| Type | Name | Value | TTL |
|------|------|-------|-----|
| A | @ | [Your Server IP] | 600 |
| A | www | [Your Server IP] | 600 |

**Example:**
```
Type: A
Name: @
Value: 76.76.21.21
TTL: 600 seconds

Type: A
Name: www
Value: 76.76.21.21
TTL: 600 seconds
```

5. Click **Save**
6. Wait 30-120 minutes for propagation

#### Method 2: Change Nameservers (Transfer DNS Management)

1. Log in to [GoDaddy](https://www.godaddy.com)
2. Go to **My Products** → **Domains**
3. Click **Manage** next to your domain
4. Scroll to **Nameservers** section
5. Click **Change**
6. Select **Custom**
7. Enter your hosting provider's nameservers:
   ```
   Nameserver 1: [provided by hosting]
   Nameserver 2: [provided by hosting]
   ```
8. Click **Save**
9. Wait 24-48 hours for propagation

### Step 4: Verify Domain Connection

After DNS propagation, verify your domain is working:

1. **Check DNS Propagation:**
   - Visit: https://dnschecker.org
   - Enter your domain name
   - Check if A records point to correct IP

2. **Test Website Access:**
   - Open browser
   - Visit: `http://yourdomain.com`
   - Visit: `http://www.yourdomain.com`
   - Both should load your website

3. **Check SSL Certificate:**
   - Most hosting providers auto-generate SSL
   - Your site should be accessible via `https://`
   - May take a few hours after domain connection

## Common Hosting Provider Instructions

### Vercel Deployment

1. Deploy website to Vercel
2. In Vercel dashboard, go to **Domains**
3. Add your custom domain
4. Vercel will provide DNS records
5. Add these records to GoDaddy DNS:
   ```
   Type: A
   Name: @
   Value: 76.76.21.21
   
   Type: CNAME
   Name: www
   Value: cname.vercel-dns.com
   ```

### Netlify Deployment

1. Deploy website to Netlify
2. Go to **Domain Settings**
3. Click **Add custom domain**
4. Netlify will provide DNS records
5. Add these records to GoDaddy DNS:
   ```
   Type: A
   Name: @
   Value: 75.2.60.5
   
   Type: CNAME
   Name: www
   Value: [your-site].netlify.app
   ```

### Cloudflare (Recommended for Performance)

1. Sign up at [Cloudflare](https://www.cloudflare.com)
2. Add your domain
3. Cloudflare will scan existing DNS records
4. Cloudflare will provide nameservers:
   ```
   Example:
   ns1.cloudflare.com
   ns2.cloudflare.com
   ```
5. Update nameservers at GoDaddy (Method 2 above)
6. Add A record in Cloudflare pointing to your server IP
7. Enable SSL/TLS (Full or Full Strict)
8. Benefits: Free SSL, CDN, DDoS protection, faster loading

## Troubleshooting

### Domain Not Loading After 48 Hours

1. **Check nameservers are correct:**
   ```bash
   nslookup -type=NS yourdomain.com
   ```

2. **Check A records:**
   ```bash
   nslookup yourdomain.com
   ```

3. **Clear browser cache:**
   - Chrome: Ctrl+Shift+Delete
   - Try incognito mode

4. **Check with different DNS:**
   - Use Google DNS: 8.8.8.8
   - Use Cloudflare DNS: 1.1.1.1

### SSL Certificate Issues

1. Wait 24 hours after domain connection
2. Check hosting provider's SSL settings
3. Force HTTPS redirect in hosting settings
4. Contact hosting support if issues persist

### Email Not Working After Nameserver Change

If you change nameservers away from GoDaddy:
1. You'll lose GoDaddy email forwarding
2. Need to set up MX records at new DNS provider
3. Or keep email at GoDaddy and only change A records

**GoDaddy Email MX Records:**
```
Type: MX
Priority: 0
Value: smtp.secureserver.net

Type: MX
Priority: 10
Value: mailstore1.secureserver.net
```

## DNS Propagation Time

- **A Record changes**: 30 minutes - 2 hours
- **CNAME changes**: 30 minutes - 2 hours
- **Nameserver changes**: 24-48 hours (up to 72 hours)
- **TTL (Time To Live)**: Lower TTL = faster updates

## Security Best Practices

1. **Enable HTTPS/SSL** - Most hosts provide free SSL
2. **Use Cloudflare** - Free CDN and DDoS protection
3. **Enable DNSSEC** - Prevents DNS spoofing (if supported)
4. **Set up domain lock** - Prevents unauthorized transfers
5. **Use strong passwords** - For domain registrar account
6. **Enable 2FA** - Two-factor authentication at GoDaddy

## Contact Information

**Domain Registrar:** GoDaddy
- Support: https://www.godaddy.com/help
- Phone: 1-480-505-8877

**Hosting Provider:** [Your hosting provider]
- Check your hosting dashboard for support contact

## Quick Reference Commands

**Check nameservers:**
```bash
nslookup -type=NS yourdomain.com
```

**Check A record:**
```bash
nslookup yourdomain.com
```

**Check DNS propagation:**
```bash
dig yourdomain.com
```

**Flush local DNS cache (Windows):**
```bash
ipconfig /flushdns
```

**Flush local DNS cache (Mac):**
```bash
sudo dscacheutil -flushcache
```

**Flush local DNS cache (Linux):**
```bash
sudo systemd-resolve --flush-caches
```

## Next Steps

1. ✅ Identify your hosting provider
2. ✅ Get server IP address or nameservers from hosting provider
3. ✅ Log in to GoDaddy
4. ✅ Configure DNS records (Method 1) or change nameservers (Method 2)
5. ✅ Wait for DNS propagation
6. ✅ Verify domain is working
7. ✅ Enable SSL certificate
8. ✅ Test website on custom domain

---

**Need Help?**
- GoDaddy Support: https://www.godaddy.com/help/manage-dns-680
- DNS Checker: https://dnschecker.org
- SSL Checker: https://www.sslshopper.com/ssl-checker.html
