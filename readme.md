Install-Package MySql.Data.EntityFrameworkCore -Version 8.0.15
[MySql for Visual Studio Download](https://dev.mysql.com/downloads/file/?id=507212)

Make migrations to MySql
Add-Migration InitialCreate

Make migrate
Update-Database

add in Startup.cs
```csharp=
using Pomelo.EntityFrameworkCore.MySql.Infrastructure;
public class Startup
{         
    public void ConfigureServices(IServiceCollection services)
        {
           
	     services.AddDbContext<MvcMovieContext>(options =>
            {
                options.UseMySql(Configuration.GetConnectionString("MvcMovieContext"), mysqlOptions =>
                {
                    mysqlOptions.ServerVersion(new Version(8, 0, 21), ServerType.MySql);
                });
            });
           
           
        }
}
```

dotnet Mysql dependencies
Install-Package Pomelo.EntityFrameworkCore.MySql -Version 5.0.2
Install-Package MySql.Data.EntityFramework -Version 8.0.27
Install-Package MySql.Data -Version 8.0.27