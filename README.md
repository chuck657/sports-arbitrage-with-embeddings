Detects sports betting arbitrage opportunities using NLP-based embedding similarities between differing market names

## Introduction
Arbitrage is a clever way to make guaranteed profit from betting sites. Sites sometimes are inconsistent in their betting rates, causing an arbitrage opportunity to arise. What this means is, you hedge bets on opposite outcomes, with varying amounts such that either outcome winning would yield you an overall profit. To find these bets means you would need to scour multiple betting sites to check rates, and plug it into the arbitrage opportunity formula to see if it yields profit. This script aims to automate that process, directly scraping JSON files from the betting websites to gather betting data, and comparing rates to find arbitrage opportunities.

## 🔍 What it does 🔍
- First scrapes JSON data from Sportsbet and PointsBet APIs, extracting betting lines and rates from both sources
- Converts market names into sentence embeddings using 'sentence-transfomers'
- Matches semantically similar markets using cosine similarity
- Detects arbitrage opportunities using implied probability formula < 1
- (Optional) utilises Google's embedding API to more accurately match pairs (However API is't free for this amount of use)

## ⚙️ How it works ⚙️
SportsBet and PointsBet use different market names, it is hard to manually match the names since the markets are differing. Instead, the model uses a pre-trained BERT-based embedding model (sentence-transformers/stsb-distilroberta-base-v2) to comapre similarities in market names. Once matched, it checks the associated prices and calculates possible arbitrage opportunities using the formula:

<p align="center">
  <img src="https://github.com/user-attachments/assets/0d155739-c755-42ba-ab38-c717bba2d2ed" alt="Equation" />
</p>

If the total is less than one, it is flagged as an arbitrage opportunity.

## ✅ To-Do List ✅
- [X] Implement SportsBet and PointsBet Scraping
- [X] Add sentence embedding-based market matching
- [X] Calculate arbitrage opportunities
- [ ] Add more betting sites for wider range of rates
- [ ] Handle multi-line bets (bets with 3+ outcomes)
- [ ] Add profit margin estimator with most optimal bets to place
- [ ] Calculate most optimal arbitrage across all the sports, rather than just picking one
- [ ] Find and use more optimal sentence-embedding model to better match the markets without needing to proof-read
