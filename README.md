# BlazorPlus
ASP.NET Core Blazor Server Session,Navigation,Dialog,Container,Controls,Components,FileUploader

This project is testing internally, More samples are being prepaired


## Samples

live demo : http://demo.blazorplus.com/

demo code : https://github.com/BlazorPlus/BlazorPlusDemo

![Screenshot](https://github.com/BlazorPlus/BlazorPlusDemo/raw/master/demoscreenshots/s001.jpg)


## Installation : 

1 - add BlazorPlus.dll reference
download from this github repo , 
or here https://www.nuget.org/packages/BlazorPlus/

2 - Startup.cs
```
	services.AddHttpContextAccessor();
	services.AddScoped<BlazorPlus.BlazorSession>();
	endpoints.Map("/_blazorplus_handler", BlazorPlus.BlazorSession.ProcessRequestAsync);
```

3 - _Host.cshtml in head tag
```
	<script src="/_blazorplus_handler?action=script" type="text/javascript"></script>
```

4 - _Imports.razor
```
	@using BlazorPlus
```

5 - App.razor
```
	<BlazorContainer IsShared="true" />
```

6 - Index.razor
```
	<button @onclick="ShowHelloWorld">Hello World</button>
	@code{
		void ShowHelloWorld()
		{
			BlazorSession.Current.Alert("Greeting", "Hello World");
		}
	}
```
  
  Suggestion :
  ```
	 _Host.cshtml set App RenderMode to Server :
	@(await Html.RenderComponentAsync<App>(RenderMode.Server))
	or
	<component type="typeof(App)" render-mode="Server" />

	_Host.cshtml in head tag , for IE11
	@{
		string useragent = Request.Headers["User-Agent"].FirstOrDefault();
	}
	@if (useragent != null && (useragent.Contains("MSIE") || useragent.Contains("Trident")))
	{
		<script src="https://github.com/Daddoon/Blazor.Polyfill/releases/download/3.0.8/blazor.polyfill.min.js" type="text/javascript"></script>
	}
```