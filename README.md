# YouTube Channel Analytics Scraper

Python tool using YouTube Data API v3 to fetch and analyze channel statistics including subscribers, views, video counts, and playlists.

## Features

- Fetch channel statistics (subscribers, views, total videos)
- Extract video IDs from channel playlists
- Data visualization with Seaborn
- Handles pagination for large playlists
- Compare multiple channels

## Installation

```bash
pip install google-api-python-client pandas seaborn matplotlib
```

## Setup

1. Get YouTube Data API key from [Google Cloud Console](https://console.cloud.google.com/)
2. Add API key to the notebook

## Usage

```python
from googleapiclient.discovery import build

# Initialize API
api_key = 'YOUR_API_KEY'
youtube = build('youtube', 'v3', developerKey=api_key)

# Channel IDs to analyze
channel_ids = [
    'UCBJycsmduvYEL83R_U4JriQ',  # Marques Brownlee
    'UCYqsJbDDngvxb_rbHzHpYGA',  # Magic Noah
    'UCsBjURrPoezykLs9EqgamOA',  # Fireship
]

# Get statistics
channel_stats = get_channel_stats(youtube, channel_ids)
```

## Functions

### `get_channel_stats(youtube, channel_ids)`
Fetches channel information:
- Channel name
- Subscriber count
- Total views
- Total videos
- Upload playlist ID

### `get_video_ids(youtube, playlist_id)`
Extracts all video IDs from a channel's upload playlist with automatic pagination handling.

## Data Visualization

The notebook includes Seaborn visualizations for:
- Subscriber comparison
- Total views comparison
- Video count comparison

## Example Output

```
Channel_name        Subscribers  Views        Total_videos
Marques Brownlee    19200000     4376117149   1673
Fireship            3210000      455411233    655
Magic The Noah      1030000      103017809    245
```

## API Quota

YouTube Data API has daily quota limits. Each request costs units:
- `channels().list()`: 1 unit
- `playlistItems().list()`: 1 unit
- Default quota: 10,000 units/day

## Requirements

- Python 3.6+
- YouTube Data API v3 key
- Libraries: google-api-python-client, pandas, seaborn

## Files

- `main.ipynb` - Main analysis notebook

## Notes

- API key should be kept private
- Large channels may require multiple API calls (pagination)
- Statistics are fetched in real-time
