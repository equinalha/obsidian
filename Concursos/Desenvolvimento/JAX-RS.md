---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-14T14:38:00
Owner:
  - Eduardo Quinalha
---
[https://www.logicbig.com/tutorials/java-ee-tutorial/jax-rs/getting-started-with-jax-rs.html](https://www.logicbig.com/tutorials/java-ee-tutorial/jax-rs/getting-started-with-jax-rs.html)

JAX-RS, que significa Java API for RESTful Web Services, é uma especificação Java que facilita a criação de serviços web RESTful.

Com base nas anotações e configurações, o JAX-RS cuidará da serialização e desserialização dos dados, permitindo que você foque na lógica de negócios do serviço web. É importante observar que você precisa de um contêiner JAX-RS, como Apache CXF ou Jersey, para implantar e executar esses serviços web RESTful em um servidor de aplicação Java EE ou em um ambiente compatível com JAX-RS.

```java
import javax.ws.rs.*;
import javax.ws.rs.core.*;

@Path("/exemplo")
public class ExemploResource {

    @GET
    @Produces(MediaType.TEXT_PLAIN)
    public String getMensagem() {
        return "Isso é um exemplo de serviço web RESTful em Java usando JAX-RS.";
    }

    @GET
    @Path("/{param}")
    @Produces(MediaType.TEXT_PLAIN)
    public String exibirParametro(@PathParam("param") String parametro) {
        return "Parâmetro passado: " + parametro;
    }

    @POST
    @Path("/enviar")
    @Consumes(MediaType.TEXT_PLAIN)
    public Response enviarMensagem(String mensagem) {
        // Realiza alguma lógica com a mensagem recebida
        return Response.status(201).entity("Mensagem recebida: " + mensagem).build();
    }
}
```
