# MySQL Slow Query Log Visualizer

A single-file, browser-based tool that turns raw MySQL slow query logs into an interactive visual report. Upload a `slow-query.log` file or paste log text directly, then explore timings, spot the slowest queries, filter by user, and export a polished PDF report — all without a server, build step, or dependencies.

> **🚀 Live Demo:** [https://mysql-slow-query-log-visualizer.vercel.app/](https://mysql-slow-query-log-visualizer.vercel.app/)
>
> Try it instantly in your browser — no installation needed.

---

## Table of Contents

- [Features](#features)
- [Live Demo](#live-demo)
- [Quick Start](#quick-start)
- [Usage](#usage)
  - [Loading a log](#loading-a-log)
  - [Exploring the data](#exploring-the-data)
  - [Filtering and sorting](#filtering-and-sorting)
  - [Exporting to PDF](#exporting-to-pdf)
- [PDF Report](#pdf-report)
  - [Filename convention](#filename-convention)
  - [Light and dark modes](#light-and-dark-modes)
- [Supported Log Format](#supported-log-format)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Customization](#customization)
- [Browser Support](#browser-support)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **Two input modes** — drag-and-drop a `.log` / `.txt` file, or paste raw log content into a textarea.
- **Parses standard MySQL slow query logs** — extracts timestamp, user, host, query time, lock time, rows sent, rows examined, and the full SQL statement.
- **Summary statistics** — total queries, total query time, average time, slowest query, rows examined, unique patterns, and how many queries exceeded 1 second.
- **Top query patterns** — SQL is normalized (literals replaced) so similar queries group together; ranked by total time with severity-colored bars.
- **Query Time Timeline** — a full-width canvas scatter plot showing each query's execution time against its timestamp, with the slowest query highlighted.
- **User filter** — auto-populated dropdown of every user found in the log.
- **Additional filters** — free-text search, minimum query time, and five sort orders.
- **Expandable SQL cells** — click any query in the table to expand or collapse the full statement.
- **PDF export** — styled A4 report with summary stats, top patterns, timeline image, and the full filtered table.
- **Light and dark PDF modes** — export the report in either theme, with dark mode getting extra padding for print.
- **User-aware filenames** — exports are named `DD-MM-YYYY_[username_]slow-query.pdf`.
- **Zero dependencies** — one HTML file, no npm, no bundler, no backend. Bootstrap Icons loads from a CDN.

---

## Live Demo

**Try it now:** [https://mysql-slow-query-log-visualizer.vercel.app/](https://mysql-slow-query-log-visualizer.vercel.app/)

The hosted version is the same single-file application — nothing is uploaded to a server, and all parsing, filtering, and PDF generation happen entirely in your browser. You can safely paste real logs without worrying about data leaving your machine.

If you prefer to run it locally, follow the [Quick Start](#quick-start) steps below.

---

## Quick Start

### Option 1 — Use the hosted version (fastest)

Open [https://mysql-slow-query-log-visualizer.vercel.app/](https://mysql-slow-query-log-visualizer.vercel.app/) in any modern browser. Done.

### Option 2 — Run it locally

1. Download or clone this repository.
2. Open `slow-query-visualizer.html` in any modern browser.
3. Drop in a slow query log file, or paste log text and click **Visualize**.

There is no server, no installation, and no configuration.

```bash
git clone https://github.com/<your-username>/mysql-slow-query-visualizer.git
cd mysql-slow-query-visualizer
open slow-query-visualizer.html      # macOS
# or: start slow-query-visualizer.html   (Windows)
# or: xdg-open slow-query-visualizer.html (Linux)