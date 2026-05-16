# 🚀 Selenium Hybrid Automation Framework

[![Java](https://img.shields.io/badge/Java-11-ED8B00?style=flat-square&logo=openjdk&logoColor=white)](https://www.java.com)
[![Selenium](https://img.shields.io/badge/Selenium-4.18-43B02A?style=flat-square&logo=selenium&logoColor=white)](https://selenium.dev)
[![Cucumber](https://img.shields.io/badge/Cucumber-7.15-23D96C?style=flat-square&logo=cucumber&logoColor=white)](https://cucumber.io)
[![TestNG](https://img.shields.io/badge/TestNG-7.9-FF6C37?style=flat-square)](https://testng.org)
[![Maven](https://img.shields.io/badge/Maven-3.x-C71A36?style=flat-square&logo=apachemaven&logoColor=white)](https://maven.apache.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

A **production-grade, scalable BDD Hybrid Automation Framework** built with Selenium WebDriver, Java, TestNG, and Cucumber — designed to simulate real-world enterprise test automation for a web application.

---

## 📁 Project Structure

```
selenium-hybrid-framework/
├── src/
│   ├── main/java/com/automationexercise/
│   │   ├── config/
│   │   │   └── ConfigReader.java          # Reads config.properties
│   │   ├── pages/
│   │   │   ├── BasePage.java              # Reusable Selenium wrapper methods
│   │   │   ├── HomePage.java              # Home page POM
│   │   │   ├── LoginPage.java             # Login page POM
│   │   │   ├── ProductsPage.java          # Products page POM
│   │   │   ├── CartPage.java              # Cart page POM
│   │   │   └── DashboardPage.java         # Dashboard page POM
│   │   └── utils/
│   │       ├── DriverManager.java         # ThreadLocal WebDriver management
│   │       └── ScreenshotUtil.java        # Auto screenshot on failure
│   └── test/
│       ├── java/com/automationexercise/
│       │   ├── stepdefinitions/
│       │   │   └── LoginStepDefinitions.java
│       │   ├── hooks/
│       │   │   └── Hooks.java             # Before/After lifecycle hooks
│       │   └── runners/
│       │       └── TestRunner.java        # Cucumber + TestNG runner
│       └── resources/
│           ├── features/
│           │   ├── Login.feature          # Login BDD scenarios
│           │   └── Products.feature       # Product BDD scenarios
│           └── config/
│               └── config.properties      # Environment config
├── reports/                               # Auto-generated test reports
├── testng.xml                             # TestNG suite configuration
├── pom.xml                                # Maven dependencies
└── Jenkinsfile                            # CI/CD pipeline config
```

---

## ✨ Framework Features

| Feature | Details |
|---|---|
| **Design Pattern** | Page Object Model (POM) |
| **BDD Framework** | Cucumber 7 with Gherkin syntax |
| **Test Runner** | TestNG with parallel execution support |
| **Browser Support** | Chrome, Firefox, Edge |
| **Driver Management** | WebDriverManager (auto driver setup) |
| **Thread Safety** | ThreadLocal WebDriver for parallel runs |
| **Reporting** | Extent Reports + Cucumber HTML Reports |
| **Screenshots** | Auto-capture on test failure |
| **Logging** | Log4j2 integration |
| **CI/CD Ready** | Jenkins pipeline integration |

---

## 🛠️ Prerequisites

- Java JDK 11+
- Maven 3.8+
- Chrome / Firefox / Edge browser
- Git

---

## ⚡ Quick Start

### 1. Clone the repository
```bash
git clone https://github.com/anandtomarhub-ops/selenium-hybrid-framework.git
cd selenium-hybrid-framework
```

### 2. Install dependencies
```bash
mvn clean install -DskipTests
```

### 3. Run all regression tests
```bash
mvn clean test
```

### 4. Run specific tags
```bash
# Run only Smoke tests
mvn clean test -Dcucumber.filter.tags="@SmokeTest"

# Run only Login tests
mvn clean test -Dcucumber.filter.tags="@Login"

# Run only Negative tests
mvn clean test -Dcucumber.filter.tags="@NegativeTest"
```

### 5. Run on different browsers
```bash
# Run on Firefox
mvn clean test -Dbrowser=firefox

# Run on Edge
mvn clean test -Dbrowser=edge
```

---

## 📊 Test Reports

After execution, reports are generated at:

```
reports/
├── ExtentReport.html        # Detailed Extent Report with screenshots
├── cucumber-html-report.html # Cucumber HTML Report
└── screenshots/             # Failure screenshots
```

Open `reports/ExtentReport.html` in any browser to view the detailed report.

---

## 🔄 CI/CD Integration (Jenkins)

This framework is **Jenkins-ready**. To configure:

1. Create a new Pipeline job in Jenkins
2. Point it to this repository
3. Jenkins will auto-detect the `Jenkinsfile` and run the pipeline

**Pipeline stages:**
- Checkout → Build → Test → Publish Report

---

## 🏷️ Tag Strategy

| Tag | Purpose |
|---|---|
| `@Regression` | All regression tests |
| `@SmokeTest` | Critical path / smoke tests |
| `@Login` | Login module tests |
| `@Products` | Product module tests |
| `@PositiveTest` | Happy path scenarios |
| `@NegativeTest` | Error/validation scenarios |

---

## 👨‍💻 Author

**Anand Tomar**
- 💼 [LinkedIn](https://www.linkedin.com/in/anand-tomar-03411420b/)
- 📧 [tomaranand968@gmail.com](mailto:tomaranand968@gmail.com)
- 🐙 [GitHub](https://github.com/anandtomarhub-ops)

---

## 📄 License

This project is licensed under the MIT License.
