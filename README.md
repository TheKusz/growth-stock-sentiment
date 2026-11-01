# Growth stock sentiment pipeline

Finds growth stocks, collects web text about them and ranks the companies by sentiment. Python, SQLite, BeautifulSoup, NLTK (VADER). MSc Data Science coursework

## Pipeline

1. Scraper pulls growth stocks from Investopedia's "Best Growth Stocks" list
2. BFS web spider starts from 10+ financial sites and collects company and sector context
3. SQLite database (`stockAnalysis.db`, created by the notebook) stores the scraped data
4. Analysis scores the texts with VADER, aggregates per company and sector, and plots boxplots and word clouds

Covers 6 companies in 4 sectors

## Run

```bash
pip install -r requirements.txt
jupyter lab growth-stock-sentiment.ipynb
```

- `prettytable==0.7.2` is pinned on purpose, newer versions break the `%sql` magic
- The spider runs for a limited time by default, so a fresh run differs from the saved outputs

## Notes

- The scraper rate-limits and handles errors, the collected data is not included
- The notebook covers tool choices (VADER vs FinBERT) and ethics of scraping
- Sentiment of web text is exploratory, not investment advice
