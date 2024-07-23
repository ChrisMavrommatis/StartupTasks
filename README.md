# StartupTasks

`ChrisMavrommatis.StartupTasks` is a .NET library that enables you to define and execute a set of tasks during the startup phase of your ASP.NET Core application, just before the web host begins running.

## Installation

Install the package via NuGet Package Manager
```bash
Install-Package ChrisMavrommatis.StartupTasks
```

Or via .NET CLI:
```bash
dotnet add package ChrisMavrommatis.StartupTasks
```

## Usage

1. Create a startup task by inheriting from `IStartupTask`
   ```csharp
   public class SampleStartupTask : IStartupTask
   {
     public async Task ExecuteAsync(CancellationToken cancellationToken = default)
     {
       // Your startup task logic here
     }
   }
   ```
   
2. Register the task using the `AddStartupTask` extension method
   ```csharp
   // Other service registrations
   
   services.AddStartupTask<SampleStartupTask>();
   
   // Other service registrations
   ```

3. Use the `RunStartupTasksAsync` extension method in your startup class just before you call the `RunAsync`. 
   ```csharp
   public static async Task Main(string[] args)
   {
       /*
       ... Other Code
       */
       await app.RunStartupTasksAsync();
       await app.RunAsync();
   }
   ```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

