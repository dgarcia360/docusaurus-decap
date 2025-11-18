# Docusaurus + Decap CMS Integration

This project demonstrates how to integrate Decap CMS (formerly Netlify CMS) with Docusaurus for content management.

## Setup

### Prerequisites

- **Node.js 20+** (required - Node 18 will fail with "ReferenceError: File is not defined")
- Sign up for GitHub and Netlify
- Install the GitHub CLI
- Install and authenticate the Netlify CLI

**Important:** This project requires Node.js 20+ due to dependencies that use the `File` API. If you encounter "ReferenceError: File is not defined", upgrade Node.js using `nvm install 20 && nvm use 20`.

### Local Development

1. Install dependencies:
```bash
npm install
```

2. Start the development server:
```bash
npm start
```

3. Access the admin interface:
   - Visit `http://localhost:3000/admin` to access Decap CMS

### Deployment

1. Push your project to GitHub:
```bash
git init
git branch -m main
git add .
git commit -m 'Initial commit'
gh repo create docusaurus-decap
git push -u origin main
```

2. Publish using Netlify CLI:
```bash
netlify init
```
   - Choose "Create & configure a new site"
   - Choose your team and site name
   - Choose `yarn build` for your build command
   - Choose `build` for your deployment directory

### GitHub Authentication Setup

To access `/admin/` through your Netlify domain, you need to set up GitHub as an authentication provider:

1. **Configure GitHub:**
   - Create a new GitHub OAuth application
   - Enter your Netlify domain as the Homepage URL
   - Enter `https://api.netlify.com/auth/done` as the Authorization callback URL
   - Click "Register application"
   - Click "Generate a new client secret"
   - Copy the provided client secret and client ID

2. **Configure Netlify:**
   - On Netlify, go to Site configuration > Access & security > OAuth > Authentication providers
   - Click "Install provider"
   - Enter your client secret and client ID from GitHub
   - Click "Install"

## Configuration

- Admin interface: `static/admin/index.html`
- Decap CMS config: `static/admin/config.yml`
- Update the `repo` field in `config.yml` with your GitHub username/repo

## Features

- Visual editing of blog posts
- GitHub-backed content storage
- Netlify integration for deployment
- Markdown support with frontmatter

## Notes

- Any changes published through the admin interface will only affect your remote GitHub repository
- To retrieve changes locally, run `git pull` from your local repository
- The blog collection is configured to create posts with the format: `YYYY-MM-DD-slug.md`
