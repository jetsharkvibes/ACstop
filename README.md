# ACstop - TRMNL Plugin

A TRMNL e-ink display plugin that shows real-time bus arrivals at any AC Transit stop.

![AC Transit Logo](https://www.actransit.org/sites/default/files/actransit-logo.svg)

## Features

- **Real-time arrivals** for any AC Transit bus stop
- **Route indicators** showing bus line numbers and destinations
- **Multiple routes** displayed with arrival times
- **Multiple layout options** for different TRMNL screen sizes
- **Zero infrastructure** - no backend server required, calls AC Transit API directly
- **Store-ready** - optimized with 6 or fewer inline styles per template

## Layouts

Choose from 4 responsive layouts:

### Full (3-column grid)
Best for: Full-screen displays showing 6 upcoming buses
- Large time display (2.6em)
- Detailed bus info including route and destination

### Half Horizontal (4-column grid)
Best for: Horizontal half-screen displays showing 4 upcoming buses
- Compact design with abbreviated labels
- Efficient use of horizontal space

### Half Vertical (Vertical stack)
Best for: Vertical half-screen displays showing 4 upcoming buses
- Tight vertical spacing
- Optimized for tall, narrow displays

### Quadrant (2-column grid)
Best for: Quarter-screen displays showing 2 upcoming buses
- Medium time display (1.9em)
- Balanced information density

## Setup

### 1. Add to TRMNL

1. Go to your TRMNL dashboard
2. Click "Add Plugin"
3. Paste the GitHub repository URL: `https://github.com/jetsharkvibes/ACstop`
4. Select your preferred layout template
5. Configure your settings (see below)

### 2. Configuration

**AC Transit Stop ID** (required)
- Enter your AC Transit stop ID (e.g., 51234, 52345)
- Find your stop ID at https://api.actransit.org/transit/stops/ or use the AC Transit website

**AC Transit API Token** (required)
- Register for a free API token at https://api.actransit.org
- Paste your token in the configuration field

**Route Filter** (optional)
- Leave blank for all routes at this stop
- Enter specific route numbers to filter (e.g., "6,51,800")

### 3. Refresh Interval

Default: 60 seconds (recommended)
- AC Transit API updates in real-time
- Faster refresh = more current data, but more API calls

## Technical Details

### API Integration
- **Endpoint**: AC Transit Real-Time Predictions API
- **Format**: JSON
- **Authentication**: User-provided API token (register at https://api.actransit.org)
- **Rate limiting**: Respectful polling every 60 seconds

### Code Quality
- **Inline styles**: 2-3 per template (well under TRMNL's 6-style limit)
- **Framework**: TRMNL v2 with utility-first CSS classes
- **Templating**: Liquid (Shopify template language)
- **Responsive**: Adapts to 1-bit through 4-bit e-ink displays

### Data Processing
- Converts Pacific timezone automatically
- Shows arrival times in local time format
- Displays route numbers and destination information
- Filters by specific routes when configured

## Error Handling

If no buses are available:
- Displays ⚠️ warning emoji
- Shows "No buses available" message
- Automatically recovers when service resumes

## License

Public Domain - feel free to modify and distribute

## Credits

- Created by jetsharkvibes
- Forked from [BARTstop](https://github.com/jetsharkvibes/BARTstop)
- AC Transit API provided by [Alameda-Contra Costa Transit District](https://www.actransit.org/)
- Built for [TRMNL](https://usetrmnl.com/)

## Support

For issues or feature requests, please open an issue on GitHub:
https://github.com/jetsharkvibes/ACstop/issues

## Version History

### v1.0.0 (2025-11-19)
- Initial release of ACstop (forked from BARTstop)
- 4 responsive layouts (full, half_horizontal, half_vertical, quadrant)
- Real-time bus arrivals with route indicators
- Route filtering support
- Store-ready optimization (≤6 inline styles per template)
