# Azure DevOps Pipeline & ACR Complete Guide

A comprehensive explanation of Azure DevOps CI/CD pipelines and Azure Container Registry concepts for learning and implementation.

---

## Table of Contents

1. [Azure DevOps Pipeline Overview](#azure-devops-pipeline-overview)
2. [Pipeline Triggers & Variables](#pipeline-triggers--variables)
3. [Stage 1: Build_Test_Scan](#stage-1-build_test_scan)
4. [Stage 2: Build_Docker_Image](#stage-2-build_docker_image)
5. [Stage 3: Push_To_ACR](#stage-3-push_to_acr)
6. [Overall Pipeline Flow](#overall-pipeline-flow)
7. [What is Azure Container Registry (ACR)?](#what-is-azure-container-registry-acr)
8. [ACR Creation Methods](#acr-creation-methods)
9. [ACR Image Management](#acr-image-management)
10. [ACR Integration in CI/CD](#acr-integration-in-cicd)
11. [ACR Portal Creation Guide](#acr-portal-creation-guide)
12. [ACR Best Practices](#acr-best-practices)

---

## Azure DevOps Pipeline Overview

Azure DevOps Pipelines is Microsoft's CI/CD platform that automates building, testing, and deploying applications. This guide explains a complete pipeline that builds a Java application, packages it into a Docker container, and pushes it to Azure Container Registry.

### Key Pipeline Concepts

**YAML Pipeline Structure**:
```yaml
# Basic structure
trigger: # When to run
variables: # Reusable values
stages: # Major phases
  - stage: StageName
    jobs:
      - job: JobName
        steps:
          - task: TaskName
```

**Pipeline Benefits**:
- **Version Controlled**: Pipeline code stored in Git
- **Automated**: No manual intervention needed
- **Scalable**: Handle multiple projects
- **Traceable**: Full audit trail of deployments

---

## Pipeline Triggers & Variables

### Triggers

Triggers define when the pipeline should automatically start running.

```yaml
trigger:
  branches:
    include:
      - main                    # Run on main branch pushes
      - releases/*              # Run on any branch under releases/
```

**Trigger Types**:
- **Push Triggers**: Run when code is pushed to specified branches
- **Pull Request Triggers**: Run when PR is created/updated
- **Scheduled Triggers**: Run at specific times (CRON)
- **Manual Triggers**: Run on-demand

**Why This Configuration**:
- `main` branch: Production-ready code
- `releases/*`: Release branches for versioned deployments

### Variables

Variables store reusable values that can be referenced throughout the pipeline.

```yaml
variables:
  acrName: 'acrebrdeastus01'                    # ACR service connection name
  acrLoginServer: 'acrebrdeastus01.azurecr.io'  # ACR URL
  imageName: 'ems-api'                          # Docker image name
  dockerTag: '1.0'                              # Version tag
  azureServiceConnection: 'azure-connection'    # Azure subscription connection
  azureResourceGroup: 'my-rg'                   # Resource group name
  sonarProjectKey: 'ems-api-project'            # SonarQube project identifier
  selfHostedAgentPool: 'ebrd_agent'             # Agent pool for execution
```

**Variable Types**:
- **Pipeline Variables**: Defined in YAML
- **Variable Groups**: Shared across multiple pipelines
- **Environment Variables**: Set at runtime
- **Secret Variables**: Encrypted sensitive values

**Benefits**:
- **DRY Principle**: Don't repeat values
- **Maintainability**: Change in one place
- **Security**: Secrets are encrypted
- **Flexibility**: Different values per environment

---

## Stage 1: Build_Test_Scan

### Purpose

This stage compiles the Java application, runs unit tests, measures code coverage, performs security scans, and prepares artifacts for deployment.

### Detailed Breakdown

```yaml
- stage: Build_Test_Scan
  displayName: Build, Unit Tests, Coverage, Sonar, Fortify
```

### Step-by-Step Process

#### 1. Code Checkout
```yaml
- checkout: self  # Checkout the source code from Git
```

**What happens**:
- Downloads the repository code
- Creates a clean workspace
- Prepares for build process

#### 2. Maven Build & Unit Tests
```yaml
- task: Maven@3
  inputs:
    mavenPomFile: 'pom.xml'
    goals: 'clean verify'
    publishJUnitResults: true
    testResultsFiles: '**/surefire-reports/TEST-*.xml'
```

**Maven Goals Explained**:
- `clean`: Removes old build artifacts (`target/` folder)
- `verify`: Runs all lifecycle phases including tests

**What happens**:
- Compiles Java source code (`.java` → `.class`)
- Downloads dependencies from Maven Central
- Runs JUnit unit tests
- Generates test reports
- Fails pipeline if tests fail

#### 3. Code Coverage Analysis
```yaml
- task: PublishCodeCoverageResults@1
  inputs:
    codeCoverageTool: 'JaCoCo'
    summaryFileLocation: 'target/site/jacoco/jacoco.xml'
    reportDirectory: 'target/site/jacoco'
```

**JaCoCo (Java Code Coverage)**:
- Measures how much code is covered by tests
- Generates detailed HTML reports
- Shows line-by-line coverage
- Helps identify untested code

**Coverage Metrics**:
- **Line Coverage**: % of executable lines covered
- **Branch Coverage**: % of decision points covered
- **Method Coverage**: % of methods executed
- **Class Coverage**: % of classes instantiated

#### 4. Artifact Publishing
```yaml
- task: PublishBuildArtifacts@1
  inputs:
    PathtoPublish: 'target/*.jar'
    ArtifactName: 'drop'
    publishLocation: 'Container'
```

**What happens**:
- Uploads built JAR file to Azure DevOps
- Makes it available for next stages
- Stores as "drop" artifact

### Stage Outcome

✅ **Validated Application**: Code compiles successfully
✅ **Tested Code**: All unit tests pass
✅ **Coverage Report**: Code coverage metrics available
✅ **Ready Artifact**: JAR file stored for next stages

---

## Stage 2: Build_Docker_Image

### Purpose

Package the compiled Java application (JAR) into a Docker container image that can run anywhere.

### Dependencies

```yaml
dependsOn: Build_Test_Scan  # Must complete before this stage runs
```

### Step-by-Step Process

#### 1. Download Previous Artifacts
```yaml
- task: DownloadBuildArtifacts@0
  inputs:
    downloadType: 'single'
    artifactName: 'drop'
    downloadPath: '$(System.ArtifactsDirectory)'
```

**What happens**:
- Downloads JAR file from Stage 1
- Places in `$(System.ArtifactsDirectory)`

#### 2. Debug Artifact Listing
```yaml
- script: |
    echo "Listing downloaded artifacts:"
    ls -la $(System.ArtifactsDirectory)/
```

**Purpose**: Troubleshooting step to verify files are downloaded correctly

#### 3. Prepare JAR for Docker
```yaml
- script: |
    mkdir -p target
    cp $(System.ArtifactsDirectory)/drop/*.jar target/
```

**What happens**:
- Creates `target/` directory
- Copies JAR to expected location
- Dockerfile will reference this location

#### 4. Docker Image Build
```yaml
- task: Docker@2
  inputs:
    containerRegistry: 'acr-connection'
    repository: 'ems-api'
    command: 'build'
    Dockerfile: '**/Dockerfile'
    tags: |
      $(dockerTag)
      latest
```

**Docker Build Process**:
1. Finds `Dockerfile` in repository
2. Builds image layer by layer
3. Copies JAR file into image
4. Tags with version `1.0` and `latest`

**Example Dockerfile**:
```dockerfile
FROM openjdk:11-jre-slim
WORKDIR /app
COPY target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
```

#### 5. Save Docker Image
```yaml
- script: |
    docker save $(acrLoginServer)/$(imageName):$(dockerTag) -o $(Build.ArtifactStagingDirectory)/docker-image.tar
```

**What happens**:
- Exports Docker image to `.tar` file
- Portable format for transfer
- Ready for next stage

#### 6. Publish Docker Artifact
```yaml
- task: PublishBuildArtifacts@1
  inputs:
    PathtoPublish: '$(Build.ArtifactStagingDirectory)/docker-image.tar'
    ArtifactName: 'docker-image'
    publishLocation: 'Container'
```

**What happens**:
- Uploads `.tar` file to Azure DevOps
- Available for deployment stages

### Stage Outcome

✅ **Containerized Application**: JAR packaged in Docker image
✅ **Tagged Image**: Versioned as `1.0` and `latest`
✅ **Portable Artifact**: `.tar` file ready for deployment

---

## Stage 3: Push_To_ACR

### Purpose

Push the Docker image to Azure Container Registry for secure storage and distribution to deployment targets.

### Dependencies & Agent

```yaml
dependsOn: Build_Docker_Image
pool: $(selfHostedAgentPool)  # Uses self-hosted agents
```

**Why Self-Hosted Agents?**
- Docker operations require Docker daemon
- Self-hosted agents have Docker installed
- Microsoft-hosted agents have limitations

### Step-by-Step Process

#### 1. Download Docker Image Artifact
```yaml
- task: DownloadBuildArtifacts@0
  inputs:
    downloadType: 'single'
    artifactName: 'docker-image'
    downloadPath: '$(System.ArtifactsDirectory)'
```

**What happens**: Downloads `.tar` file from Stage 2

#### 2. Load Docker Image
```yaml
- script: |
    docker load -i $(System.ArtifactsDirectory)/docker-image/docker-image.tar
```

**What happens**:
- Imports `.tar` file into local Docker
- Image becomes available locally

#### 3. Tag for ACR
```yaml
- script: |
    docker tag $(acrLoginServer)/$(imageName):$(dockerTag) $(acrLoginServer)/$(imageName):$(dockerTag)
    docker tag $(acrLoginServer)/$(imageName):$(dockerTag) $(acrLoginServer)/$(imageName):latest
```

**What happens**:
- Tags image with ACR registry URL
- Prepares for push to registry

#### 4. Push to ACR
```yaml
- task: Docker@2
  inputs:
    containerRegistry: $(acrName)
    repository: $(imageName)
    command: 'push'
    tags: |
      $(dockerTag)
      latest
```

**What happens**:
- Authenticates with ACR
- Uploads both `1.0` and `latest` tags
- Image stored securely in Azure

### Stage Outcome

✅ **Published Image**: Available in ACR for deployment
✅ **Multiple Tags**: Versioned and latest tags
✅ **Secure Storage**: Private registry access

---

## Overall Pipeline Flow

### Complete Workflow

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Code Push     │ -> │ Build_Test_Scan  │ -> │Build_Docker_Image│
│  (Git Trigger)  │    │                  │    │                 │
│                 │    │ • Maven Build    │    │ • Download JAR  │
│ • main branch   │    │ • Unit Tests     │    │ • Docker Build  │
│ • releases/*    │    │ • Code Coverage  │    │ • Save .tar     │
└─────────────────┘    │ • Publish JAR    │    └─────────────────┘
                       └──────────────────┘             │
                                                        v
                                               ┌─────────────────┐
                                               │   Push_To_ACR   │
                                               │                 │
                                               │ • Download .tar │
                                               │ • Load Image    │
                                               │ • Tag for ACR   │
                                               │ • Push to ACR   │
                                               └─────────────────┘
```

### Pipeline Benefits

✅ **Automated Quality Gates**: Tests and coverage ensure code quality
✅ **Containerization**: Application packaged for any environment
✅ **Secure Distribution**: Images stored in private ACR
✅ **Deployment Ready**: Images available for AKS, App Service, etc.

### Execution Time

- **Stage 1**: 5-10 minutes (build + tests)
- **Stage 2**: 2-5 minutes (Docker build)
- **Stage 3**: 1-3 minutes (ACR push)
- **Total**: ~8-18 minutes from code push to ACR

---

## What is Azure Container Registry (ACR)?

### Definition

Azure Container Registry (ACR) is a managed, private Docker registry service provided by Microsoft Azure that allows you to store and manage container images and other OCI (Open Container Initiative) artifacts.

### Key Features

#### Storage & Management
- **Private Registry**: Secure storage for Docker images
- **Geo-replication**: Copy images across Azure regions (Premium SKU)
- **Retention Policies**: Automatically delete old/unused images
- **Metadata**: Store custom metadata with images

#### Security
- **Azure AD Integration**: Use Azure Active Directory for authentication
- **RBAC**: Role-based access control
- **Content Trust**: Sign and verify image integrity
- **Vulnerability Scanning**: Scan images for security issues
- **Private Endpoints**: Secure access within Azure network

#### Integration
- **AKS**: Seamless integration with Azure Kubernetes Service
- **App Service**: Deploy to Web Apps for Containers
- **Azure Functions**: Container-based serverless functions
- **ACR Tasks**: Build images directly in ACR

### ACR vs Docker Hub

| Feature | ACR | Docker Hub |
|---------|-----|------------|
| **Privacy** | Private | Public/Private |
| **Security** | Azure AD, RBAC | Basic auth |
| **Integration** | Deep Azure integration | Limited |
| **Cost** | Pay for storage/transfer | Free tier available |
| **Geo-distribution** | Global replication | Limited |

### Use Cases

1. **CI/CD Pipelines**: Store build artifacts
2. **Multi-environment**: Dev, staging, production images
3. **Team Collaboration**: Share images across teams
4. **Compliance**: Keep images within organization
5. **Backup**: Reliable storage with Azure SLA

---

## ACR Creation Methods

### Method 1: Azure CLI

#### Prerequisites
- Azure CLI installed
- Azure subscription
- Appropriate permissions

#### Step-by-Step Creation

```bash
# Set variables
RESOURCE_GROUP="myResourceGroup"
ACR_NAME="myacrname"  # Must be globally unique
LOCATION="eastus"

# Create resource group (if needed)
az group create --name $RESOURCE_GROUP --location $LOCATION

# Create ACR
az acr create \
  --resource-group $RESOURCE_GROUP \
  --name $ACR_NAME \
  --sku Basic \
  --location $LOCATION
```

#### SKU Options

| SKU | Description | Use Case |
|-----|-------------|----------|
| **Basic** | Entry-level, 10GB storage | Development, testing |
| **Standard** | 100GB storage, webhooks | Production workloads |
| **Premium** | 500GB storage, geo-replication | Enterprise, multi-region |

#### Verification

```bash
# Check ACR creation
az acr show --name $ACR_NAME --resource-group $RESOURCE_GROUP

# List all ACRs in subscription
az acr list --output table
```

### Method 2: Azure Portal (See detailed guide below)

### Method 3: Terraform

```hcl
resource "azurerm_container_registry" "acr" {
  name                = "myacrname"
  resource_group_name = azurerm_resource_group.rg.name
  location            = azurerm_resource_group.rg.location
  sku                 = "Basic"
  admin_enabled       = false

  tags = {
    environment = "dev"
    project     = "ems"
  }
}
```

---

## ACR Image Management

### Authentication Methods

#### 1. Azure CLI Login
```bash
az acr login --name myacrname
```

#### 2. Docker Login
```bash
docker login myacrname.azurecr.io
```

#### 3. Service Principal
```bash
# Create service principal
az ad sp create-for-rbac --name acr-service-principal

# Assign role
az role assignment create \
  --assignee <service-principal-id> \
  --role AcrPush \
  --scope /subscriptions/<subscription-id>/resourceGroups/<rg>/providers/Microsoft.ContainerRegistry/registries/<acr-name>
```

### Image Operations

#### Tagging Images

```bash
# Tag local image for ACR
docker tag ems-api:1.0 myacrname.azurecr.io/ems-api:1.0
docker tag ems-api:1.0 myacrname.azurecr.io/ems-api:latest
```

**Tagging Strategy**:
- **Version Tags**: `1.0`, `1.1`, `2.0`
- **Latest Tag**: `latest` (always points to newest)
- **Environment Tags**: `dev`, `staging`, `prod`
- **Build Tags**: `build-12345`

#### Pushing Images

```bash
# Push tagged images
docker push myacrname.azurecr.io/ems-api:1.0
docker push myacrname.azurecr.io/ems-api:latest
```

#### Listing Images

```bash
# List repositories
az acr repository list --name myacrname --output table

# List tags for specific repository
az acr repository show-tags --name myacrname --repository ems-api --output table

# Show image details
az acr repository show --name myacrname --image ems-api:1.0
```

#### Pulling Images

```bash
# Pull specific version
docker pull myacrname.azurecr.io/ems-api:1.0

# Pull latest
docker pull myacrname.azurecr.io/ems-api:latest
```

#### Deleting Images

```bash
# Delete specific tag
az acr repository delete --name myacrname --image ems-api:old-tag

# Delete entire repository
az acr repository delete --name myacrname --repository old-repo
```

### Image Lifecycle Management

#### Retention Policies
```bash
# Set retention policy (Premium SKU)
az acr config retention update \
  --registry myacrname \
  --status enabled \
  --days 30 \
  --policy-type UntaggedManifests
```

#### Cleanup Commands
```bash
# Remove untagged manifests older than 7 days
az acr manifest list-metadata --registry myacrname --filter "timestamp < 7d"

# Bulk delete old images
az acr repository delete --name myacrname --image ems-api:old-tag-1 --image ems-api:old-tag-2
```

---

## ACR Integration in CI/CD

### Pipeline Integration Pattern

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Source    │ -> │   Build     │ -> │  Container  │ -> │   Registry  │
│   Code      │    │   App       │    │   Image     │    │   (ACR)     │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
                                                                │
┌─────────────┐    ┌─────────────┐    ┌─────────────┐             │
│  Deploy to  │ <- │  Pull from  │ <- │   AKS      │ <───────────┘
│ Production  │    │    ACR      │    │            │
└─────────────┘    └─────────────┘    └─────────────┘
```

### Azure DevOps Integration

#### Service Connection Setup
1. Go to Project Settings → Service Connections
2. Add new service connection → Docker Registry
3. Select Azure Container Registry
4. Choose subscription and ACR

#### Pipeline Integration
```yaml
# Build and push in one task
- task: Docker@2
  inputs:
    containerRegistry: 'acr-service-connection'
    repository: 'ems-api'
    command: 'buildAndPush'
    Dockerfile: '**/Dockerfile'
    tags: |
      $(Build.BuildNumber)
      latest
```

### Kubernetes Deployment

#### AKS Integration
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ems-api
spec:
  replicas: 3
  selector:
    matchLabels:
      app: ems-api
  template:
    metadata:
      labels:
        app: ems-api
    spec:
      containers:
      - name: ems-api
        image: myacrname.azurecr.io/ems-api:1.0
        ports:
        - containerPort: 8080
      imagePullSecrets:
      - name: acr-secret
```

#### Image Pull Secret
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: acr-secret
type: kubernetes.io/dockerconfigjson
data:
  .dockerconfigjson: <base64-encoded-config>
```

### App Service Integration

#### Web App for Containers
```json
{
  "name": "ems-api",
  "type": "Microsoft.Web/sites",
  "properties": {
    "serverFarmId": "/subscriptions/.../serverfarms/my-plan",
    "siteConfig": {
      "linuxFxVersion": "DOCKER|myacrname.azurecr.io/ems-api:1.0"
    }
  }
}
```

---

## ACR Portal Creation Guide

### Step-by-Step Portal Creation

#### Step 1: Access Azure Portal
- Navigate to https://portal.azure.com
- Sign in with your Azure account

#### Step 2: Navigate to Container Registry
- Use the search bar at the top
- Type "Container Registry"
- Select "Container registries" from results

#### Step 3: Create New Registry
- Click the "+ Create" button
- Select "Container Registry" from the marketplace

#### Step 4: Configure Basic Settings

**Subscription**:
- Choose your Azure subscription
- Must have appropriate permissions

**Resource Group**:
- Select existing resource group
- Or create new one: "Create new" → Enter name

**Registry Name**:
- Must be globally unique
- 5-50 characters, lowercase letters and numbers only
- Example: `myacr123`, `emsregistry`

**Location**:
- Choose Azure region closest to your workloads
- Consider data residency requirements

**SKU (Pricing Tier)**:
- **Basic**: Development/testing, 10GB storage
- **Standard**: Production, 100GB storage, webhooks
- **Premium**: Enterprise, 500GB storage, geo-replication

#### Step 5: Configure Advanced Settings

**Networking**:
- **Public access**: Accessible from internet
- **Private access**: Restrict to private networks
- Configure private endpoints for enhanced security

**Encryption**:
- Azure automatically encrypts data at rest
- Customer-managed keys available in Premium

**Tags**:
- Key-value pairs for resource organization
- Examples: `environment=dev`, `team=platform`, `project=ems`

#### Step 6: Review and Create
- Review all settings
- Click "Create"
- Deployment takes 1-2 minutes

#### Step 7: Access Created Registry
- Go to resource group
- Find your ACR resource
- Note the "Login server" URL (e.g., `myacr123.azurecr.io`)

### Post-Creation Configuration

#### Enable Admin User (Optional)
```bash
az acr update --name myacrname --admin-enabled true
```

#### Configure Webhooks
- In ACR → Webhooks → Add webhook
- Trigger on push/pull events
- Send notifications to external systems

#### Set up Geo-replication (Premium)
- In ACR → Geo-replication
- Add regions for global distribution
- Automatic image synchronization

---

## ACR Best Practices

### Security Best Practices

#### 1. Use Private Endpoints
- Restrict access to Azure network
- No public internet exposure
- Enhanced security for compliance

#### 2. Implement RBAC
```bash
# Assign roles
az role assignment create \
  --assignee user@domain.com \
  --role AcrPull \
  --scope /subscriptions/.../registries/myacr

# Available roles: AcrPull, AcrPush, AcrDelete, AcrImageSigner
```

#### 3. Enable Content Trust
```bash
az acr config content-trust update \
  --registry myacrname \
  --status enabled
```

#### 4. Regular Vulnerability Scanning
- Use Azure Security Center integration
- Scan images for known vulnerabilities
- Set up automated scanning in pipelines

### Performance Optimization

#### 1. Use Geo-replication
- Deploy images closer to users
- Reduce latency
- Improve pull performance

#### 2. Optimize Image Size
```dockerfile
# Use multi-stage builds
FROM maven:3.8-openjdk-11 AS build
COPY . .
RUN mvn clean package

FROM openjdk:11-jre-slim
COPY --from=build target/*.jar app.jar
```

#### 3. Implement Caching
- Use ACR as cache for frequently pulled images
- Reduce bandwidth costs

### Cost Management

#### 1. Choose Appropriate SKU
- Basic: Development environments
- Standard: Most production workloads
- Premium: Large-scale, multi-region deployments

#### 2. Implement Retention Policies
```bash
# Auto-delete untagged images after 30 days
az acr config retention update \
  --registry myacrname \
  --status enabled \
  --days 30
```

#### 3. Monitor Usage
- Use Azure Monitor for ACR metrics
- Track storage usage and transfer costs
- Set up alerts for cost thresholds

### Operational Best Practices

#### 1. Use Semantic Versioning
```
major.minor.patch
├── 1.0.0 (initial release)
├── 1.1.0 (new features)
├── 1.1.1 (bug fixes)
└── 2.0.0 (breaking changes)
```

#### 2. Implement CI/CD Integration
- Automate image building and pushing
- Use immutable tags for production
- Implement rollback strategies

#### 3. Monitor and Alert
- Set up Azure Monitor alerts
- Track pull/push metrics
- Monitor storage usage
- Alert on security vulnerabilities

#### 4. Backup and Disaster Recovery
- Use geo-replication for redundancy
- Export images regularly
- Document recovery procedures

### Troubleshooting Common Issues

#### Authentication Issues
```bash
# Check login status
az acr login --name myacrname

# Verify permissions
az role assignment list --scope /subscriptions/.../registries/myacrname
```

#### Push/Pull Failures
```bash
# Check network connectivity
curl -I https://myacrname.azurecr.io/v2/

# Verify image exists
az acr repository show-tags --name myacrname --repository ems-api
```

#### Storage Issues
```bash
# Check storage usage
az acr show-usage --name myacrname

# Clean up old images
az acr repository delete --name myacrname --image ems-api:old-tag
```

---

## Summary

This guide covers the complete Azure DevOps pipeline for building Java applications, containerizing them with Docker, and managing them through Azure Container Registry. Key concepts include:

- **Pipeline Stages**: Build → Test → Containerize → Publish
- **ACR Management**: Creation, authentication, image operations
- **Integration**: Seamless connection between DevOps and ACR
- **Best Practices**: Security, performance, cost optimization

The pipeline ensures automated, secure, and efficient delivery of containerized applications to production environments.

---

**Last Updated**: April 3, 2026
**Version**: 1.0
**Status**: Complete learning guide