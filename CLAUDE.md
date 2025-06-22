# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Life Timeline Visualization** project - a simple HTML/CSS/JavaScript application that displays important life events in a visual timeline format. It's based on the original [cheeaun/life](https://github.com/cheeaun/life) project and customized with personal life events and gadget history.

## Architecture

### Core Components

- **index.html**: Single-page application containing all HTML, CSS, and JavaScript
- **life.md**: Markdown file containing life events data in a specific format
- **config.json**: Configuration file for timeline display settings
- **config.example.json**: Template for configuration settings

### Key JavaScript Architecture

The application consists of two main objects:

1. **life object** (`index.html:186-463`): Core timeline functionality
   - `loadConfig()`: Loads configuration from `config.json`
   - `fetch()`: Loads life events from `life.md`
   - `parse()`: Parses markdown format into timeline data
   - `parseTime()`: Handles various date formats (YYYY, MM/YYYY, DD/MM/YYYY, ranges, estimates)
   - `render()`: Generates HTML for timeline visualization
   - `renderEvent()`: Creates individual event elements with positioning
   - `renderYears()`: Creates year axis with optional age display

2. **slider object** (`index.html:465-495`): Mouse interaction for timeline navigation
   - Handles click-and-drag scrolling functionality

### Data Format

Life events in `life.md` follow this syntax:
- `- YYYY Event description` - events in a specific year
- `- MM/YYYY Event description` - events in a specific month/year  
- `- DD/MM/YYYY Event description` - events on a specific date
- `- YYYY1-YYYY2 Event description` - events spanning multiple years
- `- ~YYYY Event description` - approximate year events
- `- YYYY-~ Event description` - ongoing events from a year

Special formatting:
- `**text**` - bold text
- `_text_` - italic text
- `[link text](url)` - markdown links
- `#hashtag` - colored tags (with CSS classes for different device types)

## Development Commands

### Local Development Server
```bash
# Using Python (recommended - already available)
python3 -m http.server 8000

# Alternative: Install and use http-server
npm install -g http-server
http-server
```

### File Structure
- Keep `life.md` and `config.json` in the `gh-pages` branch for GitHub Pages deployment
- The `master` branch should contain the base template files
- Personal life data should not be committed to the `master` branch

## Configuration

### Timeline Display Settings (`config.json`)
- `yearLength`: Width of year grids in pixels (default: 120)
- `hideAge`: Hide age numbers from year axis (default: false)  
- `customStylesheetURL`: Path to custom CSS file (default: null)

### Device Type Colors (CSS classes in `index.html:66-92`)
- `#desktop` - Yellow (`#fef08a`)
- `#laptop` - Green (`#a7f3d0`)
- `#phone` - Purple (`#ddd6fe`)
- `#tablet` - Cyan (`#a5f3fc`)
- `#earphones` - Red (`#fca5a5`)
- `#watch` - Pink (`#fbcfe8`)
- `#tv` - Purple (`#d8b4fe`)
- `#console` - Pink (`#fda4af`)
- `#trackpad` - Teal (`#99f6e4`)

## Deployment

This project is designed for GitHub Pages deployment:
1. Fork the repository
2. Create/switch to `gh-pages` branch
3. Add your `life.md` and `config.json` files
4. Push to GitHub Pages
5. The timeline will be available at `https://username.github.io/life`