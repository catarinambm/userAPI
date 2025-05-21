
## Etapa 1: Criar projeto spring e adicionar dependências
- Spring Boot: cria logo uma app com um main() que levanta o servidor "embutido" (Tomcat) -> na classe
  java/com.catarina.userapi/UserApiApplication.java
- Spring Web: para criar endpoints HTTP
- Spring Data JPA: para lidar com conexões à base de dados (usando ORM - para automaticamente conseguirmos guardar
- e ir buscar dados guardados na BD sem ter que recorrer a SQL. Mapeam-se objetos java para tabelas da base de dados)
- H2 Database: Base de dados leve que roda em memória (?)
- DevTools

## Etapa 2: Criar a entidade *User*
 Nesta etapa é criada a classe User.java, que representa um "user". 
 É usada a annotation @Entity para que o Spring/JPA consiga perceber que a classe 
 é uma tabela na base de dados.
 São criados atributos como "id", "name" e "email", que serão também colunas da tabela User
 na base de dados.
 
## Etapa 3: Criar o Repository (Interface)
 *UserRepository* é uma interface que faz uso da classe JpaRepository, que traz já vários métodos
 prontos a utilizar (findAll, save, deleteById, etc) - foi criada como interface porque apenas declaramos os métodos.
 O Spring implementa tudo isso automaticamente, 
 o que significa que não é necessário escrever SQL, basta chamar os métodos.
 
## Etapa 4: Criar o Service
 A classe *UserService* é onde colocamos a lógica da aplicação - ou seja, aquilo que
 acontece quando alguém faz um pedido à API.
 O uso da annotation @Service, faz com que o Spring reconheça esta classe como um Bean Service (injeção 
 de dependências). O serviço é responsável por receber pedidos do Controller e comunicar com o *UserRepository*
 para conseguir ir buscar ou guardar Users à base de dados.
 
## Etapa 5: Criar o Controller
O Controller é quem lida diretamente com as requisições HTTP (GET, POST, etc).
O uso da annotation @RestController permite identificar que esta classe vai responder 
pedidos HTTP e devolver JSONs como reposta. A @GetMapping permite definir que o método
responde a requisições GET /users. A @PostMapping permite definir que o método
responde a POST /users. 
Chama o *UserSerive* para realizar as ações necessárias para responder aos pedidos

## Etapa 6: Configurar o application.properties
Caminho: src/main/resources
blablabla