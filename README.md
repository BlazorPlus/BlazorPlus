# BlazorPlus
ASP.NET Core Blazor Server Session,Navigation,Dialog,Container,Controls,Components,FileUploader

This project is testing internally, More samples are being prepaired


## Samples

https://github.com/BlazorPlus/BlazorPlusDemo


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

3 - _Host.cshtml
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
  
  
