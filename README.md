<div align="center">
  <img src="logo.svg" alt="Source License Logo" width="400">
</div>

[![CodeQL Security Analysis](https://github.com/LyrinoxTechnologies/Source-License/actions/workflows/codeql.yml/badge.svg)](https://github.com/LyrinoxTechnologies/Source-License/actions/workflows/codeql.yml) [![Join our Discord](https://img.shields.io/badge/Discord-Join%20Server-7289DA?logo=discord&logoColor=white)](https://discord.gg/j6v99ZPkrQ)

# Source License - Professional Software Licensing Platform

> **ALPHA RELEASE:** Source License is currently in Alpha. While feature-complete for most use cases, you may encounter issues. Please report bugs via [GitHub Issues](https://github.com/LyrinoxTechnologies/Source-License/issues).

## [📱 Live Demo](https://source-license.onrender.com/) | [👨‍💼 Admin Demo](https://source-license.onrender.com/admin) | [📖 Documentation Wiki](https://github.com/LyrinoxTechnologies/Source-License/wiki)

A comprehensive Ruby/Sinatra-based software licensing management system with integrated payment processing, secure license validation APIs, and enterprise-grade features for independent software vendors.

## 📖 Complete Documentation

**All detailed documentation has been moved to the [Project Wiki](https://github.com/LyrinoxTechnologies/Source-License/wiki)**

- **[Installation Guide](https://github.com/LyrinoxTechnologies/Source-License/wiki/Installation-Guide)** - Complete setup instructions
- **[API Reference](https://github.com/LyrinoxTechnologies/Source-License/wiki/API-Reference)** - REST API documentation  
- **[Admin Guide](https://github.com/LyrinoxTechnologies/Source-License/wiki/Admin-Guide)** - Administrative documentation
- **[Architecture Overview](https://github.com/LyrinoxTechnologies/Source-License/wiki/Architecture-Overview)** - System design and components
- **[Development Guide](https://github.com/LyrinoxTechnologies/Source-License/wiki/Development-Guide)** - Contributing and development setup

## Overview

Source License is a complete solution for software vendors who need to sell, manage, and validate software licenses. Built with Ruby and Sinatra, it provides a robust platform for handling everything from product sales to license validation APIs that integrate directly into your software.

## 🌟 Key Features

### 💰 Complete E-Commerce Solution
- **Product Management**: Create and manage software products with pricing, descriptions, and download files
- **Shopping Cart & Checkout**: Full e-commerce flow with cart functionality and secure checkout
- **Payment Processing**: Integrated Stripe and PayPal support with webhook-first PayPal flow and signature verification
- **Order Management**: Complete order tracking and fulfillment system

### 🔐 Advanced License Management
- **Cryptographically Secure License Keys**: Multiple formats (XXXX-XXXX-XXXX-XXXX, UUID, custom)
- **Activation Control**: Limit installations per license with machine fingerprinting
- **License Types**: Support for perpetual, subscription, and trial licenses
- **License Operations**: Suspend, revoke, extend, transfer, and batch generate licenses
- **Validation API**: REST endpoints for real-time license verification in your software

### 👨‍💼 Comprehensive Admin Interface
- **Dashboard**: Real-time statistics and system overview
- **Product Management**: Create products with pricing, trial periods, and download files
- **License Administration**: Generate, manage, and monitor all licenses
- **Customer Management**: Track users, orders, and support requests
- **Order Processing**: View, manage, and fulfill customer orders
- **Reports & Analytics**: Detailed insights into sales and license usage

### 🎨 Customizable Frontend
- **Template System**: ERB templates with extensive helper functions
- **Live Customization**: Admin interface for colors, branding, and content
- **Responsive Design**: Bootstrap-based responsive layout
- **Multi-language Ready**: Template structure supports internationalization

### 🔒 Enterprise Security
- **JWT Authentication**: Secure API access with token-based auth
- **Admin Role Management**: Granular permissions and multi-admin support
- **Security Middleware**: CSRF protection, rate limiting, and security headers
- **Audit Logging**: Comprehensive logging of all license operations
- **Database Security**: Sequel ORM with prepared statements prevents SQL injection

### 🌐 REST API
- **License Validation**: Real-time license verification endpoints
- **License Activation**: Machine-based activation and deactivation
- **Order Processing**: Complete API for order creation and management
- **Webhook Support**: Stripe and PayPal webhook handling (PayPal uses verify-webhook-signature API for signature verification)
- **Settings Management**: API for configuration management

### 📊 Subscription Management
- **Recurring Billing**: Automatic subscription renewals
- **Grace Periods**: Handle failed payments gracefully
- **Trial Management**: Free trial periods with automatic conversion
- **Billing History**: Complete payment and billing tracking

## 🚀 Quick Start

### Prerequisites
- **Ruby 3.4.7** or higher  
- **Database**: MySQL, PostgreSQL, or SQLite (development only)
- **Git** for cloning the repository

### Installation

1. **Clone and install**
   ```bash
   git clone https://github.com/LyrinoxTechnologies/Source-License.git
   cd Source-License
   
   # Windows
   .\install.ps1 && .\deploy.ps1
   
   # Linux/macOS  
   ./install.sh && ./deploy.sh
   ```

2. **Access the application**
   - **Website**: http://localhost:4567
   - **Admin Panel**: http://localhost:4567/admin
   - **License Lookup**: http://localhost:4567/my-licenses

### Configuration

The installer creates a `.env` file from the template. Key settings to configure:

```env
# Database (choose one)
DATABASE_ADAPTER=mysql          # or postgresql, sqlite
DATABASE_HOST=localhost
DATABASE_NAME=source_license
DATABASE_USER=your_username
DATABASE_PASSWORD=your_password

# Security
APP_SECRET=your_secure_secret_key
JWT_SECRET=your_jwt_secret_key

# Payment Processing (optional)
STRIPE_PUBLISHABLE_KEY=pk_test_...
STRIPE_SECRET_KEY=sk_test_...
PAYPAL_CLIENT_ID=your_client_id
# Optional: set to 'true' to use webhook-first PayPal flow. When enabled, fulfillment occurs via verified webhooks.
PAYPAL_USE_WEBHOOKS=true
```

**📖 For complete installation instructions, database setup, and configuration options, see the [Installation Guide](https://github.com/LyrinoxTechnologies/Source-License/wiki/Installation-Guide).**

## 📁 Project Structure

Built with a modular Ruby/Sinatra architecture:

```
Source-License/
├── app.rb                    # Main application entry point
├── launch.rb                # Cross-platform launcher
├── lib/                     # Core application logic
│   ├── models.rb            # Database models
│   ├── controllers/         # Modular controllers
│   ├── auth.rb             # Authentication system
│   └── payment_processor.rb # Payment integration
├── views/                   # ERB templates  
├── test/                    # Test suite
└── .env.example            # Configuration template
```

**📖 For detailed architecture, database schema, and component documentation, see the [Architecture Overview](https://github.com/LyrinoxTechnologies/Source-License/wiki/Architecture-Overview).**

## 🔌 API Reference

### License Validation
```bash
curl -X GET http://localhost:4567/api/license/XXXX-XXXX-XXXX-XXXX/validate
```

### License Activation  
```bash
curl -X POST http://localhost:4567/api/license/XXXX-XXXX-XXXX-XXXX/activate \
  -d '{"machine_fingerprint": "unique_machine_id"}'
```

### Key Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth` | Get JWT authentication token |
| GET | `/api/license/:key/validate` | Validate license key |
| POST | `/api/license/:key/activate` | Activate license on machine |
| GET | `/api/products` | List available products |
| POST | `/api/orders` | Create new order |

**📖 For complete API documentation, authentication details, and code examples, see the [API Reference](https://github.com/LyrinoxTechnologies/Source-License/wiki/API-Reference).**

## 🎨 Customization & Development

- **Admin Panel Customization**: Live branding, colors, content editing
- **Template System**: ERB templates with extensive helper functions  
- **Development Setup**: `bundle install && ruby launch.rb`
- **Code Quality**: RuboCop style enforcement and auto-fixing
- **Production Deployment**: Automated scripts for Windows/Linux/macOS

**📖 For detailed customization guides, development setup, and deployment instructions, see the [Development Guide](https://github.com/LyrinoxTechnologies/Source-License/wiki/Development-Guide).**

## 📖 Use Cases

### Software Vendors
- Sell desktop applications with license management
- Distribute plugins and extensions with activation limits
- Manage trial periods and subscription renewals
- Track usage analytics and license compliance

### SaaS Applications
- License validation for client-side applications
- Machine-based activation for offline software
- Subscription management with automatic renewals
- Multi-tier licensing with different activation limits

### Educational Software
- Student/teacher license management
- Institution-wide licensing
- Temporary access and trial periods
- Bulk license generation for schools

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Check code style (`bundle exec rubocop`)
4. Commit your changes (`git commit -m 'Add amazing feature'`)
5. Push to the branch (`git push origin feature/amazing-feature`)
6. Open a Pull Request

## 📄 License

This project is licensed under the GNU General Public License v2.0 - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Issues**: [GitHub Issues](https://github.com/LyrinoxTechnologies/Source-License/issues)
- **Documentation**: [Project Wiki](https://github.com/LyrinoxTechnologies/Source-License/wiki)
- **Discussions**: [GitHub Discussions](https://github.com/LyrinoxTechnologies/Source-License/discussions)

## 📈 Roadmap

### Current Version (v1.0-ALPHA)
- ✅ Complete license management system
- ✅ Stripe and PayPal integration
- ✅ REST API with JWT authentication
- ✅ Admin dashboard and user management
- ✅ Cross-platform launcher
- ✅ Multiple database support

### Future Enhancements
- 🔄 Advanced analytics and reporting
- 🌐 Multi-language support
- 📱 Mobile-responsive admin interface
- 🔧 Plugin system for extensions
- 📊 Advanced subscription management
- 🌍 International payment methods

---

**Built with ❤️ using Ruby and Sinatra by the [Lyrinox Technologies team](https://lyrinox.com)**

*Source License - Empowering software vendors with professional licensing solutions*
