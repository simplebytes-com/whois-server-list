# Setting Up whois-list.org

## Step 1: Enable GitHub Pages

1. Go to repository **Settings** → **Pages**
2. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
3. Click **Save**

## Step 2: Configure Custom Domain

1. In the same **Pages** settings, under **Custom domain**:
   - Enter: `whois-list.org`
   - Click **Save**
2. Wait for DNS check (may take a few minutes)
3. ✅ Enable **Enforce HTTPS** (after DNS propagates)

## Step 3: DNS Configuration

Add these records at your DNS provider (e.g., Cloudflare, Namecheap, GoDaddy):

### A Records (apex domain - whois-list.org)

```
Type: A
Name: @  (or leave blank for apex domain)
Value: 185.199.108.153
TTL: Auto or 3600

Type: A
Name: @
Value: 185.199.109.153
TTL: Auto or 3600

Type: A
Name: @
Value: 185.199.110.153
TTL: Auto or 3600

Type: A
Name: @
Value: 185.199.111.153
TTL: Auto or 3600
```

### CNAME Record (www subdomain - www.whois-list.org)

**Option 1: Point www to apex domain** (recommended)
```
Type: CNAME
Name: www
Value: whois-list.org
TTL: Auto or 3600
```

**Option 2: Point www directly to GitHub Pages**
```
Type: CNAME
Name: www
Value: simplebytes-com.github.io
TTL: Auto or 3600
```

**Note**: Both options work. Option 1 is simpler and follows the apex domain automatically.

## Step 4: Verify

After DNS propagates (5-30 minutes):

1. **Test apex domain**: https://whois-list.org
2. **Test www subdomain**: https://www.whois-list.org (should redirect to apex)
3. **Test primary endpoint**: https://whois-list.org/whois_servers.json
4. **Test alternative endpoint**: https://whois-list.org/data.json
5. **Test HTTPS**: Ensure the lock icon shows in browser

## 🎯 What Users Will Get

### Landing Page
- `https://whois-list.org` → Beautiful landing page
- `https://www.whois-list.org` → Redirects to apex domain

Features:
- API endpoints with copy buttons
- Quick examples (cURL, JavaScript, Python)
- Download link
- Links to GitHub

### Direct JSON Access (Multiple Endpoints)
- `https://whois-list.org/whois_servers.json` → Raw JSON data
- `https://whois-list.org/data.json` → Same data (alternative endpoint)
- `https://www.whois-list.org/whois_servers.json` → Works via www too

### GitHub Documentation
`https://github.com/simplebytes-com/whois-server-list` → Full docs

## 🔧 Troubleshooting

### DNS Not Propagating
```bash
# Check DNS propagation
dig whois-list.org
nslookup whois-list.org

# Should show GitHub Pages IPs (185.199.108-111.153)
```

### HTTPS Not Working
1. Wait for DNS to fully propagate
2. Disable HTTPS in Settings
3. Wait 5 minutes
4. Re-enable HTTPS

### Custom Domain Not Saving
1. Make sure CNAME file exists in repository root
2. Make sure DNS A records point to GitHub Pages
3. Wait for DNS propagation before setting custom domain

## 📚 References

- [GitHub Pages Custom Domain Docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [GitHub Pages IP Addresses](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
