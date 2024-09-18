## Table of Contents
- [Model](#model)
- [Repository](#repository)
- [Service](#service)
- [Controller](#controller)
- [Mapper Optional](#mapper-optional)

## Model
model usually have :
- relationship anotation: @OneToMany, @ManyToOne, @OneToOne, @ManyToMany
- join : @JoinColumn >  @JoinColumn(name = "company_id")
- manage json so it doesnt keep looping : @JsonBackReference , @JsonManagedReference
```java 
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
@Table(name = "idols")
public class Idol {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "idol_name", nullable = false)
    private String name;
    private String company;
    // Constructors
    public Idol() {}
    public Idol(String name, String company) {
        this.name = name;
        this.company = company;
    }
    // Getters and Setters after that   
}
```

## Repository
In this we going to use JPA Repository dependencies

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface IdolRepository extends JpaRepository<Idol, Long> {
    // Custom query methods can be defined here if needed ->  List<Idol> findIdolsByCompanyCustom(String company);
}


//teh in custome repository you can write method for findIdol by company
// in IdolRepoCustom you can  add this code 
    @PersistenceContext
    private EntityManager entityManager;

    @Override
    public List<Idol> findIdolsByCompanyCustom(String company) {
        String query = "SELECT i FROM Idol i WHERE i.company = ?1"; // Note the ?1 here Using JPQL
        TypedQuery<Idol> typedQuery = entityManager.createQuery(query, Idol.class);
        typedQuery.setParameter(1, company); // Positional parameter index as an integer
        return typedQuery.getResultList();
    }
// end code for custom repo class 
```

## Service
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;
import java.util.Optional;

@Service
public class IdolService {
    @Autowired
    private IdolRepository idolRepository;

    // Get all idols
    public List<Idol> getAllIdols() {
        return idolRepository.findAll();
    }

    // Get an idol by ID
    public Optional<Idol> getIdolById(Long id) {
        return idolRepository.findById(id);
    }

    // Add a new idol
    public Idol addIdol(Idol idol) {
        return idolRepository.save(idol);
    }

    // Update an idol
    public Idol updateIdol(Long id, Idol idolDetails) {
        return idolRepository.findById(id).map(idol -> {
            idol.setName(idolDetails.getName());
            idol.setCompany(idolDetails.getCompany());
            return idolRepository.save(idol);
        }).orElseThrow(() -> new RuntimeException("Idol not found"));
    }

    // Delete an idol
    public void deleteIdol(Long id) {
        idolRepository.deleteById(id);
    }
}
```

## Controller
The annotation for controoler this is function for the maper 
- @GetMapping : Retrieve data from server.(like select for sql)
- @PostMapping : Submit new data to server. (like insert)
- @PutMapping : Update existing data completely.(like update)
- @DeleteMapping :  Remove data from server. (like delete)

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import java.util.List;

@RestController
@RequestMapping("/idols")
public class IdolController {
    @Autowired
    private IdolService idolService;
    // Get all idols
    @GetMapping
    public List<Idol> getAllIdols() {
        return idolService.getAllIdols();
    }
    // Get an idol by ID
    @GetMapping("/{id}")
    public ResponseEntity<Idol> getIdolById(@PathVariable Long id) {
        return idolService.getIdolById(id)
                .map(ResponseEntity::ok)
                .orElse(ResponseEntity.notFound().build());
    }
    // Add a new idol
    @PostMapping
    public Idol addIdol(@RequestBody Idol idol) {
        return idolService.addIdol(idol);
    }
    // Update an idol
    @PutMapping("/{id}")
    public ResponseEntity<Idol> updateIdol(@PathVariable Long id, @RequestBody Idol idolDetails) {
        return ResponseEntity.ok(idolService.updateIdol(id, idolDetails));
    }
    // Delete an idol
    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteIdol(@PathVariable Long id) {
        idolService.deleteIdol(id);
        return ResponseEntity.noContent().build();
    }
}
```

## Mapper Optional
this class usually creating identical obj as model but it doesnt have ORM. cause it's function as request body in controller
```java
public class IdolMapper {
    public static IdolDto toDto(Idol idol) {
        IdolDto dto = new IdolDto();
        dto.setId(idol.getId());
        dto.setName(idol.getName());
        dto.setCompany(idol.getCompany());
        return dto;
    }
    public static Idol toEntity(IdolDto dto) {
        Idol idol = new Idol();
        idol.setName(dto.getName());
        idol.setCompany(dto.getCompany());
        return idol;
    }
}
```
