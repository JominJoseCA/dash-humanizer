# Dash Humanizer

A Chrome extension that transforms em-dashes and en-dashes used as clause breaks into ellipsis (…) with normalized spacing, making your writing feel more natural and conversational.

## Features

- **Smart Text Transformation**: Automatically converts em-dashes (—) to ellipsis (…) while preserving numeric ranges and URLs
- **Multiple Interaction Methods**: 
  - Selection bubble for quick preview and transformation
  - Right-click context menu for instant transformation
  - Live typing mode for automatic transformation as you type
- **Privacy-First**: All processing happens locally in your browser - no data ever leaves your device
- **Works Everywhere**: Compatible with Gmail, LinkedIn, Twitter/X, Notion, Google Docs, and more

## Installation

### Install Pre-built Package (Recommended)

1. Download the `dist.zip` file
2. Extract the ZIP file to a folder on your computer
3. Open Google Chrome and navigate to `chrome://extensions/`
4. Enable **Developer mode** by toggling the switch in the top right corner
5. Click the **Load unpacked** button
6. Select the extracted folder (containing `manifest.json`)
7. The Dash Humanizer icon should now appear in your Chrome toolbar


## Documentation

For comprehensive help and usage examples, open the extension's help page:
- Click the extension icon → "Help" link
- Or open [help.html](help.html) directly

The help page includes:
- Detailed usage examples with visual guides
- Complete keyboard shortcuts reference
- FAQ section with common questions
- Troubleshooting guide
- Privacy and security information

## Usage

### Quick Start

1. **Selection Bubble**: Select any text containing em-dashes, and a bubble will appear showing the transformed version
2. **Context Menu**: Right-click selected text and choose "Humanize dashes"
3. **Live Typing**: Enable "Auto-humanize as I type/paste" in settings for automatic transformation

### Settings

Click the extension icon and select "Settings" to configure:

- **Auto-humanize on selection**: Show transformation bubble when you select text
- **Auto-humanize as I type/paste**: Automatically transform dashes while typing or pasting
- **Also convert en dashes**: Include en-dashes (–) in addition to em-dashes (—)

## Privacy & Security

🔒 **Complete Privacy Guarantee**: All text processing occurs locally in your browser. The extension:
- **Makes zero network requests** - No data ever leaves your device
- **Collects no data** - We don't see, store, or transmit any of your text
- **Includes no analytics or tracking** - No third-party services or telemetry
- **Only stores your preference settings locally** - Settings are stored using Chrome's secure storage API
- **Open source** - All code is available for inspection and audit


## Permissions

The extension requires the following permissions:

- **contextMenus**: To add the "Humanize dashes" option to the right-click menu
- **storage**: To save your settings preferences
- **activeTab**: To access and modify text on the current page
- **<all_urls>**: To work on all websites you visit

## Accessibility

♿ **Fully Accessible**: The extension is built with accessibility as a core feature:

- **Keyboard Navigation**: All functionality accessible via keyboard (Tab, Enter, Escape)
- **Screen Reader Support**: Full ARIA implementation with helpful announcements
- **Focus Management**: Proper focus indicators and focus trapping in dialogs
- **High Contrast Mode**: Enhanced visibility in high contrast mode
- **WCAG 2.1 AA Compliant**: Meets all Level AA accessibility standards

### Keyboard Shortcuts

- **Tab**: Navigate between buttons in bubble/modal
- **Shift+Tab**: Navigate backwards
- **Enter** or **Space**: Activate focused button
- **Escape**: Close bubble or modal dialog


## Supported Applications

The extension has been tested and verified to work with the following applications:

### Fully Supported
- ✅ **Gmail** - Compose window, reply, and forward
- ✅ **LinkedIn** - Post editor, comments, and messages
- ✅ **Twitter/X** - Tweet composer and replies
- ✅ **Notion** - All page types and block types
- ✅ **Google Docs** - Document body (with undo/redo support)
- ✅ **Standard HTML** - All textarea and input fields
- ✅ **ContentEditable** - Any contentEditable element

### How It Works
The extension provides three interaction methods:

1. **Selection Bubble** (Default)
   - Select text containing dashes
   - Preview the transformation in a popup
   - Click "Copy" or "Replace Selection"

2. **Context Menu**
   - Select text and right-click
   - Choose "Humanize dashes"
   - Text is transformed instantly

3. **Live Typing** (Optional)
   - Enable in settings
   - Type naturally with dashes
   - Automatic transformation as you type

### Compatibility Notes
- Works on any website with text input fields
- Some custom rich text editors may have limited support
- Cross-origin iframes are restricted by browser security (expected)
- Best results with standard HTML input elements

## Technical Details

- **Manifest Version**: 3 (latest Chrome extension standard)
- **Architecture**: Service worker + content scripts


## Development


### Project Structure

```
dash-humanizer/
├── manifest.json           # Extension configuration
├── background.js           # Service worker
├── content.js             # Content script (page interaction)
├── transform.js           # Core transformation logic
├── settings.js            # Settings management
├── error-handler.js       # Error handling utilities
├── build.js               # Build script
├── package.js             # Packaging script
├── package.json           # NPM configuration
├── popup/                 # Action popup UI
│   ├── popup.html
│   ├── popup.js
│   └── popup.css
├── options/               # Settings page
│   ├── options.html
│   ├── options.js
│   └── options.css
├── components/            # Reusable UI components
│   ├── bubble.js
│   └── bubble.css
├── icons/                 # Extension icons
│   ├── icon16.png
│   ├── icon48.png
│   └── icon128.png
├── dist/                  # Build output (generated)
└── README.md
```

### Testing

The extension includes comprehensive testing files for all functionality. See [TESTING_GUIDE.md](TESTING_GUIDE.md) for complete testing instructions.

#### Quick Test Overview

**Integration Testing** (`integration-test.html`)
- Complete user flow testing on all target sites
- Tests selection bubble, copy, replace, live typing, and paste
- Covers plain textareas, input fields, and contentEditable elements
- Includes edge case testing

**Context Menu Testing** (`context-menu-test.html`)
- Tests right-click "Humanize dashes" functionality
- Verifies in-place replacement in editable fields
- Verifies modal fallback for non-editable content
- Tests on all target sites

**Settings Testing** (`settings-test.html`)
- Tests settings persistence and synchronization
- Verifies cross-tab sync without reload
- Tests default settings on fresh install
- Tests action popup toggle

**Edge Cases Testing** (`edge-cases-test.html`)
- Tests very long text (50,000+ characters)
- Tests iframe handling
- Tests extension disabled state
- Tests clipboard permission denied scenarios
- Tests protected contexts (code blocks, URLs)

**Accessibility Testing** (`accessibility-audit-verification.html`)
- Comprehensive WCAG 2.1 AA compliance verification
- Tests all keyboard navigation (Requirements 9.1-9.5)
- Verifies ARIA implementation and screen reader support
- Tests high contrast mode and reduced motion support
- Includes focus management and focus trap verification

#### Performance Testing

Run automated performance benchmarks:

```bash
# Command-line automated tests
node performance-test.js

# Interactive browser tests
start performance-benchmark.html  # Windows
open performance-benchmark.html   # macOS
```

See [PERFORMANCE_TESTING.md](PERFORMANCE_TESTING.md) for detailed benchmarks.

#### Unit Testing

Run the transformation logic tests:

```bash
node transform.test.js
```

All 23 unit tests should pass.

#### Running Tests

1. Load the extension in Chrome using "Load unpacked"
2. Open any test HTML file in your browser
3. Follow the instructions on each test page
4. Check off items in the test results checklist
5. Monitor browser console (F12) for errors

#### Test Cases

Try these examples in any test page:
- `He went—without saying goodbye` → `He went … without saying goodbye`
- `The year 2019—it was memorable` → `The year 2019 … it was memorable`
- `First—second—third` → `First … second … third`
- `Years 2019–2023` → `Years 2019–2023` (preserved - numeric range)
- `Temperature: -5°C` → `Temperature: -5°C` (preserved - minus sign)

### Testing Notes and Assumptions

**Implementation Notes:**
- The extension uses placeholder icons during development
- All core functionality is implemented with minimal dependencies
- Performance benchmarks are measured during development
- Live typing transformation uses 100ms debouncing to avoid performance issues
- Paste events are transformed before insertion to maintain smooth UX

**Testing Assumptions:**
- Tests assume Chrome browser version 88 or higher (Manifest V3 support)
- Some tests require manual verification due to browser security restrictions
- Cross-origin iframe tests may fail due to browser security policies (expected behavior)
- Clipboard API tests require user permission grant
- Screen reader tests require NVDA or JAWS installed on Windows
- Performance tests should be run on a system with at least 4GB RAM for accurate results
- Live typing tests work best with standard keyboard input (some IME inputs may behave differently)

**Known Limitations:**
- Rich text editors with custom implementations (e.g., some CMS systems) may require manual copy/paste
- Cross-origin iframes cannot be accessed due to browser security (graceful fallback provided)
- Some websites with strict Content Security Policies may limit functionality
- Extension must be reloaded after code changes during development

