'''mermaid
graph TD
    %% Pengguna (Browser)
    subgraph Client["Pengguna (Browser)"]
        A[Next.js Frontend]
    end

    %% Server (Vercel/Node.js)
    subgraph Server["Server (Vercel/Node.js)"]
        B[Next.js Backend API Routes]
        C[Core Logic Layer (/lib)]
    end

    %% Infrastruktur & Layanan Pihak Ketiga
    subgraph Infra["Infrastruktur & Layanan Pihak Ketiga"]
        D[MongoDB Atlas]
        E[External AI Services]
        F[Vercel Blob Storage]
    end

    %% Arahkan alur utama
    A -->|HTTP Request (fetch)| B
    B -->|Memanggil Fungsi| C

    %% Frontend Details
    subgraph FrontendDetails["Frontend"]
        direction LR
        A1[Halaman & Layout (/app)]
        A2[Komponen UI (/components)]
        A3[State Management (React Context/Hooks)]
    end
    A1 --> A2 --> A3 --> A

    %% Backend API Routes
    subgraph BackendRoutes["Backend API Routes"]
        direction LR
        B1[Auth API (/api/auth)]
        B2[Fitur API (/api/quiz, /api/notebooks)]
        B3[Admin API (/api/admin)]
    end
    B1 --> B2 --> B3 --> B

    %% Core Logic Layer
    subgraph CoreLogic["Core Logic Layer"]
        direction TB
        C1[Models (Mongoose) (/lib/models)]
        C2[Logika Bisnis (/lib/services, /lib/quiz-gen)]
        C3[Utilitas & Auth (/lib/utils, /lib/auth)]
        C4[Konektor Database (/lib/database)]
    end
    C1 --> C2 --> C3 --> C4 --> C

    %% Koneksi eksternal
    C4 -->|Koneksi & Query| D
    C2 -->|API Call| E
    C2 -->|Upload/Download| F

    %% Styling
    style A fill:#D6EAF8,stroke:#3498DB
    style B fill:#D5F5E3,stroke:#2ECC71
    style C fill:#FADBD8,stroke:#E74C3C
    style D fill:#FCF3CF,stroke:#F1C40F
    style E fill:#E8DAEF,stroke:#8E44AD
    style F fill:#E8DAEF,stroke:#8E44AD
