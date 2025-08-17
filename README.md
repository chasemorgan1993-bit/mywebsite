# TheMerchantGuide

> The smart way for small retailers, e-commerce startups, and regional businesses to find payment processors that actually fit their needs and budget.

## 🚀 Live Site

Visit [themerchantguide.com](https://themerchantguide.com) to use the payment processor finder tool.

## 📋 Features

- **Payment Processor Finder Tool** - Interactive form to get personalized processor recommendations
- **Fee Calculator** - Compare costs across different payment processors
- **Educational Blog** - Insights and guides for choosing payment solutions
- **Podcast Section** - Interviews with small business owners (coming soon)
- **Resource Center** - Tools and guides for payment processing decisions

## 🛠️ Technology Stack

- **Hugo** v0.148.2 - Static site generator
- **HTML/CSS/JavaScript** - Frontend
- **Netlify** - Hosting and deployment
- **GitHub** - Version control

## 🏗️ Local Development

### Prerequisites
- Hugo v0.148.2 or later
- Git

### Setup
```bash
# Clone the repository
git clone https://github.com/yourusername/themerchantguide.git
cd themerchantguide

# Start the development server
hugo server

# Open http://localhost:1313
```

### File Structure
```
themerchantguide/
├── content/
│   ├── blog/           # Blog posts
│   ├── podcasts/       # Podcast episodes
│   └── resources/      # Resource pages
├── layouts/
│   ├── _default/       # Default templates
│   ├── shortcodes/     # Reusable components
│   └── index.html      # Homepage template
├── static/
│   └── css/           # CSS files
├── hugo.toml          # Site configuration
└── netlify.toml       # Deployment configuration
```

## 🎨 Design System

The site uses a cohesive green color system:
- **Primary Green**: `#7ED957` - Main CTAs and highlights
- **Light Green**: `#ACE1AF` - Borders and accents
- **Text Colors**: `#36454F` - Primary text
- **Backgrounds**: `#F5F5DC` - Card backgrounds

CSS variables are defined in `static/css/variables.css` for consistent theming.

## 📝 Content Management

### Adding Blog Posts
Create new files in `content/blog/` with frontmatter:

```yaml
---
title: "Your Post Title"
date: 2024-08-17
description: "Post description"
tags: ["payment processing", "small business"]
---

Your content here...
```

### Adding Resources
Create new files in `content/resources/` following the same pattern.

## 🚀 Deployment

The site automatically deploys to Netlify when changes are pushed to the main branch.

### Manual Deployment
```bash
# Build the site
hugo --gc --minify

# Deploy the /public folder to your hosting provider
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact

For questions about payment processing or the site, visit [themerchantguide.com](https://themerchantguide.com) or use the contact form.