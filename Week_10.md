## Guidance

Answer the following questions considering the learning outcomes for

- [Week 010](https://learn.foundersandcoders.com/course/syllabus/developer/week10-project05-DOTNET-intro/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

> **[Learning outcomes...]**

#### Wrote models in C# to work with entity framework

```csharp
public class User
{
    public int Id { get; set; }
    public required string Name { get; set; }
    public required string Email { get; set; }
    public required string Hash { get; set; }

    [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
    public DateTime? CreatedAt { get; set; } = DateTime.UtcNow;
}
```

#### Wrote Minimal API endpoints

```csharp
  app.MapPost(
            "/colours",
            async (Colour colour, ColourContext context) =>
            {
                context.Colours.Add(colour);

                await context.SaveChangesAsync();

                return Results.Created($"/colours/{colour.Id}", colour);
            }
        );
```

#### Fully linked our React frontend to our database through a Minimal API and Entity Framework ORM!!!

#### Used Swagger to document and test our endpoints

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

#### The level of abstration in .NET and C# is confusing

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddDbContext<ColourContext>(options =>
    options.UseNpgsql(builder.Configuration.GetConnectionString("DefaultConnection"))
);
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

builder.Services.AddCors(options =>
{
    options.AddPolicy(
        "AllowFrontend",
        policy =>
        {
            policy
                .WithOrigins("http://localhost:5174")
                .AllowAnyHeader()
                .AllowAnyMethod();
        }
    );
});`
```

#### Struggled with installing PostgreSQL but hope to do more on that next week!

## Feedback (For CF's)

> [**Course Facilitator name**]

Alexander

> [*What went well*]

Clear implementation of C# models and Minimal API endpoints. Successfully connected React frontend with .NET backend and documented with Swagger.

> [*Even better if*]

Explain what specifically confuses you about .NET's abstraction level - the code example shows CORS and DB setup but doesn't highlight your struggles. Detail what PostgreSQL installation issues you faced for better learning documentation.
