# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a simple shopping list web application built as a single-page HTML file with inline CSS and JavaScript. The application is written in Korean (쇼핑 리스트 - Shopping List) and uses localStorage for data persistence.

## Architecture

**Single-File Structure**: The entire application is contained in `index.html`:
- **HTML (lines 1-174)**: Page structure with input field, add button, list container, and statistics
- **CSS (lines 7-152)**: Inline styles with gradient background, card-based layout, and hover effects
- **JavaScript (lines 176-279)**: Vanilla JavaScript for all functionality

**Data Model**: Simple array-based structure stored in localStorage:
```javascript
items = [
  { id: timestamp, text: string, checked: boolean }
]
```

**Key Functions**:
- `loadItems()`: Loads shopping list from localStorage on page load
- `saveItems()`: Persists items array to localStorage
- `addItem()`: Creates new item with timestamp-based ID
- `deleteItem(id)`: Removes item by filtering array
- `toggleItem(id)`: Toggles checked state of item
- `renderList()`: Updates DOM with current items state
- `updateStats()`: Displays total and checked item counts

## Running the Application

Simply open `index.html` in a web browser. No build process, server, or dependencies required.

## Testing

The `.playwright-mcp/` directory contains test artifacts:
- `shopping-list-test-result.png`: Screenshot of test results

## Environment Variables

The `.env` file contains a GitHub personal access token. This token should be kept secure and not committed to version control (currently tracked).

## Development Notes

- All state management happens through the `items` array
- DOM updates are handled imperatively through `renderList()`
- Event handlers are attached using both inline `onclick`/`onchange` attributes and `addEventListener`
- IDs are generated using `Date.now()` which may cause collisions if items are added rapidly
