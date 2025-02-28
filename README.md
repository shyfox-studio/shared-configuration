<h1 align="center">
<img src="https://raw.githubusercontent.com/shyfox-studio/branding/51d21485b8b524893dd84a735f05d1bd154066f0/logos/org/shyfox.svg" alt="ShyFox Studio Logo" width="256" />
<br />
ShyFox Studio Shared Configuration
</h1>

<div align="center">

[![License: MIT](https://img.shields.io/badge/LICENSE-MIT-f8723d)](LICENSE)

</div>

This repository contains shared configuration used for all of the ShyFox Studio repositories.

This is designed to be installed as a git submodule at the root of any ShyFox Studio repository.  The ShyFox Studio repository needs to be setup so that it conforms to the following project structure:

```sh
├── .gitignore
├── license
├── solution.sln
├── readme.md
└── src
    └── project
       └── project.csproj
└── tests
    └── project.tests
        └── project.tests.csproj
```

Once the project is setup, add the shared configuration as a git submodule in the root directory of the MonoGame Community Toolkit repository.

```sh
git submodule add https://github.com/shyfox-studio/shared-configuration.git shared-configuration
```

Next create a new **Directory.Build.props** file at the root of the ShyFox Studio repository with the following content:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project>
    <PropertyGroup>
        <!-- This MUST be defined before importing props. -->
        <SolutionDirectory>$(MSBuildThisFileDirectory)</SolutionDirectory>
    </PropertyGroup>

    <!-- Import the shared global .props file -->
    <Import Project="$(MSBuildThisFileDirectory)shared-infrastructure\msbuild\Shared.Global.props" />
</Project>
```

Next, create a **Directory.Build.targets** file at the root of the ShyFox Studio repository with the following content:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project>
    <!-- Import the shared global .props file -->
    <Import Project="$(MSBuildThisFileDirectory)shared-infrastructure\msbuild\Shared.Global.targets"/>
</Project>
```
