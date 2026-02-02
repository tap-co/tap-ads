---
name: tap-ads
description: Complete advertising skill for campaign planning, media buying, inventory search, and budget optimization across radio, TV, podcasts, and digital platforms.
---

# Tap Ads Skill

Plan advertising campaigns, search media inventory, and optimize budget allocation using the Tap advertising platform.

## Triggers

Activate this skill when the user:
- Mentions "campaign", "advertising", "media plan", or "ad buy"
- Asks about radio, TV, podcast, or digital advertising
- Wants to find advertising inventory or platforms
- Needs help with budget allocation or media planning
- References CPM, reach, impressions, or audience targeting

## Setup

### Install the Tap CLI

```bash
npm install -g @tap-co/cli
```

### Authenticate

```bash
tap auth login
```

Enter your API key when prompted. Get an API key at https://docs.tap.co/request-access

### Verify Installation

```bash
tap auth status
tap --help
```

## Available Commands

### Search Inventory

Find advertising platforms matching criteria:

```bash
# Search by market
tap search --market "New York"

# Search by format
tap search --format radio

# Search with budget constraint (max CPM)
tap search --market "Los Angeles" --format podcast --budget 30

# Get JSON output for processing
tap search --market "Chicago" --json
```

### Generate Campaign Plans

Create optimized media plans:

```bash
# Basic plan with budget
tap plan --budget 50000

# Plan with goal and audience
tap plan --budget 100000 --goal awareness --audience "25-54"

# Multi-market plan
tap plan --budget 75000 --markets "New York,Los Angeles,Chicago"

# Get JSON output
tap plan --budget 50000 --json
```

### Manage Campaigns

```bash
# List all campaigns
tap campaigns list

# List active campaigns only
tap campaigns list --status active

# Get campaign details
tap campaigns get cmp_abc123

# Create campaign from a plan
tap plan --budget 25000 --json | tap campaigns create --from-stdin
```

## Workflow

### 1. Gather Campaign Objectives
Ask the user for:
- Campaign goal (awareness, consideration, conversion)
- Target audience (demographics, interests, location)
- Budget range
- Timeline/flight dates
- Preferred media channels (radio, TV, podcast, digital, or all)

### 2. Search Inventory
Use Tap CLI to find matching platforms:

```bash
tap search --market "New York" --format radio --audience "25-54"
```

- Filter by market/geography
- Filter by audience demographics
- Filter by format (audio, video, display)
- Sort by CPM efficiency or reach

### 3. Build Media Plan
Create an optimized allocation:

```bash
tap plan --budget 50000 --goal awareness --audience "25-54" --markets "New York"
```

- Distribute budget across platforms
- Balance reach vs. frequency
- Consider daypart targeting for broadcast
- Account for production costs

### 4. Present Recommendations
Provide the user with:
- Summary of recommended platforms
- Budget breakdown by channel
- Estimated reach and frequency
- CPM and total impressions
- Next steps for activation

## Example Prompts

- "Find radio stations in Chicago reaching women 25-54"
- "Create a $50,000 awareness campaign for a new product launch"
- "What podcast advertising options are available in the tech category?"
- "Help me plan a multi-channel campaign with TV and digital"
- "Search for digital display inventory under $15 CPM"

## Scripting & Automation

Combine commands for automation:

```bash
# Search and filter with jq
tap search --market NYC --json | jq '.platforms[] | select(.cpm < 20)'

# Create campaign from generated plan
tap plan --budget 25000 --json | tap campaigns create --from-stdin

# Export results to file
tap search --market "Los Angeles" --json > la-inventory.json
```

## Environment Variables

- `TAP_API_KEY` - API key (alternative to `tap auth login`)
- `TAP_API_URL` - API base URL (default: `https://api.tap.co/v1`)

## Resources

- [Tap CLI Documentation](https://docs.tap.co/cli)
- [Tap API Reference](https://docs.tap.co/api)
- [Request API Access](https://docs.tap.co/request-access)
