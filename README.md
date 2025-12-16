# Can I Do Your Dishes?

A Blazor WebAssembly application explaining why I want to help young families with their dishes and chores.

## About

This website serves as a platform to explain my mission of supporting young families by taking care of their dishes and household chores, giving them back precious time to spend with their loved ones.

## Technology Stack

- **.NET 7.0** - Modern .NET framework
- **Blazor WebAssembly** - Client-side web framework using C# and Razor
- **GitHub Actions** - CI/CD pipeline for automated builds and deployments

## Getting Started

### Prerequisites

- [.NET 7.0 SDK](https://dotnet.microsoft.com/download/dotnet/7.0) or later

### Running Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/canidoyourdishes.git
   cd canidoyourdishes
   ```

2. Restore dependencies:
   ```bash
   dotnet restore
   ```

3. Run the application:
   ```bash
   dotnet run
   ```

4. Open your browser and navigate to `https://localhost:5001` or `http://localhost:5000`

### Building for Production

```bash
dotnet publish -c Release
```

The output will be in the `bin/Release/net7.0/publish/wwwroot` directory, ready for deployment to any static hosting service.

## CI/CD

This project uses GitHub Actions for continuous integration and deployment. The workflow:

- Builds the project on every push
- Runs on pull requests
- Publishes the Blazor WASM app as static files
- Can be configured to deploy to various hosting platforms (GitHub Pages, Azure Static Web Apps, etc.)

See `.github/workflows/ci-cd.yml` for the complete workflow configuration.

## Deployment

The application can be deployed to any static hosting service that supports static websites:

- **GitHub Pages** - Free hosting for public repositories
- **Azure Static Web Apps** - Integrated with GitHub Actions
- **Netlify** - Easy deployment with drag-and-drop
- **Vercel** - Fast global CDN
- **Any web server** - Just upload the `wwwroot` folder contents

## Project Structure

```
canidoyourdishes/
├── Pages/              # Blazor pages/components
├── Shared/             # Shared components (layouts, nav menu)
├── wwwroot/            # Static files (CSS, HTML, images)
├── Properties/         # Launch settings
├── .github/            # GitHub Actions workflows
└── CanIDoYourDishes.csproj
```

## License

This project is private and personal.

## Contact

For questions or inquiries, please reach out through the contact information on the website.

