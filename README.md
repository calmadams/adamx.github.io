# adamx.me

Personal site hosted on GitHub Pages at [adamx.me](https://adamx.me).

## Custom Domain Setup (Namecheap → GitHub Pages)

The `CNAME` file in this repository already tells GitHub Pages to serve this site at `adamx.me`.
You also need to configure DNS records in your Namecheap account.

### Namecheap DNS Configuration

1. Log in to [namecheap.com](https://www.namecheap.com) and go to **Domain List → Manage → Advanced DNS**.
2. Delete any existing `A` records or `CNAME` records for the root (`@`) and `www` hosts.
3. Add the following **A records** (for the apex domain `adamx.me`):

   | Type | Host | Value           | TTL       |
   |------|------|-----------------|-----------|
   | A    | @    | 185.199.108.153 | Automatic |
   | A    | @    | 185.199.109.153 | Automatic |
   | A    | @    | 185.199.110.153 | Automatic |
   | A    | @    | 185.199.111.153 | Automatic |

4. Add a **CNAME record** (for `www.adamx.me` → GitHub Pages):

   | Type  | Host | Value                  | TTL       |
   |-------|------|------------------------|-----------|
   | CNAME | www  | calmadams.github.io.   | Automatic |

5. DNS propagation can take up to 48 hours. Once it propagates, GitHub Pages will automatically issue an HTTPS certificate via Let's Encrypt.

### GitHub Pages Settings

In the repository **Settings → Pages**:
- **Source**: Deploy from the `main` (or `master`) branch.
- **Custom domain**: `adamx.me` (this is already set via the `CNAME` file).
- **Enforce HTTPS**: enable this checkbox after the certificate is issued.
