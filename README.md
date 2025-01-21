
# **eShopio Reference Application**  

## **Overview**  
A reference **.NET application** implementing an **e-commerce website** using a **services-based architecture** built with **.NET** and following best practices in modern software development.

---

## **Key Features**  
- **Scalable and Modular Design**: Built for an e-commerce platform with extensibility in mind.  
- **Secure Transactions**: Implements DevSecOps practices to ensure security at every stage of development.  
- **Microservices Architecture**: Handles product catalogs, user management, and order processing as separate services.  
- **Cloud Deployment Ready**: Supports deployment to cloud platforms for scalability and high availability.  
- **REST APIs**: Provides extensibility and integration with external systems.  
- **User-Friendly Interface**: Prioritizes a clean, intuitive, and responsive UI for the best user experience.  

---

## **Technologies Used**  
- **.NET Core**: Backend application framework.  
- **ASP.NET MVC**: For building the web application layer.  
- **Entity Framework Core**: For database management and operations.  
- **Docker**: Containerization for seamless deployment.  
- **Azure/AWS**: For cloud hosting and scalability.  
- **CI/CD Pipeline**: Integrated with GitHub Actions for automated builds, tests, and deployments.

--- 
![eShopio_architecture](https://github.com/user-attachments/assets/2a8d623b-4d1f-4796-9b0a-b1fd4e02611d)



## Getting Started with eShopio

This version of eShopio is built on **.NET 9**. Below are the streamlined steps to set up and run the application effectively.

---

### Previous Versions
- [.NET 8 eShopio Version](https://github.com/dotnet/eshop)

---

### Prerequisites
1. **Clone the Repository**
   ```bash
   git clone https://github.com/dotnet/eShopio
   ```

2. **Install and Start Docker Desktop**
   Ensure Docker Desktop is running for container-based services.

---

### Setup for Windows with Visual Studio
#### Option 1: Manual Setup
1. Install **Visual Studio 2022 (v17.10 or newer)**.
2. Select the following workloads during installation:
   - **ASP.NET and Web Development**
   - **.NET Aspire SDK** (found in Individual Components).
   - (Optional) **.NET MAUI Development** to run client apps.

#### Option 2: Automated Setup
Run the following commands in PowerShell (Administrator mode):
```powershell
Install-Module -Name Microsoft.WinGet.Configuration -AllowPrerelease -AcceptLicense -Force
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
get-WinGetConfiguration -file .\.configurations\vside.dsc.yaml | Invoke-WinGetConfiguration -AcceptConfigurationAgreements
```
This script installs all required tools and prompts a system restart.

#### Option 3: Use Dev Home
1. In **Dev Home**, navigate to **Machine Configuration > Clone Repositories**.
2. Enter the repository URL.
3. Confirm the detected configuration file and select **Run File**.

---

### Setup for macOS, Linux, or Windows (Without Visual Studio)
1. Install the latest **.NET 9 SDK**.

2. Run the following commands in a terminal (Administrator mode):
   ```powershell
   Install-Module -Name Microsoft.WinGet.Configuration -AllowPrerelease -AcceptLicense -Force
   $env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
   get-WinGetConfiguration -file .\.configurations\vscode.dsc.yaml | Invoke-WinGetConfiguration -AcceptConfigurationAgreements
   ```
3. (Optional) Install **Visual Studio Code** and extensions for .NET development.

---

### Running the Application
#### Important
Ensure Docker is running before proceeding.

#### Option 1: Using Visual Studio (Windows Only)
1. Open `eShopio.Web.slnf` in Visual Studio.
2. Set `eShopio.AppHost.csproj` as the startup project.
3. Press **Ctrl+F5** to launch Aspire.

#### Option 2: Using Terminal
1. Navigate to the application directory:
   ```bash
   cd src/eShopio.AppHost
   ```
2. Run the project:
   ```bash
   dotnet run --project eShopio.AppHost.csproj
   ```
3. Note the dashboard URL in the console output:
   ```plaintext
   Login to the dashboard at: http://localhost:19888/login?t=your-unique-code
   ```
4. Install ASP.NET Core HTTPS certificates if prompted. Learn more [here](https://aka.ms/aspnet/https-trust-dev-cert).

---

### Azure OpenAI Integration
1. Update `appsettings.json` in `eShopio.AppHost`:
   ```json
   "ConnectionStrings": {
       "OpenAi": "Endpoint=your-endpoint;Key=your-key;"
   }
   ```
2. Enable OpenAI in `Program.cs`:
   ```csharp
   bool useOpenAI = true;
   ```
3. Learn more about the [.NET Aspire OpenAI component](https://github.com/dotnet/eshop).

---

### Deploying with Azure Developer CLI
#### Steps:
1. Install or update Azure Developer CLI:
   ```bash
   az upgrade
   ```
2. Authenticate to Azure:
   ```bash
   azd auth login
   ```
3. Initialize the project:
   ```bash
   azd init
   ```
   - Select "Use code in the current directory."
   - Confirm "Use .NET (Aspire)."
   - Name your environment.
4. Deploy the application:
   ```bash
   azd up
   ```
   The deployment URL will be displayed after completion.

---

### Additional Information
- **Sample Data**: Catalog data in `catalog.json` was generated using GPT-35-Turbo. Images were created with DALL·E 3.
- For Azure deployment, check the [eShopio on Azure repo](https://github.com/dotnet/eshop).

---

### Contribution
Read the [contribution guidelines](https://github.com/dotnet/eshop/blob/main/CONTRIBUTING.md) and the [Code of Conduct](https://github.com/dotnet/eshop/blob/main/CODE_OF_CONDUCT.md).

---

For any questions or troubleshooting, refer to the [FAQ](https://github.com/dotnet/eshop).

