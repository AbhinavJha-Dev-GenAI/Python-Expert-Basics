# Project 3: High-Performance Async Scraper 🕸️

Build a scraper that can fetch data from hundreds of URLs concurrently using `asyncio` and `aiohttp`.

## 1. Objectives
- Fetch HTML from multiple pages simultaneously.
- Parse specific data using `BeautifulSoup`.
- Implement rate limiting (semaphores) to avoid getting blocked.
- Save results to a single JSON file.

## 2. Implementation Steps

### Step 1: Async Fetch Function
```python
import aiohttp
import asyncio

async def fetch(session, url):
    async with session.get(url) as response:
        return await response.text()
```

### Step 2: Main Loop with Semaphore
```python
async def main(urls):
    sem = asyncio.Semaphore(10) # Max 10 concurrent requests
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_with_limit(session, url, sem) for url in urls]
        return await asyncio.gather(*tasks)
```

## 3. Best Practices
- **User-Agent**: Always include a custom User-Agent in headers.
- **Error Handling**: Use `try/except` around the `session.get` to handle timeouts or 404s.
- **Respect robots.txt**: Be a good web citizen.

## 4. Challenges for You
- Implement a **Proxy Rotation** system.
- Add a **Retry Logic** with exponential backoff for failed requests.
