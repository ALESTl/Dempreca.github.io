<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dempreca.ve - Catálogo de Productos</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #FF7F00;
            --primary-dark: #E67300;
            --primary-light: #FFA64D;
            --secondary: #FFB366;
            --accent: #FFE0CC;
            --text: #333333;
            --text-light: #666666;
            --background: #FFF9F2;
            --white: #FFFFFF;
            --shadow: rgba(0, 0, 0, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background);
            color: var(--text);
            line-height: 1.6;
        }

        /* HEADER RESPONSIVE */
        header {
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
            color: white;
            box-shadow: 0 4px 12px var(--shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            text-decoration: none;
            color: white;
        }

        .logo h1 {
            font-size: 1.8rem;
            margin: 0;
        }

        .logo-icon {
            font-size: 2rem;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-menu li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
            padding: 0.5rem 0;
            position: relative;
        }

        .nav-menu li a:hover {
            color: var(--accent);
        }

        .nav-menu li a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background-color: var(--accent);
            transition: width 0.3s ease;
        }

        .nav-menu li a:hover::after {
            width: 100%;
        }

        .hamburger {
            display: none;
            flex-direction: column;
            cursor: pointer;
            gap: 4px;
        }

        .hamburger span {
            width: 25px;
            height: 3px;
            background-color: white;
            transition: all 0.3s ease;
        }

        /* NUEVAS MEJORAS PARA EL CATÁLOGO */
        
        /* Barra de búsqueda */
        .search-container {
            width: 90%;
            max-width: 1200px;
            margin: 1rem auto;
            display: flex;
            justify-content: center;
        }
        
        .search-box {
            display: flex;
            width: 100%;
            max-width: 500px;
        }
        
        .search-input {
            flex: 1;
            padding: 0.8rem 1rem;
            border: 2px solid var(--primary);
            border-radius: 30px 0 0 30px;
            font-size: 1rem;
            outline: none;
        }
        
        .search-button {
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 0 30px 30px 0;
            padding: 0 1.5rem;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        
        .search-button:hover {
            background-color: var(--primary-dark);
        }
        
        /* Controles de vista */
        .view-controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin: 1.5rem auto;
            width: 90%;
            max-width: 1200px;
            flex-wrap: wrap;
            gap: 1rem;
        }
        
        .sort-options {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .sort-select {
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            background-color: white;
        }
        
        .view-toggle {
            display: flex;
            gap: 0.5rem;
        }
        
        .view-btn {
            background: white;
            border: 1px solid #ddd;
            padding: 0.5rem;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .view-btn.active {
            background-color: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        
        /* Indicador de resultados */
        .results-info {
            margin: 1rem auto;
            width: 90%;
            max-width: 1200px;
            color: var(--text-light);
        }
        
        /* Breadcrumb */
        .breadcrumb {
            width: 90%;
            max-width: 1200px;
            margin: 1rem auto;
            font-size: 0.9rem;
        }
        
        .breadcrumb a {
            color: var(--primary);
            text-decoration: none;
        }
        
        .breadcrumb a:hover {
            text-decoration: underline;
        }
        
        /* Productos en lista (vista alternativa) */
        .products-list {
            display: none;
            flex-direction: column;
            gap: 1rem;
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .product-list-item {
            display: flex;
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 2px 10px var(--shadow);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        
        .product-list-item:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px var(--shadow);
        }
        
        .list-image {
            width: 200px;
            height: 150px;
            object-fit: cover;
        }
        
        .list-info {
            padding: 1.5rem;
            flex: 1;
        }
        
        /* Paginación */
        .pagination {
            display: flex;
            justify-content: center;
            margin: 2rem 0;
            gap: 0.5rem;
        }
        
        .page-btn {
            padding: 0.5rem 1rem;
            border: 1px solid #ddd;
            background-color: white;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .page-btn.active {
            background-color: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        
        .page-btn:hover:not(.active) {
            background-color: #f5f5f5;
        }
        
        /* Botón flotante WhatsApp */
        .whatsapp-float {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #25D366;
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            z-index: 999;
            transition: all 0.3s ease;
            text-decoration: none;
        }
        
        .whatsapp-float:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.3);
        }
        
        /* Botón volver arriba */
        .back-to-top {
            position: fixed;
            bottom: 90px;
            right: 20px;
            background-color: var(--primary);
            color: white;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            z-index: 999;
            cursor: pointer;
            transition: all 0.3s ease;
            opacity: 0;
            visibility: hidden;
        }
        
        .back-to-top.show {
            opacity: 1;
            visibility: visible;
        }
        
        .back-to-top:hover {
            background-color: var(--primary-dark);
            transform: translateY(-3px);
        }
        
        /* Etiquetas de producto */
        .product-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: var(--primary);
            color: white;
            padding: 0.3rem 0.7rem;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: 600;
            z-index: 2;
        }
        
        .product-card {
            position: relative;
        }
        
        /* Filtros avanzados */
        .advanced-filters {
            width: 90%;
            max-width: 1200px;
            margin: 1rem auto;
            background-color: white;
            padding: 1rem;
            border-radius: 10px;
            box-shadow: 0 2px 10px var(--shadow);
            display: none;
        }
        
        .filter-toggle {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            cursor: pointer;
            color: var(--primary);
            margin-bottom: 1rem;
        }
        
        .filter-options {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 1rem;
        }
        
        .filter-group {
            margin-bottom: 1rem;
        }
        
        .filter-group h4 {
            margin-bottom: 0.5rem;
            color: var(--text);
        }
        
        .filter-checkbox {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 0.3rem;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }

            .nav-menu {
                position: fixed;
                top: 70px;
                right: -100%;
                width: 80%;
                height: calc(100vh - 70px);
                background: linear-gradient(135deg, var(--primary-dark), var(--primary));
                flex-direction: column;
                align-items: center;
                justify-content: flex-start;
                padding-top: 2rem;
                gap: 2rem;
                transition: right 0.5s ease;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            }

            .nav-menu.active {
                right: 0;
            }

            .hamburger.active span:nth-child(1) {
                transform: rotate(45deg) translate(5px, 5px);
            }

            .hamburger.active span:nth-child(2) {
                opacity: 0;
            }

            .hamburger.active span:nth-child(3) {
                transform: rotate(-45deg) translate(7px, -6px);
            }
            
            .product-list-item {
                flex-direction: column;
            }
            
            .list-image {
                width: 100%;
                height: 200px;
            }
            
            .view-controls {
                flex-direction: column;
                align-items: flex-start;
            }
        }

        @media (max-width: 480px) {
            .logo h1 {
                font-size: 1.5rem;
            }
            
            .logo-icon {
                font-size: 1.7rem;
            }
            
            .filter-options {
                grid-template-columns: 1fr;
            }
        }

        /* Resto del CSS existente */
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem 0;
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            text-align: center;
            margin-top: 1rem;
        }

        .filters {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1rem;
            margin: 2rem 0;
        }

        .filter-btn {
            background-color: var(--white);
            border: 2px solid var(--primary);
            color: var(--primary);
            padding: 0.7rem 1.5rem;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .filter-btn:hover, .filter-btn.active {
            background-color: var(--primary);
            color: white;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background-color: var(--white);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 15px var(--shadow);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px var(--shadow);
        }

        .product-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .product-info {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            color: var(--primary-dark);
        }

        .product-type {
            display: inline-block;
            background-color: var(--accent);
            color: var(--primary-dark);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
            margin-bottom: 1rem;
        }

        .product-description {
            color: var(--text-light);
            font-size: 0.9rem;
            margin-bottom: 1rem;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }

        .view-details {
            color: var(--primary);
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            overflow-y: auto;
            padding: 2rem 0;
        }

        .modal-content {
            background-color: var(--white);
            width: 90%;
            max-width: 800px;
            margin: 2rem auto;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            animation: modalFade 0.3s ease;
        }

        @keyframes modalFade {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 1.8rem;
            color: white;
            cursor: pointer;
            background-color: rgba(0, 0, 0, 0.5);
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1001;
        }

        .modal-header {
            position: relative;
        }

        .modal-images-container {
            position: relative;
            overflow: hidden;
        }

        .modal-images {
            display: flex;
            transition: transform 0.3s ease;
        }

        .modal-image {
            width: 100%;
            height: 350px;
            object-fit: cover;
            flex-shrink: 0;
        }

        /* Flechas de navegación */
        .modal-nav {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(255, 255, 255, 0.7);
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 1.2rem;
            color: var(--primary-dark);
            transition: all 0.3s ease;
            z-index: 10;
        }

        .modal-nav:hover {
            background-color: rgba(255, 255, 255, 0.9);
        }

        .modal-nav.prev {
            left: 15px;
        }

        .modal-nav.next {
            right: 15px;
        }

        /* Indicadores de imagen */
        .modal-indicators {
            position: absolute;
            bottom: 15px;
            left: 0;
            right: 0;
            display: flex;
            justify-content: center;
            gap: 8px;
            z-index: 10;
        }

        .modal-indicator {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.5);
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .modal-indicator.active {
            background-color: var(--white);
            transform: scale(1.2);
        }

        .modal-body {
            padding: 2rem;
        }

        .modal-title {
            font-size: 1.8rem;
            color: var(--primary-dark);
            margin-bottom: 0.5rem;
        }

        .modal-type {
            display: inline-block;
            background-color: var(--accent);
            color: var(--primary-dark);
            padding: 0.4rem 1rem;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 1.5rem;
        }

        .modal-description {
            color: var(--text);
            margin-bottom: 1.5rem;
            line-height: 1.7;
        }

        .contact-info {
            background-color: var(--accent);
            padding: 1.5rem;
            border-radius: 10px;
            margin-top: 1.5rem;
        }

        .contact-title {
            font-size: 1.2rem;
            margin-bottom: 1rem;
            color: var(--primary-dark);
        }

        .contact-details {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 0.7rem;
        }

        .contact-icon {
            color: var(--primary);
            font-size: 1.2rem;
        }

        footer {
            background-color: var(--primary-dark);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }

        @media (max-width: 768px) {
            .products-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
                gap: 1.5rem;
            }
            
            .modal-image {
                height: 250px;
            }
            
            .modal-body {
                padding: 1.5rem;
            }
            
            .modal-nav {
                width: 35px;
                height: 35px;
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="header-container">
            <a href="#" class="logo">
                <i class="fas fa-boxes logo-icon"></i>
                <h1>DEMPRECA</h1>
            </a>
            
            <nav>
                <ul class="nav-menu">
                    <li><a href="#inicio">Inicio</a></li>
                    <li><a href="#productos" class="active">Productos</a></li>
                    <li><a href="#nosotros">Nosotros</a></li>
                    <li><a href="#contacto">Contacto</a></li>
                </ul>
                
                <div class="hamburger">
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
            </nav>
        </div>
    </header>

    <!-- Breadcrumb -->
    <div class="breadcrumb">
        <a href="#">Inicio</a> > <a href="#">Productos</a> > <span>Catálogo</span>
    </div>

    <!-- Barra de búsqueda -->
    <div class="search-container">
        <div class="search-box">
            <input type="text" class="search-input" placeholder="Buscar productos...">
            <button class="search-button"><i class="fas fa-search"></i></button>
        </div>
    </div>

    <!-- Filtros avanzados -->
    <div class="advanced-filters" id="advancedFilters">
        <div class="filter-toggle" id="filterToggle">
            <i class="fas fa-filter"></i>
            <span>Filtros avanzados</span>
        </div>
        <div class="filter-options">
            <div class="filter-group">
                <h4>Precio</h4>
                <div class="filter-checkbox">
                    <input type="checkbox" id="price1">
                    <label for="price1">Menos de $50</label>
                </div>
                <div class="filter-checkbox">
                    <input type="checkbox" id="price2">
                    <label for="price2">$50 - $100</label>
                </div>
                <div class="filter-checkbox">
                    <input type="checkbox" id="price3">
                    <label for="price3">Más de $100</label>
                </div>
            </div>
            <div class="filter-group">
                <h4>Disponibilidad</h4>
                <div class="filter-checkbox">
                    <input type="checkbox" id="stock1">
                    <label for="stock1">En stock</label>
                </div>
                <div class="filter-checkbox">
                    <input type="checkbox" id="stock2">
                    <label for="stock2">Próximamente</label>
                </div>
            </div>
            <div class="filter-group">
                <h4>Características</h4>
                <div class="filter-checkbox">
                    <input type="checkbox" id="feature1">
                    <label for="feature1">Novedad</label>
                </div>
                <div class="filter-checkbox">
                    <input type="checkbox" id="feature2">
                    <label for="feature2">Más vendido</label>
                </div>
                <div class="filter-checkbox">
                    <input type="checkbox" id="feature3">
                    <label for="feature3">Oferta especial</label>
                </div>
            </div>
        </div>
    </div>

    <div class="container">
        <p class="subtitle">Descubre nuestra amplia gama de productos de calidad</p>
        
        <!-- Controles de vista -->
        <div class="view-controls">
            <div class="results-info">
                Mostrando <strong>6</strong> de <strong>12</strong> productos
            </div>
            <div class="sort-options">
                <label for="sort">Ordenar por:</label>
                <select id="sort" class="sort-select">
                    <option value="popular">Más populares</option>
                    <option value="newest">Más recientes</option>
                    <option value="price-low">Precio: menor a mayor</option>
                    <option value="price-high">Precio: mayor a menor</option>
                </select>
            </div>
            <div class="view-toggle">
                <button class="view-btn active" id="gridView"><i class="fas fa-th"></i></button>
                <button class="view-btn" id="listView"><i class="fas fa-list"></i></button>
            </div>
        </div>
        
        <div class="filters">
            <button class="filter-btn active" data-filter="all">Todos</button>
            <button class="filter-btn" data-filter="tipo1">Tipo 1</button>
            <button class="filter-btn" data-filter="tipo2">Tipo 2</button>
            <button class="filter-btn" data-filter="tipo3">Tipo 3</button>
            <button class="filter-btn" id="showFiltersBtn"><i class="fas fa-filter"></i> Más filtros</button>
        </div>

        <!-- Vista en cuadrícula (por defecto) -->
        <div class="products-grid" id="productsGrid">
            <!-- Producto 1 - Tipo 1 -->
            <div class="product-card" data-type="tipo1">
                <span class="product-badge">Nuevo</span>
                <img src="./img_files/102.jpg" alt="Producto 1" class="product-image">
                <div class="product-info">
                    <h3 class="product-title">Producto Tipo 1 - A</h3>
                    <span class="product-type">Tipo 1</span>
                    <p class="product-description">Descripción breve del producto. Este es un producto de alta calidad con características especiales que lo hacen único en el mercado.</p>
                    <span class="view-details">Ver detalles <i class="fas fa-arrow-right"></i></span>
                </div>
            </div>

            <!-- Producto 2 - Tipo 1 -->
            <div class="product-card" data-type="tipo1">
                <span class="product-badge">Oferta</span>
                <img src="./img_files/101.jpg" alt="Producto 2" class="product-image">
                <div class="product-info">
                    <h3 class="product-title">Producto Tipo 1 - B</h3>
                    <span class="product-type">Tipo 1</span>
                    <p class="product-description">Descripción breve del producto. Este es un producto de alta calidad con características especiales que lo hacen único en el mercado.</p>
                    <span class="view-details">Ver detalles <i class="fas fa-arrow-right"></i></span>
                </div>
            </div>

            <!-- Producto 3 - Tipo 2 -->
            <div class="product-card" data-type="tipo2">
                <span class="product-badge">Popular</span>
                <img src="./img_files/103.jpg" alt="Producto 3" class="product-image">
                <div class="product-info">
                    <h3 class="product-title">Producto Tipo 2 - A</h3>
                    <span class="product-type">Tipo 2</span>
                    <p class="product-description">Descripción breve del producto. Este es un producto de alta calidad con características especiales que lo hacen único en el mercado.</p>
                    <span class="view-details">Ver detalles <i class="fas fa-arrow-right"></i></span>
                </div>
            </div>

            <!-- Producto 4 - Tipo 2 -->
            <div class="product-card" data-type="tipo2">
                <img src="./img_files/101.jpg" alt="Producto 4" class="product-image">
                <div class="product-info">
                    <h3 class="product-title">Producto Tipo 2 - B</h3>
                    <span class="product-type">Tipo 2</span>
                    <p class="product-description">Descripción breve del producto. Este es un producto de alta calidad con características especiales que lo hacen único en el mercado.</p>
                    <span class="view-details">Ver detalles <i class="fas fa-arrow-right"></i></span>
                </div>
            </div>

            <!-- Producto 5 - Tipo 3 -->
            <div class="product-card" data-type="tipo3">
                <span class="product-badge">Nuevo</span>
                <img src="./img_files/102.jpg" alt="Producto 5" class="product-image">
                <div class="product-info">
                    <h3 class="product-title">Producto Tipo 3 - A</h3>
                    <span class="product-type">Tipo 3</span>
                    <p class="product-description">Descripción breve del producto. Este es un producto de alta calidad con características especiales que lo hacen único en el mercado.</p>
                    <span class="view-details">Ver detalles <i class="fas fa-arrow-right"></i></span>
                </div>
            </div>

            <!-- Producto 6 - Tipo 3 -->
            <div class="product-card" data-type="tipo3">
                <img src="./img_files/103.jpg" alt="Producto 6" class="product-image">
                <div class="product-info">
                    <h3 class="product-title">Producto Tipo 3 - B</h3>
                    <span class="product-type">Tipo 3</span>
                    <p class="product-description">Descripción breve del producto. Este es un producto de alta calidad con características especiales que lo hacen único en el mercado.</p>
                    <span class="view-details">Ver detalles <i class="fas fa-arrow-right"></i></span>
                </div>
            </div>
        </div>

        <!-- Vista en lista (alternativa) -->
        <div class="products-list" id="productsList">
            <!-- Los mismos productos pero en formato lista -->
            <!-- Se generan dinámicamente con JavaScript -->
        </div>

        <!-- Paginación -->
        <div class="pagination">
            <button class="page-btn"><i class="fas fa-chevron-left"></i></button>
            <button class="page-btn active">1</button>
            <button class="page-btn">2</button>
            <button class="page-btn">3</button>
            <button class="page-btn"><i class="fas fa-chevron-right"></i></button>
        </div>
    </div>

    <!-- Botón flotante de WhatsApp -->
    <a href="https://wa.me/1234567890" class="whatsapp-float" target="_blank">
        <i class="fab fa-whatsapp"></i>
    </a>

    <!-- Botón volver arriba -->
    <div class="back-to-top" id="backToTop">
        <i class="fas fa-chevron-up"></i>
    </div>

    <!-- Modal para detalles del producto -->
    <div class="modal" id="productModal">
        <div class="close-modal">&times;</div>
        <div class="modal-content">
            <div class="modal-header">
                <div class="modal-images-container">
                    <div class="modal-images">
                        <!-- Las imágenes se cargarán dinámicamente con JavaScript -->
                    </div>
                    <!-- Flechas de navegación -->
                    <button class="modal-nav prev" id="prevImage">
                        <i class="fas fa-chevron-left"></i>
                    </button>
                    <button class="modal-nav next" id="nextImage">
                        <i class="fas fa-chevron-right"></i>
                    </button>
                    <!-- Indicadores de imagen -->
                    <div class="modal-indicators" id="imageIndicators">
                        <!-- Los indicadores se generarán dinámicamente con JavaScript -->
                    </div>
                </div>
            </div>
            <div class="modal-body">
                <h2 class="modal-title" id="modalProductTitle">Título del Producto</h2>
                <span class="modal-type" id="modalProductType">Tipo</span>
                <p class="modal-description" id="modalProductDescription">Descripción completa del producto.</p>
                
                <div class="contact-info">
                    <h3 class="contact-title">¿Te interesa este producto?</h3>
                    <div class="contact-details">
                        <div class="contact-item">
                            <i class="fas fa-phone contact-icon"></i>
                            <span>+1 234 567 890</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-envelope contact-icon"></i>
                            <span>contacto@empresa.com</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-map-marker-alt contact-icon"></i>
                            <span>Dirección de la empresa</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <p>&copy; 2025 Todos los derechos reservados.</p>
        </div>
    </footer>
    
    <script>
        // Menú hamburguesa
        const hamburger = document.querySelector('.hamburger');
        const navMenu = document.querySelector('.nav-menu');
        
        hamburger.addEventListener('click', () => {
            hamburger.classList.toggle('active');
            navMenu.classList.toggle('active');
        });
        
        // Cerrar menú al hacer clic en un enlace
        document.querySelectorAll('.nav-menu li a').forEach(n => n.addEventListener('click', () => {
            hamburger.classList.remove('active');
            navMenu.classList.remove('active');
        }));

        // NUEVAS FUNCIONALIDADES PARA EL CATÁLOGO
        
        // Alternar entre vista de cuadrícula y lista
        const gridViewBtn = document.getElementById('gridView');
        const listViewBtn = document.getElementById('listView');
        const productsGrid = document.getElementById('productsGrid');
        const productsList = document.getElementById('productsList');
        
        gridViewBtn.addEventListener('click', () => {
            gridViewBtn.classList.add('active');
            listViewBtn.classList.remove('active');
            productsGrid.style.display = 'grid';
            productsList.style.display = 'none';
        });
        
        listViewBtn.addEventListener('click', () => {
            listViewBtn.classList.add('active');
            gridViewBtn.classList.remove('active');
            productsGrid.style.display = 'none';
            productsList.style.display = 'flex';
            
            // Generar vista de lista si no existe
            if (productsList.children.length === 0) {
                generateListView();
            }
        });
        
        // Generar vista de lista
        function generateListView() {
            const productCards = document.querySelectorAll('.product-card');
            
            productCards.forEach(card => {
                const listItem = document.createElement('div');
                listItem.className = 'product-list-item';
                
                const image = card.querySelector('.product-image').cloneNode(true);
                image.className = 'list-image';
                
                const info = document.createElement('div
