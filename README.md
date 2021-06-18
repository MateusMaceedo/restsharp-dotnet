<h1 align="center">
<img src="https://api.nuget.org/v3-flatcontainer/restsharp/106.11.7/icon" width="67.5" height="67.5">
 <br>
 RestShap
</h1>

- [x] [Documentação Oficial](https://www.nuget.org/packages/RestSharp)
- [x] [Controladores de teste unitário](https://docs.microsoft.com/pt-br/aspnet/web-api/overview/testing-and-debugging/unit-testing-controllers-in-web-api) 

#### Aqui está um exemplo de um controlador cujas ações retornam HttpResponseMessage.

```
public class ProductsController : ApiController
{
    IProductRepository _repository;

    public ProductsController(IProductRepository repository)
    {
        _repository = repository;
    }

    public HttpResponseMessage Get(int id)
    {
        Product product = _repository.GetById(id);
        if (product == null)
        {
            return Request.CreateResponse(HttpStatusCode.NotFound);
        }
        return Request.CreateResponse(product);
    }

    public HttpResponseMessage Post(Product product)
    {
        _repository.Add(product);

        var response = Request.CreateResponse(HttpStatusCode.Created, product);
        string uri = Url.Link("DefaultApi", new { id = product.Id });
        response.Headers.Location = new Uri(uri);

        return response;
    }
}
```

<a href="https://www.linkedin.com/in/mateus-macedo-937a32163/">
 <img style="border-radius:50%" width="100px; "src="https://avatars.githubusercontent.com/u/63172367?s=460&u=11fd26ea8a7f5663d7707d7ef254e4f8bfca1b05&v=4"/>
 <p>Mateus Macedo</p>
</a>
