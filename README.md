# Suparank Connector for WordPress

Connect your WordPress site to [Suparank](https://suparank.io) for AI-powered content publishing. This plugin enables seamless integration with the Suparank MCP (Model Context Protocol) for automated blog post creation.

## Features

- **Secure API Authentication** - Token-based authentication with WordPress-generated secret keys
- **Direct Publishing** - Publish AI-generated content directly from Claude, Cursor, or ChatGPT
- **Category & Tag Support** - Automatic category and tag assignment
- **Featured Images** - Upload and set featured images from URLs
- **Author Selection** - Choose which WordPress user to attribute posts to
- **Draft or Publish** - Control publication status

## Requirements

- WordPress 5.0 or higher
- PHP 7.4 or higher
- Suparank account with MCP configured

## Installation

### From GitHub

1. Download the latest release from [Releases](https://github.com/Suparank/Suparank-WordPress-Plugin/releases)
2. Upload to `/wp-content/plugins/suparank-connector/`
3. Activate through the WordPress admin panel
4. Go to **Settings > Suparank Connector**

### Manual Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/Suparank/Suparank-WordPress-Plugin.git
   ```
2. Copy to your WordPress plugins directory:
   ```bash
   cp -r Suparank-WordPress-Plugin /path/to/wordpress/wp-content/plugins/suparank-connector
   ```
3. Activate and configure in WordPress admin

## Configuration

1. Navigate to **Settings > Suparank** in your WordPress admin
2. Copy the generated **Secret Key**
3. Configure Suparank MCP with the interactive wizard:

   ```bash
   npx suparank secrets
   ```

   Select **WordPress Publishing** and enter your site URL and secret key.

   Or add manually to `~/.suparank/credentials.json`:

   ```json
   {
     "wordpress": {
       "site_url": "https://your-site.com",
       "secret_key": "your-secret-key-here"
     }
   }
   ```

4. Test the connection using the **Test Connection** button in WordPress or run `npx suparank test`

## API Endpoints

The plugin exposes these REST API endpoints:

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/wp-json/suparank/v1/publish` | POST | Create/publish a post |
| `/wp-json/suparank/v1/categories` | GET | List available categories |
| `/wp-json/suparank/v1/tags` | GET | List available tags |
| `/wp-json/suparank/v1/authors` | GET | List available authors |
| `/wp-json/suparank/v1/ping` | GET | Test connection |

### Authentication

All requests require the `X-Suparank-Key` header:

```bash
curl -X POST https://your-site.com/wp-json/suparank/v1/publish \
  -H "X-Suparank-Key: your-secret-key" \
  -H "Content-Type: application/json" \
  -d '{"title": "My Post", "content": "Post content..."}'
```

### Publish Endpoint

**Request Body:**

```json
{
  "title": "Post Title",
  "content": "Post content in HTML or Markdown",
  "status": "draft",
  "categories": ["Technology", "AI"],
  "tags": ["suparank", "automation"],
  "featured_image_url": "https://example.com/image.jpg",
  "author_id": 1
}
```

**Response:**

```json
{
  "success": true,
  "post_id": 123,
  "url": "https://your-site.com/my-post/",
  "edit_url": "https://your-site.com/wp-admin/post.php?post=123&action=edit"
}
```

## Security

- **Timing-safe key comparison** - Prevents timing attacks on authentication
- **Nonce verification** - AJAX operations use WordPress nonces
- **Capability checks** - Only administrators can manage settings
- **No sensitive data exposure** - Secret keys are never exposed in client-side code

## Troubleshooting

### "Authentication failed"

- Verify the secret key matches exactly
- Check that the plugin is activated
- Ensure your site URL is correct (with or without trailing slash)

### "Connection test failed"

- Check your WordPress site is accessible
- Verify REST API is not blocked by security plugins
- Test the ping endpoint directly: `https://your-site.com/wp-json/suparank/v1/ping`

### "Categories/tags not found"

- Categories and tags are created automatically if they don't exist
- Ensure the authenticated user has permission to create terms

## Development

### Building

No build step required. The plugin is pure PHP.

### Testing

```bash
# Test connection
curl https://your-site.com/wp-json/suparank/v1/ping \
  -H "X-Suparank-Key: your-secret-key"

# Expected response
{"success":true,"message":"Pong! Connection successful.","version":"1.0.0"}
```

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

## Support

- **Documentation:** [suparank.io/docs/wordpress](https://suparank.io/docs/wordpress)
- **Issues:** [GitHub Issues](https://github.com/Suparank/Suparank-WordPress-Plugin/issues)
- **Email:** hello@suparank.io

## License

MIT License - see [LICENSE](LICENSE) for details.

## Related

- [Suparank MCP](https://github.com/Suparank/Suparank-MCP) - Main MCP package (`npx suparank`)
- [Suparank](https://suparank.io) - AI-powered SEO content platform
