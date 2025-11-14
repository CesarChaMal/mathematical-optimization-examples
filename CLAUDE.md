# CLAUDE.md - AI Assistant Guide

## Project Overview

This is a **Mathematical Optimization Examples** repository - a Kotlin-based project demonstrating mathematical optimization algorithms and techniques. The project uses Maven for dependency management and build automation.

**Project Metadata:**
- **Group ID:** org.nield
- **Artifact ID:** mathematical-optimization-examples
- **Version:** 1.0-SNAPSHOT
- **Language:** Kotlin 1.1.61
- **Build Tool:** Maven
- **Testing Framework:** JUnit 4.12

## Repository Structure

```
mathematical-optimization-examples/
├── pom.xml                          # Maven project configuration
├── .gitignore                       # Git ignore rules (IntelliJ IDEA)
└── src/
    └── main/
        └── kotlin/
            └── org/
                └── nield/
                    └── MultiplantOptimizer.kt   # Main optimization example
```

### Key Directories

- **`src/main/kotlin/`** - Main Kotlin source code
  - Package: `org.nield`
  - Primary namespace for optimization algorithms

- **`src/test/kotlin/`** - Test code (to be created as needed)
  - Uses JUnit for testing
  - Should mirror main source package structure

## Technology Stack

### Core Technologies
1. **Kotlin 1.1.61** - Primary programming language
2. **Maven** - Build and dependency management
3. **JUnit 4.12** - Unit testing framework

### Dependencies
- `kotlin-stdlib` - Kotlin standard library
- `kotlin-test-junit` - Kotlin JUnit integration (test scope)
- `junit` - JUnit testing framework (test scope)

## Development Workflows

### Building the Project

```bash
# Compile the project
mvn compile

# Run tests
mvn test

# Package as JAR
mvn package

# Clean build artifacts
mvn clean

# Full clean build
mvn clean install
```

### Running Examples

Since this is an examples project, individual optimization examples should be:
1. Implemented as standalone Kotlin files with `main()` functions
2. Runnable via Maven exec plugin or IDE
3. Well-documented with comments explaining the optimization approach

### Adding New Optimization Examples

When creating new optimization examples:

1. **Create new Kotlin file** in `src/main/kotlin/org/nield/`
2. **Use descriptive naming** (e.g., `KnapsackOptimizer.kt`, `TravelingSalesmanSolver.kt`)
3. **Include package declaration**: `package org.nield`
4. **Add main function** for runnable examples:
   ```kotlin
   package org.nield

   fun main(args: Array<String>) {
       // Optimization example code
   }
   ```

5. **Document the algorithm** with KDoc comments
6. **Add unit tests** in `src/test/kotlin/org/nield/`

### Testing Conventions

- **Test file naming:** `<ClassName>Test.kt` (e.g., `MultiplantOptimizerTest.kt`)
- **Test package:** Should mirror main package (`org.nield`)
- **Test framework:** JUnit 4.12
- **Assertion style:** Use Kotlin's test assertions and JUnit assertions

Example test structure:
```kotlin
package org.nield

import org.junit.Test
import kotlin.test.assertEquals

class MultiplantOptimizerTest {
    @Test
    fun testOptimization() {
        // Test implementation
    }
}
```

## Code Conventions

### Kotlin Style Guidelines

1. **Naming Conventions:**
   - Classes: PascalCase (e.g., `MultiplantOptimizer`)
   - Functions: camelCase (e.g., `calculateOptimalSolution`)
   - Constants: UPPER_SNAKE_CASE (e.g., `MAX_ITERATIONS`)
   - Variables: camelCase (e.g., `totalCost`)

2. **File Organization:**
   - One public class per file
   - File name should match the class name
   - Package declaration at top
   - Imports after package declaration

3. **Documentation:**
   - Use KDoc comments for public APIs
   - Include algorithm complexity information where relevant
   - Explain optimization constraints and objectives

4. **Code Structure:**
   - Prefer immutable values (`val`) over mutable (`var`)
   - Use data classes for model objects
   - Leverage Kotlin's null safety features
   - Use extension functions where appropriate

### Mathematical Optimization Conventions

When implementing optimization examples:

1. **Clear problem definition:**
   - State the objective function
   - List all constraints
   - Define decision variables

2. **Algorithm documentation:**
   - Specify the optimization technique used (linear programming, genetic algorithms, etc.)
   - Note time and space complexity
   - Include references to algorithms/papers when applicable

3. **Input/Output clarity:**
   - Clearly define input parameters
   - Show expected output format
   - Include sample data for examples

## AI Assistant Guidelines

### When Modifying Code

1. **Always preserve package structure** - Keep `org.nield` as the base package
2. **Maintain Maven compatibility** - Ensure changes work with existing pom.xml
3. **Follow Kotlin idioms** - Use Kotlin-specific features appropriately
4. **Add tests for new functionality** - Create corresponding test files
5. **Update documentation** - Keep comments and KDoc current

### When Adding Dependencies

1. Add new dependencies to `pom.xml` in the `<dependencies>` section
2. Respect scope (compile, test, provided)
3. Use properties for version management when adding multiple related dependencies
4. Prefer stable, well-maintained libraries

Example:
```xml
<dependency>
    <groupId>com.example</groupId>
    <artifactId>optimization-lib</artifactId>
    <version>${optimization.version}</version>
</dependency>
```

### When Creating New Examples

1. **Start with a clear problem statement** in comments
2. **Implement step-by-step** with explanatory comments
3. **Include sample inputs/outputs** in the documentation
4. **Add error handling** for invalid inputs
5. **Consider edge cases** in the optimization logic

### Common Optimization Topics to Implement

Based on the project name and structure, consider implementing:

- **Linear Programming** problems
- **Integer Programming** examples
- **Multi-objective optimization**
- **Supply chain optimization** (MultiplantOptimizer suggests this)
- **Resource allocation problems**
- **Scheduling algorithms**
- **Network flow optimization**
- **Combinatorial optimization**

### File Templates

#### Main Class Template
```kotlin
package org.nield

/**
 * [Brief description of the optimization problem]
 *
 * Objective: [What we're optimizing]
 * Constraints: [What limitations exist]
 * Algorithm: [Optimization technique used]
 */
class ExampleOptimizer {

    fun optimize(): Solution {
        // Implementation
    }
}

fun main(args: Array<String>) {
    val optimizer = ExampleOptimizer()
    val solution = optimizer.optimize()
    println(solution)
}
```

#### Test Template
```kotlin
package org.nield

import org.junit.Test
import kotlin.test.assertEquals
import kotlin.test.assertNotNull

class ExampleOptimizerTest {

    @Test
    fun testBasicOptimization() {
        val optimizer = ExampleOptimizer()
        val solution = optimizer.optimize()
        assertNotNull(solution)
    }
}
```

## Git Workflow

### Branch Strategy
- **Main branch:** Contains stable, working code
- **Feature branches:** Use descriptive names (e.g., `feature/knapsack-solver`, `fix/optimizer-bug`)
- **Claude branches:** AI-generated changes use `claude/` prefix

### Commit Messages
Follow conventional commit format:
```
<type>: <description>

[optional body]

[optional footer]
```

Types: `feat`, `fix`, `docs`, `test`, `refactor`, `chore`

Examples:
- `feat: add traveling salesman optimization example`
- `fix: correct constraint calculation in MultiplantOptimizer`
- `docs: update README with algorithm explanations`
- `test: add unit tests for optimizer validation`

### Before Committing
1. Ensure code compiles: `mvn compile`
2. Run tests: `mvn test`
3. Check for code style issues
4. Update documentation if needed

## IDE Configuration

### IntelliJ IDEA (Recommended)
- Project files (`.iml`, `.idea/`) are gitignored
- Import as Maven project
- Kotlin plugin should be enabled
- Configure Kotlin compiler compatibility: 1.1.61

### Build Configuration
- **Source encoding:** UTF-8
- **Source directory:** `src/main/kotlin`
- **Test directory:** `src/test/kotlin`
- **Output:** JAR packaging

## Troubleshooting

### Common Issues

1. **Kotlin version mismatch:**
   - Ensure IDE Kotlin plugin matches pom.xml version (1.1.61)
   - Run `mvn clean install` to rebuild

2. **Maven dependency issues:**
   - Delete `~/.m2/repository` cache if needed
   - Run `mvn dependency:resolve` to re-download

3. **Test failures:**
   - Check JUnit version compatibility
   - Verify test package structure matches main

## Project Evolution

As this project grows, consider:

1. **Adding more dependencies** for optimization libraries (e.g., OptaPlanner, Apache Commons Math)
2. **Creating sub-packages** for different optimization categories
3. **Adding README.md** with user-facing documentation
4. **Including example data files** for realistic problem instances
5. **Adding benchmarking** to compare algorithm performance
6. **Documentation site** using KDoc and Dokka

## Resources

### Kotlin Resources
- [Kotlin Documentation](https://kotlinlang.org/docs/home.html)
- [Kotlin Coding Conventions](https://kotlinlang.org/docs/coding-conventions.html)

### Maven Resources
- [Maven Getting Started](https://maven.apache.org/guides/getting-started/)
- [Kotlin Maven Plugin](https://kotlinlang.org/docs/maven.html)

### Optimization Resources
- Research papers on specific algorithms
- Optimization library documentation
- Academic resources on operations research

---

**Last Updated:** 2025-11-13
**Project Status:** Initial setup phase - ready for optimization examples implementation
