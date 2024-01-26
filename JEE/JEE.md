# JEE Exam Preparation

## the four layers of spring framework:

### couche de présentation / web :
 
cette couche est responsable de la gestion des requêtes et des réponses HTTP. Elle contient les composants suivants :

  - les contrôleurs (controllers) : ils sont responsables de la gestion des requêtes HTTP et de la production des réponses HTTP. Ils sont les composants les plus importants de cette couche.

  - les vues (views) : elles sont responsables de la production des réponses HTTP. Elles sont généralement des pages HTML, mais elles peuvent être aussi des fichiers JSON, XML, PDF, etc.

  - les gestionnaires d'exceptions (exception handlers) : ils sont responsables de la gestion des exceptions qui peuvent être levées par les contrôleurs. Ils sont utilisés pour produire des réponses HTTP appropriées.

### couche métier (business) :

cette couche est responsable de la logique métier de l'application. Elle contient les composants suivants :

- les services (services) : ils sont responsables de la logique métier de l'application. Ils sont généralement appelés par les contrôleurs.
  
- les implémentations des services (service implementations) : ils sont responsables de l'implémentation des services. Ils sont généralement appelés par les services.

### couche d'accès aux données (data access) :

cette couche est responsable de l'accès aux données. Elle contient les composants suivants :

- les repositories (repositories) : ils sont responsables de l'accès aux données. Ils sont généralement appelés par les services.

- Data Transfer Objects (DTOs) : ils sont utilisés pour transférer des données entre les couches de l'application.

- les entités (entities) : elles sont utilisées pour mapper les données de la base de données aux objets Java.

    
### couche de base de données :

cette couche est responsable de la persistance des données. Elle contient les composants suivants :

- la base de données (database) : elle est responsable de la persistance des données.

- le système de gestion de base de données (database management system) : il est responsable de la gestion de la base de données.


## Spring Boot Annotations:
  ### Entity :
  - @Entity : pour définir une entité JPA.
  - @Table : pour définir le nom de la table de l'entité.
  - @Id : pour définir la clé primaire de l'entité.
  - @GeneratedValue : pour définir la stratégie de génération de la clé primaire de l'entité.
  - @Column : pour définir le nom de la colonne de l'attribut de l'entité.
  - @Transient : pour définir un attribut de l'entité qui n'est pas persistant.
  - @OneToOne : pour définir une relation un-à-un entre deux entités.
  - @OneToMany : pour définir une relation un-à-plusieurs entre deux entités.
  - @ManyToOne : pour définir une relation plusieurs-à-un entre deux entités.
  - @ManyToMany : pour définir une relation plusieurs-à-plusieurs entre deux entités.
  - @Autowired : pour injecter une dépendance.
  - @AllArgsConstructor : pour générer un constructeur avec un paramètre pour chaque attribut de la classe.
  - @NoArgsConstructor : pour générer un constructeur sans paramètre.
  - @Data : pour générer les méthodes equals(), hashCode(), toString(), getters et setters.
  - @Builder : pour générer un constructeur avec un paramètre pour chaque attribut de la classe.


  ### Repository JPA :

  - @Repository : pour définir un repository JPA.
  - @Transactional : pour définir une transaction.

  ### Service :

  - @Service : pour définir un service.
  - @Transactional : pour définir une transaction.
  - @Autowired : pour injecter une dépendance.
  
  ### Controller :
  
  #### Rest Controller :

  - @RestController : pour définir un contrôleur REST.

  - @GetMapping : pour définir une méthode qui gère les requêtes HTTP GET.

  - @PostMapping : pour définir une méthode qui gère les requêtes HTTP POST.

  - @PutMapping : pour définir une méthode qui gère les requêtes HTTP PUT.

  - @DeleteMapping : pour définir une méthode qui gère les requêtes HTTP DELETE.

  - @PatchMapping : pour définir une méthode qui gère les requêtes HTTP PATCH.

  - @RequestBody : pour définir un paramètre de méthode qui doit être lié au corps de la requête HTTP.

  - @PathVariable : pour définir un paramètre de méthode qui doit être lié à une variable de chemin.

  - @RequestParam : pour définir un paramètre de méthode qui doit être lié à un paramètre de requête.

  - @RequestHeader : pour définir un paramètre de méthode qui doit être lié à un en-tête de requête.

exemple methods :
```java
@GetMapping("/users")
public List<User> getUsers() {
    return userService.getUsers();
}

@GetMapping("/users/{id}")
public User getUser(@PathVariable Long id) {
    return userService.getUser(id);
}

@PostMapping("/users")
public User addUser(@RequestBody User user) {
    return userService.addUser(user);
}

@PutMapping("/users/{id}")

public User updateUser(@PathVariable Long id, @RequestBody User user) {
    return userService.updateUser(id, user);
}

@DeleteMapping("/users/{id}")

public void deleteUser(@PathVariable Long id) {
    userService.deleteUser(id);
}
```


#### SOAP Controller :

  - @Component : pour définir un composant Spring.
  - @WebService : pour définir un contrôleur SOAP.
  - @WebMethod : pour définir une méthode qui gère les requêtes SOAP.
  - @WebParam : pour définir un paramètre de méthode qui doit être lié à un paramètre de requête SOAP.

exemple methods :

```java
@WebService
@Component
public class UserSoapController {

    @Autowired
    private UserService userService;

    @WebMethod
    public List<User> getUsers() {
        return userService.getUsers();
    }

    @WebMethod
    public User getUser(@WebParam(name = "id") Long id) {
        return userService.getUser(id);
    }

    @WebMethod
    public User addUser(@WebParam(name = "user") User user) {
        return userService.addUser(user);
    }

    @WebMethod
    public User updateUser(@WebParam(name = "id") Long id, @WebParam(name = "user") User user) {
        return userService.updateUser(id, user);
    }

    @WebMethod
    public void deleteUser(@WebParam(name = "id") Long id) {
        userService.deleteUser(id);
    }
}
```

#### GraphQL Controller :

  - @Controller : pour définir un contrôleur Spring MVC.
  - @QueryMapping : pour définir une méthode qui gère les requêtes GraphQL.
  - @MutationMapping : pour définir une méthode qui gère les mutations GraphQL.
  - @Argument : pour définir un paramètre de méthode qui doit être lié à un argument GraphQL.

exemple methods :
  
  ```java
@Controller
public class UserGraphQLController {

    @Autowired
    private UserService userService;

    @QueryMapping
    public List<User> getUsers() {
        return userService.getUsers();
    }

    @QueryMapping
    public User getUser(@Argument Long id) {
        return userService.getUser(id);
    }

    @MutationMapping
    public User addUser(@Argument User user) {
        return userService.addUser(user);
    }

    @MutationMapping
    public User updateUser(@Argument Long id, @Argument User user) {
        return userService.updateUser(id, user);
    }

    @MutationMapping
    public void deleteUser(@Argument Long id) {
        userService.deleteUser(id);
    }
}
```

## Kafka :

### Producer :

  - @EnableKafka : pour activer le support de Kafka.
  - @Configuration : pour définir une classe de configuration.
  - @Bean : pour définir un bean Spring.
  - KafkaTemplate : pour envoyer des messages à Kafka.
  - ProducerFactory : pour créer des instances de KafkaProducer.
  - Map : pour définir les propriétés du producteur.
  - StringSerializer : pour sérialiser les clés et les valeurs des messages.
  - KafkaProducer : pour envoyer des messages à Kafka.
  - ProducerRecord : pour définir un message à envoyer à Kafka.

exemple :
```java
@EnableKafka
@Configuration
public class KafkaProducerConfig {

    @Bean
    public KafkaTemplate<String, String> kafkaTemplate() {
        return new KafkaTemplate<>(producerFactory());
    }

    @Bean
    public ProducerFactory<String, String> producerFactory() {
        return new DefaultKafkaProducerFactory<>(producerConfigs());
    }

    @Bean
    public Map<String, Object> producerConfigs() {
        Map<String, Object> properties = new HashMap<>();
        properties.put(ProducerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
        properties.put(ProducerConfig.KEY_SERIALIZER_CLASS_CONFIG, StringSerializer.class);
        properties.put(ProducerConfig.VALUE_SERIALIZER_CLASS_CONFIG, StringSerializer.class);
        return properties;
    }
}
```

### Consumer :

  - @EnableKafka : pour activer le support de Kafka.
  - @Configuration : pour définir une classe de configuration.
  - @Bean : pour définir un bean Spring.
  - KafkaListener : pour définir une méthode qui écoute les messages de Kafka.
  - ConsumerFactory : pour créer des instances de KafkaConsumer.
  - Map : pour définir les propriétés du consommateur.
  - StringDeserializer : pour désérialiser les clés et les valeurs des messages.
  - KafkaConsumer : pour recevoir des messages de Kafka.
  - ConsumerRecord : pour définir un message reçu de Kafka.



exemple :
```java
@EnableKafka
@Configuration
public class KafkaConsumerConfig {

    @Bean
    public ConsumerFactory<String, String> consumerFactory() {
        return new DefaultKafkaConsumerFactory<>(consumerConfigs());
    }

    @Bean
    public Map<String, Object> consumerConfigs() {
        Map<String, Object> properties = new HashMap<>();
        properties.put(ConsumerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
        properties.put(ConsumerConfig.KEY_DESERIALIZER_CLASS_CONFIG, StringDeserializer.class);
        properties.put(ConsumerConfig.VALUE_DESERIALIZER_CLASS_CONFIG, StringDeserializer.class);
        properties.put(ConsumerConfig.GROUP_ID_CONFIG, "group_id");
        return properties;
    }

    @Bean
    public ConcurrentKafkaListenerContainerFactory<String, String> kafkaListenerContainerFactory() {
        ConcurrentKafkaListenerContainerFactory<String, String> factory = new ConcurrentKafkaListenerContainerFactory<>();
        factory.setConsumerFactory(consumerFactory());
        return factory;
    }
}
```

