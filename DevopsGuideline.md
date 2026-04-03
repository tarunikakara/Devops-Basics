# DevOps Learning Guide

A comprehensive roadmap for mastering DevOps, CI/CD, Jenkins, and Azure DevOps concepts.

---

## Table of Contents

1. [What is DevOps?](#topic-1-what-is-devops)
2. [CI/CD Pipeline Overview](#topic-2-cicd-pipeline-overview)
3. [CI/CD Pipeline Steps in Detail](#topic-3-cicd-pipeline-steps-in-detail)
4. [SonarQube](#topic-4-sonarqube)
5. [Build Tools](#topic-5-build-tools)
6. [Artifact Repository](#topic-6-artifact-repository)
7. [Testing in CI/CD](#topic-7-testing-in-cicd)
8. [Approval Process](#topic-8-approval-process)
9. [Deployment Concepts](#topic-9-deployment-concepts)
10. [Agile Integration with DevOps](#topic-10-agile-integration-with-devops)
11. [Jenkins Interview Topics](#topic-11-jenkins-interview-topics)
12. [Jenkins Integrations](#topic-12-jenkins-integrations)
13. [Jenkins Interview Questions](#topic-13-jenkins-interview-questions)
14. [Azure DevOps Topics](#topic-14-azure-devops-topics)
15. [Azure DevOps YAML Pipeline](#topic-15-azure-devops-yaml-pipeline)
16. [Azure DevOps Interview Questions](#topic-16-azure-devops-interview-questions)
17. [Real-Time DevOps Scenario](#topic-17-real-time-devops-scenario)
18. [Additional Tools to Know](#topic-18-additional-tools-to-know)

---

## Main Topics You Need to Learn

---

## Phase 1: Foundation (Weeks 1-2)
- [ ] DevOps meaning and importance
- [ ] Dev + Ops collaboration concepts
- [ ] CI/CD pipeline overview
- [ ] Pipeline stages explanation

## Phase 2: Quality & Build (Weeks 3-4)
- [ ] SonarQube quality checks
- [ ] Quality gate failures
- [ ] Maven build tool
- [ ] Build tool outputs
- [ ] Gradle, MSBuild, pip basics

## Phase 3: Artifact Management (Week 5)
- [ ] Nexus repository
- [ ] JFrog Artifactory
- [ ] Artifact versioning
- [ ] Importance of artifact storage

## Phase 4: Testing & Approval (Weeks 6-7)
- [ ] JUnit, NUnit, Selenium, PyTest
- [ ] Testing location in pipeline
- [ ] Manual approval process
- [ ] BA / Product owner role

## Phase 5: Deployment Concepts (Week 8)
- [ ] Environment types (Dev, QA, Staging, Prod)
- [ ] Kubernetes deployment
- [ ] PCF deployment
- [ ] Tomcat / IIS servers
- [ ] Ansible / SSH basics

## Phase 6: Agile Integration (Week 9)
- [ ] Sprints and sprint workflow
- [ ] Planning to deployment cycle
- [ ] DevOps in Agile projects

## Phase 7: Jenkins Mastery (Weeks 10-11)
- [ ] Jenkins architecture
- [ ] Jenkinsfile creation
- [ ] Declarative vs Scripted pipelines
- [ ] Jenkins plugins
- [ ] Triggers (polling, webhooks, CRON)
- [ ] Freestyle vs Pipeline jobs
- [ ] Credentials management
- [ ] Shared library

## Phase 8: Azure DevOps (Weeks 12-13)
- [ ] Repos, Pipelines, Artifacts, Boards
- [ ] YAML pipeline structure
- [ ] Classic vs YAML pipelines
- [ ] Approvals and environments
- [ ] Secrets management
- [ ] GitHub/SonarQube integration

## Phase 9: Docker & Kubernetes (Weeks 14-15)
- [ ] Docker containerization
- [ ] Kubernetes deployment
- [ ] Helm charts

## Phase 10: Monitoring & Tools (Weeks 16-17)
- [ ] Prometheus / Grafana
- [ ] GitHub / GitLab / Bitbucket
- [ ] GitHub Actions

## Phase 11: Final Review (Week 18)
- [ ] Real-time scenario walkthrough
- [ ] Mock interview questions
- [ ] End-to-end pipeline explanation

---

## Key Interview Questions to Prepare

### DevOps & CI/CD
1. What is DevOps and why is it important?
2. Explain CI/CD pipeline stages with real examples
3. What is SonarQube and what happens if code fails quality gates?

### Build & Artifacts
4. What is Maven and what files does it generate?
5. Explain artifact versioning and repository management
6. What is the difference between Nexus and JFrog Artifactory?

### Jenkins
7. Explain Jenkins Master-Agent architecture
8. What is the difference between Freestyle and Pipeline jobs?
9. What is a Jenkinsfile and how does it work?
10. Declarative vs Scripted pipelines - advantages of each?
11. How do you trigger Jenkins jobs automatically?

### Azure DevOps
12. What is the difference between Classic and YAML pipelines?
13. Explain Azure DevOps YAML pipeline structure
14. How do you manage secrets in Azure DevOps?

### Deployment
15. Explain different deployment environments
16. How would you deploy to Kubernetes?
17. What is the role of approval gates in deployment?

### Real-Time Scenario
18. Walk me through a Java application end-to-end pipeline

---

## Tips for Success

✅ **Study Systematically**: Follow the learning order - don't skip ahead  
✅ **Hands-On Practice**: Set up Jenkins, Azure DevOps, Docker locally  
✅ **Real-World Scenarios**: Understand complete pipeline flows  
✅ **Integration Focus**: Learn how tools work together  
✅ **Interview Focus**: Practice answering real interview questions  
✅ **Documentation**: Take notes for each tool and concept  
✅ **Review Regularly**: Revisit earlier topics during later phases  

---

**Last Updated**: April 3, 2026  
**Status**: Complete learning guide with detailed concepts

---

## DETAILED CONCEPTS - LEARN FROM HERE

---

### TOPIC 1: What is DevOps?

#### **Meaning of DevOps**

DevOps = **Development + Operations**

- **Definition**: DevOps is a set of practices, tools, and cultural philosophies that combine software development (Dev) and IT operations (Ops) to enable rapid and continuous software delivery.

- **Traditional Approach (Before DevOps)**:
  - Developers write code in isolation
  - Operations team manages servers and deployment separately
  - Communication gap between Dev and Ops
  - Long release cycles (months/years)
  - High risk deployments
  - Blame culture when things go wrong

- **DevOps Approach (After DevOps)**:
  - Dev and Ops work together as one team
  - Continuous integration and continuous deployment
  - Automated processes for build, test, and deployment
  - Faster, safer releases (days/weeks)
  - Shared responsibility for application success
  - Collaborative culture

#### **Why DevOps is Used**

**Benefits of DevOps**:

1. **Faster Time to Market**
   - Reduced release cycle from months to days/weeks
   - Quick feature deployment
   - Rapid feedback loops

2. **Improved Quality**
   - Automated testing catches issues early
   - Fewer bugs in production
   - Consistent deployments

3. **Reduced Risk**
   - Automated rollback capabilities
   - Safer deployments with smaller changes
   - Better error detection

4. **Cost Reduction**
   - Automation reduces manual work
   - Less production issues and downtime
   - Better resource utilization

5. **Better Communication**
   - Dev and Ops alignment
   - Shared goals and metrics
   - Reduced finger-pointing

6. **Scalability**
   - Infrastructure as Code
   - Easy to scale applications
   - Consistent environments

#### **Dev + Ops Collaboration**

**Before** (Waterfall/Traditional):
```
Requirements → Development → Testing → Operations → User
     ↓
  (3-6 months)
```

**After** (DevOps/Agile):
```
Requirements → Dev → Test → Deploy → Monitor → Feedback
     ↓
  (Days/Weeks - Continuous Cycle)
```

**Key Collaboration Points**:
- **Shared Tools**: Use same CI/CD platforms
- **Shared Metrics**: Monitor together (uptime, performance, errors)
- **Shared Responsibility**: Both accountable for production
- **Continuous Feedback**: Operations feeds issues back to developers
- **Automation**: Both teams maintain automation

**Example Real-World Scenario**:
- Developer fixes a bug
- Code is pushed to Git
- Jenkins automatically triggers pipeline
- Code is tested automatically
- If tests pass, code is deployed to production
- Operations monitors the deployment
- If issues occur, both teams respond together

---

### TOPIC 2: CI/CD Pipeline Overview

#### **What is CI (Continuous Integration)?**

**Definition**: Continuous Integration is the practice of merging code changes from multiple developers into a shared repository multiple times a day, with each change automatically tested.

**Key Points**:
- Developers commit code frequently (multiple times per day)
- Each commit triggers automated build and tests
- Issues are caught early
- Reduces integration problems
- Developers get fast feedback (within minutes)

**CI Benefits**:
- Bugs detected early
- Reduced integration time
- Frequent working builds
- Better code quality

**Example**:
- Developer A commits code at 9 AM
- Within 2 minutes: automated build runs
- Within 5 minutes: automated tests run
- If all pass ✓ → code is ready
- If any fail ✗ → developer notified immediately

#### **What is CD (Continuous Delivery/Deployment)?**

**Continuous Delivery**:
- Code is automatically built, tested, and packaged
- But deployment to production is **manual** (requires approval)
- Code is always in a production-ready state
- Less risky - team controls when to release

**Continuous Deployment**:
- Code is automatically built, tested, and **deployed to production**
- No manual approval needed (or minimal approval)
- Every passing build goes to production
- Fastest feedback from users

**Relationship**:
```
CI → Continuous Delivery (manual approval) → Continuous Deployment (automatic)
```

#### **All Pipeline Stages End-to-End**

**Complete CI/CD Pipeline Flow**:

```
1. CODE COMMIT
   ├─ Developer pushes code to Git/GitHub
   ├─ Webhook triggered
   └─ Pipeline starts automatically

2. SOURCE CONTROL
   ├─ Code checked out from repository
   ├─ Branch merged if needed
   └─ Ready for build

3. CODE COMPILATION/BUILD
   ├─ Language-specific build (Maven, Gradle, npm, etc.)
   ├─ Compile source code
   ├─ Generate JAR/WAR/executable
   └─ If fails → notify developer, stop

4. CODE QUALITY CHECK
   ├─ SonarQube analysis runs
   ├─ Check code quality, bugs, vulnerabilities
   ├─ Quality gate applied
   └─ If fails → can still proceed (configurable)

5. UNIT TESTING
   ├─ JUnit/NUnit tests run automatically
   ├─ Test individual methods/functions
   ├─ Check code functionality
   └─ If fails → stop, notify developer

6. ARTIFACT CREATION
   ├─ Package application (JAR/WAR/Docker image)
   ├─ Version it
   └─ Store for next stages

7. ARTIFACT REPOSITORY
   ├─ Upload to Nexus/JFrog
   ├─ Store for deployment
   └─ Track versions

8. DEPLOY TO TEST ENVIRONMENT
   ├─ Deploy to QA/Staging
   ├─ Integration tests run
   ├─ Selenium tests run
   ├─ Performance tests run
   └─ If fails → notify,investigate

9. APPROVAL GATE
   ├─ Manual approval required
   ├─ QA lead reviews
   ├─ Product owner approves
   └─ Wait for approval

10. DEPLOY TO PRODUCTION
    ├─ Deploy to live environment
    ├─ Health checks
    ├─ Smoke tests
    └─ Live users access application

11. MONITORING & LOGGING
    ├─ Prometheus/Grafana monitor
    ├─ Logs collected
    ├─ Metrics tracked
    └─ Issues detected automatically

12. FEEDBACK LOOP
    ├─ Issues found
    ├─ Bugs reported
    ├─ Developers fix
    └─ Back to step 1
```

---

### TOPIC 3: CI/CD Pipeline Steps in Detail

#### **Step 1: Code Validation**

**What it is**: Checking if code meets standards before building

**Includes**:
- Syntax checking
- Linting (code style rules)
- Pre-commit checks
- Branch policies enforcement

**Tools Used**:
- Git hooks
- Pre-commit frameworks
- Linters (ESLint, Pylint, Checkstyle)

**Example**:
```
Developer writes code
  ↓
Pre-commit hook runs
  ↓
Checks for code standards
  ↓
If OK → allowed to commit
If NOT OK → commit blocked, fix required
```

#### **Step 2: Build**

**What it is**: Compiling source code into executable/deployable format

**Process**:
1. Code checkout from Git
2. Compile source code
3. Resolve dependencies
4. Linking
5. Create binary/executable

**Build Tools**:
- **Maven** (Java) - creates JAR/WAR
- **Gradle** (Java/Kotlin) - creates JAR/APK
- **MSBuild** (.NET) - creates DLL/EXE
- **npm** (JavaScript) - creates bundled JS
- **pip** (Python) - creates wheel/egg

**Build Output**:
- Compiled artifacts
- Size of artifact
- Build logs
- Dependency tree

**Example Maven Build**:
```
mvn clean install
├─ clean: removes old build
├─ compile: compiles source code
├─ test: runs unit tests
├─ package: creates JAR file
└─ install: stores in local repository
```

**Build Failure Reasons**:
- Syntax errors
- Missing dependencies
- Incompatible library versions
- Configuration issues

#### **Step 3: Artifact Management**

**What it is**: Packaging and storing compiled code

**Process**:
1. Build completes → creates artifact (JAR, WAR, image, etc.)
2. Artifact is versioned
3. Stored in repository
4. Referenced by downstream stages

**Artifact Examples**:
- Java: `app-1.0.0.jar`, `app-1.0.0.war`
- Docker: `app:v1.0.0`, `app:latest`
- Python: `app-1.0.0-py3-none-any.whl`

**Versioning Strategies**:
- **Semantic Versioning**: 1.2.3 (Major.Minor.Patch)
- **Date-based**: 2024010101
- **Build Number**: build-12345

#### **Step 4: Testing**

**What it is**: Automated verification that code works correctly

**Testing Types in Pipeline**:

| Type | When | What | Tools |
|------|------|------|-------|
| **Unit Tests** | After build | Individual functions | JUnit, NUnit, pytest |
| **Integration Tests** | After unit tests | Multiple components together | JUnit, TestNG |
| **UI Tests** | In staging | User interface | Selenium, Cypress |
| **Performance Tests** | In staging | Load/stress testing | JMeter, LoadRunner |
| **Security Tests** | In staging | OWASP top 10, vulnerabilities | OWASP ZAP, Checkmarx |

**Testing Pipeline**:
```
Code Build Success
        ↓
  Unit Tests (Fast - 5 min)
        ↓
  Integration Tests (Medium - 15 min)
        ↓
  Deploy to QA
        ↓
  UI/Selenium Tests (Slow - 30 min)
  Performance Tests
  Security Tests
        ↓
All Pass? → Approval Gate
    ↓
   NO → Developer fixed
   YES → Proceed
```

**Test Failure Actions**:
- Stop pipeline
- Notify developer
- Create bug ticket
- Email notifications
- Slack alerts

#### **Step 5: Approval Process**

**What it is**: Human review before production deployment

**Why Needed**:
- Double-check for production readiness
- Business decision on release timing
- Risk mitigation
- Compliance requirements

**Approval Gates**:
- **Dev Environment**: No approval needed
- **QA/Staging**: Maybe optional approval
- **Production**: Always required approval

**Approvers Usually**:
- QA Lead
- Tech Lead
- Product Owner
- DevOps Engineer

**Approval Workflow**:
```
Deployment Ready
        ↓
Send Approval Request
        ↓
QA Lead Reviews Tests ✓
        ↓
Product Owner Reviews Features ✓
        ↓
All Approved ✓
        ↓
Deploy to Production
```

**Approval Timeout**:
- Usually 24-72 hours
- Auto-reject if no approval
- Prevents deployment freeze

#### **Step 6: Deployment**

**What it is**: Moving code from staging to live production

**Deployment Process**:

**Blue-Green Deployment**:
```
Blue Environment (Old Version) - Live Traffic
Green Environment (New Version) - No Traffic
        ↓
            Smoke tests on Green
        ↓
            All pass?
        ↓
        Router switches traffic
        Blue → Green
        ↓
        Rollback easy (switch back to Blue)
```

**Canary Deployment**:
```
Old Version - 90% traffic
New Version - 10% traffic
        ↓
Monitor new version
        ↓
If stable: gradually increase %
        ↓
If issues: rollback
```

**Rolling Deployment**:
```
Server 1: Update
Server 2: Update (while 1 is up)
Server 3: Update (while 1,2 are up)
```

**Post-Deployment**:
- Health checks
- Smoke tests
- Monitor metrics
- Check error rates

---

### TOPIC 4: SonarQube

#### **What is SonarQube?**

**Definition**: SonarQube is a code quality and security analysis tool that automatically scans code for bugs, vulnerabilities, and code smells.

#### **Code Quality Checks**

**SonarQube Checks For**:

1. **Bugs** (~7 months to fix if not found)
   - Null pointer exceptions
   - Logic errors
   - Incorrect comparisons
   - Example: `if (obj = null)` should be `if (obj == null)`

2. **Code Smells** (maintainability issues)
   - Duplicate code blocks
   - Functions too long
   - Too many parameters
   - Unused variables/imports
   - Complex logic (cyclomatic complexity)

3. **Vulnerabilities** (security issues)
   - SQL injection risks
   - Password hardcoding
   - Insecure deserialization
   - Cross-site scripting (XSS)
   - OWASP Top 10 violations

4. **Code Coverage**
   - % of code covered by tests
   - Typical target: 80%+
   - Shows untested code

#### **Quality Gate**

**What is a Quality Gate?**

A quality gate is a set of conditions that code must pass before proceeding in pipeline.

**Example Quality Gate Rules**:
```
✓ Bugs < 5
✓ Code Coverage > 80%
✓ No critical vulnerabilities
✓ Code smell rating = A
✓ Technical debt < 5 days
✓ Duplicated lines < 3%
```

**Quality Gate Status**:
- ✓ **PASS**: Code meets all standards → proceed
- ✗ **FAILED**: Code doesn't meet standards → stop or proceed (configurable)

#### **What Happens if Code Fails Quality Gate?**

**Scenario 1: Strict Mode** (Fail the pipeline)
```
Code Built → SonarQube Analysis → Quality Gate Failed
        ↓
    Pipeline Stops
        ↓
Developer Notified
        ↓
Developer Must Fix Issues
        ↓
Re-push Code
        ↓
Quality Gate Passes ✓
```

**Scenario 2: Warning Mode** (Proceed but warn)
```
Code Built → SonarQube Analysis → Quality Gate Failed
        ↓
    Warning Logged
        ↓
    Pipeline Continues
        ↓
    Deployment Possible
        ↓
    But Issue Tracked
```

**Developer Actions to Fix**:
- Review SonarQube report
- Fix bugs (change logic)
- Increase test coverage (write more tests)
- Remove security vulnerabilities
- Fix code smells (refactor)
- Re-push code
- New analysis runs automatically

**SonarQube Report Example**:
```
Project: MyApp
Bugs: 3
  - Line 45: Null pointer risk
  - Line 67: Logic error
  - Line 89: Possible NPE

Vulnerabilities: 1
  - Line 120: SQL Injection risk

Code Smells: 15
  - Duplicate code
  - Method too long
  - Unused imports

Coverage: 65% (Target: 80%)
  - Need 15% more tests
```

---

### TOPIC 5: Build Tools

Build tools compile source code into executables/packages.

#### **Maven (Java)**

**Purpose**: Build Java applications

**Key Concepts**:
- Project Object Model (POM.xml)
- Dependency management
- Plugins for tasks

**Maven Build Lifecycle**:
```
mvn clean
├─ Clean: Delete old build (target/ folder)
└─ Removes old artifacts

mvn compile
├─ Compile source code
├─ Resolve dependencies from pom.xml
└─ Create class files in target/

mvn test
├─ Run JUnit tests
└─ Report test results

mvn package
├─ Create JAR or WAR file
└─ Package app for deployment

mvn install
├─ Install to local repository

mvn deploy
└─ Upload to Nexus/Artifactory
```

**Output Files**:
- `*.jar` - Java Archive (standalone app)
- `*.war` - Web Archive (for Tomcat/WebSphere)
- `target/` folder - Contains all build outputs

**Example pom.xml**:
```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>myapp</artifactId>
  <version>1.0.0</version>
  
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.13</version>
    </dependency>
  </dependencies>
</project>
```

#### **Gradle (Java/Kotlin)**

**Purpose**: Build Java/Kotlin/Android applications

**Advantages over Maven**:
- Faster builds
- More flexible
- Groovy DSL (easier to read)
- Better for large projects

**Gradle Build**:
```
gradle build
├─ Compile source
├─ Run tests
├─ Package JAR/WAR
└─ Store in build/ folder
```

**Output Files**:
- `*.jar`, `*.war` (same as Maven)
- `build/` folder - Contains outputs

**Example build.gradle**:
```groovy
plugins {
  id 'java'
  id 'war'
}

dependencies {
  testImplementation 'junit:junit:4.13'
}

tasks.build {
  dependsOn compileJava, compileTestJava
}
```

#### **MSBuild (.NET)**

**Purpose**: Build .NET Framework and .NET Core applications

**Key Features**:
- Integrated with Visual Studio
- Compiles C#/VB.NET code
- Creates DLL and EXE files

**MSBuild Output Files**:
- `*.dll` - Dynamic Link Library
- `*.exe` - Executable
- `bin/` folder - Contains compiled output
- `packages/` folder - NuGet dependencies

**Example**:
```
msbuild MyApp.sln /p:Configuration=Release
├─ Compile C# code
├─ Link DLLs
├─ Create executable
└─ Output to bin/Release/
```

#### **pip / setuptools (Python)**

**Purpose**: Build and distribute Python packages

**Build Process**:
```
python setup.py build
├─ Compile Python bytecode
├─ Prepare package structure
└─ Ready for distribution

python setup.py install
└─ Install package locally

pip package_name
└─ Install from PyPI repository
```

**Output Files**:
- `*.whl` - Python Wheel (binary distribution)
- `*.egg` - Python Egg (older format)
- `*.tar.gz` - Source distribution
- `dist/` folder - Contains packages

**Example setup.py**:
```python
from setuptools import setup

setup(
  name='myapp',
  version='1.0.0',
  packages=['myapp'],
  install_requires=['requests==2.25.1'],
)
```

#### **Build Tool Comparison**

| Tool | Language | Output | Speed | Learning Curve |
|------|----------|--------|-------|-----------------|
| Maven | Java | JAR/WAR | Slow | Medium |
| Gradle | Java/Kotlin | JAR/WAR | Fast | Steep |
| MSBuild | .NET | DLL/EXE | Fast | Medium |
| pip | Python | WHL/EGG | N/A | Easy |

---

### TOPIC 6: Artifact Repository

An artifact repository stores compiled code for later deployment.

#### **What is an Artifact Repository?**

**Purpose**:
- Central storage for build artifacts
- Versioning and tracking
- Dependency management
- Reuse across projects

**Artifacts Stored**:
- JAR/WAR files
- Docker images
- NPM packages
- Python packages
- DLL/EXE files

#### **Nexus (Sonatype)**

**Purpose**: Repository manager for Java, Python, Docker, etc.

**Repositories in Nexus**:
```
Nexus
├─ Maven Repositories
│  ├─ maven-releases (Release artifacts)
│  ├─ maven-snapshots (Development versions)
│  └─ maven-central (External libs)
├─ Docker Repositories
├─ npm Repositories
└─ Raw Repositories
```

**How Nexus Works**:

1. **Publishing (Deployment)**:
   ```
   Maven Build Done
        ↓
   mvn deploy
        ↓
   Uploades JAR to Nexus
        ↓
   Stored with version label
   ```

2. **Consuming (Using)**:
   ```
   Another project needs library
        ↓
   Requests from Nexus
        ↓
   Nexus sends artifact
        ↓
   Project uses it
   ```

**Nexus URL Structure**:
```
https://nexus.company.com/nexus/content/repositories/
├─ releases/com/example/myapp/1.0.0/myapp-1.0.0.jar
└─ snapshots/com/example/myapp/1.0.0-SNAPSHOT/myapp-1.0.0-20240101.jar
```

**Publishing Configuration (pom.xml)**:
```xml
<distributionManagement>
  <repository>
    <id>nexus-releases</id>
    <url>https://nexus.company.com/nexus/content/repositories/releases</url>
  </repository>
  <snapshotRepository>
    <id>nexus-snapshots</id>
    <url>https://nexus.company.com/nexus/content/repositories/snapshots</url>
  </snapshotRepository>
</distributionManagement>
```

#### **JFrog Artifactory**

**Purpose**: Similar to Nexus but more powerful

**Features**:
- Supports more repository types
- Better performance
- Advanced security features
- AI-powered insights

**Repositories Types**:
- Local (company artifacts)
- Remote (cached external repos)
- Virtual (combines multiple repos)

**Advantages over Nexus**:
- More repository types supported
- Better UI
- Advanced REST API
- More scalable for large enterprises

#### **Artifact Versioning**

**Versioning Strategies**:

1. **Semantic Versioning**: `1.2.3` (Major.Minor.Patch)
   - `1` = Major version (breaking changes)
   - `2` = Minor version (new features)
   - `3` = Patch version (bug fixes)
   - Example: `1.0.0` → `1.1.0` (new feature) → `1.1.1` (bug fix)

2. **Release vs Snapshot**:
   - **Release**: `1.0.0` (stable, final)
   - **Snapshot**: `1.0.0-SNAPSHOT` (development, changing)

3. **Date-Based**: `2024010101` (year-month-day-build)

4. **Build Number**: `build-12345`

**Example Versioning Process**:
```
Development
  ├─ Version: 1.0.0-SNAPSHOT
  ├─ Stored in snapshots repo
  ├─ Can be overwritten
  └─ Not for production

Release Ready
  ├─ Version: 1.0.0
  ├─ Stored in releases repo
  ├─ Immutable (cannot change)
  └─ Used in production

Next Development
  └─ Version: 1.0.1-SNAPSHOT
```

#### **Why Artifact Storage is Important**

1. **Traceability**
   - Know exactly what code was deployed
   - Rollback capability (deploy old version)
   - Audit trail

2. **Reusability**
   - Multiple projects can use same artifact
   - Reduces duplicate builds

3. **Performance**
   - Don't rebuild if artifact exists
   - Faster deployments
   - Efficient CI/CD

4. **Dependency Management**
   - Track dependencies of each version
   - Know which versions are compatible
   - Avoid version conflicts

5. **Release Management**
   - Separate dev and release versions
   - Clear version history
   - Easy rollback if issues

6. **Security**
   - Control who can upload/download
   - Scan artifacts for vulnerabilities
   - Archive for compliance

**Real Scenario**:
```
Day 1: Deploy version 1.0.0 to production
Day 2: Issue found in 1.0.0
Day 3: Rollback to 0.9.9 (stored in Nexus)
Day 4: Developer fixes issue
Day 5: Deploy version 1.0.1 to production
```

---

### TOPIC 7: Testing in CI/CD

#### **Testing Frameworks**

#### **JUnit (Java)**

**Purpose**: Unit testing framework for Java

**What it tests**: Individual methods/functions

**Example**:
```java
@Test
public void testCalculatorAdd() {
  Calculator calc = new Calculator();
  int result = calc.add(2, 3);
  assertEquals(5, result);  // Pass if result is 5
}

@Test(expected = IllegalArgumentException.class)
public void testDivideByZero() {
  Calculator calc = new Calculator();
  calc.divide(10, 0);  // Should throw exception
}
```

**Execution in Pipeline**:
```
mvn test
├─ Runs all tests
├─ Reports: Passed, Failed, Skipped
└─ Fails build if any test fails
```

#### **NUnit (.NET)**

**Purpose**: Unit testing framework for C#/.NET

**Example**:
```csharp
[TestClass]
public class CalculatorTests
{
  [TestMethod]
  public void TestAdd()
  {
    Calculator calc = new Calculator();
    int result = calc.Add(2, 3);
    Assert.AreEqual(5, result);
  }
}
```

#### **Selenium (Web UI Testing)**

**Purpose**: Automated testing for web applications

**What it tests**: User interface interactions

**Example**:
```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://example.com")

# Find element and click
button = driver.find_element_by_id("login_btn")
button.click()

# Check if logged in
assert "Dashboard" in driver.page_source
```

**Common Selenium Tests**:
- Login functionality
- Form submissions
- Navigation
- Button clicks
- Text validation
- Page load times

#### **pytest (Python)**

**Purpose**: Testing framework for Python

**Example**:
```python
def add(a, b):
  return a + b

def test_add():
  assert add(2, 3) == 5

def test_add_strings():
  assert add("Hello", " World") == "Hello World"
```

**Execution**:
```
pytest
├─ Discover tests
├─ Run tests
├─ Report results
└─ Exit code 0 if all pass
```

#### **Where Testing Happens in Pipeline**

**Complete Testing Pipeline**:

```
1. CODE COMMIT
        ↓
2. BUILD SUCCESS
        ↓
3. UNIT TESTS (JUnit/NUnit)         ← Developer level
   Duration: 5 minutes
   Runs locally + in pipeline
        ↓
4. CODE QUALITY (SonarQube)
   Duration: 5 minutes
        ↓
5. INTEGRATION TESTS
   Duration: 10 minutes
   Test multiple components
        ↓
6. DEPLOY TO QA
        ↓
7. UI TESTS (Selenium)              ← QA level
   Duration: 30 minutes
   Test user interface
        ↓
8. PERFORMANCE TESTS
   Duration: 20 minutes
   Load testing: Can handle X users?
        ↓
9. SECURITY TESTS
   Duration: 15 minutes
   OWASP vulnerabilities
        ↓
10. APPROVAL GATE
        ↓
11. DEPLOY TO PRODUCTION
        ↓
12. SMOKE TESTS                     ← Operations level
    Duration: 5 minutes
    Quick sanity check
```

**Testing Pyramid**:
```
         ╱╲           E2E/Manual Tests
        ╱  ╲         (Few, Slow, Expensive)
       ╱────╲
      ╱      ╲        UI/Integration Tests
     ╱        ╲      (Medium)
    ╱──────────╲
   ╱            ╲     Unit Tests
  ╱              ╲   (Many, Fast, Cheap)
 ╱────────────────╲
```

**Test Failure Handling**:
```
Test Fails
    ↓
Pipeline Stops
    ↓
Notification Sent
    ├─ Email
    ├─ Slack
    └─ Dashboard alert
    ↓
Developer Investigates
    ├─ View logs
    ├─ View failure details
    ├─ Run locally
    └─ Fix issue
    ↓
Re-push Code
    ↓
Tests Run Again
    ├─ If Pass → Continue pipeline
    └─ If Fail → Repeat above
```

---

### TOPIC 8: Approval Process

#### **Manual Approval**

**What it is**: A human review gate before production deployment

**Why Needed**:
- Business decision on release timing
- Risk assessment
- QA verification
- Compliance requirements
- Stakeholder sign-off

#### **Approval Roles**

**Typical Approvers**:

1. **QA Lead**
   - Verifies all tests passed
   - Reviews test reports
   - Checks coverage metrics
   - Quality assurance

2. **Tech Lead / Architect**
   - Reviews code changes
   - Checks for architectural compliance
   - Performance considerations

3. **Product Owner**
   - Business stakeholder
   - Decides if customer is ready
   - Feature validation

4. **DevOps Engineer**
   - Infrastructure readiness
   - Deployment process review
   - Rollback plan verification

#### **Approval Before Production Deployment**

**Approval Workflow**:

```
Stage/Staging Deployment Complete
        ↓
Approval Request Generated
        ↓
Send to Approved List
  ├─ QA Lead
  ├─ Product Owner
  └─ Tech Lead
        ↓
Approvers Review
  ├─ QA Lead: Check test reports ✓
  ├─ Product Owner: Check features ✓
  └─ Tech Lead: Check code quality ✓
        ↓
All Approved? 
  ├─ YES → Deployment approved
  └─ NO → Send rejection + reason
        ↓
If Approved → Deploy to Production
If Rejected → Stop, fix issues, re-test
```

**Approval Tools**:
- Jenkins: Manual approval step
- Azure DevOps: Approval gates
- GitHub: Required reviews
- GitLab: Merge approvals

**Example Jenkins Approval**:
```groovy
pipeline {
  stages {
    stage('Deploy to Staging') {
      steps {
        sh 'deploy-staging.sh'
      }
    }
    stage('Approval') {
      steps {
        input 'Approve deployment to production?'
      }
    }
    stage('Deploy to Production') {
      steps {
        sh 'deploy-production.sh'
      }
    }
  }
}
```

**Timeout Handling**:
- If no approval for 24-72 hours
- Automatically rejected/expires
- Prevents deployment freeze

---

### TOPIC 9: Deployment Concepts

#### **Environment Types**

**Development (Dev) Environment**:
- Developers' local machines or shared server
- Most unstable
- Frequent changes
- No approval needed
- Issues are expected

**Quality Assurance (QA) Environment**:
- Identical to production setup
- Used for testing
- More stable than Dev
- QA team tests here
- Quality gate approval needed

**Staging (Pre-Prod) Environment**:
- Exact copy of production
- Final testing before prod
- Production-like load
- Full smoke tests run
- Last chance to catch issues

**Production (Prod) Environment**:
- Live for real users
- Most critical
- Strict change control
- Full approvals required
- Highest uptime requirements
- Monitoring and alerting

**Environment Flow**:
```
Dev (Unstable) 
  ↓
QA (More Stable)
  ↓
Staging (Production-like)
  ↓
Production (Live Users)
```

#### **Kubernetes Deployment**

**What is Kubernetes?**

Container orchestration platform that automates deployment, scaling, and management of containerized applications.

**Basic Concepts**:

**Pod** - Smallest deployable unit
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
spec:
  containers:
  - name: myapp
    image: myapp:1.0.0
    ports:
    - containerPort: 8080
```

**Deployment** - Manages multiple replicas of pods
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  replicas: 3  # 3 instances running
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp
        image: myapp:1.0.0
        ports:
        - containerPort: 8080
```

**Service** - Exposes deployment to network
```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  selector:
    app: myapp
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
  type: LoadBalancer
```

**Kubernetes Deployment Process**:
```
Docker image pushed to registry
        ↓
Kubernetes deployment config
        ↓
kubectl apply -f deployment.yaml
        ↓
K8s checks available nodes
        ↓
Schedules pods on nodes
        ↓
Pulls Docker images
        ↓
Starts containers
        ↓
Service routes traffic
        ↓
Health checks monitor pods
        ↓
Auto-restart if crash
        ↓
Auto-scale if needed
```

#### **PCF (Pivotal Cloud Foundry) Deployment**

**What is PCF?**

Platform as a Service (PaaS) for deploying applications with minimal infrastructure management.

**PCF Deployment**:
```
Application Code (Git)
        ↓
cf push myapp
        ↓
PCF receives code
        ↓
Detects runtime (Java, Python, Go, etc.)
        ↓
Buildpack compiles code
        ↓
Creates droplet (executable)
        ↓
Runs on Diego cell (VM)
        ↓
Routes traffic
        ↓
Application running
```

**Advantages**:
- Automatic scaling
- Health management
- Load balancing
- Easy rollback

#### **VM Deployment (IaaS)**

**Virtual Machine Deployment**:
```
Application package (JAR, WAR, etc.)
        ↓
SSH to VM
        ↓
Stop current application
        ↓
Replace with new version
        ↓
Start new application
        ↓
Health checks
        ↓
Update load balancer (if needed)
        ↓
Old requests complete
        ↓
All traffic to new version
```

#### **Tomcat Server**

**What is Tomcat?**

Java web server for deploying Java web applications (WAR files).

**Tomcat Deployment**:
```
WAR file created by Maven
        ↓
Copy to $TOMCAT_HOME/webapps/
        ↓
Tomcat detects WAR
        ↓
Extracts application
        ↓
Loads classes
        ↓
Application running
        ↓
Access via http://server:8080/myapp
```

**Tomcat Structure**:
```
tomcat/
├─ bin/         (startup.sh, shutdown.sh)
├─ conf/        (server.xml configuration)
├─ webapps/     (deployed applications)
│  ├─ myapp/    (extracted WAR)
│  └─ ROOT/     (default app)
├─ logs/
└─ work/
```

#### **IIS Server (.NET)**

**What is IIS?**

Internet Information Services - Windows web server for .NET applications.

**IIS Deployment**:
```
.NET DLL/EXE compiled
        ↓
Copy to IIS directory
        ↓
Create IIS application pool
        ↓
Create website binding
        ↓
IIS loads application
        ↓
Application running
        ↓
Access via http://server/myapp
```

#### **Ansible / SSH Basics for Deployment**

**SSH Deployment Process**:
```
1. SSH into server
   ssh user@server.com

2. Stop current application
   ./stop.sh

3. Update code
   git pull origin main

4. Install dependencies
   npm install  (or Maven, etc.)

5. Build if needed
   npm build

6. Start new application
   ./start.sh

7. Verify running
   curl http://localhost:8080/health
```

**Ansible for Automated Deployment**:
```yaml
- name: Deploy Application
  hosts: production_servers
  tasks:
    - name: Stop current app
      service:
        name: myapp
        state: stopped

    - name: Pull latest code
      git:
        repo: https://github.com/company/myapp.git
        dest: /opt/myapp
        version: main

    - name: Install dependencies
      shell: cd /opt/myapp && npm install

    - name: Build application
      shell: cd /opt/myapp && npm build

    - name: Start application
      service:
        name: myapp
        state: started

    - name: Verify health
      uri:
        url: http://localhost:8080/health
        status_code: 200
      retries: 5
      delay: 10
```

---

### TOPIC 10: Agile Integration with DevOps

#### **Sprints**

**What is a Sprint?**

Fixed time period (usually 1-2 weeks) where team works on specific features/fixes.

**Sprint Phases**:
```
Day 1: Sprint Planning (Plan what work)
  ↓
Days 2-9: Development (Build features)
  ├─ Daily standup (15 min)
  ├─ Testing during development
  ├─ Code reviews
  └─ Continuous integration
  ↓
Day 10: Sprint Review (Show what built)
  ├─ Demo to stakeholders
  ├─ Gather feedback
  └─ Update backlog
  ↓
Day 10: Sprint Retrospective (Improve process)
  ├─ What went well?
  ├─ What needs improvement?
  └─ Action items for next sprint
```

#### **Sprint Workflow**

**Product Backlog**:
```
Feature 1: Login functionality
Feature 2: Payment processing
Feature 3: Reporting dashboard
Feature 4: Mobile app
```

**Sprint Backlog** (selected for current sprint):
```
Sprint 1 (Week of March 1):
✓ Feature 1: Login functionality
✓ Bug fix: Password reset
✓ Tech debt: Refactor authentication
```

**Daily Work**:
```
Developer picks task from Sprint Backlog
  ↓
Creates feature branch
  ↓
Writes code + tests
  ↓
Pushes to Git
  ↓
Pull request created
  ↓
Code review by teammate
  ↓
Tests automatically run (CI)
  ↓
If all pass → Merge to main
  ↓
Feature deployed to staging/QA
  ↓
QA tests feature
  ↓
If OK → Mark complete
  ↓
Pick next task
```

#### **Planning to Deployment Cycle**

**Full Cycle from Planning to Production**:

```
Sprint Planning (Week 1, Monday)
├─ Team discusses features
├─ Estimates work
├─ Selects tasks for sprint
└─ Developers start coding

Daily Development (Week 1-2)
├─ Code committed
├─ CI pipeline runs automatically
├─ Tests run
├─ Code deployed to staging
└─ QA tests

Sprint Review (Week 2, Friday)
├─ Demo to product owner
├─ Gather feedback
└─ Update backlog

Sprint Retrospective (Week 2, Friday)
├─ Team reflects
├─ Discuss improvements
└─ Plan for next sprint

Sprint 2 Planning (Week 3, Monday)
├─ Review feedback from Sprint 1
├─ Plan Sprint 2 features
├─ Development continues

Multi-Week Cycle (Every 4-8 sprints typically)
├─ Ready for production release
├─ Approval gates checked
├─ Production deployment scheduled
├─ Deploy to production
├─ Monitor
└─ Gather metrics for next cycle
```

#### **DevOps in Agile Projects**

**How DevOps Supports Agile**:

1. **Automation** - Enables rapid, safe deployments
   - Automated testing catches issues early
   - No manual deployment delays
   - Fast feedback loops

2. **Continuous Deployment** - Multiple releases per sprint
   - Features shipped to production daily
   - Quick feedback from users
   - Faster iteration

3. **Monitoring** - Real-time feedback
   - Metrics on feature usage
   - Issues detected immediately
   - Data-driven decisions

4. **Collaboration** - Shared responsibility
   - Developers care about operations
   - Operations supports development
   - Everyone owns quality

**Agile + DevOps Workflow**:
```
Agile Sprint Planning
    ↓
Development with CI
├─ Code → Git
├─ Automatic tests
├─ Deploy to staging
└─ Immediate QA feedback
    ↓
CD: Deploy multiple times per sprint
├─ Build passing → Deploy
├─ Real users test features
├─ Data collected
└─ Issues fixed quick
    ↓
Sprint Review with Real Data
├─ Show features to users
├─ Share metrics
├─ User feedback
└─ Decide on improvements
    ↓
Next Sprint
```

---

### TOPIC 11: Jenkins Interview Topics

#### **Jenkins Architecture (Master-Agent)**

**Jenkins Master** (Controller):
- Manages jobs/pipelines
- Schedules builds
- Stores configuration
- Single point for all projects
- Handles web UI access

**Jenkins Agents** (Workers):
- Execute actual builds
- Run tests
- Run deployments
- Multiple agents possible
- Parallel execution on different agents

**Architecture**:
```
Jenkins Master (Central)
  ├─ Job Definitions
  ├─ Configurations
  ├─ Build Scheduling
  ├─ Web UI
  └─ Plugins
        ↓
   (SSH/Websocket)
        ↓
Jenkins Agents (Distributed)
├─ Agent 1: Building Java projects
├─ Agent 2: Running performance tests
├─ Agent 3: Docker image builds
└─ Agent 4: Kubernetes deployments
```

**Advantages**:
- Parallel builds (multiple agents)
- Isolation (failing job doesn't affect others)
- Scaling (add more agents as needed)
- Flexibility (different OSes/tools on agents)

**Example Jenkinsfile with Agent**:
```groovy
pipeline {
  agent {
    node {
      label 'linux'  // Uses agent labeled 'linux'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install'  // Runs on agent
      }
    }
  }
}
```

#### **Jenkinsfile**

**What is Jenkinsfile?**

Pipeline as Code - Jenkins configuration stored as code in Git, not GUI.

**Benefits**:
- Version controlled
- Reviewed before execution
- Reusable across projects
- Clear documentation
- Easy to understand pipeline

**Example Jenkinsfile**:
```groovy
pipeline {
  agent any
  
  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    
    stage('Build') {
      steps {
        sh 'mvn clean compile'
      }
    }
    
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    
    stage('Build Artifact') {
      steps {
        sh 'mvn package'
      }
    }
    
    stage('Deploy') {
      steps {
        sh './deploy.sh'
      }
    }
  }
  
  post {
    always {
      junit 'target/surefire-reports/*.xml'
    }
    success {
      echo 'Deployment successful!'
    }
    failure {
      echo 'Deployment failed!'
    }
  }
}
```

#### **Declarative vs Scripted Pipeline**

**Declarative Pipeline**:
```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building...'
        sh 'mvn build'
      }
    }
  }
}
```

**Characteristics**:
- ✓ Simpler syntax
- ✓ Easier for beginners
- ✓ Pre-defined structure
- ✗ Less flexible
- ✗ Limited advanced features

**Scripted Pipeline**:
```groovy
node {
  stage('Build') {
    echo 'Building...'
    if (env.BRANCH_NAME == 'main') {
      sh 'mvn build'
    } else {
      echo 'Skip build on feature branch'
    }
  }
}
```

**Characteristics**:
- ✓ More flexible
- ✓ Full Groovy language access
- ✓ Complex logic possible
- ✗ Steeper learning curve
- ✗ More error-prone

**When to Use**:
- **Declarative**: Standard pipelines, most projects
- **Scripted**: Complex logic, advanced use cases

#### **Jenkins Plugins**

**What are Plugins?**

Extensions that add functionality to Jenkins.

**Popular Plugins**:

1. **Git Plugin** - Git source control integration
2. **Maven Plugin** - Maven build support
3. **SonarQube Scanner** - Code quality scanning
4. **Docker Plugin** - Docker image building
5. **Kubernetes Plugin** - Kubernetes deployment
6. **Email Extension** - Email notifications
7. **Slack Notifier** - Slack integration
8. **Blue Ocean** - Modern Jenkins UI
9. **Pipeline** - Pipeline support
10. **Artifactory** - Artifact management

**Plugin Installation**:
```
Jenkins -> Manage Jenkins -> Plugins
  ↓
Available tab
  ↓
Search for plugin
  ↓
Install
  ↓
Restart Jenkins (optional)
```

#### **Triggers: Polling, Webhooks, CRON**

**Polling**:
```
Jenkins periodically asks Git: "Any new commits?"
  ↓
Every 15 minutes: Check Git
  ↓
If new commits found
  ↓
Trigger build
```

Disadvantage: Wasteful, delays in detecting changes

**Webhook**:
```
Developer pushes code
  ↓
Git sends webhook to Jenkins (HTTP POST)
  ↓
Jenkins notified immediately
  ↓
Build starts immediately
```

Advantage: Instant feedback

**CRON**:
```
Schedule build for specific time
  ↓
Example: Every day at 2 AM
  ↓
2 AM: Build triggers automatically
  ↓
Usually for nightly builds, scheduled tasks
```

**Example Jenkinsfile Triggers**:
```groovy
pipeline {
  triggers {
    githubPush()                    // GitHub webhook
    poll('H/15 * * * *')            // Poll every 15 min
    cron('H 2 * * *')               // Daily 2 AM
  }
}
```

#### **Stages and Steps in Jenkins Pipeline**

**Stage** - Logical grouping of work

**Step** - Individual task within stage

**Example**:
```groovy
pipeline {
  stages {
    stage('Checkout') {           // Stage 1
      steps {
        checkout scm              // Step 1: Checkout code
      }
    }
    
    stage('Build') {              // Stage 2
      steps {
        sh 'mvn compile'          // Step 1: Compile
        sh 'mvn package'          // Step 2: Package
      }
    }
    
    stage('Test') {               // Stage 3
      steps {
        sh 'mvn test'             // Step 1: Run tests
        junit 'target/surefire-reports/*.xml'  // Step 2: Report
      }
    }
    
    stage('Deploy') {             // Stage 4
      steps {
        sh './deploy.sh'          // Step 1: Deploy
      }
    }
  }
}
```

**Pipeline Visualization**:
```
Checkout → Build → Test → Deploy
   ↓         ↓       ↓       ↓
  5sec     30sec   60sec   10sec
```

---

### TOPIC 12: Jenkins Integrations

Jenkins integrates with other tools in CI/CD pipeline.

#### **Jenkins + SonarQube**

**Integration Process**:
```
Build Success
    ↓
SonarQube Scanner runs
    ↓
Analyzes code quality
    ↓
Results sent to SonarQube server
    ↓
Quality gate checked
    ↓
Pass/Fail decision
```

**Jenkinsfile Example**:
```groovy
pipeline {
  stages {
    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('SonarQube') {
          sh 'mvn sonar:sonar -Dsonar.projectKey=my-app'
        }
        timeout(time: 1, unit: 'HOURS') {
          waitForQualityGate abortPipeline: true
        }
      }
    }
  }
}
```

#### **Jenkins + Nexus/JFrog**

**Integration for Artifact Deployment**:

```
Build Completes
    ↓
Create JAR/WAR
    ↓
Deploy to Nexus
    ↓
Nexus stores artifact
    ↓
Other jobs can consume
```

**Jenkinsfile Example**:
```groovy
pipeline {
  stages {
    stage('Publish to Nexus') {
      steps {
        sh 'mvn deploy'  // Publishes to Nexus
      }
    }
  }
}
```

#### **Jenkins + Docker**

**Integration for Container Building**:

```
Build Success
    ↓
Build Docker image
    ↓
Tag image
    ↓
Push to Docker Registry
    ↓
Image ready for deployment
```

**Jenkinsfile Example**:
```groovy
pipeline {
  stages {
    stage('Build Docker Image') {
      steps {
        script {
          app = docker.build("myapp:${BUILD_NUMBER}")
          app.push()
        }
      }
    }
  }
}
```

#### **Jenkins + Kubernetes**

**Integration for K8s Deployment**:

```
Docker Image Built
    ↓
Push to Registry
    ↓
Update K8s deployment YAML
    ↓
Apply to Kubernetes cluster
    ↓
K8s deploys pods
    ↓
Application running
```

**Jenkinsfile Example**:
```groovy
pipeline {
  stages {
    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f deployment.yaml'
        sh 'kubectl rollout status deployment/myapp'
      }
    }
  }
}
```

---

### TOPIC 13: Jenkins Interview Questions

#### **Freestyle vs Pipeline Jobs**

**Freestyle Job**:
- GUI-based configuration
- Limited flexibility
- Not version controlled
- Good for simple tasks
- Example: Single build command

**Pipeline Job**:
- Code-based (Jenkinsfile)
- More flexible
- Version controlled in Git
- Good for complex workflows
- Example: Multi-stage deployment

**When to Use**:
- **Freestyle**: Simple, one-off jobs
- **Pipeline**: Production workflows

#### **Credentials in Jenkins**

**Types of Credentials**:
1. **Username/Password**
2. **SSH Keys**
3. **Tokens** (GitHub, Docker)
4. **Certificates**

**Securing Credentials**:
```
Jenkins -> Manage Jenkins -> Credentials
    ↓
Add credentials (not visible in code)
    ↓
Reference in Jenkinsfile using ID
```

**Jenkinsfile Example**:
```groovy
pipeline {
  stages {
    stage('Git Clone') {
      steps {
        withCredentials([usernamePassword(
          credentialsId: 'github-creds',
          usernameVariable: 'GIT_USER',
          passwordVariable: 'GIT_PASS'
        )]) {
          sh '''
            git clone https://${GIT_USER}:${GIT_PASS}@github.com/repo.git
          '''
        }
      }
    }
  }
}
```

#### **Shared Library**

**What is Shared Library?**

Reusable Jenkins code shared across multiple pipelines.

**Purpose**:
- Reduce code duplication
- Standardize pipeline behavior
- Easy updates

**Example Shared Library**:
```
vars/
├─ deployToK8s.groovy
├─ runTests.groovy
└─ notifySlack.groovy

```

**Using Shared Library**:
```groovy
@Library('shared-pipeline-lib') _

pipeline {
  stages {
    stage('Deploy') {
      steps {
        deployToK8s('myapp', 'production')
      }
    }
  }
}
```

#### **Automatic Trigger After Code Push**

**GitHub Webhook Trigger**:
```
1. Configure webhook in GitHub
2. Tell GitHub to send webhook to Jenkins
3. Developer pushes code
4. GitHub sends HTTP POST to Jenkins
5. Jenkins receives notification
6. Build triggers automatically
```

**Configuration in Jenkins**:
```
GitHub Repository → Settings → Webhooks
  ↓
Add webhook
  ↓
URL: https://jenkins.company.com/github-webhook/
  ↓
Events: Push events
  ↓
Active
```

**Jenkinsfile Configuration**:
```groovy
pipeline {
  triggers {
    githubPush()  // Triggered by GitHub webhook
  }
  stages {
    stage('Build') {
      steps { /* build steps */ }
    }
  }
}
```

---

### TOPIC 14: Azure DevOps (ADO) Topics

#### **Azure DevOps Components**

**Azure Repos**:
- Git repository hosting
- Pull requests
- Branch policies
- Code reviews

**Azure Pipelines**:
- Build pipelines
- Release pipelines
- CI/CD automation
- Multi-platform support

**Azure Artifacts**:
- Package management
- NuGet, npm, Maven feeds
- Dependency management

**Azure Boards**:
- Work item tracking
- Sprint planning
- Kanban boards
- Agile reporting

**Azure Test Plans**:
- Manual testing
- Test cases
- Test suites
- Traceability

---

### TOPIC 15: Azure DevOps YAML Pipeline

**Pipeline Structure**:
```yaml
trigger:
  - main          # Trigger on main branch push

pool:
  vmImage: 'ubuntu-latest'  # Run on Linux

variables:
  buildConfiguration: 'Release'

stages:
- stage: Build
  jobs:
  - job: BuildJob
    steps:
    - task: Maven@3
      inputs:
        mavenPomFile: 'pom.xml'
        mavenOptions: '-Xmx3072m'
        javaHomeOption: 'JDKVersion'
        jdkVersionOption: '1.11'
        publishJUnitResults: true

- stage: Quality
  jobs:
  - job: SonarQube
    steps:
    - task: SonarQubePrepare@4
      inputs:
        SonarQube: 'SonarQube'
        scannerMode: 'MSBuild'
        projectKey: 'my-app'

- stage: Deploy
  jobs:
  - deployment: DeployToProd
    environment: 'production'
    strategy:
      runOnce:
        deploy:
          steps:
          - script: echo Deploying to Kubernetes
          - task: KubernetesManifest@0
            inputs:
              action: 'deploy'
              kubernetesConnection: 'k8s-prod'
              namespace: 'default'
              manifests: |
                $(Pipeline.Workspace)/manifests/deployment.yml
```

**Key Elements**:

- **trigger**: When to start pipeline
- **pool**: Where to run (Azure-hosted or self-hosted)
- **variables**: Configuration values
- **stages**: Major phases
- **jobs**: Work units within stages
- **tasks**: Individual steps
- **steps**: Shell commands or predefined tasks

---

### TOPIC 16: Azure DevOps Interview Questions

#### **Classic vs YAML Pipelines**

**Classic Pipeline**:
- GUI-based
- Visual editor
- Not version controlled
- Easier for beginners

**YAML Pipeline**:
- Code-based
- Version controlled in Git
- More powerful
- Industry standard (also used in GitHub Actions, GitLab)

#### **Approvals and Environments**

**Approval Workflow**:
```yaml
stages:
- stage: DeployToStaging
  displayName: Deploy to Staging
  jobs:
  - deployment: Deploy
    environment: 'staging'
    strategy:
      runOnce:
        deploy:
          steps:
          - script: echo Deploying to staging

- stage: ApprovalGate
  displayName: Wait for Production Approval
  jobs:
  - job: waitForValidation
    displayName: Hold for manual validation
    pool: server
    timeoutInMinutes: 1440
    steps:
    - task: ManualValidation@0
      inputs:
        notifyUsers: 'qa-team@company.com'

- stage: DeployToProduction
  displayName: Deploy to Production
  condition: succeeded()
  dependsOn: ApprovalGate
  jobs:
  - deployment: Deploy
    environment: 'production'
    strategy:
      runOnce:
        deploy:
          steps:
          - script: echo Deploying to production
```

#### **Secrets Management**

**Storing Secrets**:
```
Azure DevOps → Library → Secure Files/Variables
  ↓
Store passwords, API keys, certificates
  ↓
Not visible in pipeline logs
  ↓
Reference in YAML using secure variable syntax
```

**Using Secrets in Pipeline**:
```yaml
variables:
  API_KEY: $(ApiKey)  # Reference stored secret

steps:
- script: |
    curl https://api.example.com/deploy \
    -H "Authorization: Bearer $(API_KEY)"
  env:
    API_KEY: $(ApiKey)
```

#### **GitHub/SonarQube Integration**

**GitHub Integration**:
- Connect GitHub repos to Azure DevOps
- Trigger on GitHub push
- Pull request validation
- Status checks

**SonarQube Integration**:
- Code quality scanning in pipeline
- Break build if quality fails
- Report results in ADO

---

### TOPIC 17: Real-Time DevOps Scenario

#### **Java App End-to-End Pipeline**

**Complete Workflow**:

```
1. Developer writes Java code
   └─ Creates feature branch
   └─ Commits to GitHub

2. GitHub triggers webhook
   └─ Sends notification to Jenkins

3. Jenkins receives trigger
   └─ Creates new build job

4. Checkout stage
   └─ Git clone code
   └─ Checkout feature branch

5. Build stage
   └─ mvn clean install
   └─ Compiles Java code
   └─ Creates target/ with compiled classes

6. Unit Testing stage
   └─ mvn test
   └─ Runs JUnit tests
   └─ Reports: 450/450 tests passed ✓

7. SonarQube Analysis stage
   └─ Scans code for bugs/vulnerabilities
   └─ Results: 0 bugs, 1 vulnerability
   └─ Quality Gate: PASS ✓

8. Build Artifact stage
   └─ mvn package
   └─ Creates myapp-1.0.0.jar

9. Publish to Nexus stage
   └─ mvn deploy
   └─ Uploads JAR to Nexus repository
   └─ Versioned as: releases/myapp/1.0.0/

10. Docker Image Build stage
    └─ Create Dockerfile
    └─ docker build -t myapp:1.0.0 .
    └─ Resulting image: 250 MB

11. Push to Docker Registry stage
    └─ docker login registry.company.com
    └─ docker push registry.company.com/myapp:1.0.0
    └─ Image stored in registry

12. Deploy to QA stage
    └─ Update deployment.yaml: image: registry.company.com/myapp:1.0.0
    └─ kubectl apply -f deployment.yaml -n qa
    └─ 3 replicas of pod running in QA
    └─ Service exposes on port 8080

13. Integration Testing stage
    └─ Run Selenium tests
    └─ 200 UI tests run
    └─ All pass ✓

14. Performance Testing stage
    └─ JMeter load test
    └─ Simulate 1000 concurrent users
    └─ App handles load ✓

15. Manual Approval stage
    └─ QA Lead reviews:
       ├─ All tests passed ✓
       ├─ No critical bugs ✓
       ├─ Performance acceptable ✓
    └─ Product Owner approves
    └─ Approval granted ✓

16. Deploy to Production stage
    └─ kubectl apply -f deployment.yaml -n production
    └─ Rolling deployment:
       ├─ Pod 1: Old version → New version (healthy)
       ├─ Pod 2: Old version → New version (healthy)
       ├─ Pod 3: Old version → New version (healthy)
    └─ All users on new version ✓

17. Smoke Testing stage
    └─ curl http://myapp-prod/health
    └─ Response: 200 OK ✓
    └─ curl http://myapp-prod/metrics
    └─ Metrics: 500 req/sec ✓

18. Monitoring stage
    └─ Prometheus collects metrics:
       ├─ CPU: 45%
       ├─ Memory: 600MB
       ├─ Error rate: 0%
    └─ Grafana displays dashboards
    └─ Alerts configured
    └─ All normal ✓

19. Logging stage
    └─ ELK Stack collecting logs
    └─ Kibana for log search
    └─ No errors in logs ✓

20. Success! 
    └─ Deployment to production complete
    └─ Real users running new version
    └─ Feedback loop starts
    └─ Any issues → developer notified immediately
```

**Pipeline Execution Time**:
```
Build:15 min + Test: 30 min + QA Approval: 2 hours
+ Deployment: 5 min + Smoke test: 2 min
= Total: ~2.5-3 hours from code push to production
```

---

### TOPIC 18: Additional Tools to Know

#### **GitHub / GitLab / Bitbucket**

**Version Control Platforms**:
- Repositories
- Pull requests
- Branching strategies
- Code reviews
- API integrations

#### **Maven / Gradle / MSBuild**

- Build compilation and packaging tools
- Dependency management
- Create deployable artifacts

#### **Nexus / JFrog**

- Artifact repositories
- Store and manage build outputs
- Versioning
- Distribution

#### **Docker**

- Containerization platform
- Package application with dependencies
- Ensure consistency across environments
- Easy deployment and scaling

#### **Kubernetes / Helm**

- **Kubernetes**: Container orchestration
- **Helm**: Kubernetes package manager
- Template-based deployment
- Version management

#### **AWS / Azure**

- Cloud platforms
- Infrastructure as a Service (IaaS)
- Deployment targets
- Managed services

#### **Prometheus / Grafana**

- **Prometheus**: Metrics collection
- **Grafana**: Visualization
- Monitoring and alerting
- Performance tracking

#### **GitHub Actions**

- GitHub's CI/CD platform
- Integrated with repositories
- Workflows stored in YAML
- Similar to Jenkins/Azure DevOps



### Recommended Sequential Path:

1. **DevOps Basics**
   - Understanding DevOps principles
   - Dev + Ops collaboration model

2. **CI/CD Pipeline**
   - Pipeline overview
   - Pipeline stages in detail

3. **SonarQube**
   - Code quality checks
   - Quality gates

4. **Build Tools**
   - Maven fundamentals
   - Build process and output

5. **Artifact Repository**
   - Nexus / JFrog
   - Artifact versioning

6. **Testing**
   - Testing frameworks
   - Testing in pipeline

7. **Deployment**
   - Deployment environments
   - Deployment strategies

8. **Jenkins**
   - Jenkins architecture
   - Pipeline creation

9. **Azure DevOps**
   - Azure DevOps basics
   - YAML pipelines

10. **Docker & Kubernetes**
    - Containerization
    - Kubernetes deployment

11. **Monitoring**
    - Prometheus / Grafana
    - Application monitoring

---

## Priority Topics for Interview Preparation

### Must-Know Topics (Study First):

- ⭐ **DevOps Basics**
  - Definition and benefits
  - Dev + Ops collaboration
  
- ⭐ **CI/CD Pipeline Stages**
  - Code validation → Build → Testing → Approval → Deployment
  
- ⭐ **SonarQube**
  - Code quality, quality gates
  - Impact of failed gates
  
- ⭐ **Maven / Build Process**
  - Build lifecycle
  - Output artifacts
  
- ⭐ **Artifact Repository**
  - Nexus / JFrog
  - Versioning strategy
  
- ⭐ **Jenkins Pipeline**
  - Master-Agent architecture
  - Declarative vs Scripted
  - Jenkinsfile structure
  - Triggers and stages
  
- ⭐ **Azure DevOps Pipeline**
  - YAML structure
  - Trigger, pool, steps
  - Integrations (SonarQube, Maven)
  
- ⭐ **Docker + Kubernetes Deployment**
  - Container concepts
  - Kubernetes deployment flow
  
- ⭐ **Real-Time Scenario**
  - Complete pipeline workflow
  - GitHub → Jenkins → SonarQube → Maven → Nexus → Tests → Docker → Kubernetes → Monitoring

---

## Study Checklist

### Phase 1: Foundation (Weeks 1-2)
- [ ] DevOps meaning and importance
- [ ] Dev + Ops collaboration concepts
- [ ] CI/CD pipeline overview
- [ ] Pipeline stages explanation

### Phase 2: Quality & Build (Weeks 3-4)
- [ ] SonarQube quality checks
- [ ] Quality gate failures
- [ ] Maven build tool
- [ ] Build tool outputs
- [ ] Gradle, MSBuild, pip basics

### Phase 3: Artifact Management (Week 5)
- [ ] Nexus repository
- [ ] JFrog Artifactory
- [ ] Artifact versioning
- [ ] Importance of artifact storage

### Phase 4: Testing & Approval (Weeks 6-7)
- [ ] JUnit, NUnit, Selenium, PyTest
- [ ] Testing location in pipeline
- [ ] Manual approval process
- [ ] BA / Product owner role

### Phase 5: Deployment Concepts (Week 8)
- [ ] Environment types (Dev, QA, Staging, Prod)
- [ ] Kubernetes deployment
- [ ] PCF deployment
- [ ] Tomcat / IIS servers
- [ ] Ansible / SSH basics

### Phase 6: Agile Integration (Week 9)
- [ ] Sprints and sprint workflow
- [ ] Planning to deployment cycle
- [ ] DevOps in Agile projects

### Phase 7: Jenkins Mastery (Weeks 10-11)
- [ ] Jenkins architecture
- [ ] Jenkinsfile creation
- [ ] Declarative vs Scripted pipelines
- [ ] Jenkins plugins
- [ ] Triggers (polling, webhooks, CRON)
- [ ] Freestyle vs Pipeline jobs
- [ ] Credentials management
- [ ] Shared library

### Phase 8: Azure DevOps (Weeks 12-13)
- [ ] Repos, Pipelines, Artifacts, Boards
- [ ] YAML pipeline structure
- [ ] Classic vs YAML pipelines
- [ ] Approvals and environments
- [ ] Secrets management
- [ ] GitHub/SonarQube integration

### Phase 9: Docker & Kubernetes (Weeks 14-15)
- [ ] Docker containerization
- [ ] Kubernetes deployment
- [ ] Helm charts

### Phase 10: Monitoring & Tools (Weeks 16-17)
- [ ] Prometheus / Grafana
- [ ] GitHub / GitLab / Bitbucket
- [ ] GitHub Actions

### Phase 11: Final Review (Week 18)
- [ ] Real-time scenario walkthrough
- [ ] Mock interview questions
- [ ] End-to-end pipeline explanation

---

## Key Interview Questions to Prepare

### DevOps & CI/CD
1. What is DevOps and why is it important?
2. Explain CI/CD pipeline stages with real examples
3. What is SonarQube and what happens if code fails quality gates?

### Build & Artifacts
4. What is Maven and what files does it generate?
5. Explain artifact versioning and repository management
6. What is the difference between Nexus and JFrog Artifactory?

### Jenkins
7. Explain Jenkins Master-Agent architecture
8. What is the difference between Freestyle and Pipeline jobs?
9. What is a Jenkinsfile and how does it work?
10. Declarative vs Scripted pipelines - advantages of each?
11. How do you trigger Jenkins jobs automatically?

### Azure DevOps
12. What is the difference between Classic and YAML pipelines?
13. Explain Azure DevOps YAML pipeline structure
14. How do you manage secrets in Azure DevOps?

### Deployment
15. Explain different deployment environments
16. How would you deploy to Kubernetes?
17. What is the role of approval gates in deployment?

### Real-Time Scenario
18. Walk me through a Java application end-to-end pipeline

---

## Related Documentation Files

- [JENKINS_TERRAFORM_AZURE_PIPELINE_GUIDE.md](JENKINS_TERRAFORM_AZURE_PIPELINE_GUIDE.md)
- [GITHUB_ACTIONS_INFRASTRUCTURE_DEPLOYMENT.md](GITHUB_ACTIONS_INFRASTRUCTURE_DEPLOYMENT.md)
- [KUBERNETES_CONFIGURATIONS_SECRETS.md](KUBERNETES_CONFIGURATIONS_SECRETS.md)
- [TERRAFORM_AZURE_COMPLETE_GUIDE.md](TERRAFORM_AZURE_COMPLETE_GUIDE.md)

---

## Tips for Success

✅ **Study Systematically**: Follow the learning order - don't skip ahead  
✅ **Hands-On Practice**: Set up Jenkins, Azure DevOps, Docker locally  
✅ **Real-World Scenarios**: Understand complete pipeline flows  
✅ **Integration Focus**: Learn how tools work together  
✅ **Interview Focus**: Practice answering real interview questions  
✅ **Documentation**: Take notes for each tool and concept  
✅ **Review Regularly**: Revisit earlier topics during later phases  

---

**Last Updated**: April 3, 2026  
**Status**: Ready for study
