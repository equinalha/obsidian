---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2024-05-04T09:45:00
Status: Not started
Description: ""
---
# JWT em Java

```java
// String utilizada como chave para assinatura do token
String segredo = "b8338e24f11f4692a95738fe2e893c2ab8338e24f11f46";
byte[] keyBytes = Decoders.BASE64.decode(segredo);
Key chavePrivada = Keys.hmacShaKeyFor(keyBytes);

// Header do Token
Map<String, Object> headers = new HashMap<String, Object>();
headers.put("typ", "JWT");

// Payload do Token
HashMap<String, String> claims = new HashMap<String, String>();
claims.put("iss", "Home Banking");
claims.put("aud", "Público");
claims.put("conta", "215598");
claims.put("nome", "Ana Karla");
claims.put("tipo", "Cliente");
claims.put("acesso", "Simples");
// Não há limites para o número de declarações, mas atente-se para não informar dados sigilosos, pois o token pode ser lido.

// Datas e prazos do Token
final Date dtCriacao = new Date();
// Expiração em 15 minutos
final Date dtExpiracao = new Date(dtCriacao.getTime() + 1000 * 60 * 15);

// Criação do Token
String jwtToken = Jwts
                .builder()
                .setHeader(headers)
                .setClaims(claims)
                .setSubject("Acesso Home Banking")
                .setIssuedAt(dtCriacao)
                .setExpiration(dtExpiracao)
                .signWith(chavePrivada).compact();
                
// Validação do Token
/*Caso o token não seja válido, exceções serão lançadas, ou porque a assinatura não foi validada, ou porque seu conteúdo foi adulterado, ou porque o token está expirado.
Se nenhuma exceção for lançada, significa que o token é válido e seus dados podem ser obtidos utilizando o objeto do tipo Jws<Claims>. Veja alguns exemplos:
*/
Jws<Claims> credencial = Jwts
                .parserBuilder()
                .setSigningKey(chavePrivada)
                .build().parseClaimsJws(jwtToken);

// Leitura do Token
Iterator<String> it = credencial.getBody().keySet().iterator();
while (it.hasNext()) {
        String chave = it.next();
        String valor = credencial.getBody().get(chave).toString();
        System.out.println(chave + " = " + valor);
}
```