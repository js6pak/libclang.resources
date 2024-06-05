# libclang.resources

[![NuGet](https://img.shields.io/nuget/v/js6pak.libclang.resources?label=NuGet&logo=NuGet)](https://www.nuget.org/packages/js6pak.libclang.resources)

Clang builtin headers packaged for use with [ClangSharp](https://github.com/dotnet/ClangSharp)

Based on [ClangSharp.Pathogen.ClangResources](https://github.com/MochiLibraries/ClangSharp.Pathogen/tree/b774e5cec0efb8f08f6ca8dbb5e6ee35666cf60b/ClangSharp.Pathogen.ClangResources)

## Usage
1. Reference `js6pak.libclang.resources` using the same version as `libclang`
2. Add the equivalent of
   ```cs
   var resourceDirectoryPath = Path.Combine(AppContext.BaseDirectory, "clang-resources");
   if (!Directory.Exists(resourceDirectoryPath) || !File.Exists(Path.Combine(resourceDirectoryPath, "include", "stddef.h")))
   {
       throw new DirectoryNotFoundException("Clang resources directory not found.");
   }

   CommandLineArguments.Add("-resource-dir");
   CommandLineArguments.Add(resourceDirectoryPath);
   ```
   to your `CXTranslationUnit` usage.

## Building

1. Follow [ClangSharp native build instructions](https://github.com/dotnet/ClangSharp#building-native)
2. Build `libclang.resources` with `LlvmSourceRoot` set to the directory where you cloned `llvm-project`
