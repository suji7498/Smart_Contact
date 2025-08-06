=== SmartContact Webhook Form ===
Contributors: yourname
Tags: contact, form, webhook, n8n, zapier, popup
Requires at least: 5.0
Tested up to: 6.4
Requires PHP: 7.4
Stable tag: 1.0.0
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Beautiful contact forms that send data to webhooks (n8n, Zapier, etc.) with popup and page form options.

== Description ==

SmartContact Webhook Form is a powerful WordPress plugin that creates beautiful, customizable contact forms and sends form data directly to your webhook endpoints like n8n, Zapier, or any custom API.

**Key Features:**

* **Webhook Integration**: Send form data to n8n, Zapier, or any webhook URL
* **Dual Display Modes**: Use as normal page form OR popup with session delays
* **Customizable Content**: Admin can change form title and description
* **Multiple Themes**: 5 beautiful color themes (Sky Blue, Pink, Orange, Grey, Black)
* **Built-in Security**: Simple math CAPTCHA to prevent spam
* **Form Management**: View and manage all form submissions in WordPress admin
* **Responsive Design**: Works perfectly on all devices
* **Easy Setup**: Simple shortcode `[smartcontact_form]` for any page/post

**Perfect For:**

* Lead generation forms
* Customer support inquiries
* Newsletter signups
* Business contact forms
* Integration with automation tools (n8n, Zapier)
* Marketing funnel capture forms

**Popup Features:**

* Configurable display delay
* Session-based showing (won't annoy returning visitors)
* Easy close options
* Mobile-friendly design

== Installation ==

1. Upload the plugin files to `/wp-content/plugins/smartcontact-webhook-form/` directory
2. Activate the plugin through the 'Plugins' screen in WordPress
3. Go to **SmartContact** in your WordPress admin menu
4. Configure your webhook URL and form settings
5. Use the shortcode `[smartcontact_form]` in any page or post
6. Optionally enable popup mode for automatic display

== Frequently Asked Questions ==

= How do I set up a webhook with n8n? =

1. Create a new workflow in n8n
2. Add a "Webhook" trigger node
3. Copy the webhook URL from n8n
4. Paste it in the SmartContact settings under "Webhook URL"
5. Test the connection using the "Test Webhook" button

= Can I use both popup and page forms? =

Yes! You can enable popup mode for automatic display and still use the shortcode `[smartcontact_form]` on specific pages.

= How do I customize the form appearance? =

Go to **SmartContact > Form Settings** to:
- Change the form title and description
- Select from 5 color themes
- Enable/disable CAPTCHA
- Preview your changes in real-time

= What data is sent to the webhook? =

The plugin sends a JSON payload containing:
- name
- email  
- subject
- message
- timestamp
- source ("WordPress Contact Form")

= Can I export form submissions? =

Yes! Go to **SmartContact > Submissions** and click "Export CSV" to download all submissions.

= Is the plugin GDPR compliant? =

The plugin stores minimal data and you control where form data is sent via webhooks. Ensure your webhook endpoint complies with applicable privacy laws.

== Screenshots ==

1. Beautiful contact form with Sky Blue theme
2. Admin settings panel with webhook configuration
3. Form submissions management page
4. Popup form display example
5. Multiple color themes preview

== Changelog ==

= 1.0.0 =
* Initial release
* Webhook integration with n8n, Zapier, and custom APIs
* Popup and page form display modes
* 5 customizable themes
* Built-in CAPTCHA security
* Form submissions management
* Responsive design
* Export functionality

== Upgrade Notice ==

= 1.0.0 =
Initial release of SmartContact Webhook Form plugin.

== Usage ==

**Basic Usage:**
`[smartcontact_form]`

**Custom Title and Description:**
`[smartcontact_form title="Get a Quote" description="Tell us about your project"]`

**Custom Theme:**
`[smartcontact_form theme="pink"]`

**Hide Title:**
`[smartcontact_form show_title="false"]`

**Webhook Setup Examples:**

* **n8n**: Use the webhook URL from your n8n workflow trigger
* **Zapier**: Use the webhook URL from your Zapier webhook trigger
* **Custom API**: Use your own endpoint that accepts JSON POST requests

== Support ==

For support, feature requests, or bug reports, please visit our support forum or contact us directly.

== Privacy Policy ==

This plugin:
- Stores form submissions in your WordPress database
- Sends form data to your configured webhook endpoint
- Does not send data to any third-party services without your explicit configuration
- Includes user IP addresses for spam prevention (can be disabled)
