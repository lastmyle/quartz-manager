# Using Quartz Manager from LastMyle GitHub Packages

## Maven Configuration

To use Quartz Manager packages from LastMyle's GitHub Packages in your Maven project:

### 1. Add Repository to your `pom.xml`:

```xml
<repositories>
  <repository>
    <id>github</id>
    <url>https://maven.pkg.github.com/lastmyle/quartz-manager</url>
  </repository>
</repositories>
```

### 2. Add Dependencies:

```xml
<dependencies>
  <!-- Quartz Manager API -->
  <dependency>
    <groupId>it.fabioformosa.quartz-manager</groupId>
    <artifactId>quartz-manager-starter-api</artifactId>
    <version>4.0.12</version>
  </dependency>
  
  <!-- Quartz Manager Security (optional) -->
  <dependency>
    <groupId>it.fabioformosa.quartz-manager</groupId>
    <artifactId>quartz-manager-starter-security</artifactId>
    <version>4.0.12</version>
  </dependency>
  
  <!-- Quartz Manager Persistence (optional) -->
  <dependency>
    <groupId>it.fabioformosa.quartz-manager</groupId>
    <artifactId>quartz-manager-starter-persistence</artifactId>
    <version>4.0.12</version>
  </dependency>
  
  <!-- Quartz Manager UI (optional) -->
  <dependency>
    <groupId>it.fabioformosa.quartz-manager</groupId>
    <artifactId>quartz-manager-starter-ui</artifactId>
    <version>4.0.12</version>
  </dependency>
</dependencies>
```

### 3. Configure Authentication:

Create or update `~/.m2/settings.xml`:

```xml
<settings>
  <servers>
    <server>
      <id>github</id>
      <username>YOUR_GITHUB_USERNAME</username>
      <password>YOUR_GITHUB_TOKEN</password>
    </server>
  </servers>
</settings>
```

To create a GitHub token:
1. Go to GitHub Settings → Developer settings → Personal access tokens
2. Generate new token (classic) with `read:packages` permission
3. Use this token as the password in settings.xml

## Gradle Configuration

For Gradle projects, add to `build.gradle`:

```gradle
repositories {
    mavenCentral()
    maven {
        url = uri("https://maven.pkg.github.com/lastmyle/quartz-manager")
        credentials {
            username = project.findProperty("gpr.user") ?: System.getenv("USERNAME")
            password = project.findProperty("gpr.key") ?: System.getenv("TOKEN")
        }
    }
}

dependencies {
    implementation 'it.fabioformosa.quartz-manager:quartz-manager-starter-api:4.0.12'
    // Add other modules as needed
}
```

## Available Packages

- `quartz-manager-common` - Common utilities and classes
- `quartz-manager-starter-api` - REST API for Quartz scheduler
- `quartz-manager-starter-security` - Security layer with JWT support
- `quartz-manager-starter-persistence` - Database persistence for jobs
- `quartz-manager-starter-ui` - Web UI components
- `quartz-manager-web-showcase` - Example web application

## Version Information

- Current Version: 4.0.12
- Java Version: 17+
- Spring Boot: 2.5.6
- SpringDoc OpenAPI: 2.2.0