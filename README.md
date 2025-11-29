# AI Product Recommendation Agent

[![AI Product Recommendation Agent](https://apify.com/actor-badge?actor=matymar/ai-product-recommendation-agent)](https://apify.com/matymar/ai-product-recommendation-agent)

# AI Product Recommendation Agent 🤖🛒

## 1. Overview of the Agent

**AI Product Recommendation Agent** is an intelligent shopping assistant that delivers personalized Amazon product recommendations based on natural language queries. Users simply describe their needs (e.g., "laptop under $1000 with great battery life"), and the agent automatically searches Amazon, scrapes products + reviews, analyzes sentiment, and provides ranked recommendations with pros/cons.

Built on Apify platform with LangGraph orchestration, it combines web scraping, AI analysis, and structured output generation to create a complete e-commerce recommendation pipeline. Outputs include detailed product cards with prices, ratings, review summaries, and final recommendations in HTML/Markdown formats. [attached_file:1]

## 2. Features & Limitations

### ✅ Features
- **Natural Language Input**: "Recommend beginner music theory book" → Instant results
- **Amazon Product Scraping**: Titles, prices, ratings, descriptions, images
- **Review Analysis**: Scrapes + summarizes customer reviews with sentiment
- **Smart Ranking**: AI selects best matches based on user criteria
- **Rich Outputs**: HTML reports, JSON datasets, key-value store with visuals
- **Multiple Formats**: Dataset + downloadable HTML/Markdown recommendation pages

### ⚠️ Limitations
- **Amazon-Only**: Limited to Amazon product ecosystem
- **Scraping Dependency**: Subject to Amazon anti-bot measures/blocks
- **Cost-Based**: OpenAI tokens + Apify compute usage fees apply
- **Query Specificity**: Vague queries may yield suboptimal results
- **No Real-time Pricing**: Prices from scraped data (may vary)
- **Rate Limits**: Scraping throttles during high-volume runs [attached_file:1]

## 3. Tech Stack & APIs Used

Platform: Apify Actors (Serverless scraping platform)
Orchestration: LangGraph (AI agent workflow)
AI Engine: OpenAI GPT-4o / GPT-4o-mini / o1 / o3-mini
Scrapers:
├── junglee/Amazon-crawler (Products)
└── junglee/amazon-reviews-scraper (Reviews)
Output: Apify Dataset + Key-Value Store (HTML/Markdown)
Language: Python 93.6% + Dockerfile 6.4%


**Key APIs & Tools**:
- **OpenAI API**: Query processing, review analysis, recommendation logic [attached_file:1]
- **Apify Amazon Crawlers**: Product/review extraction [attached_file:1]
- **LangGraph**: Multi-step agent orchestration loop [attached_file:1]

## 4. Setup & Run Instructions

### Prerequisites
- Apify account (free tier available)
- OpenAI API key
- Basic Python/Docker knowledge

### 🚀 Quick Deployment (Apify Platform)

1. Fork/Clone repo
git clone https://github.com/apify-projects/ai-product-recommendation-agent.git
cd ai-product-recommendation-agent

2. Apify Platform (Recommended - No local setup)
Visit: https://console.apify.com
→ Actors → New Actor → Import from GitHub
→ Paste repo URL → Deploy
3. Run via API/Input
curl -X POST https://api.apify.com/v2/acts/YOUR_USERNAME~ai-product-recommendation-agent/runs
-H "Authorization: Bearer YOUR_APIFY_TOKEN"
-H "Content-Type: application/json"
-d '{
"query": "Recommend me a laptop under $1000 with great battery life",
"modelName": "gpt-4o-mini",
"debug": false
}'


### 🐳 Local Development
1. Install dependencies
pip install -r requirements.txt

2. Set environment variables
export OPENAI_API_KEY=your_openai_key
export APIFY_TOKEN=your_apify_token

3. Run locally
apify run


**Example Input/Output**: See music theory book recommendation demo [attached_file:1]

## 5. Potential Improvements

### 🔮 Future Enhancements
High Priority:
├── Multi-Platform Support: Walmart, BestBuy, eBay scrapers
├── Price Tracking: Historical pricing + deal alerts
├── Image Analysis: Product image recognition via GPT-4V
├── User Profiles: Personalized recommendations with purchase history
├── Comparison Tables: Side-by-side product matrices
└── Mobile-First: WhatsApp/Telegram bot integration

Medium Priority:
├── Category Auto-Detection: Smart product category inference
├── Competitor Pricing: Cross-platform price comparison
├── Review Freshness: Time-weighted review analysis
├── Affiliate Links: Revenue generation capability
└── Bulk Processing: CSV input for multiple queries

Technical:
├── Cost Optimization: Dynamic model selection (mini → full)
├── Caching Layer: Redis for repeated queries
├── Async Processing: Parallel scraping for top candidates
└── Monitoring: Run analytics + failure alerts


### 💰 Cost Breakdown [attached_file:1]
Apify: $0.005/GB startup + compute time
GPT-4o: $0.001/100 tokens (~$0.01-0.05 per query)
GPT-4o-mini: $0.00006/100 tokens (budget option)


## 📁 Example Usage

Input: "I want a laptop ~$1000, great battery, <15in screen"
Output: 3 curated laptops with review summaries + final pick

Input: "Modern white living room decor, minimalistic"
Output: Furniture/decor products ranked by style match


## 🏗️ Architecture Flow 

User Query → LangGraph Agent → Amazon URL Generation
↓
Amazon Crawler → Product Data → Review Scraper
↓
OpenAI Analysis → Ranked Recommendations
↓
HTML Report + Dataset → Key-Value Store Output
