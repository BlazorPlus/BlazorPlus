# BlazorPlus

BlazorPlus is a component library that helps you to write code more directly and easily, 
Single dll , light-weight (about 260KB dll) , 
Blazor Server/Client/WASM Side Session,Modal Dialog,Controls,File Upload,TreeView

![Screenshot](https://github.com/BlazorPlus/BlazorPlus/raw/master/images/s002.jpg)


## Samples

live demo : http://demo.blazorplus.com/

demo code : https://github.com/BlazorPlus/BlazorPlusDemo

BlazorLinuxAdmin : https://github.com/BlazorPlus/BlazorLinuxAdmin


## Nuget name : BlazorPlus https://www.nuget.org/packages/BlazorPlus/

## Installation server-side : 

1 - Startup.cs
```
in ConfigureServices :
	services.AddHttpContextAccessor();
	services.AddScoped<BlazorPlus.BlazorSession>();
in app.UseEndpoints : (before Fallback)
	endpoints.Map("/_blazorplus_handler", BlazorPlus.BlazorSession.ProcessRequestAsync);
```

2 - _Host.cshtml
```
in <head> :
	<script src="/_blazorplus_handler?action=script" type="text/javascript"></script>
```

3 - _Imports.razor
```
	@using BlazorPlus
```

4 - App.razor
```
at the front:
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

1 - Program.cs
```
	BlazorPlus.BlazorSession.InitForWasm(builder.Services);
	builder.Services.AddScoped<BlazorPlus.BlazorSession>();
```

2 - _Imports.razor
```
	@using BlazorPlus
```

3 - MainLayout.razor
```
at the front:
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