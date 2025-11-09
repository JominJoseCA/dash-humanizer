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

### Option 1: Install Pre-built Package (Recommended)

1. Download the latest `dash-humanizer-v1.0.0.zip` file
2. Extract the ZIP file to a folder on your computer
3. Open Google Chrome and navigate to `chrome://extensions/`
4. Enable **Developer mode** by toggling the switch in the top right corner
5. Click the **Load unpacked** button
6. Select the extracted folder (containing `manifest.json`)
7. The Dash Humanizer icon should now appear in your Chrome toolbar

### Option 2: Build from Source

If you want to build the extension yourself:

1. Clone or download this repository
2. Install Node.js (if not already installed)
3. Open a terminal in the project directory
4. Run the build command:
   ```bash
   npm run build
   ```
5. The built extension will be in the `dist/` folder
6. Follow steps 3-7 from Option 1, selecting the `dist/` folder

### Option 3: Development Mode

For development and testing:

1. Clone or download this repository
2. Open Google Chrome and navigate to `chrome://extensions/`
3. Enable **Developer mode** by toggling the switch in the top right corner
4. Click the **Load unpacked** button
5. Select the project root folder (where `manifest.json` is located)
6. The Dash Humanizer icon should now appear in your Chrome toolbar

### Verify Installation

After installation, you should see the Dash Humanizer icon in your browser toolbar. Click it to:
- Toggle the extension on/off
- Access settings
- View help documentation (opens [help.html](help.html) with comprehensive usage guide)

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

**Security Features:**
- Content Security Policy (CSP) prevents code injection attacks
- No use of `eval()` or inline scripts
- All user input is sanitized before display
- Minimal permissions requested (only what's necessary for functionality)
- Regular security audits performed

See [SECURITY_AUDIT.md](SECURITY_AUDIT.md) for the complete security audit report.

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

See [ACCESSIBILITY_AUDIT.md](ACCESSIBILITY_AUDIT.md) for the complete accessibility audit report.

### Keyboard Shortcuts

- **Tab**: Navigate between buttons in bubble/modal
- **Shift+Tab**: Navigate backwards
- **Enter** or **Space**: Activate focused button
- **Escape**: Close bubble or modal dialog

### Screen Reader Testing

For detailed screen reader testing instructions:
- Full guide: [screen-reader-testing-guide.md](screen-reader-testing-guide.md)
- Quick test: [screen-reader-quick-test.md](screen-reader-quick-test.md)

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
- **Performance**: 
  - Transformation: 0.82ms average for 10,000 characters (60x faster than requirement)
  - Large text: 3.81ms for 50,000 characters (131x faster than requirement)
  - Typing lag: < 1ms per keystroke
  - Bubble render: < 10ms (smooth 60fps)
- **Memory**: < 5MB when idle
- **CPU Usage**: < 1% while scrolling

See [PERFORMANCE_TESTING.md](PERFORMANCE_TESTING.md) for detailed benchmarks.

## Troubleshooting

### Extension not working on a specific site

**Symptoms**: Selection bubble doesn't appear, context menu missing, or transformations don't work

**Solutions**:
1. Refresh the page after installing the extension (Ctrl+R or Cmd+R)
2. Check that the extension is enabled (click the icon to verify it shows "ON")
3. Verify the site allows extensions - some sites with strict Content Security Policies may limit functionality
4. Try disabling other extensions that might conflict
5. Check the browser console (F12) for any error messages

### Selection bubble not appearing

**Symptoms**: Text selection doesn't show the transformation bubble

**Solutions**:
1. Check that "Auto-humanize on selection" is enabled in settings
2. Ensure you're selecting text that contains dashes (—, –, or -)
3. Try selecting text in a different area of the page
4. Verify the extension is enabled (not in "OFF" state)

### Clipboard access denied

**Symptoms**: Error message when clicking "Copy" button

**Solutions**:
1. Check Chrome's site permissions for clipboard access (click the lock icon in address bar)
2. Grant clipboard permission when prompted
3. Use the "Replace Selection" button instead of "Copy" when in editable fields
4. Try copying manually (Ctrl+C) after the transformation

### Settings not saving

**Symptoms**: Settings revert after closing options page or restarting browser

**Solutions**:
1. Ensure you're signed into Chrome (for sync storage across devices)
2. Check that Chrome sync is enabled in Chrome settings (chrome://settings/syncSetup)
3. Settings will automatically fall back to local storage if sync is unavailable
4. Try toggling the setting off and on again
5. Check browser console for storage quota errors

### Live typing not working

**Symptoms**: Dashes aren't automatically transformed while typing

**Solutions**:
1. Verify "Auto-humanize as I type/paste" is enabled in settings
2. Ensure you're typing in an editable field (textarea, input, or contentEditable)
3. Try typing a dash followed by a space to trigger transformation
4. Some rich text editors may not support live transformation - use selection bubble or context menu instead
5. Refresh the page and try again

### Extension slowing down browser

**Symptoms**: Browser feels sluggish or typing has lag

**Solutions**:
1. Disable "Auto-humanize as I type/paste" if you don't need it
2. Check CPU usage in Chrome Task Manager (Shift+Esc)
3. The extension should use < 1% CPU - if higher, try reloading the extension
4. Report the issue with details about the website and text length

### Context menu item not appearing

**Symptoms**: Right-click menu doesn't show "Humanize dashes"

**Solutions**:
1. Ensure you have text selected before right-clicking
2. Verify the extension is enabled
3. Try reloading the extension in chrome://extensions/
4. Check that no other extension is overriding the context menu

### Works in some apps but not others

**Symptoms**: Extension works in Gmail but not in another application

**Solutions**:
1. Some applications use custom editors that may require special handling
2. Try using the context menu instead of the selection bubble
3. As a workaround, copy text to a plain textarea, transform it, then copy back
4. Report the specific application for potential future support

### Extension not loading after installation

**Symptoms**: Extension icon doesn't appear in toolbar, or shows errors in chrome://extensions/

**Solutions**:
1. Verify you selected the correct folder (containing manifest.json)
2. Check for error messages in chrome://extensions/ and expand the extension details
3. Ensure you're using Chrome version 88 or higher (Manifest V3 requirement)
4. Try removing and re-adding the extension
5. If using the built version, ensure the build completed successfully

### Getting "Manifest version 2 is deprecated" warning

**Solution**: This extension uses Manifest V3 (the latest version). If you see this warning, you may have loaded the wrong folder or an old version.

### Still having issues?

If none of the above solutions work:
1. Check the browser console (F12) for error messages
2. Try disabling all other extensions to rule out conflicts
3. Test in an Incognito window (enable the extension for Incognito in chrome://extensions/)
4. Verify you're using the latest version of Chrome
5. Try uninstalling and reinstalling the extension

## Development

### Building the Extension

The extension includes build scripts to minify and optimize all files:

```bash
# Build the extension (creates dist/ folder)
npm run build

# Create a ZIP package for distribution
npm run package
```

The build process:
- Minifies all JavaScript files (43% size reduction)
- Optimizes CSS files
- Copies all necessary assets (HTML, icons, manifest)
- Creates a production-ready `dist/` folder
- Generates a `dash-humanizer-v1.0.0.zip` package

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

## Frequently Asked Questions

### Why use ellipsis instead of em-dashes?

Em-dashes (—) are often used in formal writing to indicate breaks or parenthetical thoughts. Ellipsis (…) creates a more conversational, natural tone that many writers prefer for modern communication, especially in emails and social media.

### Will this break my numeric ranges like "2019–2023"?

No! The extension is smart enough to detect numeric ranges and preserve them. It only transforms dashes used as clause breaks in sentences.

### Does it work offline?

Yes! All processing happens locally in your browser. No internet connection is required for the extension to work.

### Can I use this on mobile?

Currently, this extension is designed for desktop Chrome browsers. Mobile Chrome doesn't support extensions in the same way.

### Will it slow down my browser?

No. The extension is highly optimized and uses less than 1% CPU and 5MB of memory. Transformations happen in milliseconds.

### Can I disable it temporarily?

Yes! Click the extension icon and toggle it off. You can re-enable it anytime without losing your settings.

### Does it support other languages?

The extension works with any language that uses em-dashes or en-dashes. The transformation logic is language-agnostic.

### What's the difference between em-dash and en-dash?

- **Em-dash (—)**: Longer dash, typically used for clause breaks
- **En-dash (–)**: Shorter dash, typically used for ranges (2019–2023)

By default, the extension only transforms em-dashes. You can enable en-dash transformation in settings.

## License

MIT License - Feel free to use, modify, and distribute this extension.

## Contributing

Contributions are welcome! If you'd like to contribute:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly using the provided test files
5. Submit a pull request with a clear description

Please ensure your code:
- Follows the existing code style
- Includes appropriate comments
- Passes all existing tests
- Maintains privacy and security standards

## Support

For issues, questions, or feature requests:
- Check the [Troubleshooting](#troubleshooting) section above
- Review the [Testing Guide](TESTING_GUIDE.md) for common issues
- Open an issue on the project repository with:
  - Chrome version
  - Extension version
  - Steps to reproduce the issue
  - Expected vs actual behavior

---

**Version**: 1.0.0  
**Last Updated**: November 2025
