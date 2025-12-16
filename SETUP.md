# Setup Guide

This comprehensive guide covers everything you need to set up and deploy your Blazor WASM application.

## Table of Contents

1. [Initial GitHub Repository Setup](#initial-github-repository-setup)
2. [GitHub Pages Deployment](#github-pages-deployment)
3. [CI/CD Pipeline](#cicd-pipeline)
4. [Custom Domain Configuration](#custom-domain-configuration-optional)
5. [Troubleshooting](#troubleshooting)

---

## Initial GitHub Repository Setup

### Step 1: Create GitHub Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click the "+" icon in the top right corner
3. Select "New repository"
4. Name it `canidoyourdishes` (or your preferred name)
5. Choose **Public** or **Private** (your choice)
6. **DO NOT** initialize with README, .gitignore, or license (we already have these)
7. Click "Create repository"

### Step 2: Initialize Git and Push to GitHub

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

---

## GitHub Pages Deployment

### Step 1: Enable GitHub Pages

1. Go to your repository Settings on GitHub
2. Scroll down to "Pages" in the left sidebar
3. Under "Source", select **"GitHub Actions"** (not "Deploy from a branch")
4. Save the settings

### Step 2: Verify Deployment

1. Go to your repository on GitHub
2. Click on the "Actions" tab
3. You should see the workflow running (or completed)
4. Once the deployment completes, your site will be available at:
   - `https://YOUR_USERNAME.github.io/canidoyourdishes/`
   - Or check the workflow run for the exact URL

### Current Configuration

The project is configured to work with the default GitHub Pages URL:
- Base path: `/canidoyourdishes/`
- This matches the default GitHub Pages subpath format

---

## CI/CD Pipeline

### How It Works

The GitHub Actions workflow (`.github/workflows/ci-cd.yml`) automatically:

- **On every push/PR to `main`**: Builds and tests your Blazor WASM app
- **On pushes to `main` only**: Automatically deploys to GitHub Pages
- **On pull requests**: Only builds (no deployment)

### Workflow Steps

1. **Checkout code** - Gets your repository code
2. **Setup .NET** - Installs .NET 7.0 SDK
3. **Restore dependencies** - Downloads NuGet packages
4. **Build** - Compiles your Blazor WASM app
5. **Publish** - Creates the deployable output
6. **Upload artifacts** - Stores build output for deployment
7. **Deploy** - Publishes to GitHub Pages (only on main branch pushes)

### Updating the Workflow

- Edit `.github/workflows/ci-cd.yml`
- Commit and push changes
- GitHub Actions will automatically use the updated workflow

---

## Custom Domain Configuration (Optional)

When you're ready to use a custom domain (e.g., `www.canidoyourdishes.com`), follow these steps:

### Step 1: Purchase/Register Your Domain

You need to own the domain before you can configure it. Popular domain registrars include:
- **Namecheap** - Good prices, easy to use
- **Google Domains** - Simple interface
- **Cloudflare** - Free privacy protection
- **GoDaddy** - Widely used
- **Name.com** - Competitive pricing

### Step 2: Configure DNS Records

Once you own the domain, configure DNS records to point to GitHub Pages.

#### Option A: Using Apex Domain (canidoyourdishes.com - without www)

Add these **A records** in your domain's DNS settings:

```
Type: A
Name: @ (or leave blank, or use the root domain)
Value: 185.199.108.153
TTL: 3600 (or default)

Type: A
Name: @
Value: 185.199.109.153
TTL: 3600

Type: A
Name: @
Value: 185.199.110.153
TTL: 3600

Type: A
Name: @
Value: 185.199.111.153
TTL: 3600
```

#### Option B: Using www Subdomain (www.canidoyourdishes.com)

Add this **CNAME record**:

```
Type: CNAME
Name: www
Value: YOUR_USERNAME.github.io
TTL: 3600 (or default)
```

#### Option C: Both Apex and www (Recommended)

Configure both:
1. Add the 4 A records for the apex domain (canidoyourdishes.com)
2. Add the CNAME record for www (www.canidoyourdishes.com)

### Step 3: Update Code for Custom Domain

When using a custom domain at the root, you need to update the base path:

1. **Update `CanIDoYourDishes.csproj`**:
   ```xml
   <BasePath>/</BasePath>
   ```

2. **Update `wwwroot/index.html`**:
   ```html
   <base href="/" />
   ```

3. Commit and push the changes

### Step 4: Add Domain in GitHub Pages

1. Go to your repository Settings → Pages
2. In the "Custom domain" section, enter your domain:
   - For www: `www.canidoyourdishes.com`
   - For apex: `canidoyourdishes.com`
   - Or both (you can add both)
3. Click "Save"
4. GitHub will verify the DNS configuration (this can take a few minutes to 24 hours)

### Step 5: Enable HTTPS

Once DNS is verified:
1. GitHub will automatically provision an SSL certificate
2. Check the "Enforce HTTPS" checkbox
3. Your site will be available at `https://www.canidoyourdishes.com`

### DNS Propagation Notes

- DNS changes can take **5 minutes to 48 hours** to propagate globally
- You can check DNS propagation using tools like:
  - [whatsmydns.net](https://www.whatsmydns.net)
  - [dnschecker.org](https://dnschecker.org)

### Custom Domain Troubleshooting

**"DNS check unsuccessful" Error:**
- Wait: DNS propagation can take time
- Verify DNS records: Make sure A records or CNAME are correctly configured
- Check with your registrar: Some registrars have specific DNS management interfaces
- Use "Check again" button: GitHub will re-verify after you fix DNS

**HTTPS Not Available:**
- HTTPS is only available after DNS is properly configured
- Wait for GitHub to provision the SSL certificate (usually automatic)
- Make sure "Enforce HTTPS" is checked after DNS verification succeeds

**Site Not Loading:**
- Verify the base path in your code matches your domain setup
- Clear your browser cache
- Check that GitHub Pages deployment succeeded in the Actions tab

---

## Troubleshooting

### GitHub Actions Not Running?

- Make sure the workflow file is in `.github/workflows/ci-cd.yml`
- Check that you've pushed the file to GitHub
- Verify the branch name matches (should be `main`)

### Build Failing?

- Check the Actions tab for error details
- Ensure .NET 7.0 SDK is available (the workflow handles this)
- Verify all project files are committed
- Check that the project builds locally: `dotnet build`

### Deployment Not Working?

- Verify GitHub Pages is enabled with "GitHub Actions" as the source
- Check that the workflow completed successfully in the Actions tab
- Ensure you're pushing to the `main` branch (deployment only happens on main)
- Wait a few minutes for the site to become available

### Site Not Loading?

- Verify the base path matches your URL structure:
  - Default GitHub Pages: `/canidoyourdishes/`
  - Custom domain at root: `/`
- Clear your browser cache
- Check the browser console for errors
- Verify the deployment succeeded in GitHub Actions

### Need to Test Locally?

```bash
# Restore dependencies
dotnet restore

# Run the application
dotnet run

# Visit https://localhost:5001 or http://localhost:5000
```

---

## Next Steps

1. **Test locally**: Run `dotnet run` to verify everything works
2. **Customize content**: Edit `Pages/Index.razor` with your specific messaging
3. **Add more pages**: Create additional Razor components as needed
4. **Deploy**: Your site is already set up for automatic deployment!
5. **Custom domain**: When ready, follow the custom domain section above

---

## Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Blazor WebAssembly Documentation](https://learn.microsoft.com/en-us/aspnet/core/blazor/host-and-deploy/webassembly)
- [GitHub Pages Custom Domain Guide](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

