## Results
Successfully verified that `MetadataUpdateHandler` is invoked on hot reload with:
- VS Windows 17.7.0 Preview 3.0
- .NET 8 Preview 6
- Windows App SDK 1.4 preview 1 (so without MAUI)

## Steps to Repro:
1. Debug the app (unpackaged)
2. Edit and save code `myButton_Click` in `MainWindow.xaml.cs` (enable hot reload on save)
3. After VS status bar shows `Code changes were applied successfully` the title of the app window updates to `Hot Reload!`

## How this was built:

I followed the guidance in https://learn.microsoft.com/en-us/visualstudio/debugger/hot-reload-metadataupdatehandler to add `HotReloadService.cs` to a new WinUI3 in Desktop Blank App (updated to .NET 8 and Windows App SDK 1.4), and instead of the MAUI initialize and rebuild code from that guidance I added the code within `#if DEBUG` directives in `App.xaml.cs`



