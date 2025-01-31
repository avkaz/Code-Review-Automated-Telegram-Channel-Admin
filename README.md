# Code Review Automated Telegram Channel Admin

This repository contains the components for automating a Telegram channel focused on Code Review-related memes and content.  The system consists of three bots working together to manage content, filter memes, post to Telegram, and scrape content from Reddit.

## Project Overview

The Code Review Automated Telegram Channel Admin project automates the management of a meme-based channel specializing in programmer humor.  It streamlines meme filtering, posting, and content scraping from Reddit.

The three main bots are:

*   **Reddit Memes Filtering Bot:** [https://github.com/avkaz/reddit-it-memes-filtering-bot](https://github.com/avkaz/reddit-it-memes-filtering-bot) Filters and approves memes scraped from Reddit. Users can browse, approve, delete, and add their own memes.
*   **Automatic Telegram Posting Bot:** [https://github.com/avkaz/reddit-it-memes-automatic-posting-telegram-bot](https://github.com/avkaz/reddit-it-memes-automatic-posting-telegram-bot) Posts approved memes from the database to a Telegram channel at scheduled times.  Also sends status updates to a private channel and creates TikTok/Instagram-style videos from memes.
*   **Automatic Reddit Scraper:** [https://github.com/avkaz/reddit-r.ProgrammerHumor-python-selectolax-scrapper](https://github.com/avkaz/reddit-r.ProgrammerHumor-python-selectolax-scrapper) Scrapes content from the ProgrammerHumor subreddit twice daily, using proxies to bypass Reddit's bot protections.

Each bot has a distinct role, contributing to a seamless automated content curation and posting experience.

## Features

*   **Reddit Memes Filtering Bot:**
    *   Scrapes memes from Reddit and enables filtering and approval.
    *   Supports meme management (browse, approve, add comments, delete).
    *   Allows users to add custom memes (photo or video upload).
    *   Displays statistics (number of memes scraped, approved, etc.).

*   **Automatic Telegram Posting Bot:**
    *   Posts approved memes to a Telegram channel at scheduled times.
    *   Sends status updates to a private Telegram channel.
    *   Creates TikTok/Instagram-style videos from memes (background and music).

*   **Automatic Reddit Scraper:**
    *   Scrapes the ProgrammerHumor subreddit twice a day.
    *   Uses proxies to avoid Reddit IP blocks.
    *   Sends status updates to a helper Telegram channel.

## Setup Instructions

1.  **Clone the Repository:**

    ```bash
    git clone <repository_url>
    cd code-review-automated-telegram-channel-admin
    ```

2.  **Install Docker & Docker Compose:** Install Docker and Docker Compose from the official Docker website: [https://www.docker.com/](https://www.docker.com/)

3.  **Set Up Environment Variables:**

    *   **Firebase API Key:** Place your `key.json` file in the project's root directory.
    *   **Telegram Bot Tokens:** Place your bot tokens in the `main.py` files of each bot.  You'll need to create Telegram bots using BotFather.
    *   **Channel IDs:** In the Automatic Telegram Posting Bot's `main.py`, specify the IDs for the main posting channel and the two supporting channels (status updates and videos).
    *   **ScrapeOps API Key:** Place your API key in the Reddit Scraper Bot's `spider.py` file (line 62).  You'll need to sign up for a ScrapeOps account.
    *   **Database Configuration:** The bots use a PostgreSQL database.  The `docker-compose.yml` file configures the database service.

4.  **Docker Compose Setup:**

    *   **Build and Start the Services:**

    ```bash
    docker-compose up --build
    ```

    This builds the images and starts all services in the background:

    *   `reddit-r.ProgrammerHumor-python-selectolax-scrapper` (Reddit Scraper Bot)
    *   `reddit-it-memes-automatic-posting-telegram-bot` (Automatic Telegram Posting Bot)
    *   `reddit-it-memes-filtering-bot` (Reddit Memes Filtering Bot)
    *   `comments_delete_bot` (Bot for managing deleted memes)
    *   `db` (PostgreSQL database)

    *   **Run Services in the Background (detached mode):**

    ```bash
    docker-compose up -d
    ```

    *   **Check Logs:**

    ```bash
    docker-compose logs -f
    ```

    *   **Stop Services:**

    ```bash
    docker-compose down
    ```

## Bot Configuration

Each bot has specific configuration parameters set in its respective `main.py` or configuration files.

1.  **Reddit Memes Filtering Bot:**
    *   Firebase API Key: `key.json` in the project root.
    *   Telegram Bot Token: In `main.py`.
    *   Database Configuration: Connection string in `config.py`.

2.  **Automatic Telegram Posting Bot:**
    *   Telegram Bot Token: In `main.py`.
    *   Channel IDs: In `main.py`.
    *   Posting Times: In `main.py`.

3.  **Automatic Reddit Scraper Bot:**
    *   ScrapeOps API Key: In `spider.py` (line 62).
    *   Telegram Bot Token: In `main.py`.
    *   Telegram Channel ID: In `main.py`.

## Channel

The bot posts to the Code Review Telegram Channel: `<telegram_channel_link>` (Replace with the actual link).

## Additional Information

*   **License:** This project is open-source and distributed under the MIT License. See the `LICENSE` file for details.
*   **Support:** Open an issue in the repository or contact me directly for issues or questions.
