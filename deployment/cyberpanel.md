# CyberPanel Deployment

## Create Website

1. Log in to CyberPanel.
2. Go to **Websites → Create Website**.
3. Enter:
   - Domain: `docs.example.com`
   - Package: Default
   - Owner: admin

## Upload Files

1. Go to **File Manager**.
2. Navigate to `/home/docs.example.com/public_html`
3. Upload your `index.html` and assets.

## SSL Certificate

1. Go to **SSL → Hostname SSL** or **Websites → List Websites**.
2. Click **Issue SSL** for your domain.
3. Let's Encrypt SSL is free and auto-renews.

## LiteSpeed Cache

1. Install LiteSpeed Cache plugin if using WordPress.
2. For static sites, caching is automatic.
3. Purge cache after updates: **Websites → List Websites → Cache**.

## OpenLiteSpeed Configuration

Advanced users can edit vhost config at:
```
/usr/local/lsws/conf/vhosts/docs.example.com/vhost.conf
```
