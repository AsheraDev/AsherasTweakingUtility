# AsherasTweakingUtility

Ashera's Tweaking Utility is a Windows desktop optimization and monitoring app built with WPF (.NET 8).  
It combines real-time system telemetry with one-click tweak controls and rollback-safe operations.

## What It Does

- Displays live system telemetry for:
  - CPU usage and speed
  - Memory usage
  - Disk usage
  - GPU usage
  - Ethernet upload/download throughput
  - CPU/GPU temperature view (with source selection)
- Provides a categorized tweak center (`General Tweaks`) with:
  - On/off toggle cards
  - live applied state
  - warnings where admin/system impact is higher
- Includes utility actions:
  - Analyze current system state
  - Apply gaming profile
  - Rollback profile changes
  - System restore point creation
  - startup/app/resource reports
- Includes controller polling profile management for supported devices.

## Project Structure

- `MainWindow.xaml` / `MainWindow.xaml.cs`: UI layout, navigation, telemetry refresh loop, interaction logic.
- `Services/OptimizerService.cs`: tweak execution, registry/service operations, reports, rollback state handling.
- `Models/`: state and card models used by the dashboard and tweak cards.
- `PercentageToArcConverter.cs`: circular gauge rendering converter.
- `package.ps1`: publish/build packaging script for distributable output.

## Tech Stack

- .NET 8
- WPF (XAML + C#)
- Windows registry + service control operations
- `System.Management` (WMI/perf data)

## Build And Run

From the project root:

```powershell
dotnet build .\WinOptApp.csproj
dotnet run --project .\WinOptApp.csproj
```

## Package (Portable EXE)

```powershell
powershell -ExecutionPolicy Bypass -File .\package.ps1
```

Output files are written under `dist/` (runtime-specific folder + timestamped executable).

## Downloads

- EXE: `downloads/AsherasTweakingUtility-win-x64-latest.exe`

## Notes

- Some tweaks require Administrator privileges.
- Always review tweak descriptions before applying changes.
- Rollback and restore functionality is included for safer iteration.
