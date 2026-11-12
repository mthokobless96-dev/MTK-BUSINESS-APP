# MTK Business Manager for Windows

The Windows app is a desktop program with a bundled copy of the MTK business
manager. It opens without internet, keeps records in the Windows WebView2
profile on this PC, and stores app-password-encrypted records there. Use
**Print receipt / save PDF**, **Print customer report / save PDF**, or
**Print statement / save PDF** on a customer record, choose a filename, and
attach the PDF to a message. Exported JSON backups are not encrypted.

On first use, set an app password and save the recovery key somewhere safe.
Records stored here are separate from the phone app, APK, and Chrome PWA.
Export a JSON backup on one device and import it on the other to transfer
records.

## Run

Open `MTKBusinessManager.exe` and keep the accompanying `wwwroot` folder beside
it. No separate .NET install is needed. The Windows **Microsoft Edge WebView2
Runtime** must be installed; it is preinstalled on many Windows 10 and Windows
11 PCs.

## Build

Install the .NET 8 SDK and Microsoft Edge WebView2 Runtime, then run:

```powershell
dotnet publish .\MTKBusinessManager.Windows.csproj -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -p:IncludeNativeLibrariesForSelfExtract=true -o "$HOME\Documents\MTK Business Manager PC"
```

The single-file executable and its bundled `wwwroot` app files are published to
that folder. The WebView2 runtime itself is provided by Windows and is not
included in the app.
