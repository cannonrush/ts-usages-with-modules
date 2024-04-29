# "Unused" warning for TypeScript in a Gradle module
IntelliJ IDEA (2024.1) _stops_ detecting TS usages if Gradle modules are involved. 
This means:
- "Find usages" shows no results
- Refactoring operations do not work correctly
- "Unused function" warning is shown

This is a minimal reproducible example of the issue.

1. Open the project in IDEA and run `pnpm install -r` to set up the pnpm workspace
2. Navigate to [**exportedFunction** declaration](lib/index.ts) 
and observe that it's [usage in **app** module](app/index.ts) is not recognised.
3. Open [**settings.gradle.kts**](settings.gradle.kts) and comment out the `includes(...)` statements, 
then load Gradle changes and see that "usages" are working as expected
