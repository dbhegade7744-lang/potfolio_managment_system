package com.example.portfolio.entities;

import jakarta.persistence.*;
import java.util.List;

@Entity
@Table(name = "portfolios")
public class Portfolio {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @OneToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "client_id", nullable = false)
    private Client client;

    @OneToMany(mappedBy = "portfolio", cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    private List<PortfolioSecurity> holdings;

    public Portfolio() {}

    public Portfolio(Client client, List<PortfolioSecurity> holdings) {
        this.client = client;
        this.holdings = holdings;
    }

    // Getters and Setters
    public Long getId() { return id; }
    public Client getClient() { return client; }
    public void setClient(Client client) { this.client = client; }
    public List<PortfolioSecurity> getHoldings() { return holdings; }
    public void setHoldings(List<PortfolioSecurity> holdings) { this.holdings = holdings; }
}
