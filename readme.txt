=== Suparank Connector ===
Contributors: suparank
Tags: ai, content, publishing, automation, seo
Requires at least: 5.0
Tested up to: 6.4
Requires PHP: 7.4
Stable tag: 1.0.0
License: MIT
License URI: https://opensource.org/licenses/MIT

Connect your WordPress site to Suparank for AI-powered content publishing via MCP (Model Context Protocol).

== Description ==

Suparank Connector enables seamless integration between your WordPress site and the Suparank AI content platform. Publish AI-generated blog posts directly from Claude, Cursor, ChatGPT, or any MCP-compatible AI assistant.

**Key Features:**

* **Secure API Authentication** - Token-based authentication with WordPress-generated secret keys
* **Direct Publishing** - Publish content directly from your AI assistant
* **Category & Tag Support** - Automatic category and tag assignment
* **Featured Images** - Upload and set featured images from URLs
* **Author Selection** - Attribute posts to any WordPress user
* **Draft or Publish** - Full control over publication status

**How It Works:**

1. Install and activate the plugin
2. Copy your secret key from Settings > Suparank Connector
3. Add the key to your Suparank MCP configuration
4. Start publishing from your AI assistant!

**Requirements:**

* Suparank account ([suparank.io](https://suparank.io))
* Suparank MCP installed (`npx suparank`)

== Installation ==

1. Upload the `suparank-connector` folder to `/wp-content/plugins/`
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Go to Settings > Suparank Connector
4. Copy your secret key
5. Add to your Suparank MCP credentials using `npx suparank credentials`

== Frequently Asked Questions ==

= What is Suparank? =

Suparank is an AI-powered SEO content platform that helps you create and publish blog posts using AI assistants like Claude, ChatGPT, and Cursor.

= What is MCP? =

MCP (Model Context Protocol) is a standard for connecting AI assistants to external tools and services. Suparank uses MCP to publish content to your WordPress site.

= Is my secret key secure? =

Yes. Your secret key is stored securely in your WordPress database and is never exposed to the client side. All API requests use timing-safe comparison to prevent attacks.

= Can I publish as different authors? =

Yes. The API supports specifying an author ID, allowing you to attribute posts to any user on your WordPress site.

= What if a category doesn't exist? =

Categories and tags are created automatically if they don't exist when publishing a post.

== Screenshots ==

1. Settings page with secret key and connection test
2. Publishing a post via Suparank MCP

== Changelog ==

= 1.0.0 =
* Initial release
* Secure API authentication
* Post publishing with categories, tags, and featured images
* Author selection support
* Connection testing
* WordPress admin settings page

== Upgrade Notice ==

= 1.0.0 =
Initial release of Suparank Connector.

== Privacy Policy ==

This plugin does not collect any personal data. It only exposes REST API endpoints for authenticated requests from Suparank MCP.

== Support ==

For support, please visit [suparank.io/docs](https://suparank.io/docs) or open an issue on [GitHub](https://github.com/Suparank/Suparank-WordPress-Plugin/issues).
