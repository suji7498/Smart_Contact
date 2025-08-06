# SmartContact Webhook Form - Installation & Setup Guide

## Quick Installation

1. **Upload Plugin Files**
   - Upload the `Smart Contact WordPress` folder to `/wp-content/plugins/`
   - Rename folder to `smartcontact-webhook-form` 
   - Or install via WordPress admin: Plugins > Add New > Upload Plugin

2. **Activate Plugin**
   - Go to Plugins page in WordPress admin
   - Find "SmartContact Webhook Form" and click "Activate"

3. **Configure Settings**
   - Go to **SmartContact** in your WordPress admin menu
   - Configure your webhook URL and form settings

## Initial Configuration

### 1. Webhook Setup

Navigate to **SmartContact > Webhook Settings**:

- **Webhook URL**: Enter your webhook endpoint (e.g., n8n, Zapier)
- **HTTP Method**: Choose POST, PUT, or PATCH (POST recommended)
- Click **"Test Webhook"** to verify connection

### 2. Form Customization

Go to **Form Settings** tab:

- **Form Title**: Change the main heading (default: "Get in Touch")
- **Form Description**: Update the subtitle text
- **Theme**: Choose from 5 color schemes
- **Enable CAPTCHA**: Toggle spam protection on/off

### 3. Popup Configuration (Optional)

In **Popup Settings** tab:

- **Enable Popup**: Turn on automatic popup display
- **Popup Delay**: Delay before showing (milliseconds)
- **Session Delay**: Time before showing again (seconds)

## Usage Methods

### Method 1: Page/Post Shortcode

Add this shortcode to any page or post:

```
[smartcontact_form]
```

**Custom Options:**
```
[smartcontact_form title="Custom Title" description="Custom description" theme="pink"]
```

### Method 2: Popup Mode

1. Enable popup in SmartContact settings
2. Form automatically appears on all pages
3. Respects session delays to avoid annoying visitors

### Method 3: Template Integration

For theme developers, add to PHP templates:

```php
<?php echo do_shortcode('[smartcontact_form]'); ?>
```

## Webhook Integration Examples

### n8n Setup

1. Create new workflow in n8n
2. Add "Webhook" trigger node
3. Set method to POST
4. Copy the webhook URL
5. Paste in SmartContact settings
6. Test connection

**Sample n8n Workflow:**
```
Webhook Trigger → Filter Node → Email Node → Database Node
```

### Zapier Setup

1. Create new Zap in Zapier
2. Choose "Webhooks by Zapier" as trigger
3. Select "Catch Hook"
4. Copy the webhook URL
5. Paste in SmartContact settings
6. Test and continue Zap setup

### Custom API Setup

Your endpoint should:
- Accept POST requests
- Handle JSON content-type
- Process this data structure:

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "subject": "Website Inquiry",
  "message": "Hello, I'm interested in your services...",
  "timestamp": "2024-01-15 10:30:00",
  "source": "WordPress Contact Form"
}
```

## Form Management

### Viewing Submissions

1. Go to **SmartContact > Submissions**
2. View all form entries with:
   - Contact details
   - Submission timestamp
   - Webhook delivery status
   - Full message content

### Exporting Data

- Click **"Export CSV"** to download all submissions
- Includes all form fields and metadata
- Perfect for analysis or backup

### Bulk Actions

- Select multiple submissions
- Delete unwanted entries
- Keep database clean and organized

## Customization Options

### Shortcode Parameters

| Parameter | Options | Default | Description |
|-----------|---------|---------|-------------|
| `title` | Any text | Form setting | Custom form title |
| `description` | Any text | Form setting | Custom description |
| `theme` | skyblue, pink, orange, grey, black | Form setting | Color theme |
| `show_title` | true, false | true | Show/hide title section |

### Available Themes

1. **Sky Blue** - Professional, trustworthy
2. **Pink** - Creative, friendly  
3. **Orange** - Energetic, bold
4. **Grey** - Minimal, sophisticated
5. **Black** - Elegant, modern (white text)

### CSS Customization

Add custom CSS in **Appearance > Customize > Additional CSS**:

```css
/* Custom form styling */
.smartcontact-form-container {
    border-radius: 20px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
}

/* Custom button styling */
.smartcontact-submit-btn {
    background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
}
```

## Troubleshooting

### Webhook Not Working

1. **Check URL Format**: Must start with http:// or https://
2. **Test Connection**: Use "Test Webhook" button
3. **Check Method**: Ensure endpoint accepts your chosen HTTP method
4. **Review Logs**: Check webhook service logs for errors

### Form Not Displaying

1. **Check Shortcode**: Ensure `[smartcontact_form]` is correct
2. **Plugin Active**: Verify plugin is activated
3. **Theme Conflicts**: Try default WordPress theme
4. **JavaScript Errors**: Check browser console for errors

### Popup Not Showing

1. **Enable Setting**: Ensure popup is enabled in settings
2. **Clear Cookies**: Delete `smartcontact_popup_shown` cookie
3. **Check Delay**: Wait for configured delay time
4. **Inspect Element**: Look for popup HTML in page source

### Styling Issues

1. **Theme Conflicts**: Some themes may override styles
2. **Cache Issues**: Clear website cache after changes
3. **CSS Conflicts**: Check for conflicting CSS rules
4. **Mobile Issues**: Test responsive design on devices

## Security Considerations

### CAPTCHA Settings

- **Math Questions**: Simple addition problems
- **Regenerates**: New question after each attempt
- **Customizable**: Can be disabled if not needed

### Data Protection

- Form data stored securely in WordPress database
- IP addresses logged for spam prevention
- Webhook data sent via HTTPS (recommended)
- Regular database cleanup recommended

### Spam Prevention

1. Enable CAPTCHA for basic protection
2. Monitor submissions regularly
3. Use webhook filtering (n8n/Zapier)
4. Consider rate limiting at server level

## Performance Optimization

### Database Maintenance

- Export and delete old submissions periodically
- Plugin stores unlimited submissions by default
- Consider automated cleanup for high-traffic sites

### Caching Compatibility

- Works with most caching plugins
- Popup functionality uses cookies, not sessions
- AJAX submissions bypass cache naturally

## Advanced Configuration

### Developer Hooks

```php
// Modify form data before webhook
add_filter('smartcontact_webhook_data', function($data) {
    $data['custom_field'] = 'custom_value';
    return $data;
});

// Custom validation
add_filter('smartcontact_validate_submission', function($valid, $data) {
    // Custom validation logic
    return $valid;
}, 10, 2);
```

### Custom Templates

Copy template files to your theme:
```
your-theme/smartcontact/form.php
```

### Multi-language Support

Plugin is translation-ready:
1. Use Loco Translate plugin
2. Translate strings in admin
3. Create .po/.mo files for your language

## Support & Updates

### Getting Help

1. Check this documentation first
2. Review WordPress.org support forum
3. Contact plugin author for premium support
4. Report bugs via GitHub issues

### Stay Updated

- Enable automatic updates in WordPress
- Follow plugin changelog for new features
- Backup site before major updates
- Test updates on staging site first

## Best Practices

### Form Design

1. Keep forms simple and focused
2. Use clear, action-oriented titles
3. Provide helpful placeholder text
4. Test on multiple devices

### Webhook Configuration

1. Always test webhook connections
2. Use HTTPS endpoints when possible
3. Implement proper error handling
4. Monitor webhook success rates

### User Experience

1. Provide clear success messages
2. Handle errors gracefully
3. Don't make popups too aggressive
4. Respect user preferences (session delays)

### Maintenance

1. Review submissions regularly
2. Export data periodically
3. Update plugin promptly
4. Monitor performance impact

---

**Need more help?** Contact our support team or visit the plugin documentation for additional resources.
