# BlazorPlus
ASP.NET Core Blazor Server/Client/WASM Side Session,Modal Dialog,Controls,Components,File Upload

Single dll , light-weight (about 200KB) ,

The components collection allow you show modal dialog with ESC key support , and BACK button for MOBILE

And also allow you to program classic mode stateful control tree like jQuery with C# code

## Samples

server-side live demo : http://demo.blazorplus.com/

client-side WASM demo : http://wasmdemo.blazorplus.com/

demo code : https://github.com/BlazorPlus/BlazorPlusDemo

## Advanced Demo

BlazorLinuxAdmin : https://github.com/BlazorPlus/BlazorLinuxAdmin

![Screenshot](https://github.com/BlazorPlus/BlazorPlusDemo/raw/master/demoscreenshots/s001.jpg)



## Installation server-side : 

1 - add BlazorPlus.dll reference , Nuget or download from github

2 - Startup.cs
```
in ConfigureServices :
	services.AddHttpContextAccessor();
	services.AddScoped<BlazorPlus.BlazorSession>();
in app.UseEndpoints :
	endpoints.Map("/_blazorplus_handler", BlazorPlus.BlazorSession.ProcessRequestAsync);
```

3 - _Host.cshtml
```
in <head> :
	<script src="/_blazorplus_handler?action=script" type="text/javascript"></script>
```

4 - _Imports.razor
```
	@using BlazorPlus
```

5 - App.razor
```
before RouteView : 
	<BlazorContainer IsShared="true" />
```

Now test it in Index.razor: 
```
	<button @onclick="ShowHelloWorld">Hello World</button>
	@code{
		void ShowHelloWorld()
		{
			BlazorSession.Current.Alert("Greeting", "Hello World");
		}
	}
```



## Installation WebAssembly


1 - add BlazorPlus.dll reference , Nuget or download from github

2 - Program.cs
```
	BlazorPlus.BlazorSession.InitForWasm(builder.Services);
	builder.Services.AddScoped<BlazorPlus.BlazorSession>();
```

3 - _Imports.razor
```
	@using BlazorPlus
```

4 - MainLayout.razor
```
in front code :
	@inject BlazorSession bses
	<BlazorContainer IsShared="true"/>
```

Now test it in Index.razor: 
```
	<button @onclick="ShowHelloWorld">Hello World</button>
	@code{
		void ShowHelloWorld()
		{
			BlazorSession.Current.Alert("Greeting", "Hello World");
		}
	}
```