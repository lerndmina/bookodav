
# Booko-DAV - Self-Deployable WebDAV for eBook Management

## How to Setup

https://bookodav.joshuarodrigues.dev/

## Features
 
- 10GB free storage tier with R2  
- Native KOReader WebDAV compatibility  
- Basic authentication protection  
- Serverless architecture with minimal maintenance  
- Cross-platform WebDAV client support  

## Dashboard
![Screenshot 2025-03-01 at 15-01-01 BOOKO-DAV - Instructions](https://github.com/user-attachments/assets/92c9f242-6e8a-4236-b9a0-45b1a77cc3b6)
![Screenshot 2025-03-01 at 15-01-17 BOOKO-DAV - Upload](https://github.com/user-attachments/assets/5f02ea04-4d8b-4d92-bde3-6387acb16209)
![Screenshot 2025-03-01 at 15-01-30 BOOKO-DAV - List](https://github.com/user-attachments/assets/18288766-1395-4851-9bb5-c7d516160959)



## Implementation Overview

```plaintext
┌─────────────┐        ┌──────────────┐        ┌─────────────┐
│   Client    │ HTTP   │ Cloudflare   │  R2 API │  R2 Storage │
│ (KOReader)  │◄──────►│   Worker     │◄───────►│  (bookodav) │
└─────────────┘        └──────────────┘        └─────────────┘
```



## Integration

KOReader Configuration:

```yaml
WebDAV:
  URL: https://[worker-subdomain].workers.dev
  Username: [your-username]
  Password: [your-password]
```

## Configuration

### Environment Variables

You can configure Booko-DAV using environment variables in the Cloudflare Workers dashboard or in `wrangler.jsonc`:

- **`SORT_BY`**: Controls how files are sorted in listings
  - `"uploaded"` (default): Sort by upload date, newest first
  - `"modified"`: Sort by file modification date, newest first (falls back to upload date if not available)

To set this in Cloudflare Dashboard: Go to Workers → bookodav-worker → Settings → Variables → Environment Variables

## Cost Structure (Cloudflare)

| Service         | Free Tier       | Paid Tier          |
|-----------------|-----------------|--------------------|
| R2 Storage      | 10GB            | $0.015/GB-month    |
| Requests        | 100,000/day     | $0.15/million      |

## Development

Open to contributions and new features.
Contributions must maintain GPL-3.0 compliance. 


