# Meiro Server-Side GTM Template

## Overview

This README describes the Meiro template for server-side Google Tag Manager (SGTM). The template enables seamless data collection and transmission to Meiro, a Customer Data Platform (CDP), directly from your SGTM container.

## Features

- **Multiple Event Types Support**: Track page views, custom events, web banner interactions, form submissions, and outbound link clicks
- **Google Analytics 4 Integration**: Map GA4 parameters directly to Meiro's data structure
- **Flexible User Identification**: Multiple options for identifying users across sessions
- **Consent Management**: Full support for consent mode integration with Google and custom consent states
- **Custom Parameter Mapping**: Send additional custom parameters with every event
- **Ecommerce Support**: Ability to map Google Analytics 4 ecommerce data
- **Form Data Collection**: Comprehensive options for contact form submissions with multiple field types

## Setup Instructions

1. In your server-side GTM container, click **Templates** in the left navigation
2. Click **New** in the Tag Templates section
3. Click the three dots menu in the top right and select **Import**
4. Paste in the template code or select the template file
5. Save the template
6. Create a new tag using the Meiro template
7. Configure the endpoint URL and other settings as needed
8. Set appropriate triggers
9. Save and publish your container

## Configuration Options

### Basic Configuration

- **Endpoint URL Address**: The Meiro server address where events will be sent (e.g., `https://profile.meiro.com`)
- **Select Event Type**: Choose from supported event types (`page_view`, `custom_event`, `web_banner_click`, `web_banner_impression`, `contact_form_submit`, `outbound_link_click`)

### Event Type Details

Configuration options specific to the selected event type:

#### Page View Event
- **Custom Payload Parameters**: Key-value pairs to include in the payload
- **GA4 Mapping**: Option to map GA4 event parameters to Meiro payload
- **Parameters to Exclude**: GA4 parameters that should not be mapped

#### Custom Event
- **Custom Event Parameters**: Key-value pairs to include as custom event parameters
- **GA4 Event Mapping**: Option to map GA4 event parameters to Meiro custom event parameters
- **Parameters to Exclude**: GA4 parameters that should not be mapped

#### Web Banner Events
- **Web Banner ID**: Identifier for the banner being tracked
- **Destination ID** (click events only): Identifier for where the banner redirects to

#### Contact Form Submit
- **Default Form Fields**: Configure standard contact form fields (email, name, phone, etc.)
- **Custom Form Fields**: Add additional form fields with custom identifiers

#### Outbound Link Click
- **GA4 Outbound Link Mapping**: Use GA4's outbound link data
- **Custom Outbound Link URL**: Manually specify the outbound link URL

### Client Identification

Options for identifying users and sessions:

#### User ID Source
- **Meiro Browser User ID Cookie**: Use Meiro's native cookies
- **Convert GA4 Client ID**: Transform GA4 client ID into Meiro-compatible UUID
- **Hybrid**: Try Meiro cookie first, fallback to GA4
- **Manual Mapping**: Provide a custom User ID

#### Session ID Source
- **Meiro Browser Session ID Cookie**: Use Meiro's session cookies
- **Convert GA4 Session ID**: Use GA4's session identifier
- **Hybrid**: Try Meiro cookie first, fallback to GA4
- **Manual Mapping**: Provide a custom Session ID

#### External ID Source
- **GA4 User ID**: Use GA4's user identifier
- **Manual Mapping**: Provide a custom External ID

### Custom Overrides

Override specific page and browser information:

#### Page Details
- **Page Title**: Override the default page title
- **Page Location**: Override the default URL
- **Referrer**: Override the default referrer
- **IP Override**: Override the visitor's IP address

#### Browser Details
- **User-Agent String**: Override the browser's user agent
- **Browser Window Height/Width**: Override viewport dimensions
- **Browser Color Depth**: Override color depth information
- **Cookies Support**: Override browser cookie support status

### Consent Mode

Options for consent handling:

- **Map GA4 Consent Mode Parameters**: Automatically convert GA4 consent values
- **Custom Consent Status**: Manually set the consent status

## Supported Event Types

### Page View (`page_view`)
Tracks when a user views a page. Includes URL, page title, and referrer information.

### Custom Event (`custom_event`)
Tracks custom interactions defined by your implementation needs. Fully customizable with additional parameters.

### Web Banner Click (`web_banner_click`)
Tracks when users click on banner advertisements. Includes banner ID and destination URL.

### Web Banner Impression (`web_banner_impression`)
Tracks when banner advertisements are displayed to users. Includes banner ID.

### Contact Form Submit (`contact_form_submit`)
Tracks form submissions with comprehensive field mapping. Supports standard contact fields and custom fields.

### Outbound Link Click (`outbound_link_click`)
Tracks when users click links that lead to external websites.

## Technical Details

The template uses server-side technologies to:

- Generate unique identifiers compatible with Meiro's format
- Convert timestamps to ISO 8601 format
- Process cookies and local storage for user tracking
- Handle HTTP requests to Meiro's API
- Map data from GA4's event model to Meiro's data structure
- Process consent states

## Usage Examples

### Basic Page View Tracking

Configure a tag with:
- Event Type: `page_view`
- Endpoint URL: Your Meiro endpoint
- User ID Source: Hybrid (recommended)
- GA4 Mapping: Enabled

### E-commerce Transaction Tracking

Configure a tag with:
- Event Type: `custom_event`
- Endpoint URL: Your Meiro endpoint
- Custom Event Parameters:
  - event_name: purchase
  - currency: `{{Event.currency}}`
  - value: `{{Event.value}}`
- GA4 Event Mapping: Enabled

### Form Submission Tracking

Configure a tag with:
- Event Type: `contact_form_submit`
- Endpoint URL: Your Meiro endpoint
- Form ID: contact_form_homepage
- Form Fields: Configure to match your form field names

---

This template was created by Jakub Kriz at Optimics s.r.o. (jakub.kriz@optimics.cz)  
Template Version: 2024-04-05

For documentation on Meiro events, visit: [Meiro Events Documentation](https://docs.meiro.io/books/meiro-events/page/events-list-of-events)