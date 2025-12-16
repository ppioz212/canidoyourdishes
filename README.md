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

## Setup and Deployment

For complete setup instructions, including GitHub repository setup, CI/CD configuration, and deployment, see **[SETUP.md](SETUP.md)**.

This project uses GitHub Actions for continuous integration and deployment:
- Builds the project on every push
- Automatically deploys to GitHub Pages on pushes to `main`
- Runs on pull requests for testing

The application is configured to work with the default GitHub Pages URL: `https://YOUR_USERNAME.github.io/canidoyourdishes/`

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

