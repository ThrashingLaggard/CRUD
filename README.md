# CRUD+

A flexible and extensible C# CRUD repository framework, designed for rapid development of data-driven applications with [Entity Framework Core](https://learn.microsoft.com/en-us/ef/core/).

## Key Feature

**Highly generic and composable CRUD repository pattern with rich extension points for Entity Framework Core.**  
This project allows you to quickly create repositories for any entity type, leveraging a clean interface structure and asynchronous patterns. You can easily extend, customize, and add advanced data access logic.

## Highlights

- Generic repository (`CrudRepository<T>`) for any EF Core entity
- Interface-driven design:  
  - `IBaseCrud<T>` for standard CRUD  
  - `IBaseCrudExtensions<T>` for advanced extensions  
  - `IEfCoreCrudExtensions<T>` for EF Core-specific operations  
  - `IExtendedCrud<T>` as an all-in-one interface
- Returns `EntityEntry` for advanced EF Core scenarios
- Built-in support for paging (`Pageineering`)
- Integrated async logging
- Clean separation of concerns and easy testability
- Ready for use as a NuGet package for your own projects

## Prerequisites

- [.NET 8.0 SDK](https://dotnet.microsoft.com/download)
- [Entity Framework Core](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/)



## Usage Example

```csharp
// Example: Register and use the generic repository for your entity
public class User { /* ... */ }

// In your DI setup:
services.AddScoped<IExtendedCrud<User>, CrudRepository<User>>();

// Usage in your service:
public class UserService
{
    private readonly IExtendedCrud<User> _repo;
    public UserService(IExtendedCrud<User> repo) { _repo = repo; }

    public async Task CreateUser(User user)
    {
        await _repo.Create(user);
    }
}
```

## Project Structure



## Roadmap

- Publish as a NuGet package
- Add more extension points (e.g. soft deletes, auditing)
- Unit and integration tests
- Documentation and usage samples

## License

MIT (see [LICENSE.txt](LICENSE.txt))

## Author

- [ThrashingLaggard](https://github.com/ThrashingLaggard)

---

