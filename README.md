# ACstop - TRMNL Plugin

A TRMNL e-ink display plugin that shows real-time bus arrivals at any AC Transit stop.

![AC Transit Logo](https://www.actransit.org/sites/default/files/actransit-logo.svg)

## Features

- **Real-time arrivals** for any AC Transit bus stop
- **Route indicators** showing bus line numbers and destinations
- **Multiple routes** displayed with arrival times
- **Route filtering** - show only the routes you care about
- **Multiple layout options** for different TRMNL screen sizes
- **Zero infrastructure** - no backend server required, calls AC Transit API directly
- **E-ink optimized** - designed for 1-bit through 4-bit e-ink displays
- **Store-ready** - optimized with 6 or fewer inline styles per template
- **Automatic timezone conversion** - shows times in Pacific timezone
- **Error handling** - graceful display when no buses are available

## Installation

### Option 1: Automated Setup (Recommended)

1. Visit the TRMNL recipes/store page (when available)
2. Click "Install" on the ACstop plugin
3. Configure your AC Transit stop ID and API token
4. Choose your preferred layout
5. Adjust polling interval in device settings

### Option 2: Manual Installation

1. **Log into TRMNL Dashboard**
   - Go to [usetrmnl.com](https://usetrmnl.com) and sign in
   - Navigate to "Plugins" → "Create Private Plugin"

2. **Configure Form Fields**
   - Copy the contents of `settings.yml` from this repository
   - Paste into the plugin settings form, or manually create these fields:
     - **AC Transit Stop ID** (text field, required)
     - **AC Transit API Token** (text field, required)
     - **Route Filter** (text field, optional)

3. **Set Polling URL**
   ```
   https://api.actransit.org/transit/actrealtime/prediction?stpid={{ ac_stop_id }}&token={{ ac_api_token }}
   ```
   - Set polling verb to: `GET`
   - Leave polling headers and body empty
   - Recommended polling interval: 60 seconds

4. **Choose Template Layout**
   - Copy one of the `.liquid` template files from this repository:
     - `full.liquid` - 3-column grid for full screen
     - `half_horizontal.liquid` - 4-column grid for horizontal half screen
     - `quadrant.liquid` - 2-column grid for quarter screen
     - `half_vertical.liquid` - Vertical stack for vertical half screen

5. **Configure Plugin Settings**
   - **AC Transit Stop ID**: Enter your stop ID (find at [AC Transit Real-Time](https://www.actransit.org/actransit-realtime))
   - **AC Transit API Token**: Register at [api.actransit.org](https://api.actransit.org/transit/Account/Register)
   - **Route Filter** (optional): Enter comma-separated route numbers (e.g., "6,51,800")

6. **Save and Deploy**
   - Save your plugin configuration
   - Add the plugin to your TRMNL device
   - Your display will update at the configured interval

## Layouts

Choose from 4 responsive layouts optimized for different screen configurations:

### Full (3-column grid) - `full.liquid`
**Best for:** Full-screen displays showing 6 upcoming buses
- Large time display (2.6em)
- Detailed bus info including route and destination
- Grid layout with maximum information density

### Half Horizontal (4-column grid) - `half_horizontal.liquid`
**Best for:** Horizontal half-screen displays showing 4 upcoming buses
- Compact design with abbreviated labels
- Efficient use of horizontal space
- 4-column grid layout

### Half Vertical (Vertical stack) - `half_vertical.liquid`
**Best for:** Vertical half-screen displays showing 4 upcoming buses
- Tight vertical spacing
- Optimized for tall, narrow displays
- Stacked layout for vertical orientation

### Quadrant (2-column grid) - `quadrant.liquid`
**Best for:** Quarter-screen displays showing 2 upcoming buses
- Medium time display (1.9em)
- Balanced information density
- 2-column grid for small spaces

## Configuration Details

### Finding Your Stop ID

1. Visit [AC Transit Real-Time](https://www.actransit.org/actransit-realtime)
2. Use "Stops Near Me" feature or search by address
3. Select your stop to view its details
4. The stop ID is the numeric code (e.g., 55558)

### Getting Your API Token

1. Register at [AC Transit API Registration](https://api.actransit.org/transit/Account/Register)
2. Complete the registration form
3. Check your email for API token confirmation
4. Copy your token and paste into TRMNL configuration

### Route Filtering

Leave the Route Filter field **blank** to show all routes serving your stop, or enter specific route numbers separated by commas:

- Example: `6,51,800` - Shows only routes 6, 51, and 800
- Example: `1` - Shows only route 1
- Leave blank - Shows all routes at this stop

### Refresh Interval

**Recommended:** 60 seconds
- AC Transit API provides real-time predictions
- Faster refresh = more current data, but more API calls
- Balance between data freshness and API usage

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
- Icon by [iconsbysonny](https://thenounproject.com/creator/iconbysonny/)

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


