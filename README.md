# Visor Selector WordPress Plugin

A comprehensive WordPress plugin for WooCommerce that provides an interactive visor selection interface with dynamic pricing, extras options, and seamless cart integration.

## Features

### 🎯 **Interactive Product Selection**
- **Dynamic Make/Model Selection**: Choose from helmet manufacturers and models
- **Pack Type Options**: Full Pack or Insert Only configurations
- **Battery Color Selection**: Multiple color options for battery packs
- **Real-time Price Updates**: Instant price calculation as options are selected

### 🛒 **Advanced Cart Integration**
- **Seamless WooCommerce Integration**: Native cart and checkout functionality
- **Custom Line Item Data**: Selected options display clearly in cart
- **Order Persistence**: Configuration saved to final orders and emails
- **Quantity Management**: Proper cart item merging for identical configurations

### 💰 **Flexible Pricing System**
- **Configurable Extra Pricing**: Admin-controlled pricing for extras
- **Dynamic Price Calculation**: Real-time frontend and backend price updates
- **Multiple Currency Support**: Works with WooCommerce currency settings

### 📱 **Responsive Design**
- **Mobile-First Approach**: Optimized for all device sizes
- **Touch-Friendly Interface**: Large buttons and easy navigation
- **Cross-Browser Compatibility**: Works on all modern browsers

## Installation

### Requirements
- WordPress 5.0 or higher
- WooCommerce 3.0 or higher
- PHP 7.4 or higher

### Installation Steps

1. **Upload Plugin Files**
   ```
   /wp-content/plugins/visorselection/
   ├── visor-selector.php
   ├── assets/
   │   ├── visor.js
   │   └── style.css
   └── README.md
   ```

2. **Activate Plugin**
   - Go to WordPress Admin → Plugins
   - Find "Visor Selector" and click "Activate"

3. **Configure Settings**
   - Navigate to WooCommerce → Visor Selector Settings
   - Set pricing for extras and configure options

## Usage

### Basic Implementation

Add the visor selector to any page or post using the shortcode:

```php
[visor_selector]
```

### Advanced Configuration

The plugin automatically integrates with your WooCommerce products. Ensure your products have the following attributes:
- `pa_helmet_make` (Helmet Make)
- `pa_helmet_model` (Helmet Model)  
- `pa_pack_type` (Pack Type)

## Configuration

### Admin Settings

Access settings via **WooCommerce → Visor Selector Settings**

#### Pricing Configuration
- **Extra Battery Price**: Set the additional cost for extra battery (default: £134.99)
- **Extra Insert Price**: Set the additional cost for extra insert (default: £194.99)
- **Enable Extra Insert**: Toggle extra insert option availability

#### General Settings
- **Admin Menu Location**: Choose where settings appear in admin menu
- **Integration Options**: Configure WooCommerce integration preferences

### Product Setup

1. **Create WooCommerce Products**
   - Set up products for each helmet make/model combination
   - Configure both "Full Pack" and "Insert Only" variants

2. **Add Product Attributes**
   ```
   Helmet Make: Shoei, Schuberth, AGV, etc.
   Helmet Model: GT-Air II, E2, K6, etc.
   Pack Type: Full Pack, Insert Only
   ```

3. **Set Product Prices**
   - Base prices for main products
   - Extra costs handled automatically by plugin

## Customization

### Styling

The plugin includes comprehensive CSS that can be customized:

```css
/* Main container */
#visor-selector {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
}

/* Customize button styles */
.make-button, .model-button {
    background: #f8f9fa;
    border: 2px solid #dee2e6;
    /* Add your custom styles */
}
```

### JavaScript Hooks

Extend functionality with custom JavaScript:

```javascript
// Access visor data
const visorData = window.visorData;

// Custom price calculation
document.addEventListener('visorPriceUpdated', function(event) {
    console.log('New price:', event.detail.price);
});
```

## API Reference

### Shortcode Parameters

```php
[visor_selector]
```

Currently, the shortcode doesn't accept parameters, but the plugin automatically detects and displays available products.

### PHP Functions

#### Get Plugin Settings
```php
$settings = hv_get_settings();
```

#### Get Extras Pricing
```php
$pricing = hv_get_extras_pricing();
// Returns: ['extra-battery' => 134.99, 'extra-insert' => 194.99]
```

#### Get Visor Products
```php
$products = hv_get_visor_products();
```

### WordPress Hooks

#### Filters
```php
// Modify cart item data display
add_filter('woocommerce_get_item_data', 'custom_cart_display', 10, 2);

// Modify extras pricing
add_filter('hv_extras_pricing', 'custom_extras_pricing');
```

#### Actions
```php
// Before price calculation
add_action('woocommerce_before_calculate_totals', 'custom_price_logic');

// After cart item added
add_action('woocommerce_add_to_cart', 'custom_cart_logic');
```

## Troubleshooting

### Common Issues

#### Products Not Displaying
- **Check Product Attributes**: Ensure products have required attributes
- **Verify Product Status**: Products must be published and in stock
- **Clear Cache**: Clear any caching plugins

#### Pricing Not Updating
- **Check Settings**: Verify extras pricing is configured
- **Browser Cache**: Clear browser cache and cookies
- **JavaScript Errors**: Check browser console for errors

#### Cart Integration Issues
- **WooCommerce Version**: Ensure WooCommerce is up to date
- **Theme Compatibility**: Test with default WordPress theme
- **Plugin Conflicts**: Deactivate other plugins to test

### Debug Mode

Enable WordPress debug mode for troubleshooting:

```php
// wp-config.php
define('WP_DEBUG', true);
define('WP_DEBUG_LOG', true);
```

Check `/wp-content/debug.log` for error messages.

## Browser Support

- **Chrome**: 70+
- **Firefox**: 65+
- **Safari**: 12+
- **Edge**: 79+
- **Mobile Browsers**: iOS Safari 12+, Chrome Mobile 70+

## Performance

### Optimization Features
- **Efficient AJAX**: Minimal server requests
- **Cached Product Data**: Optimized database queries
- **Minified Assets**: Compressed CSS and JavaScript
- **Mobile Optimized**: Fast loading on mobile devices

### Performance Tips
- Use caching plugins (WP Rocket, W3 Total Cache)
- Optimize images for product logos
- Enable GZIP compression
- Use a CDN for static assets

## Security

### Security Features
- **Nonce Verification**: All AJAX requests verified
- **Input Sanitization**: All user inputs sanitized
- **Capability Checks**: Admin functions protected
- **SQL Injection Prevention**: Prepared statements used

### Security Best Practices
- Keep WordPress and plugins updated
- Use strong admin passwords
- Limit admin access
- Regular security scans

## Changelog

### Version 1.3.0
- Added extra insert pricing configuration
- Improved cart item merging
- Enhanced mobile responsiveness
- Fixed JavaScript price calculation
- Cleaned up debug code

### Version 1.2.0
- Added battery color selection
- Implemented extras functionality
- Enhanced WooCommerce integration
- Improved admin settings

### Version 1.1.0
- Added dynamic pricing
- Improved product matching
- Enhanced user interface
- Bug fixes and optimizations

### Version 1.0.0
- Initial release
- Basic visor selection functionality
- WooCommerce integration
- Admin settings panel

## Support

For support and questions:
- **Documentation**: Refer to this README
- **WordPress Support**: Check WordPress.org forums
- **WooCommerce Issues**: Verify WooCommerce compatibility

## License

This plugin is licensed under the GPL v2 or later.

```
This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.
```

## Credits

Developed for heated visor selection and e-commerce integration.

---

**Plugin Version**: 1.3.0  
**WordPress Tested**: 6.4  
**WooCommerce Tested**: 8.0  
**PHP Minimum**: 7.4
