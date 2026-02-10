# Development Guide - GHANBATT2 Website

## Page 1: Development Environment Setup

### Prerequisites
- **Text Editor**: VS Code, Sublime Text, or similar
- **Git**: Latest version installed
- **GitHub Account**: For version control
- **Modern Browser**: For testing
- **Local Server**: Optional (Live Server extension)

### Initial Setup
```bash
# Clone the repository
git clone https://github.com/Pamac05/GHANBATT2_New.git

# Navigate to project directory
cd GHANBATT2_New

# Create development branch
git checkout -b development

# Install Live Server (VS Code)
# Extension ID: ritwickdey.LiveServer
```

### Development Workflow
1. **Create feature branch**: `git checkout -b feature-name`
2. **Make changes**: Edit files locally
3. **Test changes**: Use Live Server for preview
4. **Commit changes**: `git add . && git commit -m "Description"`
5. **Push to GitHub**: `git push origin feature-name`
6. **Create Pull Request**: For code review

## Page 2: Project Structure Deep Dive

### Directory Organization
```
GHANBATT2_New/
├── .git/                  # Version control
├── .gitignore            # Git ignore rules
├── .nojekyll             # GitHub Pages config
├── index.html            # Homepage
├── mission.html          # Mission page
├── operations.html       # Operations page
├── gallery.html          # Photo gallery
├── contact.html          # Contact page
├── CSS/
│   └── Style.css         # Main stylesheet
├── images/               # Original images
├── images_compressed/    # Optimized images
├── docs/                 # Documentation (new)
│   ├── GHANBATT2_Documentation.md
│   ├── Technical_Specifications.md
│   ├── User_Manual.md
│   └── Development_Guide.md
└── scripts/              # Utility scripts (new)
    ├── compress_images.ps1
    └── deploy.sh
```

### File Naming Conventions
- **HTML Files**: Lowercase, hyphen-separated
- **CSS Files**: Lowercase, descriptive names
- **Images**: Descriptive names, spaces replaced with underscores
- **Documentation**: Title case with underscores

## Page 3: HTML Development Standards

### Document Structure Template
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <meta name="description" content="[Page-specific description]">
    <meta name="author" content="Azure Michael">
    <title>GHANBATT Abyei - [Page Title]</title>
    <link rel="stylesheet" href="CSS/Style.css">
    <!-- Additional head elements -->
</head>
<body>
    <!-- Navigation (consistent across pages) -->
    <nav class="navbar">
        <!-- Navigation content -->
    </nav>
    
    <!-- Page-specific content -->
    <main>
        <!-- Main content area -->
    </main>
    
    <!-- Footer (consistent across pages) -->
    <footer>
        <!-- Footer content -->
    </footer>
</body>
</html>
```

### Semantic HTML Guidelines
- Use `<header>` for page headers
- Use `<nav>` for navigation menus
- Use `<main>` for primary content
- Use `<section>` for content sections
- Use `<article>` for standalone content
- Use `<aside>` for sidebar content
- Use `<footer>` for page footers

## Page 4: CSS Development Standards

### CSS Architecture
```css
/* CSS Reset and Base Styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* CSS Variables */
:root {
    --primary-color: #1e3c72;
    --secondary-color: #2a5298;
    --accent-color: #ffd700;
    --text-color: #333333;
    --background-color: #ffffff;
}

/* Base Styles */
body {
    font-family: 'Arial', sans-serif;
    line-height: 1.6;
    color: var(--text-color);
}

/* Component Styles */
.navbar {
    /* Navigation styles */
}

.hero {
    /* Hero section styles */
}

/* Utility Classes */
.container {
    max-width: 1170px;
    margin: 0 auto;
    padding: 0 15px;
}

/* Responsive Design */
@media (max-width: 768px) {
    /* Mobile styles */
}
```

### CSS Naming Conventions
- **BEM Methodology**: Block__Element--Modifier
- **Hyphen Separation**: class-name-format
- **Descriptive Names**: Clear, meaningful class names
- **Consistent Pattern**: Follow established patterns

## Page 5: Image Management

### Image Optimization Workflow
```powershell
# Standard compression (75% quality)
$quality = 75
$outputFolder = "images_compressed"

# Aggressive compression (50% quality)
$quality = 50
$outputFolder = "images_compressed_aggressive"
```

### Image Naming Guidelines
- **Descriptive Names**: mission-operation.jpg
- **No Spaces**: Use underscores or hyphens
- **Lowercase**: Consistent lowercase naming
- **Date Inclusion**: operation-2024-02-10.jpg

### Image Formats
- **JPEG**: Photographs and complex images
- **PNG**: Simple graphics with transparency
- **WebP**: Modern browsers (future enhancement)
- **SVG**: Icons and simple graphics

## Page 6: Version Control Best Practices

### Git Workflow
```bash
# Feature development workflow
git checkout -b feature/new-page
# Make changes
git add .
git commit -m "feat: Add new page with responsive design"
git push origin feature/new-page
# Create pull request
```

### Commit Message Standards
- **feat**: New feature
- **fix**: Bug fix
- **docs**: Documentation changes
- **style**: Code style changes
- **refactor**: Code refactoring
- **test**: Test additions
- **chore**: Maintenance tasks

### Branch Strategy
- **main**: Production-ready code
- **develop**: Integration branch
- **feature/***: Feature development
- **hotfix/***: Critical fixes
- **release/***: Release preparation

## Page 7: Testing Methodology

### Manual Testing Checklist
```markdown
## Functionality Testing
- [ ] All navigation links work
- [ ] Images load correctly
- [ ] Forms validate properly
- [ ] Contact form submission
- [ ] Gallery functionality

## Responsive Testing
- [ ] Desktop (1920x1080)
- [ ] Tablet (768x1024)
- [ ] Mobile (375x667)
- [ ] Landscape orientation

## Browser Testing
- [ ] Chrome (latest)
- [ ] Firefox (latest)
- [ ] Safari (latest)
- [ ] Edge (latest)

## Performance Testing
- [ ] Page load time < 5 seconds
- [ ] Image optimization verified
- [ ] No console errors
- [ ] Mobile performance acceptable
```

### Automated Testing Setup
```javascript
// Example: Basic automated tests
describe('GHANBATT2 Website', () => {
    test('Homepage loads correctly', () => {
        cy.visit('/');
        cy.contains('GHANAIAN BATTALION IN ABYEI');
    });
    
    test('Navigation works', () => {
        cy.get('.nav-menu a').each(link => {
            cy.wrap(link).click();
            cy.url().should('include', link.attr('href'));
        });
    });
});
```

## Page 8: Deployment Process

### GitHub Pages Deployment
```bash
# Deploy to GitHub Pages
git checkout main
git merge develop
git checkout gh-pages
git merge main
git push origin gh-pages
```

### Deployment Script
```bash
#!/bin/bash
# deploy.sh - Automated deployment script

echo "Starting deployment process..."

# Switch to main branch
git checkout main

# Pull latest changes
git pull origin main

# Update gh-pages branch
git checkout gh-pages
git merge main

# Push to GitHub Pages
git push origin gh-pages

echo "Deployment complete!"
echo "Website available at: https://pamac05.github.io/GHANBATT2_New/"
```

### Pre-deployment Checklist
- [ ] All tests pass
- [ ] Images optimized
- [ ] Links verified
- [ ] Mobile responsive
- [ ] SEO meta tags updated
- [ ] Documentation updated

## Page 9: Performance Optimization

### Image Optimization Techniques
```powershell
# Batch image compression script
Add-Type -AssemblyName System.Drawing

function Compress-Image {
    param(
        [string]$InputPath,
        [string]$OutputPath,
        [int]$Quality = 75
    )
    
    $image = [System.Drawing.Image]::FromFile($InputPath)
    $jpegCodec = [System.Drawing.Imaging.ImageCodecInfo]::GetImageEncoders() | 
                Where-Object { $_.MimeType -eq "image/jpeg" }
    
    $encoderParams = New-Object System.Drawing.Imaging.EncoderParameters(1)
    $encoderParams.Param[0] = New-Object System.Drawing.Imaging.EncoderParameter(
        [System.Drawing.Imaging.Encoder]::Quality, $Quality)
    
    $image.Save($OutputPath, $jpegCodec, $encoderParams)
    $image.Dispose()
}
```

### CSS Optimization
```css
/* Minified CSS example */
.navbar{background:linear-gradient(135deg,#1e3c72 0%,#2a5298 100%);padding:1rem 0;position:fixed;width:100%;top:0;z-index:1000}
.hero{background:linear-gradient(rgba(0,0,0,0.5),rgba(0,0,0,0.5)),url('../images/mission.jpg') center/cover;height:100vh;display:flex;align-items:center;justify-content:center;text-align:center;color:white}
```

### HTML Optimization
```html
<!-- Optimized HTML structure -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <title>GHANBATT Abyei - Home</title>
    <link rel="stylesheet" href="CSS/Style.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
</head>
<body>
    <!-- Content -->
</body>
</html>
```

## Page 10: Future Development Roadmap

### Phase 1: Enhanced Features (Q2 2026)
- [ ] Interactive map integration
- [ ] Video gallery support
- [ ] Advanced search functionality
- [ ] Multi-language support (French, Arabic)

### Phase 2: Technical Improvements (Q3 2026)
- [ ] Progressive Web App (PWA) features
- [ ] Service worker implementation
- [ ] WebP image format support
- [ ] CSS Grid layout improvements

### Phase 3: Advanced Functionality (Q4 2026)
- [ ] Content management system
- [ ] User authentication system
- [ ] Real-time updates
- [ ] Mobile app development

### Technology Stack Evolution
```
Current Stack:
├── HTML5
├── CSS3
├── Vanilla JavaScript
└── GitHub Pages

Future Stack:
├── HTML5
├── CSS3 + CSS Grid
├── JavaScript Framework (Vue.js/React)
├── Node.js Backend
├── Database (MongoDB/PostgreSQL)
└── Cloud Hosting (AWS/Azure)
```

---

**Guide Version**: 1.0  
**Last Updated**: February 2026  
**Next Review**: May 2026

For development support, create an issue in the GitHub repository or contact the development team.
