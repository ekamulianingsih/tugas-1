graph TD
    A[Customer Datang & Beli Produk di Toko Fisik] --> S(Sales/Spesialis Produk: Memberikan Konsultasi/Rekomendasi);
    S --> B{Pembayaran & Verifikasi};
    
    subgraph Alur Transaksi Inti
        B --> C(Kasir: Proses Transaksi & Input Data Penjualan ke POS);
        
        C --> D{Pengambilan Barang?};
        
        D -- Ambil Langsung (In-Store) --> E(Kasir: Serahkan Produk Langsung ke Customer);
        E --> Z[Transaksi Selesai & Customer Pulang];
        
        D -- Minta Kirim (Delivery) --> F(Kasir: Meneruskan Detail Kirim ke Logistik);
        
        F --> G(Logistik: Ambil Stok dari Inventaris & Siapkan Pengiriman);
        G --> H(Logistik: Pengemasan & Pengecekan Kualitas);
        H --> I(Logistik: Kirim Barang via Kurir/Ojol);
        I --> Z;
        
        C --> J(Sales: Mencatat Data Customer untuk Retensi Promosi);
    end

    subgraph Manajemen, Stok, & Dukungan
        G --> K(Staf Inventaris: Mencatat Pengurangan Stok & Status Ketersediaan);
        K -- Stok di bawah batas --> L(Manajer Toko: Keputusan Pembelian/Restock);
        L --> P(Manajer Toko: Order Barang ke Supplier);
        
        C --> M(Manajer Toko: Menerima Laporan Penjualan Harian dari POS);
        J --> N(Manajer Toko: Analisis Data & Strategi Promosi *Offline*/Retensi);
        
        O[Sales: Promosi Produk (Sosial Media/Event Toko)] --> O;
    end

    style A fill:#A5F6AB,stroke:#333,stroke-width:2px
    style Z fill:#6C9EEB,stroke:#333,stroke-width:2px
    style C fill:#FFE099,stroke:#333
    style G fill:#E0AFFF,stroke:#333
    style K fill:#CCCCFF,stroke:#333
    style M fill:#ADD8E6,stroke:#333
    style L fill:#ADD8E6,stroke:#333
    style N fill:#ADD8E6,stroke:#333
    style J fill:#FFB3B3,stroke:#333
    style O fill:#FFB3B3,stroke:#333
    style S fill:#FFB3B3,stroke:#333
    style P fill:#ADD8E6,stroke:#333
