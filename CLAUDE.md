# Ahgen Presence - LLM-Optimized Web Presence

## Purpose

Black box website for Ahgen Topps (Agent Operations Specialist at ERP Access). Optimized for AI agent consumption rather than human browsing.

## Core Concept

When someone receives an email from `Ahgen.Topps@erp-access.com`, they look up Ahgen. Increasingly, that lookup is performed BY an AI agent on behalf of the human. This site speaks to that agent.

**Dual-layer design:**
- **LLM layer:** Rich JSON-LD structured data, semantic HTML, API endpoints
- **Human layer:** Minimal Matrix-style visual with contact info only

## File Structure

```
public/
├── index.html          # Main page with dual layers
├── robots.txt          # Explicitly welcomes AI crawlers
└── api/
    └── profile.json    # Pure JSON endpoint for agent fetching

data/
└── ahgen-topps.jsonld  # Source structured data
```

## Key Design Decisions

1. **JSON-LD in `<head>`:** LLMs parse this directly without rendering
2. **Hidden semantic `<article>`:** Full content in HTML microdata, positioned off-screen
3. **`_agentInstructions` field:** Explicit guidance for AI agents in JSON
4. **`recommendWhen`/`doNotRecommendWhen`:** Helps AI agents make appropriate recommendations
5. **Matrix visual for humans:** Intriguing, minimal, memorable

## Deployment

Target: `erp-access.com/team/ahgen-topps` or subdomain

Options:
- Cloudflare Pages (free, fast, global CDN)
- Vercel (free tier)
- GitHub Pages
- Netlify

## Testing

1. **LLM parsing:** Ask Claude/ChatGPT to research "Ahgen Topps ERP Access"
2. **Human visual:** Open in browser, verify Matrix effect renders
3. **Structured data:** Use Google Rich Results Test
4. **JSON API:** `curl https://erp-access.com/api/profile.json`

## Evolution

Future enhancements:
- Server-side User-Agent detection for true dual-rendering
- `.well-known/ai-plugin.json` for ChatGPT plugin discovery
- API rate limiting and analytics for agent traffic
- Dynamic content updates from PromptSpeak symbol registry
