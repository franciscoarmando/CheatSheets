
# Net Core MVC on VsCode #

## Create Api ##

```
dotnet new webapi
dotnet build
dotnet dev-certs https --trust
dotnet watch run 
```
### Models ## 

```
@Models
dotnet ef 
dotnet ef dbcontext scaffold "Data Source=IRIE1\SQLEXPRESS02;Initial Catalog=Todos;Integrated Security=True" Microsoft.EntityFrameworkCore.SqlServer -o Models
dotnet ef dbcontext scaffold "Server=(localdb)\mssqllocaldb;
							Database=Blogging;Trusted_Connection=True;"
							Microsoft.EntityFrameworkCore.SqlServer 
							-o Models
@settingsJson						
 "ConnectionStrings": {"TodosContext" :"Data Source=IRIE1\\SQLEXPRESS02;Initial Catalog=Todos;Integrated Security=True"}
 

@startup.cs							
using Todos.Models;
using Microsoft.EntityFrameworkCore;
  services.AddDbContext<TodosContext>(options => options.UseSqlServer(Configuration.GetConnectionString("TodosContext")));
  services.AddDbContext<TodosContext>(options => options.UseSqlServer("Data Source=IRIE1\\SQLEXPRESS02;Initial Catalog=Todos;Integrated Security=True"));

dotnet tool install -g dotnet-aspnet-codegenerator
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design --version 2.1.9
dotnet aspnet-codegenerator controller -name TodosController -m Todo.Models.Todos -dc Todo.Models.TodosContext -outDir Controllers -udl

dotnet aspnet-codegenerator controller 
-name TodosController 
-m Todo.Models.Todos 
-dc Todo.Models.TodosContext 
-outDir Controllers 
-udl 

```

## HANDE MADE CONTROLLER ##
### Expose urls ### 

```
[Route("api/[controller]")]
    [ApiController]
    public class TodosController : ControllerBase
    {
     private readonly TodosContext _context;
        // GET api/values
        [HttpGet]
        public ActionResult <List<Todos>> GetAll()
        {
            using (var _context = new TodosContext())
            {
                var todos = _context.Todos.ToList();
                 return todos;
            }
        }
          // GET api/todos/5
        [HttpGet("{id}")]
        public ActionResult<Todos> Get(int id)
        {
            using (var context = new TodosContext())
            {
                var todo = context.Todos
                    .Single(t => t.Id == id);
                return todo;
            }
        }
        // POST api/values
        [HttpPost]
        public void Post([FromBody] string value)
        {
            using (var context = new TodosContext ())
            {
                var todo = new Todos { 
                        Title="",
                        Duedate = DateTime.Now, 
                        Mstatus = false
                        };
                context.Todos.Add(todo);
                context.SaveChanges();
            }
        }
        // PUT api/values/5
        [HttpPut("{id}")]
        public void Put(int id, [FromBody] string value)
        {
            using (var context = new TodosContext())
            {
                var todo = context.Todos.Find(id);
                todo.Duedate = DateTime.Now;
                todo.Mstatus = true;
                context.SaveChanges();
            }
        }
        // DELETE api/values/5
        [HttpDelete("{id}")]
        public void Delete(int id)
        {
           using (var context = new TodosContext())
            {
                var todo = context.Todos.Find(id);
                context.Todos.Remove(todo);
                context.SaveChanges();
            }
        }
```