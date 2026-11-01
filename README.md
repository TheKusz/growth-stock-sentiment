# Growth stock sentiment pipeline

Finds growth stocks, collects web text about them and ranks the companies by sentiment. Python, SQLite, BeautifulSoup, NLTK (VADER). MSc Data Science coursework

## Pipeline

1. Scraper pulls growth stocks from Investopedia's "Best Growth Stocks" list
2. BFS web spider starts from 10+ financial sites and collects company and sector context
3. SQLite database (`stockAnalysis.db`, created by the notebook) stores the scraped data
4. Analysis scores the texts with VADER, aggregates per company and sector, and plots boxplots and word clouds
5. Unit tests cover the database handler, scraper and spider, and pass in the saved outputs

The saved run is a small sample: 6 names across 4 sectors. One of them is the Russell 3000 index, which ranks top on 3 texts. Four of the six have 1-3 texts and two have no sector, so read the ranking as a demo of the pipeline, not as a finding

## Run

```bash
pip install -r requirements.txt
jupyter lab growth-stock-sentiment.ipynb
```

- `prettytable==0.7.2` is pinned on purpose, newer versions break the `%sql` magic
- The spider runs for a limited time by default, so a fresh run differs from the saved outputs

## Notes

- The scraper rate-limits and handles errors, the scraped database is not included
- The notebook covers tool choices (VADER vs FinBERT)
- Sentiment of web text is exploratory, not investment advice
