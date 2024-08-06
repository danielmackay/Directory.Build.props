# Directory.Build.props

Add global static code analysis to your .NET projects.  This avoids having to update each `.csproj` file individually.

## Usage

Create a `Directory.Build.props` file in the root of your solution:

```xml
<Project>
    <PropertyGroup>
        <TargetFramework>net8.0</TargetFramework>
        <ImplicitUsings>enable</ImplicitUsings>
        <Nullable>enable</Nullable>

        <!-- Configure code analysis. -->
        <AnalysisLevel>latest</AnalysisLevel>
        <AnalysisMode>Recommended</AnalysisMode>
        <TreatWarningsAsErrors Condition="'$(Configuration)' == 'Release'">true</TreatWarningsAsErrors>
        <CodeAnalysisTreatWarningsAsErrors Condition="'$(Configuration)' == 'Release'">true</CodeAnalysisTreatWarningsAsErrors>
        <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
    </PropertyGroup>
</Project>
```

## Features

- `TargetFramework` - Set the target .NET framework of all projects
- `ImplicitUsings` - use default usings provided by .NET to keep your usings cleaner
- `Nullable` - Reference types are non-nullably by default.  This helps to avoid null reference exceptions
- `AnalysisLevel` - Use the latest available code analysis rules. This ensures that the code is checked against the most up-to-date standards and practices.
- `AnalysisMode` - `Recommended` Enables most rules, but is slightly less aggressive than `All` (maximum)
- `TreatWarningsAsErrors` - Any warnings will be promoted to errors for `Release` builds
- `CodeAnalysisTreatWarningsAsErrors` - Code analysis warnings (CAXXXX) will be treated as errors
- `EnforceCodeStyleInBuild` - Code analysis rules (IDEXXXX) will show as warnings

## What is a `Directory.Build.props`

A Directory.Build.props file is an MSBuild file used in .NET projects to define common properties and configurations that apply to multiple projects within a directory tree. This file helps centralize the configuration and reduce redundancy by allowing you to specify settings that will be inherited by all projects under the directory where the file is located.
