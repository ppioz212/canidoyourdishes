# GitHub Repository Setup Guide

This guide will help you set up your GitHub repository and get your CI/CD pipeline running.

## Step 1: Create GitHub Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click the "+" icon in the top right corner
3. Select "New repository"
4. Name it `canidoyourdishes` (or your preferred name)
5. Choose **Public** or **Private** (your choice)
6. **DO NOT** initialize with README, .gitignore, or license (we already have these)
7. Click "Create repository"

## Step 2: Initialize Git and Push to GitHub

Run these commands in your project directory:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Blazor WASM baseline application"

# Add your GitHub repository as remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/canidoyourdishes.git

# Rename branch to main (if needed)
git branch -M main

# Push to GitHub
git push -u origin main
```

## Step 3: Enable GitHub Pages

1. Go to your repository Settings on GitHub
2. Scroll down to "Pages" in the left sidebar
3. Under "Source", select **"GitHub Actions"** (not "Deploy from a branch")
4. Save the settings

## Step 4: Verify GitHub Actions & Deployment

1. Go to your repository on GitHub
2. Click on the "Actions" tab
3. You should see the workflow running (or completed)
4. The workflow will:
   - Build your Blazor WASM app on every push and pull request
   - **Deploy to GitHub Pages** automatically on pushes to `main` branch
   - Create artifacts with the published files

5. Once the deployment completes, your site will be available at:
   - `https://YOUR_USERNAME.github.io/canidoyourdishes/`
   - Or check the workflow run for the exact URL

## Step 5: Custom Domain Setup (When Ready)

When you're ready to use your custom domain:

1. Purchase and configure your domain
2. In your repository Settings → Pages:
   - Add your custom domain
   - Follow GitHub's instructions for DNS configuration
3. GitHub will automatically handle HTTPS certificates

## Troubleshooting

### GitHub Actions not running?
- Make sure the workflow file is in `.github/workflows/ci-cd.yml`
- Check that you've pushed the file to GitHub
- Verify the branch name matches (main or master)

### Build failing?
- Check the Actions tab for error details
- Ensure .NET 8.0 SDK is available (the workflow handles this)
- Verify all project files are committed

### Need to update the workflow?
- Edit `.github/workflows/ci-cd.yml`
- Commit and push changes
- GitHub Actions will automatically use the updated workflow

## Next Steps

1. **Test locally**: Run `dotnet run` to verify everything works
2. **Customize content**: Edit `Pages/Index.razor` with your specific messaging
3. **Add more pages**: Create additional Razor components as needed
4. **Deploy**: When ready, enable GitHub Pages or deploy to your preferred hosting service

