# MVC #

1.- Visual Studio
2 .- net Framework 
3 api 2 ef

## Mvc Cheat Sheet ## 
### cors ### 

```
ng
Install-Package Microsoft.AspNet.WebApi.Cors 
2 using System.Web.Http;
namespace WebService
{
    public static class WebApiConfig
    {
        public static void Register(HttpConfiguration config)
        {
            // New code
            
            //CORS
            EnableCorsAttribute cors = new EnableCorsAttribute("*", "*", "*");
            config.EnableCors(cors);


```

```

using System.Net.Http;
using System.Web.Http;
using System.Web.Http.Cors;

namespace WebService.Controllers
{
    [EnableCors(origins: "*", headers: "*", methods: "*")]
    public class TestController : ApiController
```
