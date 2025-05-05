# Azure Web App

A modern ASP.NET Core web application designed for deployment to Azure using GitHub Actions.

## Features

- ASP.NET Core 8.0
- Razor Pages
- Azure AD Authentication
- Application Insights Integration
- HTTPS Support
- GitHub Actions CI/CD

## Prerequisites

- .NET 8.0 SDK
- Azure Subscription
- GitHub Account
- Azure CLI (for local development)

## Project Structure

```
AzureWebApp/
├── .github/
│   └── workflows/
│       └── dotnet.yml          # GitHub Actions workflow
├── infrastructure/
│   └── main.bicep             # Azure Bicep template
├── Pages/
│   ├── Index.cshtml           # Home page
│   ├── Index.cshtml.cs        # Home page code-behind
│   ├── _Layout.cshtml         # Layout template
│   └── _ViewStart.cshtml      # View start template
├── Program.cs                 # Application entry point
├── appsettings.json          # Application configuration
├── AzureWebApp.csproj        # Project file
└── .gitignore               # Git ignore rules
```

## Configuration

1. Update `appsettings.json` with your Azure Application Insights connection string:
   ```json
   {
     "ApplicationInsights": {
       "ConnectionString": "YOUR_APPLICATION_INSIGHTS_CONNECTION_STRING"
     }
   }
   ```

2. Configure Azure AD authentication in the Azure portal and update the application settings.

## Deployment

The application is configured for automatic deployment to Azure using GitHub Actions. The workflow will:

1. Build the application
2. Run tests (if any)
3. Deploy to Azure Web App
4. Configure Application Insights
5. Set up Azure AD authentication

### Manual Deployment

If you need to deploy manually:

1. Build the application:
   ```bash
   dotnet build
   ```

2. Deploy to Azure:
   ```bash
   az webapp up --name <your-app-name> --resource-group <your-resource-group>
   ```

## Development

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd AzureWebApp
   ```

2. Restore dependencies:
   ```bash
   dotnet restore
   ```

3. Run the application:
   ```bash
   dotnet run
   ```

The application will be available at:
- HTTP: http://localhost:5000
- HTTPS: https://localhost:5001

## Azure Resources

The application requires the following Azure resources:

- Azure Web App
- Application Insights
- Azure AD Application Registration
- Key Vault (for secrets)

These resources are defined in the Bicep template in the `infrastructure` directory.

## Security

- HTTPS is enforced in production
- Azure AD authentication is required
- Application Insights for monitoring and security insights
- Secrets are stored in Azure Key Vault

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request
