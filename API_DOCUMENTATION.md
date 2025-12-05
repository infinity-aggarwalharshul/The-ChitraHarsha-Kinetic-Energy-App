# API Documentation

## 🚀 ChitraHarsha GatiVigyan V13 API

Complete API reference for integrating with our AI Innovation Platform.

## 📋 Table of Contents

- [Authentication](#authentication)
- [Innovation Analysis API](#innovation-analysis-api)
- [Patent Search API](#patent-search-api)
- [SEO Blog API](#seo-blog-api)
- [Data Compression API](#data-compression-api)
- [Rate Limits](#rate-limits)
- [Error Codes](#error-codes)

## 🔐 Authentication

All API requests require authentication using JWT tokens.

### Get Access Token

```http
POST /api/v1/auth/token
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "your_password",
  "mfa_code": "123456"
}
```

**Response:**
```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIs...",
  "refresh_token": "eyJhbGciOiJIUzI1NiIs...",
  "expires_in": 3600,
  "token_type": "Bearer"
}
```

### Using the Token

Include the token in all requests:

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

## 🧠 Innovation Analysis API

Analyze ideas for novelty, patentability, and global impact.

### Analyze Innovation

```http
POST /api/v1/innovation/analyze
Authorization: Bearer {token}
Content-Type: application/json

{
  "query": "AI-powered kinetic energy harvesting system",
  "industry": "renewable_energy",
  "target_market": "global",
  "include_scholar": true
}
```

**Response:**
```json
{
  "analysis_id": "AN-2024-001234",
  "timestamp": "2024-12-06T03:15:00Z",
  "results": {
    "novelty_score": 87.5,
    "global_impact": 92.3,
    "patentability": 85.7,
    "market_potential": 89.2,
    "similar_patents": 23,
    "research_papers": 456,
    "transformative_potential": "High"
  },
  "compression": {
    "original_size": "2.4 TB",
    "compressed_size": "7.2 MB",
    "ratio": 99.7,
    "processing_time": "0.08s"
  },
  "scholar_data": {
    "citations": 3456,
    "h_index": 28,
    "related_papers": 145,
    "top_journals": ["Nature", "Science", "IEEE"],
    "trending_topics": ["Quantum Computing", "AI Ethics"],
    "innovation_gap": "Significant"
  }
}
```

## 🔍 Patent Search API

Search and analyze patents globally.

### Search Patents

```http
GET /api/v1/patents/search?q=kinetic+energy&limit=50&offset=0
Authorization: Bearer {token}
```

**Response:**
```json
{
  "total": 12456,
  "results": [
    {
      "patent_id": "US10234567B2",
      "title": "Kinetic Energy Harvesting Device",
      "abstract": "A device for converting kinetic energy...",
      "filing_date": "2020-03-15",
      "grant_date": "2022-08-20",
      "inventors": ["John Doe", "Jane Smith"],
      "assignee": "Tech Corp",
      "status": "Active",
      "citations": 45,
      "similarity_score": 0.87
    }
  ]
}
```

## 📝 SEO Blog API

Generate SEO-optimized blog content with AI.

### Generate Blog

```http
POST /api/v1/seo/generate-blog
Authorization: Bearer {token}
Content-Type: application/json

{
  "topic": "Quantum Data Compression",
  "keywords": ["quantum", "compression", "enterprise"],
  "word_count": 1500,
  "include_images": true,
  "tone": "professional",
  "target_audience": "technical"
}
```

**Response:**
```json
{
  "blog_id": "BLG-2024-005678",
  "status": "completed",
  "content": {
    "title": "Quantum Data Compression: Achieving 99.7% Storage Efficiency",
    "body": "Full blog content here...",
    "word_count": 1547,
    "reading_time": "8 min"
  },
  "seo": {
    "score": 98,
    "meta_description": "Discover how quantum algorithms...",
    "keywords": ["quantum compression", "data storage"],
    "slug": "quantum-data-compression-efficiency",
    "rank_prediction": "#1-3"
  },
  "images": [
    {
      "url": "https://cdn.chitraharsha.com/img/blog-001.jpg",
      "alt": "Quantum compression visualization",
      "caption": "Visual representation of quantum data compression"
    }
  ],
  "analytics": {
    "estimated_views": 15000,
    "engagement_prediction": 94.2,
    "backlink_potential": 250
  }
}
```

## 🗜️ Data Compression API

Compress data using quantum algorithms.

### Compress Data

```http
POST /api/v1/compression/compress
Authorization: Bearer {token}
Content-Type: multipart/form-data

file: [binary data]
algorithm: quantum-lz4
encryption: true
```

**Response:**
```json
{
  "compression_id": "CMP-2024-009876",
  "original_size": "2.4 TB",
  "compressed_size": "7.2 MB",
  "compression_ratio": 99.7,
  "processing_time": "0.08s",
  "algorithm": "quantum-lz4",
  "encrypted": true,
  "download_url": "https://cdn.chitraharsha.com/compressed/...",
  "expires_at": "2024-12-13T03:15:00Z"
}
```

## ⚡ Rate Limits

| Plan | Requests/Hour | Requests/Day | Burst |
|------|---------------|--------------|-------|
| Free | 100 | 1,000 | 10 |
| Research Pro | 1,000 | 50,000 | 100 |
| Enterprise | Unlimited | Unlimited | 1,000 |

**Rate Limit Headers:**
```http
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 847
X-RateLimit-Reset: 1701835200
```

## ❌ Error Codes

| Code | Message | Description |
|------|---------|-------------|
| 400 | Bad Request | Invalid request parameters |
| 401 | Unauthorized | Missing or invalid token |
| 403 | Forbidden | Insufficient permissions |
| 404 | Not Found | Resource doesn't exist |
| 429 | Too Many Requests | Rate limit exceeded |
| 500 | Internal Server Error | Server error |
| 503 | Service Unavailable | Maintenance mode |

**Error Response Format:**
```json
{
  "error": {
    "code": "INVALID_PARAMETER",
    "message": "The 'query' parameter is required",
    "details": {
      "parameter": "query",
      "expected": "string",
      "received": "null"
    },
    "request_id": "req_abc123",
    "timestamp": "2024-12-06T03:15:00Z"
  }
}
```

## 📊 Webhooks

Subscribe to real-time events.

### Available Events

- `innovation.analyzed` - Innovation analysis completed
- `patent.found` - New patent match found
- `blog.generated` - Blog generation completed
- `compression.completed` - Data compression finished
- `security.alert` - Security event detected

### Webhook Payload

```json
{
  "event": "innovation.analyzed",
  "timestamp": "2024-12-06T03:15:00Z",
  "data": {
    "analysis_id": "AN-2024-001234",
    "novelty_score": 87.5,
    "status": "completed"
  },
  "signature": "sha256=abc123..."
}
```

## 🔧 SDKs & Libraries

### JavaScript/Node.js
```bash
npm install @chitraharsha/gativigyan-sdk
```

```javascript
const GatiVigyan = require('@chitraharsha/gativigyan-sdk');

const client = new GatiVigyan({
  apiKey: 'your_api_key',
  environment: 'production'
});

const result = await client.innovation.analyze({
  query: 'AI-powered solution',
  includeScholar: true
});
```

### Python
```bash
pip install chitraharsha-gativigyan
```

```python
from chitraharsha import GatiVigyan

client = GatiVigyan(api_key='your_api_key')

result = client.innovation.analyze(
    query='AI-powered solution',
    include_scholar=True
)
```

### cURL Examples

```bash
# Analyze Innovation
curl -X POST https://api.chitraharsha.com/v1/innovation/analyze \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query": "AI innovation", "include_scholar": true}'

# Search Patents
curl -X GET "https://api.chitraharsha.com/v1/patents/search?q=kinetic" \
  -H "Authorization: Bearer YOUR_TOKEN"

# Generate Blog
curl -X POST https://api.chitraharsha.com/v1/seo/generate-blog \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"topic": "Quantum Computing", "word_count": 1500}'
```

## 📞 Support

- **API Status**: https://status.chitraharsha.com
- **Documentation**: https://docs.chitraharsha.com
- **Support Email**: api-support@chitraharsha.com
- **Discord Community**: https://discord.gg/chitraharsha

---

**API Version**: v1  
**Last Updated**: December 6, 2024  
**Base URL**: https://api.chitraharsha.com
