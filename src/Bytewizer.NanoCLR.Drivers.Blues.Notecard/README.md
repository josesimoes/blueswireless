# Blues Wireless for nanoFramework

## Getting Started
This <a href="https://www.nanoframework.net/">getting started guide</a> will walk you through the setup of your development machine. Here are the basic steps required to get you started.

### Install the nanoFramework extension for Visual Studio
Launch Visual Studio and install the nanoFramework extension.

### Uploading the firmware to the Adafruit Feather
Install nanoff (nano Firmware Flasher)
```Shell
dotnet tool install -g nanoff
```
Update the firmware of an ESP32 target connected to COM7.
```Shell
nanoff --serialport COM7 --update
```
Install packages from [NuGet](https://www.nuget.org/packagesq=bytewizer.nanoclr) using the Package Manager Console :
```powershell
PM> Install-Package NanoFramework.Hardware.Esp32
PM> Install-Package Bytewizer.NanoCLR.Drivers.Blues.Notecard
```

### Simple Example
```CSharp
class Program
{
    static void Main()
    {
        // Set i2cBus1 configuration for the Adafruit ESP32 HUZZAH
        Configuration.SetPinFunction(23, DeviceFunction.I2C1_DATA);
        Configuration.SetPinFunction(22, DeviceFunction.I2C1_CLOCK);

        // Create notecard controller I2cBus1 for Feather
        var notecard = new NotecardController(1);

        var request = new JsonRequest("card.voltage");

        var results = notecard.Request(request);
        Debug.WriteLine(results.Response);
    }
}
```

## NanoCLR Packages
Install release package from [NuGet](https://www.nuget.org/packagesq=bytewizer.nanoclr) or using the Package Manager Console :
```powershell
PM> Install-Package Bytewizer.NanoCLR.Drivers.Blues.Notecard
```