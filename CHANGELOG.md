# Changelog

All notable changes to the Suparank Connector plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-01-08

### Added
- Initial release
- Secure API authentication with secret key
- REST API endpoints:
  - `POST /suparank/v1/publish` - Create and publish posts
  - `GET /suparank/v1/categories` - List available categories
  - `GET /suparank/v1/tags` - List available tags
  - `GET /suparank/v1/authors` - List available authors
  - `GET /suparank/v1/ping` - Test connection
- Featured image support via URL upload
- Automatic category and tag creation
- Author selection for posts
- Draft and publish status support
- WordPress admin settings page
- Connection testing from admin
- Secret key regeneration
- Timing-safe authentication comparison
- Legacy endpoint support for backward compatibility

### Security
- Timing-safe key comparison to prevent timing attacks
- Nonce verification for AJAX operations
- Capability checks for admin operations
- No sensitive data exposed to client-side

[1.0.0]: https://github.com/Suparank/Suparank-WordPress-Plugin/releases/tag/v1.0.0
