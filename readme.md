# Overview
Testing Paket's ability to create NuGet packages for solutions that contains multiple libraries that represent depedent packages.

## Setup
PaketTesting.Client has a project reference to PaketTesting. Both have their own `paket.template` files. PaketTesting.Client's `paket.template` file specifies `include-referenced-projects true`

## Expected Behavior
Running `dotnet paket pack ..\nugets --build-config Debug` from the PaketTesting.Client directory should create a NuGet package that contains a dependency on PaketTesting.

## Actual Behavior
PaketTesting.Client package is created without dependencies

```
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<package xmlns="http://schemas.microsoft.com/packaging/2011/10/nuspec.xsd">
  <metadata>
    <id>PaketTesting.Client</id>
    <version>1.0.0</version>
    <title>PaketTesting.Client</title>
    <authors>Jarrod Johnson</authors>
    <description>Testing Paket project refernece nuget dependencies</description>
  </metadata>
</package>
```