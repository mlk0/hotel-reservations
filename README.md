
# Contributing

[Sample HotelReservation app from Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/intro-to-containers/5-exercise-create-custom-docker-image)

[Target Frameworks in SDK-style projects](https://learn.microsoft.com/en-us/dotnet/standard/frameworks)

# Disabled Endpoint Routing

In ASP.NET Core 3.0 and later versions, Endpoint Routing was introduced as a new way to handle routing requests.
Endpoint Routing is more flexible and efficient than the previous approach, which used UseMvc and IRouter.
When you migrate from ASP.NET Core 2.2 to 3.0 or later, you’ll encounter this warning because UseMvc is not compatible with Endpoint Routing.
Solution: To resolve this issue, you have a few options: a. Replace UseMvc or UseSignalR with UseEndpoints:
In your Startup.cs file, modify the Configure method as follows:
C#
```
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseStaticFiles();
    app.UseRouting();
    app.UseCors();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute("default", "{controller=Home}/{action=Index}");
    });
}
```
 
This approach migrates your routing configuration to use UseEndpoints instead of UseMvc.