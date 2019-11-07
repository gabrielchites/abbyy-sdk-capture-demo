# Upland Mobile Image Capture Demo

This demo is a showcase of how to call Upland Mobile Image Capture plugin (Abbyy) using a Xamarin bridge accessed in plain Javascript.

## Getting Started

For this demo to work you need to run it within Upland Mobile shell application. This requires the file `index.html` to be served from an HTTP server.

### Upland Mobile

Upland Mobile is a shell application made in Xamarin Forms. It can be found under `Upland\Mobile\Xamarin\Shell`.

### Running the demo within Upland Mobile

In order for you application to be available in Upland Mobile, it needs to be added on the Shell Admin application list. This list is usually managed on https://umprod.uplandsoftware.com/shell/ (production environment.)

For development purposes, one can run Shell Admin API locally. See the project under `Upland\Mobile\Admin\ShellAdmin.Core`. 

Another alternative is to simply hardcode the application list directly into Upland Mobile. For example, the `GetAppsInfoAsync` API call inside `ShellAdminService.cs` could return a static list containing your application:

```
    public async Task<IEnumerable<AppInfo>> GetAppsInfoAsync()
    {
      // Actual implementation is removed.

      // simply returns a static list with your application URL
      return await Task.FromResult(
          new[]
          {
              new AppInfo
              {
                  Caption = "Image Capture Demo",
                  Enabled = true,
                  Id = "a2cb0253-5fe7-2a43-b3a8-fd7fd9e9dbb2",
                  Url = "https://YOUR-URL-HERE",
                  LogoName = "some-logo.jpg",
                  Features = new []
                  {
                      new Feature{Id = "f364b737-bb24-42d9-92a5-285ec508d675", Name = PluginFeature.ImageCapture, Platform = Platform.Android},
                      new Feature{Id = "f364b737-bb24-42d9-92a5-285ec508d676", Name = PluginFeature.ImageCapture, Platform = Platform.iOS}
                  }
              },
          });
```

## Authors

* **Gabriel de Mello** - *Initial work* - gmello@uplandsoftware.com

