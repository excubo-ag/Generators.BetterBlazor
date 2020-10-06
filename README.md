
# Excubo.Generators.BetterBlazor

[![Nuget](https://img.shields.io/nuget/v/Excubo.Generators.BetterBlazor)](https://www.nuget.org/packages/Excubo.Generators.BetterBlazor/)
[![Nuget](https://img.shields.io/nuget/dt/Excubo.Generators.BetterBlazor)](https://www.nuget.org/packages/Excubo.Generators.BetterBlazor/)
[![GitHub](https://img.shields.io/github/license/excubo-ag/Generators.BetterBlazor)](https://github.com/excubo-ag/Generators.BetterBlazor)

This project aims at improving performance for blazor with source generators.

Blazor uses reflection to handle `[Parameter]`s of components. This is a source of inefficiency in the framework.
The `SetParametersAsync` generator overrides the default reflection-based implementation of `Task SetParametersAsync(ParameterView parameters)` by one
that is generated at compile time, similar to
[the recommendation by MS](https://github.com/dotnet/AspNetCore.Docs/blob/1e199f340780f407a685695e6c4d953f173fa891/aspnetcore/blazor/webassembly-performance-best-practices.md#implement-setparametersasync-manually)

## How to use

### 1. Install the nuget package Excubo.Generators.BetterBlazor

Excubo.Generators.BetterBlazor is distributed [via nuget.org](https://www.nuget.org/packages/Excubo.Generators.BetterBlazor/).
[![Nuget](https://img.shields.io/nuget/v/Excubo.Generators.BetterBlazor)](https://www.nuget.org/packages/Excubo.Generators.BetterBlazor/)

#### Package Manager:
```ps
Install-Package Excubo.Generators.BetterBlazor
```

#### .NET Cli:
```cmd
dotnet add package Excubo.Generators.BetterBlazor
```

#### Package Reference
```xml
<PackageReference Include="Excubo.Generators.BetterBlazor" />
```

### 2. Enable `GenerateSetParametersAsync` for all components

Add `@attribute [Excubo.Generators.BetterBlazor.GenerateSetParametersAsync]` to your `_Imports.razor` file. This enables the source generator on _all_ components.
As sometimes you might want to override the method yourself, you can opt-out of the source generator by adding `@attribute [Excubo.Generators.BetterBlazor.DoNotGenerateSetParametersAsync]` to a component.
