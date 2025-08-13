# WPILib CLI Templates
The `templates` directory contains WPILib templates. 

These templates define the initial file structure, Java code, Gradle configuration, and vendor dependencies for various WPILib robot project types.

## 📂 Directory Structure
Each template is stored in its own folder.

Inside each template folder, you'll typically find:
- Java source code
- `.vscode` settings and launch configurations
- `.wpilib` directory containing the WPILib configuration file
- Gradle build scripts and wrapper files
- `vendordeps` directory
- A `manifest.json` file

Example (`commandbasedskeleton`):
```
commandbasedskeleton/
 ├── .vscode/
 ├── .wpilib/
 ├── gradle/wrapper/
 ├── vendordeps/
 ├── .gitignore
 ├── WPILib-License.md
 ├── build.gradle
 ├── gradlew
 ├── gradlew.bat
 ├── settings.gradle
 ├── Main.java
 ├── Robot.java
 ├── RobotContainer.java
 └── manifest.json
```

> [!NOTE]
> You don't need to put all the Java files in `src/main/java/frc/robot/`!
> You can put them in the root directory as long as they are in the `manifest.json` file.

## 📜 Template Metadata (`templates.json`)
The file `templates.json` in the `templates/` directory defines all available templates.

Check out their [templates.json](https://github.com/wpilibsuite/allwpilib/blob/main/wpilibjExamples/src/main/java/edu/wpi/first/wpilibj/templates/templates.json) from WPILib repo

## 📝 Manifest File (`manifest.json`)
Each template folder contains a `manifest.json` file, which tells the tool exactly which files to include when creating a new project.

It has two keys:

| Key           | Description                            |
| ------------- |----------------------------------------|
| `build_files` | Gradle, WPILib, and IDE settings Files |
| `code_files`  | Java files for the template            |

Example:
```json
{
  "build_files": [
    ".vscode/launch.json",
    ".vscode/settings.json",
    ".wpilib/wpilib_preferences.json",
    "gradle/wrapper/gradle-wrapper.jar",
    "gradle/wrapper/gradle-wrapper.properties",
    "vendordeps/WPILibNewCommands.json",
    ".gitignore",
    "WPILib-License.md",
    "build.gradle",
    "gradlew",
    "gradlew.bat",
    "settings.gradle"
  ],
  "code_files": [
    "Main.java",
    "Robot.java",
    "RobotContainer.java"
  ]
}

```
You **must** add all required files to the manifest so the CLI knows exactly what to copy.

## 🛠️ Adding a New Template
1. Create a new folder inside `templates/` with a unique name (matches `foldername` in `templates.json`)
2. Copy in all required Java, Gradle, `.vscode`, `.wpilib`, and vendor dependency files
3. Create a `manifest.json` listing all build and code files
4. Add an entry to `templates.json` with metadata about the template
5. Execute:
```base
wpilib-cli --create
# or
wpilib-cli -c
```
