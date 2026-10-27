# Nginx deployment templates

`eduassets-api.conf.example` is an operator template, not an active or verified production configuration ([template in the backend repository](https://github.com/edu-assets/eduAssets/blob/main/deploy/nginx/eduassets-api.conf.example)). Replace the hostname and certificate paths only after DNS and TLS are configured.

The backend repository also provides [`eduassets-cloudflare-realip.conf.example`](https://github.com/edu-assets/eduAssets/blob/main/deploy/nginx/eduassets-cloudflare-realip.conf.example), generated from Cloudflare's official IP-range sources. Re-check the official list immediately before installation and periodically thereafter; copy reviewed ranges to `/etc/nginx/snippets/eduassets-cloudflare-realip.conf`. Validate the complete Nginx configuration with `nginx -t`, and restrict inbound origin traffic to those ranges at both the cloud network-security layer and the host firewall.

Trust `CF-Connecting-IP` only after Nginx verifies the peer against the current Cloudflare list. The API port must remain loopback-only. The template returns 404 for public `/auth/rfid` and `/ws/rfid` endpoints because a loopback address observed by Nginx does not prove that the original caller is local. Keep RFID functionality in a separately secured kiosk configuration. A direct, non-Cloudflare deployment needs a separately reviewed proxy-trust policy.

Official references: [Cloudflare IP Ranges](https://www.cloudflare.com/ips/) and [Cloudflare IP addresses documentation](https://developers.cloudflare.com/fundamentals/concepts/cloudflare-ip-addresses/).
