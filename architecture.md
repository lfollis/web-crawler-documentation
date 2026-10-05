# Architecture

## Overview

The Web Content Audit Crawler is designed to locate specific phrases across one or more websites by combining sitemap discovery, internal link crawling, PDF scanning, and JavaScript rendering.

The crawler visits pages, extracts content, searches for target terms, and exports results to an Excel workbook.

---

## Workflow

Home Pages
↓
Sitemap Discovery
↓
Build Crawl Queue
↓
Render Page with Playwright
↓
Extract Page Content
↓
Search for Keywords
↓
Discover New Links
↓
Process PDFs
↓
Process Iframes
↓
Export Results to Excel

---

## Components

### Playwright

Used to render JavaScript-generated content and load pages in a browser environment.

Responsibilities:

- Load pages
- Wait for page content to render
- Extract page text
- Access dynamically generated content

---

### BeautifulSoup

Used to parse HTML after a page has been rendered.

Responsibilities:

- Extract links
- Find iframe sources
- Parse page structure

---

### PDF Processor (PyMuPDF)

Used to read PDF documents discovered during crawling.

Responsibilities:

- Download PDFs
- Extract text
- Search PDF content for keywords

---

### URL Discovery

URLs are discovered from three sources:

1. Home pages
2. XML sitemaps
3. Internal links

URLs are normalized to reduce duplicate crawling.

---

### Search Engine

The crawler searches extracted content using configurable patterns.

Example:

- American Heart Association
- AHA

Matches include:

- URL
- Match found
- Source type
- Context surrounding the match

---

## Output

The crawler produces an Excel workbook containing:

### Matches

All detected keyword occurrences.

### Crawled URLs

Every URL successfully crawled.

### Errors

Pages, PDFs, or sitemaps that could not be processed.

---

## Data Flow

URL
↓
Load Page
↓
Extract Text
↓
Search Content
↓
Find Links
↓
Queue New URLs
↓
Repeat

↓

Excel Report

---

## Future Enhancements

Potential enhancements include:

- Multi-threaded crawling
- Duplicate content detection
- Additional file type support
- Screenshot capture
- Scheduled audits
- Dashboard reporting