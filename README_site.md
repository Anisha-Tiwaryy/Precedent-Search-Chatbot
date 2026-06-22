# Nyaya - Site

Frontend for Nyaya, a precedent search engine for Indian Supreme Court judgements. This repository holds the website (a single page) that people actually use. The data, database, and API that power it are kept in a separate backend repository (see below).

## What this is

A precedent search interface for Supreme Court of India judgements. You can search by case name, citation, or legal issue, open the full judgement inside the site, and ask for similar precedents to any case. It supports keyword, semantic, and hybrid search.

The page connects to the backend API, which serves real Supreme Court judgements from a database (24,000+ judgements, 1995 to 2025). If the API cannot be reached, the page falls back to a small built-in set of landmark cases so it still works.

## How it works

This is a single `index.html` file (HTML, CSS, and JavaScript in one page). On load, it calls the backend API to fetch real judgements and replaces its sample data with them. Search, case view, and find-similar all run against that live data.

## Deployment

The site is deployed as a static page on Vercel. It points at the backend API, which is deployed separately on Render. Because the data lives in the backend database, new judgements appear on the site automatically without redeploying this repository.

Note: the backend runs on a free tier that sleeps when idle, so the first load after a period of inactivity can take up to a minute while the server wakes up.

## Backend repository

All the other files for this project, the database setup, the data loaders, and the API, are kept in a separate repository:

[link to your nyaya-backend repository here]

That repository explains where the judgement data comes from and how it is loaded.

## Data sources, in short

- The Supreme Court's official eCourts judgements, published as open data, loaded into our own database.
- Fresh judgements pulled from the Supreme Court site's no-captcha latest-judgements feed using the open source bharat-courts library.

The Supreme Court search page is captcha-protected and cannot be queried directly, so the project uses the official open dataset for the archive and the latest-judgements feed for recent cases, keeping the data real without bypassing the captcha.
