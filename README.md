## Criando um projeto Spring boot do zero no IntelliJ

Ao abrir o IntelliJ clicar em Create New Project. Em Maven, no campo Project SDK escolher a opção 1.8 Oracle OpenJDK version 1.8.0_241.
No campo GroupId: inserir io.github.cleoconstantino

O mavem é um gerenciador de build para Java, pode adicionar plugins e dependências.

Pare criar um projeto em SringBoot deve-se adicionar um parent no pom.xml (parent é uma biblioteca que vai configurar todo o projeto em SringBoot).

Para adicionar o parent, deve-se entrar no site [https://mvnrepository.com/](https://mvnrepository.com/) e no campo localizar digite: spring boot starter parent. Copia e cola no arquivo pom.xml, o lugar de 'dependecy' -> digitar 'parent'.

Para trazer as funcionalidades mais básicas do SpringBoot devemos inserir o starter:

    <dependencies>  
		<dependency>
		     <groupId>org.springframework.boot</groupId>  
		     <artifactId>spring-boot-starter</artifactId>  
	    </dependency>
     </dependencies>

E temos que adicionar também o plugin do SpingBoot:

    <build>  
	     <plugins> 
		     <plugin> 
			     <groupId>org.springframework.boot</groupId>  
			     <artifactId>spring-boot-maven-plugin</artifactId>  
		     </plugin> 
	     </plugins>
     </build>

Dentro da pasta > Main > Java > New Java Class, criar: io.github.cleoconstantino.VendasApplication - a classe que vai inicializar a aplicação deve ter o sufixo Application.

Ao utilizar a anotação @SpringBootApplication a classe será reconhecida que vai iniciarlizar um projeto em SpringBoot.

A classe ficará no seguinte formato:

    package io.github.cleoconstantino;  
      
    import org.springframework.boot.SpringApplication;  
    import org.springframework.boot.autoconfigure.SpringBootApplication;  
      
    @SpringBootApplication  
    public class VendasApplication {  
      
        public static void main(String[] args) {  
        //run recebe dois parâmetros: a classe que vai iniciarlizar o projeto em SpringBoot e os argumentos.  
      SpringApplication.run(VendasApplication.class, args);  
      }  
    }


## Hello Word com Spring Boot

    package io.github.cleoconstantino;  
      
    import org.springframework.boot.SpringApplication;  
    import org.springframework.boot.autoconfigure.SpringBootApplication;  
    import org.springframework.web.bind.annotation.GetMapping;  
    import org.springframework.web.bind.annotation.RestController;  
      
    @SpringBootApplication  
    @RestController  
    public class VendasApplication {  
      
        @GetMapping("/hello")  
        public String helloWord(){  
            return "Hello Word";  
      };  
      
     public static void main(String[] args) {  
            //run recebe dois parâmetros: a classe que vai iniciarlizar o projeto em SpringBoot e os argumentos.  
      SpringApplication.run(VendasApplication.class, args);  
      }  
    }
No arquivo pom.xml deve injetar a dependencia abaixo:

    <dependency>  
	     <groupId>org.springframework.boot</groupId>  
	     <artifactId>spring-boot-starter-web</artifactId>  
    </dependency>

Para verificar oprojeto rodando: http://localhost:8080/hello

## Starters: Como funciona a mágica por trás do Spring Boot

 - spring-boot-starter-parent: tem as funcionalidades básicas do Spring Boot;
 - spring-boot-starter: básico para o Spring Boot rodar;
 - spring-boot-starter-web: básico para aplicações web;
