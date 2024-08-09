# Spring Boot Annotationen

Spring verwendet Dependency Injection, um Anwendungen zu konfigurieren und zu verbinden.

| Annotation       | Beschreibung | Class | Field | Constructor | Method | Parameter |
|------------------|--------------|:-----:|:-----:|:-----------:|:------:|:---------:|
| `@Configuration` |              |   ✔   |       |             |        |           |
| `@ComponentScan` |              |   ✔   |       |             |        |           |
| `@Import`        |              |   ✔   |       |             |        |           |
| `@Component`     |              |   ✔   |       |             |        |           |
| `@Service`       |              |   ✔   |       |             |        |           |
| `@Autowired`     |              |       |   ✔   |      ✔      |   ✔    |           |
| `@Bean`          |              |       |       |             |   ✔    |           |
| `@Lookup`        |              |       |       |             |   ✔    |           |
| `@Primary`       |              |   ✔   |       |             |   ✔    |           |
| `@Required`      |              |       |   ✔   |      ✔      |   ✔    |           |
| `@Value`         |              |       |   ✔   |      ✔      |   ✔    |           |
| `@DependsOn`     |              |   ✔   |       |             |   ✔    |           |
| `@Lazy`          |              |   ✔   |       |             |   ✔    |           |
| `@Scope`         |              |   ✔   |       |             |   ✔    |           |
| `@Profile`       |              |   ✔   |       |             |        |           |