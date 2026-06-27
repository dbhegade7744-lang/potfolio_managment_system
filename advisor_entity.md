package com.example.portfolio.entities;

import jakarta.persistence.*;
import java.util.List;

@Entity
@Table(name = "advisors")
public class Advisor {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String name;

    @Column(nullable = false, unique = true)
    private String email;

    @Column(name = "employee_code")
    private String employeeCode;

    @OneToMany(mappedBy = "advisor", cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    private List<Client> clients;

    // No-arg constructor required by JPA
    public Advisor() {}

    // All-args constructor (excluding ID if generated automatically)
    public Advisor(String name, String email, String employeeCode, List<Client> clients) {
        this.name = name;
        this.email = email;
        this.employeeCode = employeeCode;
        this.clients = clients;
    }

    // Getters and Setters
    public Long getId() { return id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }
    public String getEmployeeCode() { return employeeCode; }
    public void setEmployeeCode(String employeeCode) { this.employeeCode = employeeCode; }
    public List<Client> getClients() { return clients; }
    public void setClients(List<Client> clients) { this.clients = clients; }
}
