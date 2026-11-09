# ProVaticanus Multi-Page Feed Monitor

An automated notification pipeline that monitors publishing channels under the **ProVaticanus** network, checks for newly published content, and instantly dispatches webhook alerts.

## Supported Channels
* **Blogger / Blogspot:** `provaticanus.blogspot.com`
* **Substack:** `provaticanus.substack.com`
* **Rumble:** Video and channel syndication feeds

## How It Works
1. **Scheduled Polling:** A GitHub Actions workflow runs every 15 minutes.
2. **State Tracking:** It parses official RSS feeds and compares the latest post IDs against a local state tracker (`seen_posts.json`).
3. **Webhook Dispatch:** If a new post is detected on any tracked platform, it sends an HTTP POST request containing the post title, link, and platform name to your configured target webhook URL.

## Setup & Installation

1. **Create the Workflow:** Place the YAML configuration inside `.github/workflows/feed-monitor.yml`.
2. **Configure Secrets:** 
   - Navigate to your repository **Settings > Secrets and variables > Actions**.
   - Create a new repository secret named `TARGET_WEBHOOK_URL` containing your destination endpoint.
3. **Initialize:** Trigger the workflow manually once from the **Actions** tab to generate the initial state tracker.
