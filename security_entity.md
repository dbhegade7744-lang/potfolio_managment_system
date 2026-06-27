package com.example.portfolio.entities;

import jakarta.persistence.*;

@Entity
@Table(name = "securities")
public class Security {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false)
    private String name;

    @Column(nullable = false)
    private String category; // e.g., Stock, Bond, ETF

    @Column(nullable = false, unique = true)
    private String ticker;

    public Security() {}

    public Security(String name, String category, String ticker) {
        this.name = name;
        this.category = category;
        this.ticker = ticker;
    }

    // Getters and Setters
    public Long getId() { return id; }
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
    public String getCategory() { return category; }
    public void setCategory(String category) { this.category = category; }
    public String getTicker() { return ticker; }
    public void setTicker(String ticker) { this.ticker = ticker; }
}
